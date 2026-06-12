---
title: "slackware/ubuntu fstab's"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by 999alfred on 2007-02-28
I have a question concerning a slackware installed 2.4.22 kernel install and a Unbuntu 6.1 kernel 2.6 (cann't remeber the sub number) install. Here's what I did.
INstall brand new 100GB hard drive as primary, no other hard drive in system(didn't want to screw up my work slackware install).
Install Unbuntu 6.1 and get everything working, of course it uses grub.
Now, reinstall slackware disk as primary(/dev/hda) and Unbuntu as secondary(/dev/hdb) and boot. 
My slackware loads(I use lilo) and I mount my ubuntu(mount /dev/hdb /ubuntu) and I go to /ubuntu/etc and look at ubuntu's fstgab so I can chnage it so the root fs is on /dev/hdb1 and swap is on /dev/hdb2. Intead of /dev/hda which this disk was at intstall. 
Now I find UUID's for the partitions and not /dev/hda. 
Now, I have never done a 2.6 kernel before.
So I have two questions:
Do I need to change the ubuntu's fstab from UUID's to /dev/hdb1 and /dev/hdb2 respectively. Or, will the 2.6 kernel automatically know to use /dev/hb1 & 2 respectively? (An ignorance of 2.6 that I hope to rectify as I use Unbuntu.)
Will the folowing work in my lilo.conf on the slackware /dev/hda1

image = /boot/bzImage.scsicd
  root = /dev/hda2
  append="hdc=ide-scsi hdd=ide-scsi"
  vga = extended
  label = Slackware Linux
  read-only # Non-UMSDOS filesystems should be mounted read-only for checking

image= /boot/vmlinuz-2.6.17-11-generic
  root=/dev/hdb1 
  initrd=/boot/initrd.img-2.6.17-11-generic
  append="hdc=ide-scsi hdd=ide-scsi"
  vga = extended
  label=Ubuntu, kernel 2.6.17-11-generic
  read-only

other = /dev/hda1
  label = Dos
  table = /dev/hda

And a third question.
What about the splash that was in the grub kernel line?

Sorry to get so long winded, but the Slackware is my work for a living install and I really don't want to screw this up :) 

tj

---

### Post by dannyboy79 on 2007-02-28
i can tell you this, fstab doesn't care if you use UUID's or dev positions and since you're not sure what will happen if you stick with the uuid's than I would suggest you use what you know will work! Go with the /dev/hdx etc etc. I can't comment on your lilo config as I use grub.

---

