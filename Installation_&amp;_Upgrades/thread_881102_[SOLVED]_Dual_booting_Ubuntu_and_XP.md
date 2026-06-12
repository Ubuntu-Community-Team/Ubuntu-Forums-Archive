---
title: "[SOLVED] Dual booting Ubuntu and XP"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by y-aji on 2008-08-05
Hi all,

I've been trying to get my system to dual boot into XP.  I already have Ubuntu installed and have modified the Grub loader to point to XP:

```

title Windows XP
root (hd1,0)
makeactive
chainloader +1 

```

The difference with mine in contrast to most of the articles I have read is that I actually have two separate hard drives, one with XP and one with Ubuntu.  When I select this choice, it sees the partition, but just sits at a blinking cursor like it can't find anything until I power off the computer.  What do I have to do to make this work with two hard drives?

Thanks in advance,
Y-aji

---

### Post by pseudo-random on 2008-08-05
A few things it could be:
Your Physical Jumper settings on your Drives (Slave/Master etc) could be wrong.
Your partition may not be active/bootable. Check with Gparted to see if it is.

---

### Post by coffeecat on 2008-08-05
Windows can't boot from a second drive, so you have to trick it. See [Grub Manual - Windows]("http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows"). Try out

```
map (hd0) (hd1[FONT=Verdana]
[/FONT]map (hd1) (hd0)
```[FONT=Verdana]But I can't remember whether it's then '[/FONT][FONT=Verdana]root (hd1,0)' or 'root (hd0,0)'. You'll have to experiment.

If that doesn't work, try the unhide/hide trick.

**Edit**: I've just remembered - a similar thread a week ago [here]("http://ubuntuforums.org/showthread.php?t=869238"). The OP fixed the problem with a combination of both map and unhide/hide. That was to boot DOS, but the same trick should work with Windows.
[/FONT]

---

### Post by Pumalite on 2008-08-05
Search in the Forum:
Dualboot Two Hard Drives by confused57

---

### Post by y-aji on 2008-08-06
I hate having to put Windows on my computer, but the games are such a pain in the butt to play without it..  

Thank you all for the prompt help.. I love how quickly you get an answer from this forum and appreciate it to no end.

The following quote from coffeecat fixed the problem.

> **coffeecat said:**
> Windows can't boot from a second drive, so you have to trick it. See [Grub Manual - Windows]("http://www.gnu.org/software/grub/manual/grub.html#DOS_002fWindows"). Try out

```
map (hd0) (hd1[FONT=Verdana]
[/FONT]map (hd1) (hd0)
```[FONT=Verdana]But I can't remember whether it's then '[/FONT][FONT=Verdana]root (hd1,0)' or 'root (hd0,0)'. You'll have to experiment.

If that doesn't work, try the unhide/hide trick.

**Edit**: I've just remembered - a similar thread a week ago [here]("http://ubuntuforums.org/showthread.php?t=869238"). The OP fixed the problem with a combination of both map and unhide/hide. That was to boot DOS, but the same trick should work with Windows.
[/FONT]


My menu.lst file looks like the following:
```

title Play a Game
root (hd1,0)
map (hd1) (hd0)
map (hd0) (hd1)
makeactive
chainloader +1
```

This made the whole thing work like a charm.

Thanks again to everyone for the advice.

---

