---
title: "Wubi 12.04 install sys crashed"
date: 2012-05-27
forum: Installation &amp; Upgrades
---

### Post by Paul.E.T on 2012-05-27
[SIZE="3"]From bcbc[/SIZE] another post
error on wubi install 'Cannot download metalink and therefore ISO'
by catsten888
[http://ubuntuforums.org/showthread.php?t=1987215&highlight=wubi](http://ubuntuforums.org/showthread.php?t=1987215&highlight=wubi)

"You don't need to hard reboot. If you look in the Wubi guide it states up front that this is dangerous (in fact it can damage any filessystem). Use Alt+SysRq R-E-I-S-U-B instead."

From memory Ctrl+ Alt Del did not work. With a **dead keyboard** I don't understand how to enter the above Alt+.... cmd ?  That was a new problem froze keyboard (USB) that forced me to do a hard shutdown.

Thread:  Wubi megathread
access your data in the following way:

Comments here (#) are mine.
live CD Code:

**sudo mkdir /media/win**     #  OK make a directory to use for the mount command.

**sudo mount /dev/sdb1 /media/win**  #  Mount my Hard Disk Drive in the directory under "win"

**sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt**  #  do not under stand the extra mount cmd here ?

**nautilus /mnt**   #  Don't understand what this cmd will do ? I'm looking up last two cmd's now.

Usefull Wubi Info:

  "Wubi boots via an entry in the windows boot manager, that calls grub4dos (wubildr.mbr)."

---

### Post by wilee-nilee on 2012-05-27
What keeps you from just doing a partitioned install of Ubuntu?

---

### Post by Paul.E.T on 2012-05-27
A dual boot partitioned install was my first goal.  However, I have a notebook where I installed Kubuntu and the dual boot worked great for over two years.  Then got an update and lost internet access with Kubuntu but not M$ XP.  So I continued to use XP and tried to figure out the no network access with Kubuntu.  No easy task for sure since networking seems to be in a world of it's own.  My son will soon graduate with an IT degree mostly in network security so I'm embarrased since he know more than me by far  :>)  Anyway, I can just remove the partition with Kubuntu in it but now I'll be stuck with GRUB booting win's, a dead/empty partition with GRUB data corrupted w/out an OS in  a empty partition.  So I left Kubuntu in sys but took it down to a couple of GB to save space.  GRUB has it's own language to fool with so this additional just confuses me more.  i.e. GRUB used to count HDD's starting with zero but I last read it's back to counting starting at one ? Muddy waters for sure!!  What else has GRUB changed to confuse things ??
    Used Wubi a couple of years ago and it worked great on the same AMD box that just crashed trying to put 12.04 LTS on 2nd HDD, extended 30GB device "o" for Oscar.
    Being an older conservative fellow I just got a new PC, AMD 4x, 16GB ram, two 60GB SSD, w/Two terrabyte HDD's, Dual head graphics running 64bit W-7 pro. Haven't plugged it in yet.   Second goal is: I want to put in Linux with/or BSD in a dual/triple boot configuration for new box.  I would prefer BSD since in my younger days I used Sys 7 and enjoyed it.  So Wubi seemed ideal.  Wanted something stable.  So the reasons for not immediately sticking in Ubuntu with a hard partition.
    Hope I didn't bore you :>).
    PaulT

---

### Post by wilee-nilee on 2012-05-27
> **Paul.E.T said:**
> A dual boot partitioned install was my first goal.  However, I have a notebook where I installed Kubuntu and the dual boot worked great for over two years.  Then got an update and lost internet access with Kubuntu but not M$ XP.  So I continued to use XP and tried to figure out the no network access with Kubuntu.  No easy task for sure since networking seems to be in a world of it's own.  My son will soon graduate with an IT degree mostly in network security so I'm embarrased since he know more than me by far  :>)  Anyway, I can just remove the partition with Kubuntu in it but now I'll be stuck with GRUB booting win's, a dead/empty partition with GRUB data corrupted w/out an OS in  a empty partition.  So I left Kubuntu in sys but took it down to a couple of GB to save space.  GRUB has it's own language to fool with so this additional just confuses me more.  i.e. GRUB used to count HDD's starting with zero but I last read it's back to counting starting at one ? Muddy waters for sure!!  What else has GRUB changed to confuse things ??
    Used Wubi a couple of years ago and it worked great on the same AMD box that just crashed trying to put 12.04 LTS on 2nd HDD, extended 30GB device "o" for Oscar.
    Being an older conservative fellow I just got a new PC, AMD 4x, 16GB ram, two 60GB SSD, w/Two terrabyte HDD's, Dual head graphics running 64bit W-7 pro. Haven't plugged it in yet.   Second goal is: I want to put in Linux with/or BSD in a dual/triple boot configuration for new box.  I would prefer BSD since in my younger days I used Sys 7 and enjoyed it.  So Wubi seemed ideal.  Wanted something stable.  So the reasons for not immediately sticking in Ubuntu with a hard partition.
    Hope I didn't bore you :>).
    PaulT

XP could of had its bootloader reinstalled with a recovery or install disc.

Grub has changed from grub-legacy to grub 2, grub 2 has a os-prober that will find other OS, and add them to the grub menu.

A MS friendly bootloader called lilo from a ubuntu live cd could have been use to boot XP straight in.

I don't have a problem with a wubi install, just wondering.

---

