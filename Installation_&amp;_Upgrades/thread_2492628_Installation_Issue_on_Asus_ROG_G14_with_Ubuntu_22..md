---
title: "Installation Issue on Asus ROG G14 with Ubuntu 22.04.3 LTS"
date: 2023-11-18
forum: Installation &amp; Upgrades
---

### Post by vloxium on 2023-11-18
I recently attempted to fresh install Ubuntu 22.04.3 LTS Desktop on my Asus ROG G14 2021 (GA401QM) laptop. Ubuntu Live USB is working (Try Ubuntu) but encountered some issues during the installation process (Install Ubuntu).

**Hardware Information:**

[LIST]
[*]Model: Asus ROG G14 2021 (GA401QM)
[*]CPU: R9 5900HS (with Radeon Graphics 3300 MHz)
[*]GPU: RTX 3060 6GB GDDR6
[*]SSD: 1TB NVME
[*]BIOS American Megatrends 415, GOP 2.16, EC FG070F0D.306
[*]ErP, SVM, Armoury Crate: Disabled
[*]Fast Boot, Secure Boot, Legacy USB Support: Disabled
[*]USB Mass Storage Driver Support: Enabled
[*]Ubuntu Version to be installed: 22.04.3 LTS Desktop
[/LIST]
No repair history. All hardware are default.

**Installation Steps:**

[LIST=1]
[*]I used a flash drive with the ISO image flashed using Balena Etcher.
[*]Connected to WiFi.
[*]Selected Minimal Installation.
[*]Enabled downloading updates during installation.
[*]Disabled the installation of third-party apps.
[*]Chose "Erase disk and install Ubuntu" without selecting advanced settings.
[/LIST]

**Issue Description:**
After the installation process, when prompted to restart the system, I briefly see the [first picture]("https://i.stack.imgur.com/i0I42.jpg") with these lines:
```
[FAILED] Failed to start ZSYS daemon service.
[FAILED] Failed to start Clean up old snapshots to free space.
```
This is followed by a quick transition to the [next picture]("https://i.stack.imgur.com/zfnEh.jpg").
```
Please remove the installation medium, then press Enter.
```
When I remove the flash drive, I encounter [four lines of messages]("https://i.stack.imgur.com/ZtY5c.jpg"):
```
Failed to unmount /oldroot: Device or Resource busy
Failed to unmount /oldroot/dev: Device or Resource busy
shutdown[1]: Could not detach loopback /dev/loop0: Device or Resource busy
shutdown[1]: Failed to finalize file systems, loop devices, ignoring.
```
Manually rebooting doesn't result in Ubuntu booting successfully.

**What I've Tried:**

[LIST]
[*]Using another installation media (flash drive)
[*]Trying other USB ports
[*]Enabling all disabled options in BIOS
[*]Reinstalling Windows 11 and then attempting to reinstall Ubuntu
[*]Trying ZFS as the file system
[*]Using Rufus GPT and MBR method.
[*]Trying custom partitioning from [this tutorial]("https://averagelinuxuser.com/linux-partitioning-recommendations/").
[/LIST]

I am relatively new to Ubuntu, transitioning from Windows 11. Please let me know if there is any additional information needed to address this issue.

---

### Post by MAFoElffen on 2023-11-18
Sometimes the installer has problems if you sarted and possibly went back, so that a ZFS pool was created, then tries to create it again (pre-existing).

From the Ubuntu 22.04.3 installer LiveUSB, do "try". At the desktop, open a terminal session and do
```

lsblk -e7 -o name,size,model

```
Take note of the disk device name. Lets say it said "sda". Substitute by what yours says...
```

sudo su -
wipefs -a /dev/sda
blkdiscard -f /dev/sda
sgdisk --zap-all /dev/sda
sgdisk -o /dev/sda
reboot

```
That will zero the disk remove everything, then add a new fresh GPT partition table.

On the reboot, select "Install"...

Install with your ZFS options...

If it has problems booting again on the first boot, please post back and I will guide you from there...

---

### Post by vloxium on 2023-11-18
I tried your suggestion twice: once without advanced settings and once selecting ZFS. When I installed it without advanced settings, it prompted the same three-step issues. When I installed it with ZFS, the installer crashed. It says: ```
We're sorry; the installer crashed. After you close this window, we'll allow you to file a bug report using the integrated bug reporting tool. This will gather information about your system and your installation process. The details will be sent to our bug tracker and a developer will attend to the problem as soon as possible.
```

---

### Post by MAFoElffen on 2023-11-18
"it prompted the same three-steps issues" <--- Please explain.

And when it crashed, did you choose to see what it crashed on? That would give a clue to what is happening...

Did you very the image checksum to verify it downloaded successfully and that you have a good image?

---

### Post by apatel415 on 2024-02-24
I can confirm the issues described above with Ubuntu 22.04.3 LTS while attempting to install Asus ROG G14 [COLOR=#000000] (GA401QM) .[/COLOR] Live USB works fine and the installation goes smoothly. The reboot hangs but that has happened before and you just have to do a hard power-off. The issue I was having, post install and post what OP described, is that once you reboot, is boot process starts and looks like it loading the kernel and then goes blank. Can't access TTY2 either from CTR+ALT+F2. I was following this install guide ([https://gist.github.com/vijay-prema/cfcf8cc4085663b7bb48f34172c10629](https://gist.github.com/vijay-prema/cfcf8cc4085663b7bb48f34172c10629)).

I saw that 22.04.4 was released today so I decided to give it a try. I also used Balena Etcher to create the startup drive (NOT SURE THIS MADE A DIFFERENCE). I also researched and saw that there were issue with the graphics driver being use (presumably ***nouveau*** for the Nvidia card) so opted for the "Safe Graphics" option to start the boot. That worked smoothly so I now have a bootable and accessible OS and can configure everything else from here. 

Following this guide as well: [https://gist.githubusercontent.com/Raltar/586be522a0f3ddf2a52c5ba71533bdfc/raw/2b3ab26533dcb2819598c0885f9251be719cde81/gistfile1.txt](https://gist.githubusercontent.com/Raltar/586be522a0f3ddf2a52c5ba71533bdfc/raw/2b3ab26533dcb2819598c0885f9251be719cde81/gistfile1.txt)

---

