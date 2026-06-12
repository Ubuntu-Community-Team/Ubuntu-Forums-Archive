---
title: "Problem Dual Booting after update"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by S3TH88 on 2008-06-29
Hello, I'm pretty new to ubuntu, and linux in general.  I decided to install it on my laptop this summer to see what it was like.  I decided to dual boot with Windows Vista (which I already had on my laptop).  The installation went fine and for a while I had Vista and Hardy Heron working nicely together.

For the last month I've been less ambitious in learning about ubuntu and have been using Vista mostly.  Today I decided to boot up the Ubuntu partition and saw that I had a bunch of updates to install.  After they were installed it prompted me to restart and when I did my Windows choice was gone from the GRUB menu.  I can't figure out how to boot into windows again.  

I'm sure the files are still there because in Ubuntu, under "places", there is a drive called "OS" that has all the files on my Vista partition.  This still works and I can find all my files, but is there any way to actually run windows again?  

Any ideas?  I'm not sure what you need to know to help, so just ask if you need me to post any more specific details.

---

### Post by Pumalite on 2008-06-29
Edit menu.lst and below the automagic line add:
title Vista
root (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by S3TH88 on 2008-06-29
That did the trick!  Thank you very much.

---

### Post by Pumalite on 2008-06-29
You are welcome. Good luck.

---

