---
title: "Dapper install (no cd-rom or floppy)"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by brb84 on 2007-03-08
I have a strange situation.  My current machine has no cd-rom or floppy drive installed, and I want to install the dapper release by pulling the downloaded iso image from my hard drive.  I have seen several different tutorials on this, but most of them at least involve either 
a.) using floppies
b.) doing this with edgy instead of dapper

My hard drive is already partitioned with a separate partition for the .iso file.  I have also already done this successfully with the edgy release in the past.  Here is how far I have gotten:

1.) Downloaded the "alternate" dapper iso image

2.) Downloaded the vmlinuz and initrd.gz files from [http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/)

3.) Edited /boot/grub/menu.lst file as:

title		New Install
root		(hd0,2)
kernel	      (hd0,0)/newinstall/vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd		(hd0,0)/newinstall/initrd.gz


Upon selecting that boot choice, my computer successfully enters the installation process.  It then searches for a suitable .iso image.  Ater that, It gives me an error message saying: "No kernel modules found" (meaning it found the iso image but doesn't like it)  It goes on to say it probably has to do with the boot installer's version not matching the iso image's version.  Attempting to continue anyway results in strange failures such as the network card not being detected (again,  it worked perfectly from this part when I did this with edgy).

I have tried as many vmliuz/initrd.gz files as I could think of to try to find ones that matched the iso's version, including the ones I used for the edgy install, but they all give the same mismatch error.

So I guess my big question is: Where can I find the vmlinuz/initrd.gz files that match the kernel module versions that exist in the dapper alternate iso file?

By the way, attempting to use the vmlinuz/initrd.gz files from the alternate iso file itself results in the installer simply halting after asking that the CD-ROM be inserted (it's specifically only set up to search for a mounted cd-rom..not hard disk)

If anyone has any other ideas on how I can do this, I'd appreciate it!

---

### Post by zvacet on 2007-03-09
[http://ubuntuforums.org/showthread.php?t=331293&highlight=install+from+iso]("http://ubuntuforums.org/showthread.php?t=331293&highlight=install+from+iso")

---

### Post by brb84 on 2007-03-12
I checked those threads, and none of the posters were experiencing my particular problem.  The error message I'm getting after the installer *successfully* finds the correct .iso file is:


"No kernal modules were found.  This probably is due to a mismatch between the kernel used by this version of the installer and the kernel version available in the archive.

If you're installing from a mirror, you can work around this problem by choosing to install a different version of ubuntu.  The install will probably fail to work if you continue without kernel modules."

Here are the details of the files I am using:

iso file: ubuntu-6.06.1-alternate-i386.iso from ubunutu mirror site
*Booted to installer via USB flash drive using boot.img file from [http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/dapper/main/installer-i386/current/images/hd-media/)



Why are these showing "mismatched?"  Does this method simply not work with Dapper?


**Edit**  I am currently now attempting to do a full-fledged FTP install instead.  I booted with the net-boot img file and pointed the installer to the US.archives.ubuntu ftp location, and it seems to be working so far.  I just hate that this will probably take an hour or two longer to install this way when I have the iso already downloaded on my hard drive.

---

