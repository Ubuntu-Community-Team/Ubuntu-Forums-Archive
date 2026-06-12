---
title: "[SOLVED] Reinstall"
date: 2008-03-23
forum: Installation &amp; Upgrades
---

### Post by barnowl13 on 2008-03-23
Can anyone tell if I use the live CD to reinstall would it create a new partion or would it automatcial install over ubuntu that is already installed?

Reason I ask this question I am having problems with it at the moment I had 6.10 but could not get connected to the internet I solved this problem and upgraded to 7.10 but now I get to the log in screen no problem enter user name and password then just get a blank screen which is in ubuntu colours but no icons just a blank screen?

---

### Post by Pumalite on 2008-03-23
You can use the Live CD< go -Manual- and point to the partitions used before.

---

### Post by barnowl13 on 2008-03-23
Thank you for that I will go and try that now and hopefully I will not back, thanks again for your help.

---

### Post by Pumalite on 2008-03-23
You are welcome. Good luck.

---

### Post by barnowl13 on 2008-03-23
Sorry to be a pain but I am back I went into manual and this came up.
/dev/hda1 ntfs /media/hda1 20974mb 15200mb
/dev/hda5 ntfs/media/hda5 89639mb 69700mb
/dev/hda6 swap                      542mb 0mb
/dev/hda3 ext3/media/hda3 11778 5700
/dev/hdb1 ntfs /media/hdb1 20974mb 16399mb
/dev/hdb5 ntfs /media/hdb5 101960mb 71800mb

How can I tell which one has ubuntu on?
looking at my drive D it shows Linux swap 517.69mb linux 10.97gb 
so would I tick both /hda6 swap  and the hda3 ext3 boxes?
Sorry if I am coming over a bit thick but just don't want to balls this up?
Thanks again for your help.

---

### Post by Pumalite on 2008-03-23
hda3 and hda6 look to me like the ones.

---

### Post by barnowl13 on 2008-03-23
Sorry I am back again I went into manuel and tick the box for hda3 ext3 when I pressed forward I got message "No root file system is defined please correct this from partitioning menu" I could not place a tick in HDA6 swap?

---

### Post by Pumalite on 2008-03-23
If hda3 is the partition for your systemfile, go vmanual, first delete it. Then make 'New' partition, leave the size untouched, where it says 'mount point', you have to plant a simple / in the blank space. /swap has it's own format.

---

### Post by barnowl13 on 2008-03-23
Okay it has worked and much better than before it seems to have installed itself correctly Thank you I could not have done it with out your help so thanks again and hope I will not have the same problem when Hardy Heron comes out. I looking forward to it as have red lots of good things about it. Thanks again!!!

---

### Post by Pumalite on 2008-03-23
Happy Ubuntuing!

---

