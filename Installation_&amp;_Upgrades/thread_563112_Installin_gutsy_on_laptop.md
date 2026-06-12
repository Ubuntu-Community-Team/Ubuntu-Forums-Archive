---
title: "Installin gutsy on laptop"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by garylouden on 2007-09-29
well my question is:

i have a toshiba laptop which has a 160gb hdd, it came with 2 partitions, 1 for vista and another 74gb partition that is clean for data. I was wondering if i installed usy on the blank partition would it work okay? i have ran the live cd and it works brill, the wireless is great.

another problem i see is that when i want to get rid of linux for any reason how would i go about this?

---

### Post by Pumalite on 2007-09-29
It should be OK. If you have problems; post back.

---

### Post by garylouden on 2007-09-29
i know it will work and everything im just woried about how to get it uninstalled. in what i remember from installing on my desktop once you install it you cant see a partition in windows to format and it had me stuck fr a while.

if i could get some info on how it could be uninstalling i would go ahead. Also is it easy to select what partition you want it installed on so it wont touch my vista instalation. Will it alter ANYTHING on my vista partition?

---

### Post by Pumalite on 2007-09-29
If it did mess up your Vista you would be lucky (just kidding)
It can be easily  uninstalled just erasing the installation and restoring the Vista MBR. No big deal.

---

### Post by garylouden on 2007-09-29
could you go into more detail, how would i go about "erasing the installation and restoring the Vista MBR"

---

### Post by garylouden on 2007-10-01
please can anyone give me this info? im really loving ubuntu but would love the option to have it installed.


Also when i install will it be easy to select the empty partition?

---

### Post by logos34 on 2007-10-01
If you install ubuntu and use Grub to dual boot both OS's, it will overwrite the vista boot manager on the mbr.  If you ever uninstall ubuntu (heaven forbid!) you will need the vista install dvd to restore the bootloader (which I'll bet didn't come with your computer).  Or else boot into vista just before you delete ubuntu and rewrite the vista bootloader to the mbr, then format the linux partition using vista's own disk management tools.  

Antoher option is to send grub to a floppy during ubuntu install, leaving the vista bootloader on the mbr untouched. 

Or 

use vista boot manager to boot linux, in which case you would write grub to the bootsector of the linux root partition, and add an ubuntu entry to vista using [EasyBCD.]("http://neosmart.net/wiki/display/EBCD/Linux")

---

### Post by garylouden on 2007-10-02
yes i use easybsd on my desktop with xp/vista/MACOS/ubuntu

thing is how would i go about doing this when its on the same hdd? with the desktop i just uninstalled all hdd's except the one im installing ubunutu on so it wouldnt auto touch my bootloader

---

### Post by logos34 on 2007-10-02
you're worrying too much.  Use vista boot manager to boot linux if it makes you feel better...if you decide you don't want ubuntu, just delete/format the partition using vista's disk management or gparted on the livecd.  It doesn't matter that it's on the same hard disk, it won't affect vista partition or bootloader.

---

