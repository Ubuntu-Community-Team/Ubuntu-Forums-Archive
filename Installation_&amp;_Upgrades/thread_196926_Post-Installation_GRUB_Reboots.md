---
title: "Post-Installation GRUB Reboots"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by FallsUpStairs on 2006-06-15
Using the Ubuntu Dapper Drake (6.06) Server install (checksum validates):

I have used both the "LAMP Server" and "Install to Hard Drive" installation choices, including using the guided partitioning utility to choose the partitioning scheme automatically, as well as setting it up myself.

Currently I am running the "Install to Hard Drive" option with two partitions, the first being my base (/) running Ext3 and the second being linux swap.

When I boot the computer, I get "GRUB loading, please wait..." After the menu timeout, I see the kernel loading sequence start, and I can catch the final "boot" line just prior to the entire system doing a full restart.

No error messages are printed, and the system repeats it all again.

The first listing in the GRUB menu is "Ubuntu, kernel 2.6.15-23-server" and is comprised of the following: ```
root (hd0,0)
kernel     /boot/vmlinuz-2.6.15-23-server root=/dev/hda1 ro quiet splash
initrd     /boot/initrd.img-2.6.15-23-server
savedefault
boot
```
Subsequently, booting to "...(recovery mode)" also fails in the same manner, however "...memtest86+" works perfectly, therefore the file system is obviously accessible.

System specs:
AMD K6-2/400
224MB/RAM
(NOTE: The processor is labeled K6-2/500, there has been a recurring problem of incorrect detection, however both Hoary Hedgehog and Breezy Badger have installed correctly [including a dist-upgrade to Dapper Drake]. Whether this is a problem seems far-fetched, but I'm throwing it out there.)

---

### Post by cgeddie on 2006-06-15
Hi FallsUpStairs,

I have the same situation, more or less, and am also looking for the solution.  I had a lot of problem getting Dapper (AMD64) installed on my system -- I boot from a software mirrored RAID setup, and had to follow the text-based method shown at [http://ubuntu-in.org/wiki/SATA_RAID_Howto](http://ubuntu-in.org/wiki/SATA_RAID_Howto).  Finally, I have my grub install set up, and I get the grub boot menu.

If I select my pre-existing Windows XP-SP2 install, it boots properly.  However, if I choose either Dapper or Dapper (recovery mode) gives the same behavior it does for you -- instant reboot without any info on the screen before the reboot.  Memtest works just as in your case.

My hd(0) has these partitions (in GRUB numbering)
0: WinXP NTFS
1: Dapper ext3 (/boot)
2: Dapper ext (/)
3: Linux swap

My menu.lst is:
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

splashimage=(hd0,1)/grub/splash.xpm.gz

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

title		Ubuntu 6.06 (Dapper), 2.6.15-23-amd64-generic
root		(hd0,1)
kernel		/vmlinuz-2.6.15-23-amd64-generic root= ro quiet splash
initrd		/initrd.img-2.6.15-23-amd64-generic
boot

title		Ubuntu 6.06 (Dapper), 2.6.15-23-amd64-generic (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.15-23-amd64-generic root= ro single
initrd		/initrd.img-2.6.15-23-amd64-generic
boot

title		Ubuntu 6.06 (Dapper), memtest86+
root		(hd0,1)
kernel		/memtest86+.bin 
boot
```

Anyone who can figure out how I can fix this, please let me know.

My suspicion: I might have the wrong kernel.  Here's the listing of my /boot partition:
```
[FONT="Courier New"]total 9952
drwxr-xr-x   4 root root    1024 2006-06-07 00:18 .
drwxr-xr-x 24 root root    4096 2006-06-08 05:58 ..
-rw-r--r-- 1 root root  260598 2006-05-23 14:09 abi-2.6.15-23-amd64-generic
-rw-r--r-- 1 root root   62867 2006-05-23 13:44 config-2.6.15-23-amd64-generic
drwxr-xr-x 3 root root    1024 2006-06-11 14:19 grub
-rw-r--r-- 1 root root 7334080 2006-06-08 06:30 initrd.img-2.6.15-23-amd64-generic
drwx------  2 root root   12288 2006-06-06 22:25 lost+found
-rw-r--r-- 1 root root   94760 2005-10-25 10:36 memtest86+.bin
-rw-r--r-- 1 root root  887284 2006-05-23 14:09 System.map-2.6.15-23-amd64-generic
-rw-r--r--  1 root root 1484727 2006-05-23 14:09 vmlinuz-2.6.15-23-amd64-generic

```[/FONT]

Key Words: reboot restart grub Dapper install

---

### Post by milwen on 2006-07-16
I have also had this problem after installing Ubuntu Server 6.06.  I have reinstalled and still had the same problem.  It restarts just as the system gets to "boot" during the startup process.  It does the same even if I choose to boot into "recovery mode" from GRUB.

One thing that seemed interesting to me:  like the first post, I also have an AMD-K6.

AMD-K6  500MHz
192MB SDRAM

This is the first I've tried to install Ubuntu on this machine.  I have also redownloaded the iso and tried another disc.

---

### Post by ... on 2006-07-16
I am thinking it is a problem with dapper not working with the k6/2 500's reason being that I am having the exact promlem as you guys on my box (k6/2 550 with 256mb ram on a asus tx97xe mobo) The breezy worked great on it, but this new version doesn't play nicley.

---

### Post by milwen on 2006-07-17
Just an update:  I tried installing the desktop version and it installed and booted ok.  I'll just have to make my own "server" version from here.

---

