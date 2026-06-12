---
title: "Problem: computer keeps rebooting non stop"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by jbullfrog on 2008-05-16
I recently resized and moved all my partitions on my laptop using Gparted.  I have a Dell Vostro 1400.  I also deleted one partition, the 2.5GB that was used for Dell Media Direct.

I left one large unallocated space at the very end of all my partitions.  I never installed Ubuntu.

Now when I boot up my computer, the DELL screen keeps on loading over and over again.

What the heck happened?  How do I solve this?

I am terribly lost and confused.

---

### Post by Rallg on 2008-05-16
When you say you never installed Ubuntu, I presume that you are trying to locate Windows (Vista or XP) on the hard drive?

Use the Ubuntu live CD to launch GParted. What is the format of each partition? Is each partition primary, or a logical partition within an extended partition? Which one contains the Windows operating system?

Is one of the partitions marked with the "boot" flag? If not, or if it is the wrong one, you can change that and try again.

Can you actually locate the Windows operating system files? For that, don't use GParted. Mount the hard drive to the live desktop, and locate the place where Windows out to be. Are its files really there?

My guess as to the nature of your problem: The hard drive master boot record (MBR) is pointing to the start of a particular partition, where the boot loader files are kept. But you moved the start point of that partition, and now the boot loader files cannot be located. That will probably have to be fixed using Windows technology, rather than Ubuntu technology. If you have the Windows installation DVD or CD for your system, it has a boot restore feature. If you don't have the install media but have XP (and if your Windows files can still be located), you may need to use "Bart PE" technology (search for it on the Internet). If you have Vista without the install media, I don't know what to do.

It might be tht case that merely moving the boot flag in GParted will fix your problem. In any case, you will probably find more joy by searching for Windows boot restore on the Internet, since merely moving partitions would not create a Linux-related problem.

---

### Post by Sef on 2008-05-16
> Use the Ubuntu live CD to launch GParted. What is the format of each partition? Is each partition primary, or a logical partition within an extended partition? Which one contains the Windows operating system?

From the Live CD, Applications > Accessories > Terminal, then type in this code:

```
sudo fdisk -l
``` Small L

then paste the results here.

That will tell us what partitions you have; what is the boot partition, and what is on each partition.

---

### Post by jbullfrog on 2008-05-16
[IMG]http://jeremiahstonybrook.googlepages.com/2008-05-15_071924.jpg/2008-05-15_071924-full;init:.jpg[/IMG]

I deleted the 2nd partition (used for dell media connect) and reduced the size of the other 3 partitions.  I also left a large unallocated space (~50 GB) following the first three partitions.  

My third partition was the one that contained Vista.

I don't understand what you mean when you say "Mount the hard drive to the live desktop, and locate the place where Windows out to be. Are its files really there?"

How do I do this?  Could you give me some steps?

---

### Post by Pumalite on 2008-05-16
Get a Knoppix Live CD. It'll mount all your drives/partitions automatically at boot.
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Burn to disk and boot from it.

---

### Post by Rallg on 2008-05-16
Based on the above, it looks like your Windows is still there, and ready to go. You just don't have the correct master boot record pointer.

Do you have the Vista installation DVD? If so, boot to it. It has a utility for repairing your boot.

If the DVD claims that there is no existing installation of Windows, it means that the partition record is amiss. This can still be fixed BUT it is a matter for expert Windows Vista advice, rather than Ubuntu advice. My point is that Ubuntu is not causing your problem.

Given that you appear not to be a regular Linux user, trying to fix the problem via Linux (Ubuntu, Knoppix, etc.) might be confusing and dangerous. Get your advice from a Vista-specific help board somewhere, and only use Linux if that's the advice.

It is possible (not likely) that you might have to re-install Vista. If that is the only solution, you can still recover any useful files that you have sitting in the former installation. BEFORE re-installing, use a live Linux CD to copy files from your hard drive to some other media, such as a USB stick.

---

### Post by jbullfrog on 2008-05-17
Hi everyone.  I eventually had to reinstall vista, but I was luckily able to save all my necessary files beforehand using Ubuntu live cd.

I now have a dual boot between vista and ubuntu, and as of now, have no problems.

Thanks everyone!

BTW, here are my partitions right now,  Is this a good setup?

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001c19b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7296    58602539+   7  HPFS/NTFS
/dev/sda2            7297       14593    58613152+   5  Extended
/dev/sda5            7297        7420      995998+  82  Linux swap / Solaris
/dev/sda6            7421        9287    14996646   83  Linux
/dev/sda7            9288       14593    42620413+  83  Linux
Name@Silas:~$

---

### Post by Sef on 2008-05-17
> BTW, here are my partitions right now, Is this a good setup?

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001c19b

Device Boot Start End Blocks Id System
/dev/sda1 * 1 7296 58602539+ 7 HPFS/NTFS
/dev/sda2 7297 14593 58613152+ 5 Extended
/dev/sda5 7297 7420 995998+ 82 Linux swap / Solaris
/dev/sda6 7421 9287 14996646 83 Linux
/dev/sda7 9288 14593 42620413+ 83 Linux
Name@Silas:~$ 

Yes, that looks good.  Windows is on the first partition, which it needs to be.  (Windows requires it.)

---

