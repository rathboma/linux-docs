# This is for the Framework Laptop 16 (AMD Ryzen™ 7040 Series) ONLY.

## This will:

- Getting  your laptop fully updated.
- Allow both CPU and platform drivers to be simultaneously active.
- Enable improved fractional scaling support Fedora's GNOME environment using Wayland.
- Enabling tap to click on the touchpad.

&nbsp;
&nbsp;
&nbsp;

### Step 1 Updating your software packages

- Browse to the horizontal line in the upper left corner, click to open it.
- Type out the word terminal, click to open it.
- Copy the code below in the gray box, right click/paste it into the terminal window.
- Then press the enter key, user password, enter key, **reboot.**


```
sudo dnf upgrade
```
> **TIP:** You can use the little clipboard icon to the right of the code to copy to your clipboard.


**Reboot**

&nbsp;
&nbsp;
&nbsp;

### Step 2 - Allow both CPU and platform drivers to be simultaneously active

> ***TIP:*** [This will eventually appear](https://koji.fedoraproject.org/koji/taskinfo?taskID=110470581) in during standard upgrades, but to [get this addressed immediately](https://gitlab.freedesktop.org/upower/power-profiles-daemon/-/merge_requests/127), follow the steps below. This reflects the contents of this [AMD maintained Copr repo](https://copr.fedorainfracloud.org/coprs/mariolimonciello/power-profiles-daemon/).

- Browse to the horizontal line in the upper left corner, click to open it.
- Type out the word terminal, click to open it.
- Copy the code below in the gray box, right click/paste it into the terminal window.
- Then press the enter key, user password, enter key, **reboot.**

```
sudo dnf copr enable mariolimonciello/power-profiles-daemon && sudo dnf update
```

- Enter your password when promoted.
- **Reboot**
- Verify you have the updated power-profiles-daemon from the terminal.

```
rpm -q power-profiles-daemon
```

- You should see power-profiles-daemon-0.13-6 or greater.


### Step 3 - If you want to enable fractional scaling on Wayland:

- Browse to the horizontal line in the upper left corner, click to open it.
- Type out the word terminal, click to open it.
- Left click and drag to highlight and copy the code below in the gray box, right click/paste it into the terminal window.
- Then press the enter key.
- Browse to the horizontal line in the upper left corner, click to open it.
- Type out the word Displays.
- Look for "Scale", set it to your preference, click Apply.


```
gsettings set org.gnome.mutter experimental-features "['scale-monitor-framebuffer']"
```
> **TIP:** You can use the little clipboard icon to the right of the code to copy to your clipboard.

&nbsp;
&nbsp;
&nbsp;
### Step 4 -  If you want to enable "tap-to-click" on the touchpad:

- Browse to the horizontal line in the upper left corner, click to open it.
- Type out the word mouse, look for Mouse and Touchpad, click to open it.
- Click the touchpad option at the top.
- Under "Clicking", select Tap to Click and enable it.
  
&nbsp;
&nbsp;
&nbsp;
## Optional and *only if needed* - current AMD Ryzen 7040 Series workarounds to common issues

### To prevent graphical artifacts from appearing:
(Note, this workaround may be unneeded as it is difficult to reproduce, however, if you find you're experiencing [the issue described here](https://bugzilla.redhat.com/show_bug.cgi?id=2247154#c3), you can implement this boot parameter)


- Browse to the horizontal line in the upper left corner, click to open it.
- Type out the word terminal, click to open it.
- Then press the enter key, user password, enter key.

```
sudo grubby --update-kernel=ALL --args="amdgpu.sg_display=0"
```
> **TIP:** You can use the little clipboard icon to the right of the code to copy to your clipboard.


**Reboot**

## Addtionally, we recommend the following as well if you are experiencing graphical artifacts from appearing

- Please follow the steps outlined in this guide:
  https://knowledgebase.frame.work/allocate-additional-ram-to-igpu-framework-laptop-13-amd-ryzen-7040-series-BkpPUPQa

&nbsp;
&nbsp;
&nbsp;
