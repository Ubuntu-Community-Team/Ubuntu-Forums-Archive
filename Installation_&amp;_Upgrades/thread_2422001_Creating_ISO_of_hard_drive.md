---
title: "Creating ISO of hard drive"
date: 2019-06-30
forum: Installation &amp; Upgrades
---

### Post by papage on 2019-06-30
Hi Everyone,

I'm wanting to create an ISO of my Hard drive (Ubuntu 16.04 LTS) with all metapackages and data included in the ISO. I've read you can use the dd command but I haven't seen a definitive answer other than something like:
```
sudo dd if=/dev/sda of=file.iso
```
I was wondering if anyone can verify this for me and also assist me with how I would make this bootable to reinstall itself? As in if I put the ISO on a USB, how do I make it easy enough to install back onto a drive?

The drive I'd be installing to would be clean with no OS as what I am trying to do is generate a backup of the whole drive (OS and all). I've looked into clonezilla but it doesn't look very user friendly and the initial backup it creates is all files?

Thanks, Grant.

---

### Post by rbmorse on 2019-06-30
Is your intent to just make a backup of the machine in a "clean" state, or would you be looking to be able to boot any PC with a disk reader into your personalized Ubuntu environment?

---

### Post by papage on 2019-06-30
> **rbmorse said:**
> Is your intent to just make a backup of the machine in a "clean" state, or would you be looking to be able to boot any PC with a disk reader into your personalized Ubuntu environment?

The goal is to create an image of the hard drive and be able to restore the hard drive to that image. I have begun the process with clonezilla but do not have any progress to report yet. Definitely still open to ideas

[SIZE=6]**EDIT**[/SIZE]:
I followed:
[https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image](https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/01_Save_disk_image)
and then
[https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/04_Create_Recovery_Clonezilla](https://clonezilla.org/show-live-doc-content.php?topic=clonezilla-live/doc/04_Create_Recovery_Clonezilla)

and was able to create a recoverable disk image. I thought clonezilla would be hard to use based on appearance but following these guides helped.

The image I made does not support resizing and I would appreciate it if someone could point to me how to enable the resizing in cloning :) (250Gb SSD -> 120Gb SSD)

---

### Post by Artim on 2019-07-01
I like (and need) simple and graphical tools for such jobs.  My favorite for making restore points *and* making bootable iso of my installed system with all the changes I have made (settings, bookmarks, etc) is called **SystemBack**.  A link to it's installation is [here](https://www.linuxbabe.com/ubuntu/install-systemback-ubuntu-18-04-bionic-18-10).

---

### Post by rbmorse on 2019-07-01
For what you want, Clonezilla is my choice.  

I have a chicken superstition about messing around with disk parameters while in the process of copying/cloning/moving partitions or disk images.  Resize first, then clone. It makes things less messy if there is a problem.

---

### Post by C.S.Cameron on 2019-07-01
I have been playing with:
dd if=/dev/sdx of=papage.img
where sdx is your Hard drive.
See [https://askubuntu.com/questions/1153912/how-do-i-put-oem-installation-into-live-usb?noredirect=1#comment1919618_1153912](https://askubuntu.com/questions/1153912/how-do-i-put-oem-installation-into-live-usb?noredirect=1#comment1919618_1153912)
I understand 
sudo dd if=/dev/sda of=file.iso 
works, but you cannot Boot the resulting ISO as if it was a Live USB.

---

