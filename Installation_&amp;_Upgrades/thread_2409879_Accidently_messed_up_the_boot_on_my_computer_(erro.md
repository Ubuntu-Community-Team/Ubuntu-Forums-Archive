---
title: "Accidently messed up the boot on my computer (error: no such partition)"
date: 2019-01-07
forum: Installation &amp; Upgrades
---

### Post by leomv on 2019-01-07
Hello.

I'm relatively new to Ubuntu, I've been using it for 2 months.
My problem began when my Ubuntu Mate started to show a lot of problems such as not showing the top options toolbar, or not opening the Terminal with CTRL+ALT+T.
So I decided to format the partition and reinstall Ubuntu. But I probably chose the worst way to do it.

Inside the Windows partition of my computer, I opened the partitions configuration, and deleted the partition where Ubuntu was installed. All of it.
Then I restarted the computer, and the following message appears:

[B] error: no such partition
Entering rescue mode...
grub rescue>

[/B]I looked up how to solve the problem but couldn't find anything, since my problem is that I deleted the Ubuntu partition. I tried the "insmod normal" solution, but other error messages shows, like "Unknown command: normal".

Anyone can help me with that?

---

### Post by yancek on 2019-01-08
Which version of windows do you have installed?  If you have 8 or 10 it is likely a UEFI install and if you have 7 or older it is likely an MBR/Legacy install.
If you have a UEFI install, you should be able to boot windows from the BIOS by selecting it in the BIOS.
If you have a Legacy/MBR install and you were booting both Ubuntu and windows from the Grub code in the MBR and you deleted the partition with Ubuntu on it you also deleted almost all the necessary boot files which were on the Ubuntu partition.

If you have a Legacy install, you should be able to use your windows installation DVD or recovery CD to repair the windows boot from the Repair option which should put windows code in the MBR.

---

### Post by leomv on 2019-01-10
I fixed the problem, without loosing any data from my Windows partition. Here's what I did:

-I downloaded the .iso file for Windows 7 installation and created a bootable USB with it.
-I started the computer with the bootable USB.
-Instead of installing Windows, I chose the "Recover" options
-I opened the CMD option for recovery
-Using /bootrec /FixMbr, the problem would be solved

Then, I restarted the computer and Windows booted normally.

---

### Post by oldos2er on 2019-01-11
Would you please mark this thread 'Solved' under Thread Tools at the top of the page? Thank you.

---

