---
title: "The current kernel upgrade wont install"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by baracuda68 on 2007-12-20
Hi.   Using Gutsy, 
The current kernel upgrade wont install. I get the message , with adept:
There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages. 

With apt-get I get this:

bob@baracuda:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  linux-image-2.6.22-14-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/18.5MB of archives.
After unpacking 4096B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 174800 files and directories currently installed.)
Preparing to replace linux-image-2.6.22-14-generic 2.6.22-14.46 (using .../linux-image-2.6.22-14-generic_2.6.22-14.47_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.22-14-generic ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.47_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./lib/modules/2.6.22-14-generic/kernel/drivers/net/ppp_generic.ko')
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.22-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.47_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have the updates "available icon" sitting in my tray bugging me now and it wont go away because of this.

Any ideas??:confused:

---

### Post by yabbadabbadont on 2007-12-20
Delete the .deb file so that it gets downloaded again.  Sounds like it might be corrupted.

```
sudo rm /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.47_i386.deb
```

---

### Post by PmDematagoda on 2007-12-20
baracuda68 please don't start duplicate threads as it is not allowed on the forums, and I already gave you the same solution as given by yabbadabbadont in your other thread.

---

### Post by yabbadabbadont on 2007-12-20
<Homer>DOH!</Homer>

I didn't think to check if it was a dupe.  Glad to know that someone seconds my opinion though.  :D

Edit: I guess I seconded *your* opinion, since you posted your suggestion first.  ;)

---

### Post by PmDematagoda on 2007-12-20
> **yabbadabbadont said:**
> <Homer>DOH!</Homer>

I didn't think to check if it was a dupe.  Glad to know that someone seconds my opinion though.  :D

Edit: I guess I seconded *your* opinion, since you posted your suggestion first.  ;)

:lolflag:, the chances of duplicate threads occurring are rather little, and the chances of actually finding them are rather smaller, so there might have been a situation where *you* found the duplicate thread before me:). And thanks for seconding my opinion:D. And nice to see another The Simpsons fan other than myself:).

---

### Post by baracuda68 on 2007-12-21
> **PmDematagoda said:**
> baracuda68 please don't start duplicate threads as it is not allowed on the forums, and I already gave you the same solution as given by yabbadabbadont in your other thread.


Sorry about dupin'...I'll try to control myself next time :) Posted early this morning and got no hits :( I know...no excuse! Thanks anyways!

---

### Post by baracuda68 on 2007-12-21
> **yabbadabbadont said:**
> Delete the .deb file so that it gets downloaded again.  Sounds like it might be corrupted.

```
sudo rm /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.47_i386.deb
```


This worked great. I hope remember this next time that it happens! thanks!

---

### Post by Sef on 2007-12-21
Locked Duplicate Thread.  [Orginal Thread]("http://ubuntuforums.org/showthread.php?t=645595").

---

