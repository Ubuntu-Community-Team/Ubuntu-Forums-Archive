---
title: "Installation has stuffed my WinXP system"
date: 2006-05-16
forum: Installation &amp; Upgrades
---

### Post by Amnesiac5 on 2006-05-16
I tried to install Ubuntu 5.10 (Breezy Badger) Linux to co-exist with Win XP Pro x64. When the install process rebooted, grub failed with error 17.

After a mere 10 minute install session my system is now a very expensive paper weight. ](*,) 

Deciding that enough was enough I tried to manually restore from the XP Recovery Panel with bootcfg, fixmbr and fixboot.

I now get the dreaded "error loading operating system".

How can I avoid a complete reinstall of WinXP? ie HELP!! :confused: 


     System:
     MS Win XP Pro x64
     v2003 Service Pack 1

     Computer:
     AMD Athlon 64 3200+
     2.01 GHz, 1.00 GB ram

     Mobo:
     Gigabyte GA-K8N-SLI
     nForce4 SLI chipset

---

### Post by Sef on 2006-05-16
From Linuxself help:

> 17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

From Gentoo:

> 17. Grub segfaults when trying to install

Situation

The situation described below is only relevant for grub-0.95.x at the moment of installing grub at the boot sector.

Code Listing 17.1: Installing Grub

grub> root (hd0,0)

grub> setup (hd0)

Segmentation fault

Solution

This is a known bug related to this problem and has been fixed in grub 0.96. It is also known that grub 0.94 r1 and grub 0.94 r2 should work correctly. If that fails too, you can try to emerge grub-static which is currently stable on amd64 and unstable on x86 (~x86). Check out bug #79378 for additional information.


Bug report:

[http://bugs.gentoo.org/show_bug.cgi?id=79378]("http://bugs.gentoo.org/show_bug.cgi?id=79378")

Do you have a Live CD, so you could reinstall GRUB?

---

### Post by Amnesiac5 on 2006-05-16
Yes, I have a live CD, but that doesn't work either.

I *think *it can't find the appropriate drivers for my vid card. It dumps me at a command prompt, difficult to be certain as the screen is filled with ASCII garbage.

---

### Post by Amnesiac5 on 2006-05-17
The last time this happened (when will I learn :cry: ) I was able to fix it as follows;
to eradicate grub:
fdisk /mbr

to activate the partition:
fdisk

This time no joy. fdisk yields to following info

partition
      1      EXT DOS     2275Mb
      2      Non-DOS   18599Mb
      3      NTFS        80003Mb
      4      Non-DOS   16363Mb

fdisk will not allow the current partition to be set to 1
if the current partition is set to 2 or 3, the boot sequence just stops
if the current partition is set to 4, I get "error loading operating system".

I'm guessing that XP has to be on the primary partition and the layout above is unacceptable. Can I delete partitions 1 and 2?

At this point in time, I'm just trying to restore my system to a working state.

The live cd doesn't work, I just get hundreds of command lines before it freezes. The last line is something about not being able to find a font, I think.

---

### Post by Sef on 2006-05-17
> I'm guessing that XP has to be on the primary partition

Yes, it has to be on the first primary partition.

If you can download and burn a rescue disc this might help you.

[http://trinityhome.org/trk/]("http://trinityhome.org/trk/")

---

### Post by Amnesiac5 on 2006-05-18
I'll have to burn the disk at work, since my home computer has been hobbled (my fallback OS, Win ME, doesn't recognise my CD-RW drive), but this certainly looks promising. 

I'll let you know how it goes. Thanks.

---

### Post by dion on 2006-05-18
Hi AmnesiaC5,

This may not actually be the solution you are looking for, I'm still relatively a newbie myself.  My suggestion would be to try a different bootloader, I have used this one before when faced with a similar problem and it worked great.  What usually happens is that Win & Linux sometimes read and write the partition tables differently hence they get pointed to the wrong part of the hard drive where they find a file system that they do not understand.

Okay, back to my suggested solution.  Go to this URL [http://gag.sourceforge.net]("http://gag.sourceforge.net")
On this page you should be able to download the Gag Boot Loader, it is reasonably small in size and can run from your MBR itself or from a floppy if you so prefer.  You can then point it to any of these 4 partitions and it would load the partition if it is bootable.

---

### Post by Amnesiac5 on 2006-05-19
[QUOTE=Sef]Yes, it has to be on the first primary partition.

If you can download and burn a rescue disc this might help you.

[http://trinityhome.org/trk/]("http://trinityhome.org/trk/")[/QUOTE]
Ok, burnt it, booted up and go straight to a Linux command line. Sadly, I *don't know* Linux, which is rather the problem.

---

### Post by RavenOfOdin on 2006-05-19
My XP install isn't recognized by GRUB (returning "filesystem unknown", chainloader +1) but it still works correctly.

Did you install GRUB in the Ubuntu installer the first time around, or after the fact?

---

### Post by Amnesiac5 on 2006-05-22
Phew!

Partition logic ([http://partitionlogic.org.uk/](http://partitionlogic.org.uk/)) sorted out my partition woes. Yay! :D 
It threw up about 10 error warnings which it then fixed, and once again I had a bootable hdd.

Sadly, I still had to complete the Win XP installation process I'd started previously, bit of a drag but everything's up and running and all my files and settings seem intact. Yay, again!

Excellent bit of software, it even comes with a GUI and all on a single floppy.

Thanks for the help and suggestions, much appreciated.

---

