---
title: "Ubuntu loader is NOT visible in BIOS screen but visible at boot"
date: 2019-04-13
forum: Installation &amp; Upgrades
---

### Post by maxrexfax on 2019-04-13
Intel Core i5-7400, MB MS-7996, Disk - ATA SSDPR-CX300-240
I have Ubuntu 18.04 and Windows 10 on one SSD disk. Here screenshot of Gparted.
[[IMG]https://i.postimg.cc/yxQJ28xd/boot03.jpg[/IMG]]("https://postimages.org/")
At boot, after pressing F11 i can choose OS to boot. Ubuntu loader is VISIBLE!

[[IMG]https://i.postimg.cc/G2nvjtTn/boot01.jpg[/IMG]]("https://postimages.org/")
But i can boot Ubuntu only MANUALLY! Below image with my boot menu in BIOS. Windows loader in BIOS is visible, Ubuntu - not!
[[IMG]https://i.postimg.cc/G2Rsyf6c/boot02.jpg[/IMG]]("https://postimages.org/")
Whats wrong and how can i do Ubuntu make first to load by default?

---

### Post by Rubi1200 on 2019-04-13
Hi,

Please use a LiveCD/USB to run the boot info (link in my signature) and report back here with the summary. Do not repair anything just post the summary here so we can take a closer look at the setup and offer advice.

Thanks.

---

### Post by yancek on 2019-04-13
In the image you posted, you show UEFI Hard Disk Drive.  Arrow down to that and highlight it and hit the Enter key.  Do you see options there including Ubuntu?  What is the manufacturer of the computer?
Running boot repair with the Create BootInfo Summary option and posting the link here will help as it gives more details on your system.

---

### Post by maxrexfax on 2019-04-14
paste.ubuntu.com/p/7Gzh7r69Pk 
I forgot to tell - there was one more Ububntu install on /dev/sdb2 - it boot started if i choose to boot from sda - ssd disk. I think i made too many OSs on one PC.

---

### Post by maxrexfax on 2019-04-14
Legacy+UEFI
[https://postimg.cc/PP5j1804](https://postimg.cc/PP5j1804)
[https://postimg.cc/75CrWrHJ](https://postimg.cc/75CrWrHJ)
[https://postimg.cc/xq0DSzj2](https://postimg.cc/xq0DSzj2)

---

### Post by oldfred on 2019-04-14
Please do not post large screen shots. You can use forum's advanced Editor and paperclip icon.

Is this your Summary report, as clickable link?
[http://paste.ubuntu.com/p/7Gzh7r69Pk/](http://paste.ubuntu.com/p/7Gzh7r69Pk/)

You have UEFI system with sda as gpt but sdb as the old MBR(msdos) partitioning. 
Windows only installs in UEFI boot mode using gpt partitioning.
But Ubuntu will let you install to a MBR partitioned drive in UEFI mode, even though not recommended by UEFI.

The Ubuntu UEFI entry is set to boot install in sda2. You have to have UEFI setting in UEFI to allow UEFI boot.
The grub in the MBR of sdb, is set to boot install in sdb2. You would have to have BIOS/CSM/Legacy setting on in UEFI to allow BIOS boot.
Some systems have UEFI & legacy and will find correct way to install based on boot option you choose. But my system using UEFI+legacy would only boot in BIOS mode. I had to change to UEFI only to boot in UEFI mode.

Your UEFI entries do not seem to be showing any entry for booting sdb, it would be a hard drive entry. Do you have setting in UEFI for UEFI only?

The grub in sda, will not auto find the install in sdb as you cannot switch from UEFI to BIOS in the middle of booting. You can only choose from UEFI boot menu.
Or better to convert sdb to gpt and install only in UEFI mode on all drives.

---

### Post by maxrexfax on 2019-04-14
So if i have BOTH disks as GPT than UEFI loader will work properly?

---

### Post by yancek on 2019-04-14
Do you have any particular reason to have the same release version of the same sysem (Ubuntu 18.04) on the same computer?
Your grub.cfg on sda2 where you have the Ubuntu EFI install has correct entries for itself, windows and the second Ubuntu on the external drive, all of which should boot from that menu since Grub on an EFI drive should boot a Linux install on another drive.  Might be hardware/motherboard related but this works with no problem on my HP notebook.

If you need/want to set Ubuntu to boot first, have you tried my suggestion in the last post as you appear to have multiple options with the "UEFI Hard Disk Drive" BIOS option?
Have you tried using:  efibootmgr to set the priority to Ubuntu?

---

### Post by oldfred on 2019-04-14
UEFI will only boot one install as default, and then from grub you can boot other installs if other installs are UEFI.

You can dual boot if UEFI settings are configured or you change them from UEFI to BIOS to boot BIOS install or  to UEFI to boot UEFI installs.
Better, easier to have all as UEFI.
But you can only have one as default in UEFI.

I have with some difficulty been able to configure a second install to have its boot from an ESP on a separate drive.
You need to change sdb to gpt and add an ESP.
But since grub boots my other Ubuntu installs, I just use ESP on sdb as backup to ESP on sda drive. Most backup tools do not backup ESP, so good to do that anyway.

Be sure to have good backups.
       Converting from MBR to gpt:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)

---

### Post by maxrexfax on 2019-04-18
The main goal was to find out why i dont see Ubuntu loader in BIOS screen. Compare my 2nd and 3rd pictures. I tryed to delete all partitions on SDB and PC cant boot at all.
I reinstalled Ububntu on SDA. Now i have only Ubuntu and it boot well.

---

### Post by john19432 on 2019-04-19
[COLOR=#242729][FONT=Arial]There are potential problems and complications with any of these options. The most likely complicating factor is if there are old or alternative [/FONT][/COLOR]ubuntu[COLOR=#242729][FONT=Arial] boot entries. It's important that you move the correct one to the top position in the boot order [/FONT][/COLOR][[COLOR=#000000]Walgreens Listens[/COLOR]]("https://www.walgreenslistens.us/")[COLOR=#242729][FONT=Arial].[/FONT][/COLOR]

---

