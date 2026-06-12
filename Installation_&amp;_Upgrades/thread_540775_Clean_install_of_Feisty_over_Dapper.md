---
title: "Clean install of Feisty over Dapper"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by merlin114 on 2007-09-02
I have a dual-boot setup with WinXP and Dapper on two separate drives.  The WinXP drive has two 40GB partitions, with one empty.  The other drive is 40GB with only Dapper on it.  

I've got a Feisty install CD, but I'm afraid to overwrite my Dapper setup even though I did backup my /home folder to a USB drive -- I don't want to lose anything, and I want to be able to use my old Dapper setup if I can't get everything working in Feisty, including some extra applications.  So I'm thinking I want to repartition my Ubuntu drive (shrinking the portion with Dapper on it), and do a clean install of Feisty on the new partition.

When I went to install Feisty, I selected Manual partitioning and it looks like I can just shrink the Dapper partition to 20GB, then install Feisty on the other partition, is that right?  When it repartitions, how can I be sure I'm selecting the empty partition to install Feisty?  Will I still be able to boot Dapper?  Will it automatically detect Dapper on the other partition and set up dual booting? Will I have to edit a config file?  I just want to be sure I don't dork this up and lose stuff, especially when it says "you can't undo this...".  Any recommendations welcome.

---

### Post by mikewhatever on 2007-09-02
> **merlin114 said:**
> 

When I went to install Feisty, I selected Manual partitioning and it looks like I can just shrink the Dapper partition to 20GB, then install Feisty on the other partition, is that right?
Yes.
> When it repartitions, how can I be sure I'm selecting the empty partition to install Feisty?
When the new partition is created, it gets a name, something like sda5. Make sure you know which one is which and note the new partitions location relative to the other partitions. For example, sda5 may be located between sda2 and sda7.

> Will I still be able to boot Dapper?  Will it automatically detect Dapper on the other partition and set up dual booting? 
Yes, it should.
> Will I have to edit a config file?  I just want to be sure I don't dork this up and lose stuff, especially when it says "you can't undo this...".  Any recommendations welcome.
Yes, you might. The most troubles users seem to have with multiple OSs and HDDs is with GRUB setup. Hopefully yours will go ok. It is very hard to be 100% sure nothing goes wrong, while doing complicated stuff such as repartitioning, so backup everything you can't loose.

---

### Post by merlin114 on 2007-09-02
Thanks.  Well, I decided to install feisty on the empty partition on my other hard drive and not mess with the partition on my ubuntu drive.  The repartitioning went okay after a couple false starts, and the install proceeded to about the 80% point, at which point it said it couldn't install Grub, and that it was a fatal error.  When I closed the window, the install dialogue closed.  Looking at the drive, the install looked like it was proceeding okay.  Don't know if Grub was the last thing on the list, or whether a bunch of later items didn't occur too.

Should I try reinstalling Feisty and see if it makes it this time?  Should I reboot without the live CD and see if the new Feisty install boots?  If so, can I install Grub after the fact?

---

### Post by merlin114 on 2007-09-03
After my failed Feisty install attempt, I rebooted to Dapper and noted that the drive I tried to install Feisty on was not mountable.  So I did a disk integrity check on the live CD (no errors) and then re-ran the Feisty install from the live CD and got the same results.  Everything was fine until it got 94% complete and began running "grub-install (hd0)".  Then I got an error box indicating "Executing 'grub-install (hd0)' failed. This is a fatal error".  When I closed the dialog box, the installer closed.  

Anybody have an idea of where I should go from here?  My next thought was to try Gutsy Tribe 5 and see if I can at least complete an install.  Then, when the stable version comes out in October, I can just update.  Anybody have other tricks to try???

Thanks!

---

