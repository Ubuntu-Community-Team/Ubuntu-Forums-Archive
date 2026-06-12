---
title: "Error mounting volumes"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by javierdl on 2012-11-05
Hi all,

Please bare with me, I'm a total rookie with Ubuntu/Linux :(

I'm running Ubuntu 12.04 from a USB key drive (4Gb). I was able to install some apps in the USB drive but it ran out of space quickly. It would be great if I could install more on the local Hard drive partitions. Problem is, I get the error below when attempting to mount them with Disks.

" Error mounting filesystem
Adding read ACL for uid 999 to '/media/ubuntu' failed: Operation not supported (g-io-error-quark, 15) "

Any ideas?

Thanks in advance guys :)

JDL

---

### Post by darkod on 2012-11-05
A 4GB stick is barely enough to install ubuntu on it. It will not have free space to work with.

Since you plan to use some hdd space too, why not simply install on that hdd space?

Or get an 8GB or 16GB stick (better 16GB).

---

### Post by demuxer on 2012-11-05
If your live-usb installation needs more space use 
```
sudo apt-get clean
```

this will erase old .deb and packages downloaded/used when you installed apps

---

### Post by javierdl on 2012-11-05
darkod,
I was surprised too when I saw in the "[Create a USB stick]("http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows")" page that even a 2Gb USB stick would do.
I think back with Ubuntu 10 the stick was required to be at least 4Gb.
Thanks for the advise.

Demuxer,
Thanks for the code, sure it'll come in handy.

I remember when trying release 10 I was able to access my local hard drives. And using them was not a problem at all. Whether it was to move files in/out or even installing programs.
Now with release 12.04 I can see the local drives icons, but I can't open them. I used "Disks" to attempt to mount the largest hard disk I have, but I only got an error.

JDL

---

### Post by darkod on 2012-11-06
There is no surprise for Create a Start up disk. I misunderstood that you have ubuntu INSTALLED onto the stick as a destination.

For creating a bootable usb stick to run ubuntu in live mode from it, or install it on a computer, even a 1GB stick is enough since the ubuntu CD is 680-750MB.

But in that case that is only a live usb, usually called. If you make space for persistancy it can keep some settings and packages you install after a restart, but in most cases is not used to really run ubuntu from it. If you want a stick with full ubuntu that you can run on many computers, usually you would make a full installation on the stick. But it wouldn't allow you to do that on 4GB, it needs a minimum of 4.7GB or similar.

---

### Post by javierdl on 2012-11-07
darkod,

Ahh! Now I get it! Thank you so much for the clear explanation.
Indeed I wanted to have the full installation on the USB stick. No wonder I could only run the try out. Oh well! Now I have it installed on the local hard disk.
I love it so far! It's considerably better than the last time I tried it (10).

JDL

---

### Post by jsantander on 2012-11-08
If I may. I just had the same problem. I Created a persistent USB with Lili ([http://www.linuxliveusb.com/](http://www.linuxliveusb.com/))  and I was unable to mount any of my drives (all indicated *"Adding read ACL for uid 999 to `/media/ubuntu' failed: Operation not supported (g-io-error-quark, 15)"*)

It seems that the problem has nothing to do with free space, it is simply that the /media/ubuntu directory does not exists.

Solution, open a terminal and 
sudo mkdir /media/ubuntu

I've just done it and I could then mount the drives. I wonder if the directory will still be there next time I boot... but at least I know how to fix it.

---

### Post by StefanSTS on 2013-02-02
> **jsantander said:**
> It seems that the problem has nothing to do with free space, it is simply that the /media/ubuntu directory does not exists.

Solution, open a terminal and 
sudo mkdir /media/ubuntu

Thanks, that solved my problem on a Live USB with Ubuntu 12.10 to recover my files from my harddrive.

Switching from Win XP to dual boot now, after long time back to Linux. Thanks for this easy and feature full OS.

Stefan

---

### Post by rapidvagabond on 2013-04-03
This guy... Saving me from a nervous breakdown.

---

### Post by Juanxho on 2013-04-07
> **jsantander said:**
> If I may. I just had the same problem. I Created a persistent USB with Lili ([http://www.linuxliveusb.com/](http://www.linuxliveusb.com/))  and I was unable to mount any of my drives (all indicated *"Adding read ACL for uid 999 to `/media/ubuntu' failed: Operation not supported (g-io-error-quark, 15)"*)

It seems that the problem has nothing to do with free space, it is simply that the /media/ubuntu directory does not exists.

Solution, open a terminal and 
sudo mkdir /media/ubuntu

I've just done it and I could then mount the drives. I wonder if the directory will still be there next time I boot... but at least I know how to fix it.

Without words. You're a genius. Thank you very much for your cooperation and great help!

---

