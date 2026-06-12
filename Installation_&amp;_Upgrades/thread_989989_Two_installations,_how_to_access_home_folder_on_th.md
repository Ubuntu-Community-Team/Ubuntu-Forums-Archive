---
title: "Two installations, how to access home folder on the other partion?"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by musta78 on 2008-11-22
Hi
I've got one Xubuntu 8.04.1 that I'm running my currently setup.
I've installed ubuntu server 8.04.1 on another partion.  I do not have a desktop on this, so I'm only able to use console.  

Before I do the complete switch I want to do a complete test.  I'm using XBMC and have some issues with cpu running very high in idle on a hd3200 screencard.  

On this server edition I've got some very promising results where idle is down to only 2% ( in the other it is around 90 to 100%).

But I can't figure out how to access the home folder on the other partion!

---

### Post by theApokalypsis on 2008-11-22
So I understand you want to access the home folder on the Server edition from you Xubuntu desktop edition?

If you mount any partition it should show up in /media folder of your file system as whatever named folder your partition was named.

like ex /media/disk/home

am i off? lol

---

### Post by musta78 on 2008-11-22
Vice versa.

So how do you mount a partion in console?

---

### Post by lswb on 2008-11-22
I suggest something like this: While running the server system, make a mountpoint:

sudo mkdir /xfce

Run the command "sudo fdisk -l" and/or "sudo blkid" From the output you should be able to identify which partition your desktop system is using. Lets day it is /dev/sda3 and uses the ext3 filesystem

Then you can mount it:

sudo mount -t ext3 /dev/sda3 /xfce

Now you can access all files on the xubuntu partition through /xfce. If this is what you want, put an appropriate entry in /etc/fstab of the server system so it is automatically mounted at boot. You can search for other threads on how to do that and see the man pages for mount and fstab.

---

### Post by musta78 on 2008-11-22
Thanks for pointing the way!  I will give this a shot tommorow!

---

### Post by musta78 on 2008-11-23
This was what I did to make it work!

sudo fdisk -l
sudo mkdir /media/hardy
sudo mount /dev/[partition hardy is installed on] /media/hardy

---

