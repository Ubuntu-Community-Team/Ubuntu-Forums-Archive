---
title: "Trying to dualboot windows/unbutu"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by lekidos on 2008-08-19
I have a 400gb hard drive, which is split into 6 partitions:
20gb for windows
80gb for programs
100g for games
50gb for media
50gb for downloads
and the remaining for linux and swap

After going through the DVD ubuntu installer package, trying to get into live cd which wouldn't happen (couldnt get in on 64 but,  worked with 32, but couldnt see any drives to install on), I came to download and burn the x64 alternate install.

After going throguh the prompts, I got to the partitioner.  I deleted the last partition, and split it into a 4gb and a remaining 70ish gb.  Set the 4gb as swap, and the 70ishgb for EX3 formatting, and set as bootable disk with "/" as root.  

Fo through the prompts, installs.  On reboot, I get  GRUB error, loading step 1.5, and it failing.  

I reformat the 2 newly created partitons, and try to reboot into windows to research the issue, and I get another GRUB error, the same one.    I pull out my windows XP disk, and run the repair console, trying "fixboot"   and still error, and then try "chkdks"  and "fixmbr"   Both claimed to have found errors.  When I reboot again, I receive the error invalid boot device.

I finally decide to reformat the windows partition, and reinstall; windows now works fine.  But I still have to problem of installing Linux on my 6th partition. (which, curiously, happens to be /dev/sda10?)

Are my partition parameteres wrong?  I've read how to dualboot, and my DVDs came with a magizne from Linux Identity explainin ghow, but something seems to be going wrong.

PS:  is there a way to manually add the installiationfiles to the partition, and use the windows boot manager instead of grub?

---

### Post by caljohnsmith on 2008-08-19
From what you describe, I think it would be worth running some disk checking programs on your HDD before you do any more installing. Do you have a CD with HDD tools that came with your HDD? If not, you could download the [Ultimate Boot CD]("http://www.ultimatebootcd.com") and use that.

Also, from the Live CD, please post the output of:
```
sudo fdisk -lu
```

---

### Post by Pumalite on 2008-08-19
Go Manual and put root ('/') first and /swap last

---

### Post by lekidos on 2008-08-20
> **caljohnsmith said:**
> From what you describe, I think it would be worth running some disk checking programs on your HDD before you do any more installing. Do you have a CD with HDD tools that came with your HDD? If not, you could download the [Ultimate Boot CD]("http://www.ultimatebootcd.com") and use that.

Also, from the Live CD, please post the output of:
```
sudo fdisk -lu
```


I cant get into live cd  had to use alternate install

---

### Post by Pumalite on 2008-08-20
Get a Knoppix Live CD and take a look;
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

---

