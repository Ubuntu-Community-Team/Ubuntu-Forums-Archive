---
title: "Xp doesn't see Ubuntu at boot menu"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by lime90 on 2007-04-26
Hi!

I installed Ubuntu 7.04 toady. But when I restarted my computer after the installation I didn't get any boot menu to choose wich system I wanted to boot. (I have XP and Ubuntu)

Xp and Ubuntu are installed on the same drive but different partions. 

How do I solve this problem?

---

### Post by EarthlyDilemma on 2007-04-26
You cannot use the XP boot loader, you need to use grub or lilo (grub is the default),
take a look at [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) for installation
instructions.

If for whatever reason you decide that you want to remove Ubuntu and go back to 
a pure windows system, make sure that you google that BEFORE removing Ubuntu 
because you will have to use the Recovery Console (boot off the XP disk) and 
run fixmbr before you will be able to boot into windows again.

Alternativly, you can use a windows based boot loader like Boot Magic to choose 
between Ubuntu and Windows.

I prefer grub myself, but if you're just testing Gnu/Linux for the first time and may
go back to windows full time, the 2nd option is probably better.

---

