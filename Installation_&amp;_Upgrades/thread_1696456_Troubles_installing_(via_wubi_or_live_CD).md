---
title: "Troubles installing (via wubi or live CD)"
date: 2011-02-27
forum: Installation &amp; Upgrades
---

### Post by hibbijo on 2011-02-27
I'm trying to install the 10.04.2 LTS install.
I'm trying to dual boot my current win7 install with ubuntu and am having a lot of trouble.
If I try to install through wubi(which I don't really want to do, I just tried it as a last resort and it didn't even work) upon reboot to complete installation it says "No root file system defined".
If I try to install through live CD the installer tells me that I have no OS installed and the whole drive is unallocated(which it's not). After almost losing my windows install messing with testdisk, I'm gonna stop troubleshooting myself and get some direct help. I've uploaded some screenshots of how the partitions show up in a live cd, during install, in gparted, and terminal window of "sudo fdisk -l). I also have a screen shot of how the hard drive shows up in windows, if you need more info just ask. Any help is appreciated! Thanks.

---

### Post by oldfred on 2011-02-27
Welcome to the forums.

Your one screen mentions gpt partitions. That is a newer scheme over MBR(msdos). Linux, Apple & some windows servers or 64bit windows with efi boot work with gpt but most windows do not. Also Apple uses a kludge of part MBR & part gpt hybrid to make dual boot with windows work. 

It may be you just need to remove the gpt info so you are just MBR.

Converting:
[http://ubuntuforums.org/showthread.php?t=1454252](http://ubuntuforums.org/showthread.php?t=1454252)
Windows convert from gpt to MBR. may destroy all data per srs5694
[http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html](http://www.sevenforums.com/tutorials/26203-convert-gpt-disk-mbr-disk.html)
[http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)
[http://www.microsoft.com/whdc/device/storage/GPT_FAQ.mspx](http://www.microsoft.com/whdc/device/storage/GPT_FAQ.mspx)

Remove old parts of gpt
[http://ubuntuforums.org/showpost.php?p=10022223&postcount=34](http://ubuntuforums.org/showpost.php?p=10022223&postcount=34)

If you do not have gpt and remove the extra gpt info then gparted should work and let you create the additional extended and logical partitions.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by hibbijo on 2011-02-27
In windows the properties for my disk states that it is MBR and not GPT. So you're saying I need to remove the incorrect GPT information and than it will work?

EDIT: SOLVED! Removing the GPT information fixed my problem!! You're a wizard thanks a ton!\\:D/

---

### Post by srs5694 on 2011-02-27
Your second screen shot, with the fdisk output, reveals a normal MBR partition table but also a warning to the effect that GUID Partition Table (GPT) data were detected. This almost certainly means that you used the disk with GPT at some point (on a Mac, say), then re-used it with Windows without properly erasing the old GPT data. Technically, this is OK, since the GPT specification states that this makes your disk a Master Boot Record (MBR) disk; but some utilities, including many Linux partitioning tools, get confused by this setup.

The solution is to erase the old GPT data. [This Web page of mine]("http://nessus.rodsbooks.com/gdisk/wipegpt.html") describes how to do so. The short summary is to download GPT fdisk (gdisk and sgdisk) from [its Sourceforge download page]("http://sourceforge.net/projects/gptfdisk/files/") (*do not* use the version provided in the Ubuntu repositories; through Ubuntu 10.10, that version is hopelessly out of date and won't work for this purpose). Get the .deb file for your architecture (i386 or amd64), double-click it to install it, then open a Terminal and type the following commands:

```

sudo sfdisk -d /dev/sda > parts.txt
sudo sgdisk --zap /dev/sda

```Note that these are the "s" versions of the utilities (sfdisk and sgdisk, not fdisk and gdisk). Between those two commands, copy the parts.txt file that the first command generates to a USB flash drive, floppy disc, CD-R, or some other removable medium. That provides you with insurance; if something goes badly wrong, you'll be able to use parts.txt and sfdisk to recover. When you issue the sgdisk command, it will wipe the old GPT data from the disk, leaving it as an unambiguous MBR disk. This will probably enable the installer to detect your partitions and continue on.

Edit: Oops; I must have missed that last post.

---

### Post by helosk on 2011-02-27
so I'm tremendously excited to install Ubuntu on my PC - very tired of having to hunt for programs - buying them and having them not work...

that being said - I'm having a lot of trouble installing Ubuntu on my system via the WUBI download.

I keep getting the error msg "there is no disk in the drive. Please insert a disk into drive /device/harddisk5/dr5."

I have no idea what this means...

any help?

---

### Post by srs5694 on 2011-02-28
> **helosk said:**
> so I'm tremendously excited to install Ubuntu on my PC - very tired of having to hunt for programs - buying them and having them not work...

that being said - I'm having a lot of trouble installing Ubuntu on my system via the WUBI download.

I keep getting the error msg "there is no disk in the drive. Please insert a disk into drive /device/harddisk5/dr5."

I have no idea what this means...

any help?

Please don't post your problem to an ongoing existing thread. Trying to resolve two problems in one thread becomes very confusing very quickly. Please create your own thread for this problem. Also, although I'm not familiar with WUBI, the filename you specified ("/device/harddisk5/dr5") is not a normal one in Linux, so I can't help but wonder if you've copied the message correctly. It's imperative that error messages be copied *precisely* and *completely*. If necessary, take a screen shot and post it for reference, or cut-and-paste a text-mode message in a Terminal window.

---

### Post by Rubi1200 on 2011-02-28
@helosk: thanks for posting your question in the appropriate place; see the answer by bcbc there.

@srs5694: the error message is actually correct. Wubi searches for devices and when it finds one empty it throws an exception (or actually the python runtime does). In most cases, it is related to something like a multimedia card reader. Removing the device usually solves the problem and the error goes away.

---

### Post by syed.rakib.al.hasan on 2011-08-10
> **hibbijo said:**
> EDIT: SOLVED! Removing the GPT information fixed my problem!! You're a wizard thanks a ton!\\:D/

what steps did you follow to remove the GPT information???

---

