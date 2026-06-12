---
title: "How Do I unistall Ubuntu?"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by blasteryui on 2007-09-01
Hey guys I have two hard drives, I have the newest Ubuntu, edgy* On my second hard drive, so I have it on duel boot, Windows XP on the first HDD, and Ubuntu on the second. How do I completely get rid of Ubuntu off my second HDD so that my second HDD is back to normal and is blank, and usable?

Thanks alot.

---

### Post by Pumalite on 2007-09-01
Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by merlinus on 2007-09-01
Edgy is not the latest version of ubuntu, Feisty is.

You can reformat the partition using gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by blasteryui on 2007-09-01
Sorry I ment that, ok I have this partion on a cd, do I just boot the CD while on XP or do I restart my comp and press f12 and boot from the cd?

---

### Post by Pumalite on 2007-09-01
Boot from CD (The Gparted, stand alone, burn to CD and boot program)

---

### Post by blasteryui on 2007-09-01
So restart my comp and do it that way?

---

### Post by Pumalite on 2007-09-01
Yes

---

### Post by blasteryui on 2007-09-01
Great... I am on my laptop, I restarted my pc, booted the cd I clicked format, it said format to, I formated it to the system it said it was like something 3, I forget, anyways it formated it, I deleted the linux swap thing, it said that 705mb was being used on my second HDD even knows I formated it... I restarted my computer it loaded my dell screen, then it went to a black screen, and it says grub trying to load then it says like error. I didnt even touch my first HDD, I take it, thats not how to get rid of Ubuntu... I formated like you said now my PC is messed, what do I do? My first HDD hasn't been touched so it still has XP on it. But it wont load up as I said, it still tried to load Ubuntu I guess. But theres an error so it just stays on black screen saying error.

---

### Post by blasteryui on 2007-09-01
Ok the error number is 15.

---

### Post by Pumalite on 2007-09-01
Restore XP to MBR: Boot from XP CD, hit 'r' for Recovery>FIXMBR>FIXBOOT

---

### Post by blasteryui on 2007-09-01
Oks so boot my windows XP disk and click repair? So my SECOND HDD is free now right? It doesn't have Ubuntu right?

---

### Post by Pumalite on 2007-09-01
If you reformatted; I doubt it.

---

### Post by blasteryui on 2007-09-01
Ok whats going on... I inserted the XP disk in, I reboot my pc, I click repair it makes me pick a HDD and theres only 1 and its my main one I click 1, it says put in the adminstrator password, I take it thats the password I use to logg in to my XP account right? WELL I put in the password and i says its INVAILD I did it 3 times and it makes me restart my computer, whats going on.. You dont think so? You said to format it, I clicked format to and it formatted it, and I deleted the linux swap.

---

### Post by blasteryui on 2007-09-01
Ok, I re put th GPARTION in, I went to my second HDD right clicked the partions and clicked delete, so THERES nothing on the second HDD what so ever. I restart my PC instead of getting the error 15, I get error 22. Now what?

---

### Post by Pumalite on 2007-09-01
Use Super Grub to boot Windows. And also to restore Windows to MBR.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by blasteryui on 2007-09-01
Ok, once I have the files onto a cd burnt... What do I do once I load in into my computer what do I click and stuff?

---

### Post by Pumalite on 2007-09-01
[http://supergrub.forjamari.linex.org/?section=documentation](http://supergrub.forjamari.linex.org/?section=documentation)

---

### Post by blasteryui on 2007-09-01
I just read, I dont get it.

---

### Post by blasteryui on 2007-09-01
Just what do I do, when i boot the cd...

---

