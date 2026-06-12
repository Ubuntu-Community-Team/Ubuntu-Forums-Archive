---
title: "Problems with external Ubuntu installation"
date: 2017-08-25
forum: Installation &amp; Upgrades
---

### Post by matsn0w on 2017-08-25
Hey everyone! This question came from [askubuntu.com]("https://askubuntu.com/questions/948697/problems-with-external-ubuntu-installation") where we couldn't find the answer. I was advised by @sudodus to give it a try on this forum. So here I am! Here comes the problem:

I have a laptop (HP ProBook 470 G3) with a 256 GB internal SSD. It has Windows 10 installed on it. I also have a external (USB) Seagate Expansion drive, which is 1 TB. 

Due to the limited size of my SSD, I'd like to install Ubuntu on the Seagate. To be precise: on a partition of the Seagate. (Because I have a NTFS partition with about 600 GB of data on it, and I don't want to loose that). 

So I downloaded the Ubuntu 16.04.03 LTS ISO**[SUP]1[/SUP]** and made a bootable USB-stick with Rufus. Booted into the stick and goed trough the installation process. So far so good. I've created three additional partitions and made one of them the swap and the other two ext4. (Mount point / and /home). I also set the boot loader to install on the Seagate, which is [FONT=courier new]sda[/FONT]. (My SSD is [FONT=courier new]sdb[/FONT]). The installation finished and said to me that it was time to reboot. So I removed the USB-stick and rebooted.

But... It gave me the following: 

    > 
error: unknown filesystem.
    Entering rescue mode...
    grub rescue> _


I have been troubleshooting for days and I'm really getting tired of this :(

Google told me that i have to reset the root and prefix in the GRUB rescue mode, but whatever I try, it keeps saying 'unknown filesystem'. 

However, what did work was booting the USB-stick and hit escape (or C) to give me the GRUB terminal from the stick's GRUB. Setting the root and prefix there, followed by:

    > 
insmod normal
    nornal


resulted in a proper boot. So yes, I am abled to boot into my Ubuntu, but this ofcourse isn't the way I want it to be. I've also done the thing above, followed by:

    > 
sudo grub-update
    sudo grub-install /dev/sda


in the Ubuntu terminal, but rebooting, again, resulted in the GRUB rescue mode.

I also discovered that this might be GRUB legacy? Not sure if that's a problem.

So, what are your thoughts about this? I hope that I gave enough info, and I'm really looking forward on solving this issue.

Thanks in advance,
matsn0w

PS: you can read the topic on [askubuntu.com]("https://askubuntu.com/questions/948697/problems-with-external-ubuntu-installation") to see what I've tried so far.

---

### Post by sudodus on 2017-08-25
I found the following link (about Debian Jessie). There seems to be issues but also solutions, and you can draw conclusions about which kernel series that might work also with Ubuntu, and which program package to remove or replace.

[InstallingDebianOnHPProbook 470 G3 Jessie](https://wiki.debian.org/InstallingDebianOn/HP/Probook%20470%20G3/Jessie)

I would try various versions of various linux distros, for example

- the new version of Debian, Stretch.

- Try also [the developing version of Ubuntu, Artful Aardvark](http://iso.qa.ubuntu.com/qatracker/milestones/376/builds/155168/testcases).

- Try also other linux distros, not only Debian and Ubuntu.

If you manage to run Ubuntu, Debian or another linux distro live there is good hope.

- Start by installing and if necessary tweak to make the installed system work

- If you fail with the installed system, but the live system works, you can take the step from a live-only to a persistent live system. There is a tool to make persistent live systems of Ubuntu and Debian systems, mkusb,

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

---

### Post by ubfan1 on 2017-08-26
Please run the boot-repair program, just the report, don't try to apply any fixes yet, and post a link to the report.  That will give a lot of the information I cannot find in your previous postings, like the partitioning type of the external disk.  Different boot methods require different partitions, like a UEFI boot on an MSDOS partitioned disk requires a small partition (1-2M) with the grub-bios flag.

---

### Post by matsn0w on 2017-08-27
> **ubfan1 said:**
> Please run the boot-repair program, just the report, don't try to apply any fixes yet, and post a link to the report.  That will give a lot of the information I cannot find in your previous postings, like the partitioning type of the external disk.  Different boot methods require different partitions, like a UEFI boot on an MSDOS partitioned disk requires a small partition (1-2M) with the grub-bios flag.

Somehow boot-repair didn't give me a report link, it was showing [http://paste2.org/](http://paste2.org/) without a further link. I read that Windows 10 build 1703 contains a program to convert MBR to GPT without data loss. Maybe this is needed to create a boot partition?

I am starting to think that this all has something to do with MBR/EFI stuff. It is also said that the disk can't find the GRUB because it's not at the beginning of the disk? My NTFS partition is, so...  

I don't really know what to do anymore.

---

### Post by ubfan1 on 2017-08-27
Looks like the bug 1692778, [https://bugs.launchpad.net/boot-repair/+bug/1692778](https://bugs.launchpad.net/boot-repair/+bug/1692778), which you can add yourself to by clicking on the "does this bug affect you" spot.  There is another forum link with some previous help on the issue: [https://ubuntuforums.org/showthread.php?t=2361858](https://ubuntuforums.org/showthread.php?t=2361858)

---

### Post by oldfred on 2017-08-27
You can still manually post the Boot-Repair Summary report to a pastebin site.
If run from a flash drive it may be saved in the ESP if UEFI boot. Or it may be on the hard drive in the ESP. With full installs the report is in  /var/log/boot-sav/log.

Just to see partitioning:
sudo parted -l

---

