---
title: "hal-storage-fixed-mount refused uid 999"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by xsintill on 2007-10-24
Tried to upgrade from kubuntu 7.04 to kubuntu 7.10 through the official way. but when it was installing after aprox. 10% was done the installer got stuck and wouldn't do anything. I had to restart but the system wouldn't start up anymore so i now i have to do a full install. i backed up all the files i needed to with the ubuntu 7.04 DVD which let's me see all the drives i wanted to. problem i now have is the installer only let's me know on which drives i can install but i would like to know what is on these drives so i can wipe off anything on it without worrying i chose the wrong harddisk. 
the Kubuntu install disk won't let me see the files/folders on any drive giving me back the following error:
hal-storage-fixed-mount refused uid 999

Why does 7.10 refuse access to all my drives and 7.04 will show me everything.
Is there a way to get rid of this pesky error.

Thanks in advance

xsintill

---

### Post by xsintill on 2007-10-25
ok i had to mount all the drives manually.
```
sudo mount -t ext3 /dev/sdb1 /media/sdb1
```
this finally worked for me. i found out which drive it was i needed to use for the installation.
I don't understand why they didn't make this automounted, o well hopefully this will be the only problem i'll be having with the new installation

---

### Post by theonhighgod on 2008-02-02
I have the same problem,  when i try to use a kde application to mount a hard drive, i figured maybe i needed to be in the hal-deamon group, but that did nothing so i shall not explain how i did it, 

I've tried reading a few translations from google, but none seem to have a conclusion bar using the command line, Its mildly annoying for me, but for new users it could be quite the bear trap :(

i think there is a bug fix already open about it, but its hard to distinguish between the various mount based issues,

good luck!

---

