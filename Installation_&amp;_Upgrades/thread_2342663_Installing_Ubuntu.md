---
title: "Installing Ubuntu"
date: 2016-11-08
forum: Installation &amp; Upgrades
---

### Post by ironicsin on 2016-11-08
This may or may not be a simple fix and all help would be appreciated.

Yesterday, I installed Ubuntu to my laptop using a USB. I followed the directions for using Rufus and followed the directions on the Ubuntu website. After installations were complete, I restarted my laptop and it gave me the options to try out Ubuntu/download Ubuntu again. I also noticed that I can't use the laptop anymore without the USB drive plugged in. The result I was hoping for was for Ubuntu to replace Windows 10.

I'm new to all this and hope to learn more if I can get this to work.

---

### Post by oldfred on 2016-11-08
What brand/model system?
What video card/chip?
Did you install in UEFI or BIOS boot mode?

From live installer in live mode:
 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by yancek on 2016-11-08
Remove the usb you used to install so it can boot from the hard drive.  You also need to post the bootinfo output.

---

### Post by Bucky Ball on 2016-11-08
For what it's worth, I'd boot to the install media, Try Ubuntu, launch Gparted, delete all partitions, click 'Device> Create partition table', then back to the desktop and hit the install icon.

All good in theory, but before all this is where one of oldfred's questions comes in: do you intend installing in UEFI or BIOS boot mode? If you are not using Windows, there is no compunction to install using either. EFI or BIOS is fine, but you need to know which you're going to use before launching off on this as there is a different method for each.

---

