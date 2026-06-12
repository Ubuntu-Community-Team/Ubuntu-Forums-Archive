---
title: "install to another drive, from current install"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by gcbzzzz on 2011-09-13
tldr; i'm running ubuntu on my box, and want to install another ubuntu instance to another partition. can i simple execute ubuntu-install (or whatever the application is called)?


i have ubuntu 10.10 running on a PC with 2 hard drives.

sda1 = /
sda2 = raid component
sdb1 = nothing (same size as sda1)
sdb2 = raid component

i'm running / from sda1.

drive sda is dying. clicking like crazy, taking LONG time for reads... i just failed it on the raid to be able to use the system.

my data is fine, i just need to reinstall the system on sdb1 and tomorrow add a new disk to the raid.

can i do that from the dying install i'm currently using?

i mean, the system is stable. ext4 is copying with it flawlessly. It's the same as if I were in a live CD for all that matter... is there some way to install the "installer" that sits on the desktop for the live cd?

i'm still searching, but it's hard to find factual information on ubuntu.. all i seems to ever find is step by steps of the basic tasks and common use cases... this forums is what saves me always. anyway... so far i can't even find the name of the executable for the install... asking here already as i fear my time is short :)

---

### Post by gcbzzzz on 2011-09-13
Think i've found an answer

[http://www.debian.org/releases/stable/i386/apds03.html.en](http://www.debian.org/releases/stable/i386/apds03.html.en)

---

### Post by YesWeCan on 2011-09-13
You have no access to a live CD/USB? Well, I would just copy the live fs. Better to copy it to a flash drive and use the copy to do the proper copy, if you follow. But I have copied a live fs and the world didn't come to an end.

Copy using rsync. Close all apps first, try to minimize what is running.

sudo mkdir /mnt/oldroot /mnt/newroot
sudo mount /dev/sda1 /mnt/oldroot
sudo mount /dev/sdxy /mnt/newroot
sudo rsync -vax /mnt/oldroot/ /mnt/newroot/

Then you'll have to edit the fstab in newroot to change the uuid of the / entry
Then use chroot to update and reinstall Grub
Then boot it.

---

### Post by gcbzzzz on 2011-09-13
I have one sd card with debian net install... but my mobo from 2006 does not boot from usb

I did a init 1, and cp -arx old new just to be safe.

Using debootstrap almost worked, the instructions are pre-udev... i didn't know how to create the devfs... it was missing basic stuff, like my hds :)

I ended up burning the debian install on a cd.

It still seems very dumb that i can run the installer fron a livecd but not from the current install....

---

