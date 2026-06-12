---
title: "Dual boot config / Win install / entire disk empty?"
date: 2008-08-08
forum: Installation &amp; Upgrades
---

### Post by anlag on 2008-08-08
I've run into a fair bit of problems this evening, attempting to install Windows XP onto a laptop hard drive already containing Ubuntu 8.04. Initially, the hard drive had the following partitions:

(empty, primary, intended for Win)
/boot (primary)
swap (primary)
/ (logical)
/home (logical)

The Ubuntu installation was done the other day for testing purposes. As it seemed to work well, I proceeded with trying to intall Windows into the empty, unpartitioned space. Having first had to make a change in my BIOS (switch from ACHI to 'Compatibility' mode) to allow the Windows setup to find the hard drive at all, I could see from within it the four existing partitions and the empty space of 40 GB I had left for this purpose.

The next problem was, I realized, that when the Windows XP setup utility sees there's already four partitions, it refuses to continue saying no more can be created. Here's where I took a bit of a chance, and removed the swap partition, thinking this would allow Windows to install, and that I could always re-create it using GParted from the Live CD afterwards.

Well, it worked as far as the Windows installation is concerned. It installed fine, although a bunch of hardware wasn't installed as it couldn't find appropriate drivers... no matter, I can sort that. Meant to do so by going into Ubuntu, but as I now boot using the Live CD to both reinstate the GRUB loader, and to recreate the swap partition, I find that GParted reports the ENTIRE drive as 186 GB of unallocated space! No Windows partition, none of the three Linux partitions that should still be there, and no 2 final gigs of space that had been the swap. Nada.

Thinking perhaps Ubuntu needed the ACHI mode in BIOS, I rebooted and changed that back, but no luck.

What's going on? I know for sure that when Windows formatted the area it was given, it said that it was formatting 40 GB on a 186 GB drive, indicating only that particular piece was formatted and not the entire drive. This makes me think the Linux partitions are still there, only GParted doesn't see them for some reason. Might my removing the swap partition have caused this? Can't think how.

Not about to panic just yet but let's just say while I should have backups of most things (not sure though!) I'll NOT be best pleased if it's all gone. 

Any and all advice very gratefully received! Thanks in advance.

//edit to add, from trying to sort the GRUB loader using the Live CD, I also can't do it.

grub> find /boot/grub/stage1

Error 15: File not found

---

### Post by anlag on 2008-08-08
Made some progress. Happened to see this thread bounce up...

[http://ubuntuforums.org/showthread.php?t=857564](http://ubuntuforums.org/showthread.php?t=857564)

...and looking in nautilus helped me, it did indeed see my Linux partitions and clicking them to open them up caused them to mount one by one as well. Nice. Having edited menu.lst and rebuilt grub, I now get a working grub boot menu and can boot into Linux fine. However, two issues:

1. gparted still can't see any partitions, still says the entire drive is unallocated space. Much like the issues in that other thread. It worked just fine a couple of hours ago, before I let the Windows installer touch my partitions.

2. Trying to boot into Windows now fails. I get the Win XP startup screen, followed by a bluescreen, intimating the system has encountered errors and will close. Mentions possible disk errors. Failsafe start doesn't help.


Could these errors be related, in that the partition table is still somehow not quite in order? I'll look into Gpart, as mentioned in the other thread.

---

### Post by anlag on 2008-08-11
Problems solved, thought I'd post for the sake of completeness. The two problems I had were in fact not directly related. The partition tables were indeed messed up, but testdisk was able to fix this. However, the reason Windows didn't boot was again the lack of ACHI support in the base installation; I had to set the SATA/ACHI settings to compatibility mode in my BIOS for it to boot, until I had a chance to install ACHI drivers from the laptop manufacturer website (Lenovo.) Now both systems boot fine, and GParted sees all my partitions, meaning I could also without problem recreate my swap partition.

---

