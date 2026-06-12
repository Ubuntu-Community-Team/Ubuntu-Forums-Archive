---
title: "Quick question about Photorec (Data Recovery, need help mounting USB drive)"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by diablo75 on 2007-07-24
I have a hard drive that I want to analyse with photorec and export it's findings and recovered files to an external hard drive.  The problem is that when it asks me where I want to copy the files to...I don't know where to go or what to select.

I'm using a gparted live cd, and in the gui, the USB drive shows to be mounted as dev/sda1, but in photorec inside a terminal, there is no sda1.  What do I do?

---

### Post by marcelinoM on 2007-07-25
Why are using Photorec inside GLiveCD ?   Hard to say what the problem...Photorec is available within Ubuntu.  I just used it within 7.04 to recover files from SD card.  

A few guesses for GPartedLiveCD...

type:

fdisk -l

To see disks available.

---

### Post by marcelinoM on 2007-07-25
I would say photorec is older release which does not see the media.  Ubuntu 7.04 has Photorec 6.5

---

### Post by diablo75 on 2007-07-26
Well, the reason I was using a live CD is that there there was an NTFS partition on the hard drive before formating and installing Ubuntu.  I know, I know, people will be like, "You're screwed...won't find anything."  I beg to differ.  There is data remaining on this 100 GB hard drive that Ubuntu has not overwritten yet, and I'd like to try and extract what I can from it.

So, you recommend that I use a 7.04 live CD instead of a gparted CD?

---

### Post by az on 2007-07-26
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)



You can use foremost if photorec is not allowing you to write to a certain place.

But to answer your question, you need to mount the usb drive.  You can't write to a device, you need to mount it and then write to it's mountpoint.

sudo mount /dev/sda1 /mnt

then specify that you want to write to /mnt

---

### Post by az on 2007-07-26
> **diablo75 said:**
>  I know, I know, people will be like, "You're screwed...won't find anything."  I beg to differ.  There is data remaining on this 100 GB hard drive that Ubuntu has not overwritten yet, and I'd like to try and extract what I can from it.


Of course you can recover data.  I charge $100 to $200 for that service.

---

