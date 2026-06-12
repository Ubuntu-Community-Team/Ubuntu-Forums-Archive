---
title: "Problems With Apt-Get/Synaptic After Install"
date: 2005-11-17
forum: Installation &amp; Upgrades
---

### Post by GreenHawkIA on 2005-11-17
Just put a fresh install of Breezy on my Dell Latitude D505 laptop on which Hoary worked perfectly.  However, nowI have a problem.  Both Synaptic and apt-get (run through the command line) return error messages whenever I try to update my system.  They download all the files fine, but whenever they try to install I get the message:
> Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/libssl0.9.7_0.9.7g-1ubuntu1.1_i386.deb (--unpack):
 malloc failed (1761636967 bytes): Cannot allocate memory
Errors were encountered while processing:
 /var/cache/apt/archives/libssl0.9.7_0.9.7g-1ubuntu1.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
Anybody have an idea how I fix this?

---

### Post by Treebeard on 2005-11-17
Maybe you can try this first :
```
dpkg --configure -a 
```

If this doesn't solve the situation:
```
apt-get update
rm /var/cache/apt/archives/libssl0.9.7_0.9.7g-1ubuntu1.1_i386.deb
apt-get --reinstall install libssl0.9.7
```

---

### Post by GreenHawkIA on 2005-11-17
Thanks for the help, but neither one of those worked.  I think the problem is with dpkg, but I can't tell for sure.  I can't install or upgrade anything using apt-get.  It just downloads everything, tries to install, and then I get the error message above.  Any other Ideas?

---

### Post by dcstar on 2005-11-17
[QUOTE=GreenHawkIA]Thanks for the help, but neither one of those worked.  I think the problem is with dpkg, but I can't tell for sure.  I can't install or upgrade anything using apt-get.  It just downloads everything, tries to install, and then I get the error message above.  Any other Ideas?[/QUOTE]
You aren't running our of disk/swap space, are you?

---

### Post by Treebeard on 2005-11-18
It's also possible that your /var partition is corrupted. 
**fsck.ext3** can check your filesystem, but it can also mess up your data. Should you check your fs with fsck, make sure to read the man page and to make a backup of your precious data..

---

### Post by GreenHawkIA on 2005-11-27
The install was fresh enough that I didn't have a whole ton saved, so I just reinstalled from scratch - which of course fixed it.  Thank you all for your help with everything.

---

### Post by jamespi on 2006-05-14
hi,

 i have the same problem but i dont want to resort to reinstallation just yet.
i've done all the things you say above, im not running out of ram and i fscked my disk, no problems.

i am running dapper beta on a 192meg x86 laptop. till now i have had no trouble, lots of updates to install every day, but yesterday ubuntu hung when i tried to shut down. (just got to empty brown desktop background image with spinny mouse pointer). so anyway i switched off without it finishing whatever it was trying to do, now apt-get is broken - when i try to do sudo apt-get upgrade or use the update notifier to update my system i get the following error:

Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/libc6_2.3.6-0ubuntu18_i386.deb (--unpack):
 malloc failed (1521595104 bytes): Cannot allocate memory
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.3.6-0ubuntu18_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

some guy on another thread like this suggested reinstalling dpkg but that sounds horrifiying.

[http://ubuntuforums.org/showthread.php?t=67984&page=2&highlight=malloc+failed](http://ubuntuforums.org/showthread.php?t=67984&page=2&highlight=malloc+failed)

---

### Post by jamespi on 2006-05-17
hi,

it turns out my var directory was indeed corrupt, and that i just didnt understand how to operate fsck.

i fscked the disk, and it jsut returned that the disk had no faults. after googling the "malloc failed" error message, a debian mailing list reported that it was corrupt *.list files reporting huge file sizes that induced dpkg to try to malloc tons of memory.

then i looked in my /var/lib/dpkg/info folder and nautilus hung trying to get the directory info.

so i did fsck --help to see what i missed and it turns out you need to do fsck -f to force it to actually examine and repair the disk, and ignore the (sometimes incorrect) flag that tells it the disk is clean.

once the disk was fscked the list file for gnomeprint2.2 was lost so dpkg complained about this when i tried to install a random .deb file, but nevertheless successfully unpacked and installed the random deb file (phew, dpkg fixed).

then i tried to apt-get gnomeprint and apt failed saying it couldnt load some .so module, so went to an ubuntu mirror website, found the .deb for apt, downloaded it, then used dpkg to reinstall apt, which then worked, then reinstalled gnomeprint using synaptic.

just thought i'd write all this out in  case someone else has any similar problems and finds this thread.

---

