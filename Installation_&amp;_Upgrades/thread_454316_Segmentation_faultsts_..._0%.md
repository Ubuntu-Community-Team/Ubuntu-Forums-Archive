---
title: "Segmentation faultsts ... 0%"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by jamaas on 2007-05-25
I had a system that worked fine and now synaptic is not working,

I tried apt-get and get this error
Segmentation faultsts ... 0%

I've read several posts, and deleted 
/var/cache/apt/*.bin 
but I still have something called
pkgcache.bin that belongs to some user other than root and thus I can not remove it ... :-(

drwxr-xr-x  4 root    root       4096 2007-05-25 16:32 .
drwxr-xr-x 20 root    root       4096 2007-05-14 12:19 ..
drwxr-xr-x  3 root    root      69632 2007-05-25 14:33 archives
drwxr-xr-x  3 root    root      73728 2006-04-15 08:36 archives.save
?rwxr--r-t  2 7157577 14009 876819778 1999-02-04 05:57 pkgcache.bin


Any suggestions on how I can get rid of this segmentation fault?

Relative noob here, thanks a bunch.

Jim

---

### Post by ruy_lopez on 2007-05-25
Try removing the sticky-bit (the "t" in the permissions), by typing this:
```

sudo chmod -t pkgcache.bin
```

then "ls -l" again to see if it removed the "t", then "sudo rm pkgcache.bin".

Was it giving segmentation errors before you removed everything else in the /var/cache/apt directory?

---

### Post by jamaas on 2007-05-25
Thanks Ruy ... but no luck !
got this!  Do I need to get to filesystem using the install cd or knoppix or something like that to delete it?
Thanks

Jim

sudo chmod -t pkgcache.bin 
chmod: changing permissions of `pkgcache.bin': Operation not permitted

> **ruy_lopez said:**
> Try removing the sticky-bit (the "t" in the permissions), by typing this:
```

sudo chmod -t pkgcache.bin
```

then "ls -l" again to see if it removed the "t", then "sudo rm pkgcache.bin".

Was it giving segmentation errors before you removed everything else in the /var/cache/apt directory?

---

### Post by ruy_lopez on 2007-05-25
It looks like a nasty one. It might be a file system corruption or something (judging from the "?" on the file-type bit). You might want to try running fsck from the live CD on the unmounted partition.

Run "df" to find the device, should be something like /dev/hda2 (look for the specific number it has alongside the name of your main volume.)

Then boot into a LiveCD console and try "fsck /dev/hda(number from above)"

First, though, you could try a variety of "rm" flags. Try "rm -r" in case it thinks the file is a directory. And use "ls -li" to find the inode. Then try removing it using this (from within the /var/cache/apt dir)
```

find . -inum inode_number -exec rm -rf {} \;
```

where inode_number is the number that appeared next to the file when you ran "ls -li".

---

### Post by jamaas on 2007-05-25
You are a good sport, will give it a try and be back shortly!

:-~

---

### Post by jamaas on 2007-05-25
Just for the next poor person who has this problem!

 ls -li
total 16532
589963 drwxr-xr-x 3 root    root      69632 2007-05-25 14:33 archives
  1863 drwxr-xr-x 3 root    root      73728 2006-04-15 08:36 archives.save
  1830 ?rwxr--r-t 2 7157577 14009 876819778 1999-02-04 05:57 pkgcache.bin
 

and then got

 find . -inum 1830 -exec rm -rf {} \;
rm: cannot remove `./pkgcache.bin': Operation not permitted


hmmmm .... :-(

back in a minute!

Jim

---

### Post by jgcamp99 on 2007-08-31
After using Ubuntu for well over a year, I finally got this Synaptic and Update Manager corruption too. My hard drive on my notebook (Dell L400) continually reads and is far too active. I've tried the cache removal of files and have the same remaining file. I'm just going to reinstall Ubuntu and be done with it, rather than fish around the internet for a fix.

With mine, Synaptics gets 97% done, with Update Manager, the program hangs earlier. Things like System Monitor and the Add/Remove under the menu for Applications try to start and immediately crash. I figure since my hdd is acting this way. Repairing it is a band aid for a clean install that needs to be done. Good for me that I did back up the personal files I have and it's recoverable. I think my next backup will be a disk image so that I don't have to go thru the whole PXE network install process over again. That's the issue with the Dell L400, I don't have the floppy/cdrom that boots it and the bios won't allow for a usb drive boot. Anyway, almost wished this had happened in April & November if it was going to happen at all. That way it coincides with new releases of Ubuntu.

---

