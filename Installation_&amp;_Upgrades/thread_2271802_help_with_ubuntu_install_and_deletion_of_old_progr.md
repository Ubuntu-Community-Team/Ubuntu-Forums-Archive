---
title: "help with ubuntu install and deletion of old programs"
date: 2015-04-01
forum: Installation &amp; Upgrades
---

### Post by daveritah on 2015-04-01
I have my 80 hdd partitioned with an older inpais (ubuntu offshoot), a ubuntu 10.4, and a windows xp. I have been using a "grub" boot loader to choose between them when I booted up. I would like to delete the two ubuntu's, keep the windows xp and load ubuntu 14, partitioning the hdd to give 40 gb to Windows xp and 40 gb to Ubuntu. how do I do this and how do I reset the "grub" boot loader. So far, everytime I have updated my Ubuntu, everything including the "grub", just partitions off the new ubuntu and leaves the old behind. what am I doing wrong, and how do I fix it, so that I can have only what I would like with the Xp and one Ubuntu. I am new to ubuntu, but am a former programmer if there is such a thing ( Basic/QuickBasic/some C/Cobol/Fortran) and industrial computer programming. please note: I have not installed the ubuntu 14 yet.

---

### Post by Bashing-om on 2015-04-01
daveritah; Hello;

Short answer, what I do in this instance; fire up GParted from the liveDVD(USB) - the install media for a desktop - and ->
delete the partitions I no longer want ( old operating systems) .. that yields " unallocated space"  . In GParted I set up the new partition(s) - /, /home and swap as the basic minimum for my use case .
In the installer I choose the option "something else" and direct the installer where I want what installed to which partition.
In the final install stage grub will be installed. Pay attention and direct the installer where to install the boot loader ( grub) to.
Reboot into ubuntu when the install complets. and run terminal command:
```

sudo update-grub

```
to insure that grub picked up and chainloaded the Windows (XP) install onto it's boot menu.

caveat : The 7 Ps
[INDENT][INDENT]Prior Prudent Planning Prevents Pi** Poor Performance
[/INDENT][/INDENT]

---

### Post by daveritah on 2015-04-01
thanks for the info

---

### Post by Bashing-om on 2015-04-01
daveritah; Hey;

No problem. The help files for GParted are very good but can be daunting and confusing to those not acquainted with GParted.
When you have your Plan and have read the instructions, feel free to ask here for any way we can clarify and direct your attention.

The 1st thing is ALWAYS have a good backup of important files, else they are not important. Then no matter the haps, all one looses is a bit of time. Most times, even that is not a loss as one learns something in the process.

[INDENT][INDENT]we are all in this together
[/INDENT][/INDENT]

---

