---
title: "Breezy install on Thinkpad R50 : Windows is hosed upon Ubuntu install"
date: 2005-11-07
forum: Installation &amp; Upgrades
---

### Post by deepakjois on 2005-11-07
I tried installing Ubuntu Breezy on a Thinkpad R50. The Thinkpad R50 HDD has a weird arrangement. There is a hidden partition which contains a factory default installation for recovery purposes. I suspect that is creating problems. It is possible to 'unhide' the partition using the BIOS, but I am reluctant to do that.

Here is what is happening. I tried the same thing twice and got exactly the same problem.

1. boot into a knoppix live cd and use fdisk to remove all partitions (the hidden parition does not show up in fdisk so that is intact.).

2. install windows on the first 15 gig and check that it works fine.

3. Install Ubuntu Breezy from CD. Use guided partitioning to install on largest available continuous free space.

4. Boot and check that Grub is installed fine and Ubuntu linux is fine

5. Reboot and try booting into windows. The Windows splash screen shows up, and then i get the BLUE SCREEN OF DEATH, along with an error UNMOUNTABLE_BOOT_VOLUME .

This happened both times i tried. I have come across posts on the internet talking about bad experiences due to the hidden partition. But I am reluctant to 'unhide' the partition. 

Is there any way  I can install breezy without hosing windows

---

### Post by lorenco on 2005-11-07
I have breezy running on a T41 with windows... 

A couple of comments :
1. The hidden partition is a good thing if you only want to run windows. IBM can ship recovery CD's (Better than the hidden partition) but only on request.  Contact your local IBM support center / or over the web.  This would help to get rid of this partition. (I did this and received 5 CD's)...

2.I have done both of these below with various success.
2.1 Install Ubunutu first using custom partitioning:
 2.1.1 Create Windows Partition but leave it empty (We can add this later)
 2.1.2. Create Linux Partition and swap
 2.1.3 Install Grub on the /boot or / partition (not Master Boot Record)
(I Sometimes get a failure but success upon a retry...)
 2.1.4 Install windows
 2.1.5 Set Boot back to /dev/hxx <- Where Grub is.
 2.1.6 Add grub entry :
             --- your header here (syntax not in my head ;) )
             "root (hd0,x)" Where x = partition where windows is (like 0 for /dev/hda1)
             "chainloader +1"
             "boot"

2.2 Install Windows First like you did (But this I have done after trashing my recovery partition)


3. Use XOSL (Install XOSL on you MBR with XOSL file somewhere else like a 500k Dos disk (hda1) like first primary disk.   This gives a lot of freedom for mutliple OS's... I have 2xGrub (duhhh) but still works, Win32 boot loader and XOSL aal on my Other IBM T41.

The current T41 I am using has : KUBUNTU ONLY!. Works like a charm with Windows running in VMWARE ... (The best of all solutions!)

---

### Post by Xerbee on 2005-12-30
I had the same problem yesterday while installting on my R50. If you still have problem there is a simple way of fixing it. 

Install Ubuntu, i used auto partition so its hda0 and hda1. hda0 is / and hda1 is swap. Then i installed Windows on the remaining 20gb. Windows destroyes the MBR so i boot with a live CD into Ubuntu and reinstall grub. After that my windows partition didnt boot so i just edited grub config (/boot/grub/menu.lst) and added the windows partition. 

Read "How to add Windows entry into GRUB menu?"
[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

---

### Post by Ray Hamilton on 2005-12-30
I have successfully installed breezy on  my Thinkpad R50, without removing the recovery partition.  I left this intact when installing and used/allowed grub to install where it wished.  So now my machine dual boots XP Home and Ubuntu. I have read that this means that I will not be able to use the recovery option but have not confirmed this yet (I have a friend with one also and intend to create recovery disks from that).  Of course if you have already removed the partition ....

---

### Post by wrexy on 2005-12-30
I have also install dual boot Xp home/Unbuntu. 

This is what my hdd looks like:
Disk /dev/hda: 40.0 GB, 40007761920 bytes
16 heads, 63 sectors/track, 77520 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       13579     6843658+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2           68146       77520     4725000   12  Compaq diagnostics
Partition 2 does not end on cylinder boundary.
/dev/hda3           13579       56881    21824302+  83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hda4           56881       68145     5677087+   5  Extended
/dev/hda5           56882       66958     5078808   83  Linux
/dev/hda6           66959       68145      598216+  82  Linux swap / Solaris

Partition table entries are not in disk order

Everything from IBM remains intact. I have used Gparted to resize the win partition and then install Unbuntu in the spare space. Note that the recovery partition is only a dos partition which resides at the end of the hdd.

---

