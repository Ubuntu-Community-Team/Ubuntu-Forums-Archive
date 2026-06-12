---
title: "[SOLVED] end of my rope =("
date: 2007-12-30
forum: Installation &amp; Upgrades
---

### Post by Coroney on 2007-12-30
I've been trying to get xubuntu installed for quite a while now.

My CD drive shoots out IO errors like mad so I've had to do an hd-media install from an iso image (of the alt CD) on another partition.  Everything seemed to install fine and I told the installer to install the xubuntu desktop and it did some stuff then asked to be rebooted.

now I come to a command prompt and can't seem to start X for love nor money.  Seems it's not installed afterall.  So, ok, I'll just do a:

sudo apt-get install xubuntu-desktop

Right?

NO, because that just asks me to put in a CD, which I can't get data off of.   =(

Does anybody have any ideas how I can get into X?  This is seriously disheartening.

thanks so much

---

### Post by jualin on 2007-12-30
what version of xubuntu are you trying to install, server or desktop?. Because I have heard that the server one does not have a GUI only terminal. So maybe you should check what version you have. If you keep on getting issues try the alternate CD, you could find it in the xubuntu website. When you are installing from the alternate CD it asks you if you want to install xubuntu with GUI or with just the command prompt.

---

### Post by jflaker on 2007-12-31
> **Coroney said:**
> I've been trying to get xubuntu installed for quite a while now.

My CD drive shoots out IO errors like mad so I've had to do an hd-media install from an iso image (of the alt CD) on another partition.  Everything seemed to install fine and I told the installer to install the xubuntu desktop and it did some stuff then asked to be rebooted.

now I come to a command prompt and can't seem to start X for love nor money.  Seems it's not installed afterall.  So, ok, I'll just do a:

sudo apt-get install xubuntu-desktop

Right?

NO, because that just asks me to put in a CD, which I can't get data off of.   =(

Does anybody have any ideas how I can get into X?  This is seriously disheartening.

thanks so much

Try reburning the CD at 4X...........I had this for a bit in the beginning, but solved it by reburning the image @ 4X

---

### Post by ken22 on 2007-12-31
If you have a working net connection, and you want to install xubuntu-desktop that way, edit this file: (I use emacs, you use whatever editor you use.)
```
sudo emacs /etc/apt/sources.list
```

and comment out the cdrom source:

```
# deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
```

then ```
sudo apt-get update
```

then ```
sudo apt-get install xubuntu-desktop
```

-------------------------------------------------------
[Tea by the Fire]("http://hespera.ucd.ie/ops/ken/wordpress")

---

### Post by Coroney on 2007-12-31
I did use the alt CD to install (I mentioned this in my original post) and it was the xubuntu alt CD.  (desktop version)

as far as the IO errors go it isn't the data on the CD, it is fine, the drive is just dying, it doesn't read anything well.

Cool idea ken, but I only have wireless and I highly doubt that I would be able to get it working on this machine  ...it'll need ndiswrapper and all that, although I'll look into it.


**Does anybody know how I can mount that iso image on the other partion as my cd rom?  That partition is not currently mounted.  I'm pretty sure it's possible, but I don't know how to do it.**

---

### Post by meindian523 on 2007-12-31
You can use the loop devices,I did it once but I don't remember the exact thing now.

It was something like:

```
mount -some options  /path/to/your/ISO /dev/loop0 something
```

That doesn't look much useful,but a good example is given in the mount man page,please look that up.

---

### Post by Coroney on 2007-12-31
thanks, that's what I was thinking of.

although I actually didn't use that I just solved my problem.

I edited the grub menu.lst file to point to the .iso again and reran the installer...  this time everything went perfectly and X is working...


I think maybe I somehow skipped over the installation of xubuntu-desktop last time...   uhg...   well, at least I learned some new tricks from all of this.

Thanks to you all for sharing your insight!

---

### Post by allforcarrie on 2007-12-31
try a WUBI install form windows...

---

### Post by meindian523 on 2007-12-31
Um,could you post your menu.lst with the changes you made highlighted?At best,we might gain an insight into an alternative way of doing things....and did you lose any data(which you couldn't afford to lose) when you reinstalled?

Also,please mark the thread solved.

---

### Post by Coroney on 2007-12-31
> **allforcarrie said:**
> try a WUBI install form windows...

didn't have windows, this is a clean computer, albeit a beater.


as far as grub goes, I couldn't tell you exactly since xubuntu wiped out grub when I finally got it to install.  But I believe it was something like this that I used to launch the installed from .iso file that I had on a linux formated (but unmounted in xubuntu) partition.

root (hd0,2)
kernel /home/boot/vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd /home/boot/initrd.gz

I didn't lose any data because I did not format the partition with the installer .iso on it in the xubuntu install. (had a few other things on that partition but nothing important even if I did)

---

