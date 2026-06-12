---
title: "unable to load ubuntu from live disk to HP Envy Computer"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by dnpate on 2011-11-13
when trying to load ubuntu to my new HP envy laptop from a live CD the screen goes blank but I can hear disk activity which finally quits.  There is no problem in loading to an HP laptop about 3 yrs old.  I set up a USB stick from which to boot using the older computer rather than the disk, but this does not work either.  Using the USB stick I can get the unbuntu menu asking to boot, boot in safe mode, etc, but selecting each one of these the screen again blanks with no opportunity to do anything else.  The only way to recover is to manually shut the computer down using the start button.
Any ideas?
Thanks
David

---

### Post by dnpate on 2012-05-20
I still cannot get ubuntu to load from a live disk using 12.04 (previously I tried 11.10).  Same problem.  I thought perhaps something with the kernel, etc and maybe updated by now but not luck.  I am left with a blank screen each time.  The same thing happens when trying using the gparted debian disk and with linux mint so it is something with the computer.  Is it because of "sandy bridge"?  The verbose scrolling is displayed on the start of the boot, but then the screen goes blank.  I tried to use the "sticky" instructions at the first of the installation form threads, but that did not help.  Any help out there?
TX
david

---

### Post by darkod on 2012-05-20
What boot parameters did you try to use exactly?

It didn't change anything with the problem, or there was some type of change?

---

### Post by dnpate on 2012-05-20
No boot parameters used.  Just put in the live media to boot and I have no change to enter any parameters.

---

### Post by darkod on 2012-05-20
But you said you tried to use the sticky and it didn't help. The sticky offers few options to boot by adding boot parameters and try to find which one helps you, if the default boot doesn't work.

So, you only tried booting by default, right?

What is the exact model of your HP Envy? A quick google search more or less says that it works by default.

---

### Post by dnpate on 2012-05-20
Maybe I am overlooking something but I find no place to enter parameters.  I download the installation to make a live CD from iso file.  That is used to start the boot and it begins, but I find no place to enter parameters before the screen is turns blank.  No repose to any key press.  
   Model is HP Envy 14 with i7 2GHz, 8 megs ram
David

---

### Post by dnpate on 2012-05-20
I do not ever get to the vga puplish screen displaying the the keyboard and man and the verbose boot entries.  I thought I did but that was on an older machine I was testing on.  
  also, I have the ATI Radeon video adapter.
david

---

### Post by darkod on 2012-05-20
Hm, it's strange not to get even the first screen where you can press Esc and get the older main menu.

You also mentioned not being able to boot gparted live debian and mint, so it might be machine related.

Make a cd from the alternate install ISO, and try that. The installer is text based (not the fancy GUI) but it installs the same ubuntu desktop as the live cd. And you can't run the alternate in live mode, that's the only difference.

You can get all the ISOs here, get the alternate 32bit or 64bit, as you wish:
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

---

### Post by dnpate on 2012-05-20
TX.  I'll give it a try after a rest.
David

---

