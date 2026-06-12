---
title: "uninstalling the grub"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by Peter_Bingo on 2010-04-14
I was haven't trouble uninstalling the grub on my laptop (which i don't need it on) and i manual deleted my partitions. I am now unable to boot into windows anymore and was wondering how to get rid of the grub and boot normally into windows. I have a error when i start up "error 22"

---

### Post by dominiquec on 2010-04-14
Try [http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

---

### Post by dominiquec on 2010-04-14
By the way, I assume two things here:

1) You're using Windows 7.

2) You don't want to use your Ubuntu partition anymore.

If you're using an earlier version of Windows, you might want to look at their system recovery methods.

That said, you may want to wait for other advice here.  Other folks might have better ideas.

---

### Post by Peter_Bingo on 2010-04-14
> **dominiquec said:**
> By the way, I assume two things here:

1) You're using Windows 7.

2) You don't want to use your Ubuntu partition anymore.

If you're using an earlier version of Windows, you might want to look at their system recovery methods.

That said, you may want to wait for other advice here.  Other folks might have better ideas.

I'm not using windows 7 (well not on this computer). I have used ubuntu partitioner many times before but differently. I also tried your technique to restore the mbr with both a windows sp cd and a windows 7 dvd no luck

---

### Post by oldfred on 2010-04-14
You need to use the window cd that is the same version as your install. XP is not like Vista/7.

You can install a generic windows boot loader from Ubuntu.

sudo  apt-get install lilo
sudo lilo -M /dev/sdX mbr

Make sure you have a boot flag on the windows partition as that is how the windows boot loader finds the partition to boot. It must be a primary partition.

---

### Post by Peter_Bingo on 2010-04-15
I'm still haven't the same problem. I installed lilo and typed those commands into the terminal. How do I set my windows partition to primary, it's flagged as boot. I just need to get rid of the grub so I then use the windows xp cd to repair

---

### Post by oldfred on 2010-04-15
Partitions are primary or logical when they are set up. It is just about impossible to change (some exceptions for experts exist).

Under MBR drive system (since original IBM PC) you are allowed 4 primary partitions. When everyone realized that was not enough, they modified it to convert one primary to an extended that is a container for logical partiitons. Windows boots from a primary. sda1-4 are primary, sd5 & up will be the logical.

---

### Post by Peter_Bingo on 2010-04-17
Well it it is labeled as sda1. I going to try my last resort and move the partition over to another hard drive, then format the hard drive in the laptop. If anyone has any other suggests please help

---

### Post by oldfred on 2010-04-17
with windows sometimes the PBR partition boot record or other system files get corrupted:

Vista or 7 repair
Always run chkdsk and run again until there are no errors, that may be all that is required
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe

---

