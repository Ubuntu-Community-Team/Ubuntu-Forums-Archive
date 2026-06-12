---
title: "Create COPY of my running system"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by lynxus on 2007-06-21
Hi guys,

I now have a PERFECT running copy of ubuntu now, Everything runs how i want it. hardware,beryl, sssh etc etc etc


Is it possible to create a copy of this so if it ever breaks i just put a DVD in or ( dvds ) and it will install this again for me exactly how it is...

So, lets say i backed it up over 4 DVD's i could enter DVD1 it would boot then install back to how it is now off that..

Any ideas?

Thanks
Graham

---

### Post by Uriel2006 on 2007-06-21
> **lynxus said:**
> Hi guys,

I now have a PERFECT running copy of ubuntu now, Everything runs how i want it. hardware,beryl, sssh etc etc etc


Is it possible to create a copy of this so if it ever breaks i just put a DVD in or ( dvds ) and it will install this again for me exactly how it is...

So, lets say i backed it up over 4 DVD's i could enter DVD1 it would boot then install back to how it is now off that..

Any ideas?

Thanks
Graham

Yes, it is possibile and perhaps is not an idea, due it is really old.
It will take a snapshot of your system as is.

man dump
man restore

;)

Uriel

---

### Post by coffeecat on 2007-06-21
I use tar and backup to an external usb HD. Since your personal profile details say you are a 'Feisty Fawn Testing User' (it has been released now you know :wink: ) I won't patronise you with details, but this is what I would do. (In fact my machines are all set up as multiboots so I can make tar archives from a distro on another partition, but the principle is the same.)

1 Boot up with live CD, make mountpoint and mount root partition of HD installation to mountpoint.

2 Plug in USB drive and let live CD automount it.

3 cd to mountpoint and then 'tar -czvf /media/usbdrive/filename.tar.gz * '

If you need to roll back to an earlier version you simply boot up with the live CD again, delete everything in your HD root partition and then untar the archive into the now-empty partition. You could reformat the partition but beware. I think this changes the UUID and Feisty references partitions by UUID in /etc/fstab. Search the forum for details.

If you've spread your installation over more than one partition (separate /home, /boot whatever) you simply have to make as many tarballs as there are partitions. Not as elegant as your idea of a self-booting self-installing DVD but it works. I've cloned/moved installations and restored earlier versions this way many times.

> **lynxus said:**
> So, lets say i backed it up over 4 DVD's

:shock: Just how much have you got there? :lol: A default install of Feisty is only just over 2 GB and a tarball of this will be much less than half.

---

### Post by lynxus on 2007-06-24
The big storage size is due to the amount of other crap installed that id rather not go through again lol

---

