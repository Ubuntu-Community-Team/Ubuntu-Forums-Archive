---
title: "Install Ubuntu 16 LTS on existing media - DELETE EVERYTHING"
date: 2017-11-24
forum: Installation &amp; Upgrades
---

### Post by graystrickland on 2017-11-24
Surely something obvious escapes my grasp, because it shouldn't (seem to) be this difficult.

GOAL: install Ubuntu 16.04 LTS on existing media (which has had two previous Ubuntu installations) and **_blow up (delete) all pre-existing partitions_ **in the process.

PROBLEM: When I try to install Ubuntu and get to the *Installation Type *screen: 

[https://i.stack.imgur.com/KURnS.png](https://i.stack.imgur.com/KURnS.png)


and select (1) ***Erase all***... and (2) ***Use LVM***... and (3) ***Something Else ***then I get this:

[http://i94.photobucket.com/albums/l100/graystrickland/IMG_20171124_155003_zpshqre1qrl.jpg](http://i94.photobucket.com/albums/l100/graystrickland/IMG_20171124_155003_zpshqre1qrl.jpg)

When I try to create a new partition table for /dev/sda, then I get the error ***No modifications can be made to the partition #5 of device SCSI1 (0,0,0) of (sda) for the following reasons: [COLOR=#ff0000]In use by LVM group ubuntu-vg[/COLOR].***

[http://i94.photobucket.com/albums/l100/graystrickland/IMG_20171124_155022_zpsm7uzonlr.jpg](http://i94.photobucket.com/albums/l100/graystrickland/IMG_20171124_155022_zpsm7uzonlr.jpg)

I just want to BLOW UP EVERYTHING (and install Ubuntu 16.04 LTS).

There is *nothing* on this computer that I need or want to save.

How can I just do a destructive installation that deletes all existing partitions, creates any required (new) partitions and installs the new operating system?

---

### Post by ian-weisser on 2017-11-24
I'm confused.
If you want to erase your disk, why aren't you choosing "Erase disk and install Ubuntu"?

You must use LVM tools to modify LVM partitions. Non-LVM tools, as you have discovered, don't work.

---

### Post by graystrickland on 2017-11-24
Your patience is greatly appreciated.

Upon reading your reply, I realize that I'm an ***idiot.***

I thought that I was selecting (1) to erase everything **_AND_** (2) use LVM in the new installation. 

By just selecting "*erase disk*..." I was able to get what I wanted. 

Thank you for your patience.

---

### Post by wildmanne39 on 2017-11-24
Please use thumbnails or url's when posting images because many people have slow or limited connections.

---

### Post by ian-weisser on 2017-11-24
I'm glad you got it sorted. 

Please use the Thread Tools button at the top of the page to mark the thread as [SOLVED]

---

