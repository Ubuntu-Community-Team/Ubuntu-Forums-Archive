---
title: "PROBLEMS WITH DUAL boot 2 hdd's"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by badmancaymanian on 2007-06-19
I tried to install ubuntu 7.04 on new hard drive. This means i have 4 total physical hard drives. I went through the install and set gurb to install on the new drive(using the advance button). When i restarted i get the grub menu but if i try to launch any of the OS's i get error 17 failure to load partition. Anyone know how to fix this?


oh yea i disconnected the new drive and windows still loads fine so grub is for sure on the new drive.

---

### Post by confused57 on 2007-06-19
> **badmancaymanian said:**
> I tried to install ubuntu 7.04 on new hard drive. This means i have 4 total physical hard drives. I went through the install and set gurb to install on the new drive(using the advance button). When i restarted i get the grub menu but if i try to launch any of the OS's i get error 17 failure to load partition. Anyone know how to fix this?


oh yea i disconnected the new drive and windows still loads fine so grub is for sure on the new drive.

Highlight your Ubuntu entry in your grub boot menu, press "e", change root from (hdx,y) to (hd0,y), then press "b" to boot...this is temporary, but should get your Ubuntu booted.  You can make it permanent in your /boot/grub/menu.lst.  (Note:  You'll need to press "e" again to edit the root entry).

---

### Post by badmancaymanian on 2007-06-19
my hd0 is my windows hard drive. i just changed the boot sequence so my ubuntu hard drive loads first. so do i still change it to hd0 instead of hd3?

i am very new to this but were do i edit it to make it a permanent change?

---

### Post by confused57 on 2007-06-19
> **badmancaymanian said:**
> my hd0 is my windows hard drive. i just changed the boot sequence so my ubuntu hard drive loads first. so do i still change it to hd0 instead of hd3?

i am very new to this but were do i edit it to make it a permanent change?
When you boot first to your Ubuntu drive, it becomes hd0 to grub; so try the temporary method of pressing "e"...if it boots your Ubuntu, edit your menu.lst:

Open a terminal(Applications---Accessories---Terminal):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
copy & paste each line one at a time, press "enter" after each line.
make the changes, quit & save...make sure to change the line with groot to (hd0,y), also.

You can probably add an entry to grub to boot your Window's drive.

---

