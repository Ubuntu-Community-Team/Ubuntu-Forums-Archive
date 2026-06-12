---
title: "new user, need help Ubuntu not working after install"
date: 2005-10-25
forum: Installation &amp; Upgrades
---

### Post by macleod185 on 2005-10-25
I bought a 100gig external hard drive to use to run ubuntu, I partitioned the entire drive, and ran the downloader, everything seemed fine, and I even set up my user name, password, and time settings, I have it set up so i can select my OS at start up, but when I try to load ubuntu it runs through some operations and then says: 

Alert! /dev/sdb1 does not exist. dropping to a shell!!

Busybox v1.00-pre10 (debian 20040623-1ubuntu22) Built-in shell (ash)

Enter 'help' for a full list of built-in commands.

/bin/sh: can't access tty; Job control turned off
# [4294684.150000] sdb:assuming drive cache: write through
[4294684.150000] sdb:assuming drive cache: write through


Can anyone tell me what is going on? is there a missing file? I scanned the install disk beforehand and it said everything was fine... do I need to change some settings on my BIOS? If anyone could give me instructions on how to do what i need to do I would really appreciate it. 

Thanks

---

### Post by gamesmad on 2005-10-25
Try reinstalling it, it looks like there are some missing files....

Will

---

### Post by phen on 2005-10-25
sdb1 is NOT a file. it is a handler for one of your harddisks. It is a scsi disk (or usb, as usb drives are mounted as scsi) and the first partition on that disk. i assume, that it is your external disk.

try to enable USB LEGACY Settings in your bios. it looks as if your harddisk is not recognized by grub. and turn on the external disk before you start up your computer. (not with the computer, they have a long startup time sometimes!)

good luck :-)

---

### Post by macleod185 on 2005-10-26
USB legacy settings are all on and working... It still insnt registering the usb drive...dont know what to do

I tried to follow a really complicated walk through for installing to an external USB drive, but it didnt work like it said it would

anyone have any ideas?

---

### Post by rubenjavier on 2005-10-31
this is a well known Breezy issue, since Breezy Beta, the new kernels can't boot a SCSI drive and I dont know why, I've fighting with this since Breezy Beta and Release Candidate, but Hoary do it just fine... I opted for installing Hoary first and then apt-get distupgrade to Breezy with the Breezy CD, and then at the start choose the GRUB menu and use Hoary kernel.
If anybody from the Ubuntu Team is reading this... please Fix this issue, I haven't completly moved on to Breezy because this SCSI detection Failure on my SCSI mail server
Thanks in advance

---

### Post by Naota-kun on 2005-11-12
Sorry for bumping a week-old thread, but I am getting the EXACT same messages. Are you saying that I would be able to run Hoary without this problem?

---

### Post by ssam on 2005-11-12
looks like he is saying the the problem is with the breezy installer. and the hoary should install fine. then you should be able to upgrade to breezy and it will still work.

---

### Post by mechanic on 2005-11-12
You could lways check this out with Live-CD disks before trying an install disk.

m.

---

### Post by Wide on 2005-11-13
I am also trying to upgrade to Breezy from Hoary on a duel zeon, raid 1, scsi system.

When I get to the kernel part it just stops & error codes. 

Will try again tomorrow :)



```
Preparing to replace libc6 2.3.2.ds1-20ubuntu14 (using .../libc6_2.3.5-1ubuntu12_i386.deb) ...
Unpacking replacement libc6 ...
dpkg-deb (subprocess): error in buffer_read(stream): failed to write to pipe in copy: Input/output error
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing /cdrom//pool/main/g/glibc/libc6_2.3.5-1ubuntu12_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/gconv/CP1258.so')Errors were encountered while processing:
 /cdrom//pool/main/g/glibc/libc6-dev_2.3.5-1ubuntu12_i386.deb
 /cdrom//pool/main/g/glibc/locales_2.3.5-1ubuntu12_all.deb
 /cdrom//pool/main/g/glibc/libc6_2.3.5-1ubuntu12_i386.deb
```

---

### Post by jon21 on 2005-12-03
Here's how I fixed the dreaded and common "/dev/sdb1 does not exist" problem that comes up during installs of 5.10 and 5.04 on SCSI-based PC's.

You just need to change "sdb1" to "sda1" in the /boot/grub/menu.lst file.

Here's how I did it:

1) Boot the computer using a Knoppix Live CD (I expect you could use any Live CD or other installed OS)
2) Find /mnt/sda1 in the file browser, right-click on it, and change it to read/write status.
3) Use a text editor (I used emacs) to open /mnt/sda1/boot/grub/menu.lst and replace "sdb1" with "sda1" in the bootup parameters (2-3 places in the file).

That's it.  Reboot and it's smooth sailing from there.

- Jon

---

