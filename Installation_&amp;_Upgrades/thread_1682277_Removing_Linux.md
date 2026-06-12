---
title: "Removing Linux"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by leighahh on 2011-02-05
Ok so I have been running linux for a while and I love it. However, I am in school and need windows. I have tried running wine and it doesn't work i have also tried running a virtual machine and it still doesnt work (meaning that with virtual box it freezes to much and with wine it wont load at all) How do I remove linux and do a clean install of windows here are the issues that I am having:

1. Bios is set to boot from cd/dvd drive
2. when I shut it down and restart with windows disk in drive it doesn't load and only linux does.

How can i get rid of it.

Thanks

---

### Post by davidmohammed on 2011-02-05
if you cant boot with the disk in the CD drive, then either the disk image burnt on it isnt bootable, or the CD drive is broken.

In my experience, schools rarely "require" windows.  What programs do you think you need that cant be replaced by linux equivalents?

---

### Post by leighahh on 2011-02-05
We are required to use Word and i know that Abi and open office is compatible but they are just not allowing us to use them. It took me 2 hours to reform an 8 page paper yesterday after writing it in abi and then switching it to word, may more time than i have being in medical school. Also there is a disk that is our medical dictionary and it wont run at all.

---

### Post by davidmohammed on 2011-02-05
Word 2003 & 2007 run very well in Wine.  

Are you adamant that you need windows - or can we help you work with installing MS Word in wine?

If the former - check that your CD drive actually works - can you boot with a ubuntu live CD?  If you can then as I said, your windows boot disk is duff.

---

### Post by leighahh on 2011-02-05
Thats fine with the word program but for my medical dictonary it doesnt work in wine for nothing.

I just spent $300 on boot disk for windows xp both cant be bad it is my comp. I tried to repartition but my /del/sda1 partition is locked and i can't get in it. 

I know that my disk drive works because i can put anything else in it and it works.

---

### Post by davidmohammed on 2011-02-05
can you boot with the ubuntu live CD?

If you can then use gparted to repartition you hard-drive.

---

### Post by leighahh on 2011-02-05
I suppose I can't even though the drive reads it and pulls the files up but doesn't run

---

### Post by davidmohammed on 2011-02-05
I not sure what you are saying...


"pulls the files up" - can you describe what is happening on the screen?

---

### Post by leighahh on 2011-02-05
When i put the disk in it loads linux as normal even the xp disk, then when linux is done loading it will open the disk and show me all the files when i try to click on the install one it says it cannot mount it.

---

### Post by leighahh on 2011-02-05
Let me also add that when i run each disk in virtalbox they all work but it freezes badly so i know the disks are ok for some reason i cannot get the computer to boot from disk. nothing i do reformats the HDD

---

### Post by davidmohammed on 2011-02-05
have a read of [this]("http://pcsupport.about.com/od/tipstricks/ht/bootcddvd.htm").


Are you saying that even though the bios has the CD drive as the first in the boot priority AND the CD drive is actually enabled ( some bioses show a disabled boot option with a ! in front of boot device) you cannot boot the CD?

Are you definitely sure that you dont see the text "press and key to boot the CD/DVD" when you computer is starting (with the bootable disk in it)?

If you've convinced yourself your disks are OK & the BIOS option is OK, then you'll need to consider flashing the BIOS - or changing the DVD drive.

---

### Post by leighahh on 2011-02-05
ok so how do i flash the bios because the dvd drive is 2 weeks old

---

### Post by leighahh on 2011-02-05
Ok well i cant see that part if there is text that says press anykey because some screen comes on that says intel processor ect

---

### Post by skrizzy on 2011-02-05
please, if you figure out how to install windows, let me know please.
I also need windows.

---

### Post by presence1960 on 2011-02-05
Would you consider a dual boot set up? If so post back if you need help doing that.

But first you need to solve why your optical drive will not boot.

---

### Post by davidmohammed on 2011-02-07
> **leighahh said:**
> ok so how do i flash the bios because the dvd drive is 2 weeks old

see the first post [here]("http://ubuntuforums.org/showthread.php?t=318789").

---

