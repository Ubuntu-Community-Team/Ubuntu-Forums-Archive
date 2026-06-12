---
title: "Cant install Ubuntu x64"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by stressfreesoul on 2008-09-05
I am having problems installing the 64bit version of Ubuntu.
I can boot into the disk, select my language, but when I press enter after selecting any of the options on the list, I get the Ubuntu preparing screen (just before the progress bar starts filling) then it goes black and the HDD light flashes once every second or so until I reset, remove the CD and boot back into my other OS.

I have tried two copies (both md5'd), so its not the burn.
I have unhooked all but the drive I want to install on, no difference.
I have tried using the disk check utility on the live CD, ends with the same result.

My system spec, for compatibility check...
Asus P5N-E SLI
Q6600
2Gb Transcend PC2 6400 (DDR2 800Mhz)
1Gb (2x512Mb) OCZ Gold PC2 6400 (DDR2 800Mhz)
650W PSU
XFX 8400GS
A choice of either a 40Gb WDC IDE drive or,
a 80Gb Seagate SATA2 for installing on.

I cant see anything there that isnt compatible. Is there a BIOS setting to be changed?
I have previously installed it on one of my other machines (an AMD Athlon64 3000+) without a hitch. 
Any help with this would be great.

---

### Post by cocokiwi on 2008-09-05
Hi,

 you should have 2 x 1 gig instead of the two 512g and use the SAME brand of chip as you have with the 2 gig pair!

secondly ,if you have not upgraded the BIOS since(10/2007) Last year you DO need to upgrade it! Their is a problem with the alocation of memory on the motherboards..this only allowed 3 gig as the MAX amount of memory on could use,which is what you have now! 64bit works better with 4  gig...upgrading the BIOS solved many problems.

Cheers Dennis:lolflag:

---

### Post by Therion on 2008-09-05
When you see the Grub countdown press "Esc" to intercept and go enter a Grub menu. 

Then:

* Press 'e' to start editing.

* Scroll down to the "kernel..." line. 

* Press 'e' again to edit this line.

* Move to the end of the line and change the word "quiet" to "noquiet".

* Press Enter to accept the editing.

* Press 'b' to boot using that kernel and those parameters.

Now when you boot you'll be able to see what's going on when things freeze up.  This won't solve the problem, in and of itself, but it should indicate what the problem is so we can get around to fixng it.

---

### Post by stressfreesoul on 2008-09-05
Sorry. I made a mistake in my last post. I musnt have been watching properly, as it does load through the progress bar. A few of the items that were loading up dont seem to get an ok beside them. However it *does* go to the end of the bar and *then* goes black etc. Oh yes, the "e" option didnt work, but F6 did.

---

### Post by stressfreesoul on 2008-09-06
I have an update...
I cant install any Ubuntu on my PC. I just tried with the x86 8.04 Desktop, no joy. Then tried with the x86 Ultimate Edition, with same results. Its really irritating me as I like the change of scenery away from micro$lop at least once a day.
Again, is there anything in my hardware spec above that wouldnt sit well with Ubuntu?
cocokiwi,
My BIOS is the latest, I only have three Gb in there by choice. XP doesnt require much above 2Gb and the timing on the 512s is excellent (for what I paid)

---

### Post by Therion on 2008-09-08
I would suggest you try using the Alternate Install disk for Ubuntu or using the "Install in text mode" option from the boot menu.

---

