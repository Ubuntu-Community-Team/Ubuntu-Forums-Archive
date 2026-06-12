---
title: "installer puts mbr on wrong disk!!"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by IndieRockSteve on 2005-04-14
ok, I'm using server install
I have some ide drives and some scsi drives. my / i on a scsi drive but the installer installs the mbr on the first ide disk.
how can i change this or fix it?!
also is there an expert server mode?

thanks!

---

### Post by IndieRockSteve on 2005-04-14
figured it out. apparently grub can not do what I need, so I'm using LILO. sucks to have 2 grub and 1 lilo setup, but at least it'll boot  :razz:

---

### Post by IndieRockSteve on 2005-04-14
ok, I'm still getting the 
99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 99 

error when booting. trying one more time and searching...

---

### Post by Bob D. on 2005-04-14
Darn, I was waiting to see what replies you got.

I think the issue is the Debian installer cannot do what you want. I had a huge go round with Warty with a mix of SATA hard drives and my SCSI boot drive. I was never able to get an answer off the user-mail list, so I gave up and installed Fedora Core 3. I found the answer then.

Seems the Anaconda installer gives you an 'advanced' option at the screen where you are going to write grub to the mbr. Anaconda lets you 'reorder' the disks. My SCSI drive is always seen as sdc, while my SATA drives were sda & sdb. Anaconda let me reorder the drives prior to writing to the mbr. I moved the SCSI drive to sda and 'voila', FC3 installed and booted the first time and XP was fine as well.

So that's the problem, I just don't know and have yet to hear how to work around it with Ubuntu's Debian installer. I've got Hoary on my test box right now and will be installing it after a rebuild of my main system in a week or so. The SCSI is coming out, so that will solve my issue but it sure would be nice to know how to work around it.

Bob

---

### Post by hostile on 2005-10-27
I am having the exact same issue right now.

[http://www.ubuntuforums.org/showthread.php?p=446638#post446638](http://www.ubuntuforums.org/showthread.php?p=446638#post446638)

I have tried both Debian and Ubuntu. Badger will not do what is needed either.

All the re-ordering in Anaconda does is correctly order the drives in the /boot/grub/device.map file.

The question is, how can the Debian installer do this?? I don't think it can...

:(

---

### Post by hostile on 2005-10-27
Well... taking my own advice regarding the device.map file...

Now, if one is using SCSI devices, I'm not going to go into details on how to setup controller cards and your BIOS to boot from them - you're on your own on that one. Besides, if you use SCSI, you should already know how to do that.

In order to get Ubuntu/Debian to boot form your first SCSI drive, while you have SATA and IDE drives in the same system is a little convoluted, yet fairly easy.

1) Install the system
2) Go and download/burn yourself a Knoppix CD
3) Boot from the Knoppix CD
4) Mount your SCSI device partition which contains /boot
5) Change the mount to be writeable
6) Edit /boot/grub/device.map to reflect the correct mapping, for me I had to change hd0 from /dev/hda to /dev/sdc
7) Edit /boot/grub/menu.list to reflect where your bootable and root partitions are (most likely hd0,0)
8) Save your work
9) Unmount your partition
10) Reboot
11) Enjoy!

:cool:

---

