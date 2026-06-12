---
title: "Triple Boot : XP, Vista, Ubuntu HELP!!"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by SiCYourDaddy on 2007-10-01
Ok, I know that there are tons of threads about this already but none seem to answer the issues that I'm having.

To start off, I have two HDs.  One is SATA and one is IDE.  So when they boot up, the SATA is hd0 (primary) and the IDE is hd1 (secondary).  The SATA drive had XP (hd0,0) and Vista (hd0,1) installed using Vista’s bootloader.  So, I found a tutorial on installing Ubuntu and it basically said to use Vista’s “Shrink” function to reduce the size of the Vista partition and install Ubuntu on the new unused space.  The drive will then have three partitions; XP (hd0,0), Vista (hd0,1) and Ubuntu (hd0,2).  I went ahead and installed Ubuntu on the partition as planned and then here comes the problem…  When I restarted, I got the ol’ “Missing Operating System” error.  Since then I have tried so many different things and I cannot, for the life of me, get either Vista’s bootloader or Grub to recognize all the OSs installed on the drive.  I tried EasyBCD in Vista and it didn’t work.  When I booted to the Ubuntu entry, the boot menu would just reload.  After reading around on the web, I found some info on reinstalling Grub from the LiveCD, which loading from that CD is so hit-and-miss.  So I did that and now it boots up to Grub but the hd configuration is wrong.  It thinks that Ubuntu and Vista (the only ones in the list, XP isn’t showing up) are located on hd1.  Now, if I hit “e” I can edit it and the hit “b” and it boots fine.  Next, I read up on editing the menu.lst file.  I open up Terminal, after booting to Ubuntu and type in the command that lets you edit the menu.lst, don’t remember it off the top of my head, I made the changes and now I can load to Ubuntu everytime with no issues.  The only issue I have left is editing the menu.lst to include XP and Vista.  I tried and it didn’t work.  When I try to boot to XP from the menu, it goes to start loading then it just stops.  When I try to boot to Vista, it says something like “Missing Bootloader.”  But I think, for you guys, that all may be irrelevant.  What I need is a menu.lst config that will work using the info that I have given here.  The only other thing that I can think of that you may need to know is that when XP used to boot up, it was the C: and when I booted to Vista, it was the C:.  Is there anyway to setup Grub so that this will still be the case?

I hope that this is enough, or not too much, info.  I don’t speak Linux very well yet but I’ll get there so go easy on me.
Thanks in advance,
David

---

### Post by SiCYourDaddy on 2007-10-01
Man, there are a bunch of people posting here!  I posted 4 hours ago and my thread is already bumped from the front page.

Bump!

---

### Post by logos34 on 2007-10-01
Please post the output from the following commands:

**sudo fdisk -l** (lowercase L)

**cat /boot/grub/menu.lst**

Or try this windows entry (maybe you have):

> title		Windows
root		(hd0,0)  --->or (hd0,[COLOR="Blue"]1[/COLOR])
savedefault
makeactive
chainloader	+1

You're basically trying to chainload the vista boot manager, wherever it is.  

Maybe windows is not marked 'active'

---

