---
title: "Installing Ubuntu 18.04.2 on Dell 8930 with dual boot win10"
date: 2019-02-21
forum: Installation &amp; Upgrades
---

### Post by dankegel on 2019-02-21
Hi!  I've been installing Ubuntu 18.04 on Dell machines for a while now.  My recipe for installing 18.04.2 on a Dell 8930 while preserving the Win10 installation as dual boot works pretty slick... if you don't screw up.  Right now I'm looking at a system that won't boot because I didn't react fast enough during the BIOS MOK prompt after doing 'sudo ubuntu-drivers autoinstall' and rebooting.  (It starts to boot, but hangs at "Stopping User Manager for UID 121...".  BIOS doesn't have an obvious way to trigger the MOK management prompt.  Using recovery mode to uninstall the nvidia driver lets you recover and try again.)

Here's the recipe:

First, get a USB key with the installer:

- Download ubuntu iso (preferably desktop)
- Run Startup Disk Creator (aka usb-creator-kde or usb-creator-gtk) to format a USB drive with that iso

To preserve the windows installation:

- unplug network cable
- let windows boot all the way
- when it asks which wifi network, or whether to update, just skip the step.  (You have to do this at three different times.)
- shrink the startup drive (e.g. if it's a 512 GB SSD, resize it to 220 GB) by running ```
diskmgmt.msc
```
- disable fastboot via Control Panel / Power Options / Choose what buttons do / Enable Unavailable Options / uncheck Turn On Fast Startup
- turn on safe mode via ```
bcdedit /set safeboot minimal
```
- power off
- power on, and press F2 to get into BIOS
- Ubuntu doesn't like RAID mode in BIOS, so switch to AHCI mode in BIOS; see
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en) and
[https://www.dell.com/support/article/us/en/04/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/04/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)
- power off
- power on, boot to windows, and turn off safe mode via ```
bcdedit /deletevalue safeboot
```
- power off

Then, to install Ubuntu:

- plug network cable in
- insert that USB drive into the new machine and power it on
- press F12 to pick startup device, and choose USB drive
- the installer should launch
- When it asks about installing updates or drivers during install, say no
- After it installs, reboot
- If you have an nvidia card, do ```
sudo ubuntu-drivers autoinstall
```
- When it prompts for a password to protect the machine-owner key, pick one, reboot, and enter it when bios's MOK management thingy prompts you.
- If you don't respond in 10 seconds, it'll reboot, and hang on boot.  To recover, boot into recovery mode, do e.g. 'dpkg -r nvidia-driver-390 nvidia-dkms-390', reboot, and do 'sudo ubuntu-drivers autoinstall' again.
- Finally, verify that installing chrome, opening fishgl.com, and cranking it up to 200 fish runs smoothly at (almost) 60 fps.

---

