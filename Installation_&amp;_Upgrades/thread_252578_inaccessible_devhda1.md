---
title: "inaccessible /dev/hda1 ?"
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by hifimf on 2006-09-07
hey i have formatted my hdd, so the only os will be ubuntu 6.06. it installs fine but when i restart it doesnt get past the ubuntu load up screen.  after some time it says cannot access /dev/hda1. 

i've tried enabling the partition by going to admin->disks but with no success. 

i've also tried reinstalling the os about 5 times but i still get the same message.

if anyone knows how to fix this plz let me know ;;  if its a bad partion tell me what to do to fix it, if possible. i'm new to the linux thing ^^

im runing: 
amd 64 athlon
2 crt monitors
nvidia fx 5500

---

### Post by zxee on 2006-09-07
Are there other drives on your system and what type of drive are you installing to? You may need to reinstall grub. 
Is this the desktop cd you're installing from? You should be able to do sudo grub-install from the livecd in a terminal.

---

### Post by hifimf on 2006-09-07
i only have 1 hdd, and im installing from the livecd.

ill try doing the sudo grub

---

### Post by zxee on 2006-09-07
You could also check your install from the livecd Take a look at /boot/grub/menu.lst If your install is on hda1 grub should show the ubuntu 6.06 root (hd0,0)

From the live cd open a terminal and type sudo grub
you should get a grub prompt: grub>
In grub type find /boot/grub/stage1
If that returns (hd0,0)


Actually try setup hd0 
I had orginally typed setup hd0.0 but I'm too used to installing grub to a root partition to install to your mbr hd0 should do it.

Hope that works.

---

### Post by hifimf on 2006-09-07
ok so i did the sodu grub thing. restarted and it freezes up on "waiting for   root file system" after a few minutes it switches screens and says...

ALERT! /dev/hda1 does not exist - dropping to shell!

then some other stuff...

/bin/sh: can't access tty; job control turned off

when did sodu grub i got  (hd0,0) which should mean there is a hda1, right? 0=1  if im not mistaken >_<  

ill try fiddling with it again tomorrow. thanks for the help so far zxee

---

### Post by cotcot on 2006-09-07
Suggestion. Partition and format the hdd with the Gparted LiveCD. Install ubuntu from the alternate install CD.

Maybe to check. Does your bios supports the disk size you have ?

---

### Post by zxee on 2006-09-07
> **hifimf said:**
> ok so i did the sodu grub thing. restarted and it freezes up on "waiting for   root file system" after a few minutes it switches screens and says...

ALERT! /dev/hda1 does not exist - dropping to shell!

then some other stuff...

/bin/sh: can't access tty; job control turned off

when did sodu grub i got  (hd0,0) which should mean there is a hda1, right? 0=1  if im not mistaken >_<  

ill try fiddling with it again tomorrow. thanks for the help so far zxee

Yes you're correct grub starts counting from 0 (zero)
I agree with cotcot, the alternate cd sometimes succeeds when you have problems with the desktop cd-still it should work.
What is the output from fdisk -l

---

