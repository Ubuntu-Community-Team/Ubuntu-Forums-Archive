---
title: "After new install, no longer able to see Windows partition"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by tinyctim on 2008-07-11
I've just completed installing the latest xubuntu (8.04 Hardy Heron). I have a dual boot system. 8 gigs for Windows, 6 gigs for Linux. For some reason I can no longer see my Windows partition either via Thunar File Manager or when I click the device icon that's in the panel at the bottom of my screen. I started about 6 months ago w/ a LiveCD, then installed on my hard drive. It was then that I chose to partition my hard disc as described above.

Any ideas on what I can do to get my "Gateway" media back (I have a Gateway computer and that's what the FAT32 partition was called)?

---

### Post by Pumalite on 2008-07-11
Check in /media

---

### Post by tinyctim on 2008-07-11
Well, now I have even more problems. But first, the original problem:

I have checked in /media and all I see are my cd drives and my floppy. I used to see something called Gateway and this was my Windows partition. 
It's gone now.

My new problems are:

1. All desktop icons have disappeared.
2. Worse, when I boot into Linux I get a "failed to init. HAL" error message.

I've fooled around a bit with trying to use the Synaptic Package Manager to reinstall hal stuff but I get errors when I do.

Any ideas?

---

### Post by bapoumba on 2008-07-12
> **tinyctim said:**
> Well, now I have even more problems. But first, the original problem:

I have checked in /media and all I see are my cd drives and my floppy. I used to see something called Gateway and this was my Windows partition. 
It's gone now.
Please post the output to :
```
sudo fdisk -l
cat /etc/fstab
```
> **tinyctim said:**
> 
My new problems are:

1. All desktop icons have disappeared.
2. Worse, when I boot into Linux I get a "failed to init. HAL" error message.

I've fooled around a bit with trying to use the Synaptic Package Manager to reinstall hal stuff but I get errors when I do.

Any ideas?
Which errors ?
Please post the output to:
```
sudo apt-get update
```
Do you have auto login on ?
Or look here: [lpbug]25931[/lpbug]

---

### Post by tinyctim on 2008-07-16
I just wanted to say "Thanks" to all who responded. I did try the things suggested (details omitted) but on talking to another friend about my experiences, I decided to "start from scratch."

Because the upgrade took *so* long and because I was dealing w/ a dual boot system, a 14GB hard drive and not much space in the Linux partition (I had a 8GB / 6GB Windows / Linux split), I concluded the best way to go was to install from a newly burned 8.04 .iso *and* use the *entire* 14GB hard drive for Xubuntu. My Windows OS is *gone*. :) (I do have a laptop running Windows ME so when I *need* to do Windows, I can). I actually did try to repartition my hard drive to be dual boot. I wanted the split to be more like 5GB / 9GB Windows / Linux but I was unable to figure out how to do this.

The installation took about an hour I think. I did have a little trouble getting Flash going (YouTube didn't work) but I finally got it going with the help of the suggestions at [http://ubuntuforums.org/showthread.php?t=766683&highlight=youtube+flash]("http://ubuntuforums.org/showthread.php?t=766683&highlight=youtube+flash")

Since then, I've added Java, FileZilla, burned a CD, printed a couple of things, installed a couple of favorite extensions to Firefox etc.

Still learning and loving Linux!

Thanks!

---

### Post by bapoumba on 2008-07-16
Thanks for reporting back, and congrats :)

---

