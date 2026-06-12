---
title: "Various tips for installing 9.10 on (my) laptop"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by SecretCode on 2009-12-27
I've been running various versions of Ubuntu as virtual machines for ages, and have recently switched a server over to U.Server 9.10, almost painlessly ... and now I'm installing Desktop 9.10 64 bit on my laptop ... painfully. But with the help of many threads here (and one or two articles on the rest of the web), I'm fixing things. So it's time to pay back and share some lessons.

These are things that helped me, nothing very new.

The laptop is Mecer TW7A Xpression ... not a very common brand ... with an nvidia video card.

[LIST]
[*]Experiment with the new OS in a **virtual machine** first. I use VirtualBox.
[*]Experiment with partitioning (GParted), Grub 2, and MBR recovery in a vm too!
[*]Learn to use a **recovery CD**. Ubuntu live CD is good for some things, but System Rescue CD or PartedMagic have useful extra tools ... and boot more quickly.
[*]Make a **full-disk backup** first. I use Clonezilla.
[*]If you are repartitioning a drive to enable dual boot, especially shrinking an NTFS partition: 
[list][*]you need to defragment the NTFS partition first. Twice, if not more. And clean out as much space as possible.
[*]You can make Windows unbootable if the partitioning goes wrong - even if all your data is readable on a Linux live CD or installation (it's to do with disk geometry - browse the GParted forums Nov-Dec 2009 for gory details). Be prepared to learn and use disktype, testdisk, fdisk, sfdisk and cfdisk. (All these tools are on the PartedMagic CD.) This cost me a bit of a time when I repartitioned my server, which is admittedly an old machine. (Cloning 30GB back from a USB drive took 5 hours.)
[/list]

Now, the actual install ...
[*]Obviously, you test with a live CD on your computer first. But that **doesn't** mean everything's going to go well. 

[*]I installed 9.10 Desktop 64 bit from the release CD. All fine ... except it **completely failed to start X** (ie, no graphics, no GNOME, just 20s of **flickering** and a **text-mode login**). It looked like I would have to identify and download the proprietary nvidia driver from the command-line, but in fact I just did a full package update, including the latest kernel, which allowed me to boot into X in "low graphics mode" and go to System > Admin > Hardware Drivers ... slightly easier.
[*]Then I realised I had **no sound**. At all. There are many threads here about this and there seem to be several causes. In my case it was fixed by removing the proprietary hardware driver I had installed for "software modem" at the same time as installing the nvidia driver. For some reason, laptops often have modems and sound cards running off the same chips. 
[*]My headphone jack failed to mute the speakers. That was solved as given in this thread: [http://ubuntuforums.org/showthread.php?t=1075643](http://ubuntuforums.org/showthread.php?t=1075643)
[/LIST]

---

### Post by SecretCode on 2009-12-28
I forgot one other thing: my **wireless card** wouldn't work. Whatever I set it still showed as *-network DISABLED in lshw.

The solution, suggested by a few threads here, was to boot back into Windows and enable the wireless via the special Fn-key. Why there's no BIOS function for this, and no capability available to Ubuntu, I don't know - but it worked.

---

