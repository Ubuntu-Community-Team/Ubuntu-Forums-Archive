---
title: "Can't install Ubuntu 11.10."
date: 2012-02-17
forum: Installation &amp; Upgrades
---

### Post by Hartismere on 2012-02-17
Heyho,

I've been checking Ubuntu out from CD, and I'd like to install it. I have a spare drive, which I bought for this purpose - Linux of one form or another. However, it's not happening.

I've got the Install window open. It is only showing one drive at the top (coloured bars) - I have four, and I cannot make it show any of the others. Why can I not make other drives show up here?  As far as I'm aware I made no earlier choices concerning which drive I wanted to install to, so why has it selected this one? The drive showing is, coincidentally, the drive I want to use, which is nice, but odd. It has two partitions. Partition 1 is showing green, partition two is orange. I have worked out Ubuntu's naming system; sda, sdb, and so can choose that first partition from the drop down menu under

Device for boot loader installation.

Buuuuut, does this actually refer to where I want to install Ubuntu, or does this mean something else? Why not say Device to install Ubuntu? Is the boot loader something other than Ubuntu itself? Or just differing terminology?

Then each time I try to go ahead with the install, I get a box offering;

No root file system is defined. Please correct this from the partitioning menu.

So where is this partitioning menu? I can see "New Partition Table" followed by a list of other options alongside, but nothing I do in any of them will get me past this error message. From Change, of these, I have chosen to

use it as NTFS and Format it and chosen dos AND windows as the Mount point(?).  Nada.

I understand why the NTFS and choosing to Format, but whether dos or windows I haven't a clue. Neither will allow me to proceed to install anyway. What does "Mount Point" mean and want? When I get back to the main window the Format box is not ticked, but is filled with colour, and determinedly remains so throughout other attempts to change it. I am only choosing Format because it has always given me the best outcomes when installing various Windows. So I'm not bothered either way if it doesn't matter. Incidentally, why offer me windows and dos in this, a different Operating System installation? Should I be choosing a different file system?

My PC is a self-build, and happilly dual boots XP and 7 64bit. The hard disk chosen is 250Gig; Partition 1 43Gig, P2 the rest.

Advice welcomed Ta!

---

### Post by Paddy Landau on 2012-02-18
Windows calls partitions C:, E:, and so forth (usually D: is reserved for your DVD drive), regardless of the underlying physical devices.

In Linux, sda, sdb, sdc and so forth apply to physical drives, not partitions.

Partitions within a drive are referred to with numbers; so sda might  have sda1, sda2, sda3, etc. Partition numbers are not necessarily in  numerical order, so sdb might have sdb3, sdb5, sdb6, sdb8, sdb2.

Partition numbers 1, 2, 3 and 4 are either "primary" or "extended" partitions. Partition numbers 5 and up are "logical" partitions.

When you choose the device, you'll need to choose "Something else" in order to specify the exact drive and partitions therein.

To install Ubuntu, you need two partitions, preferably three, as follows:

[LIST=1]
[*]One partition for the operating system (size 10Gb should suffice), otherwise known as "root" or *mounted* as "/".
[*]One partition for your data, otherwise known as "home" or mounted as "/home".
[*]One partition for swap. This should be the same size as your RAM. (If you have less than 1Gb RAM, you may want to consider Lubuntu instead of Ubuntu.)
[/LIST]
You can combine 1 and 2 into a single partition, in which case it will be mounted as "/".

If you need help analysing your particular computer's devices and partitions, and deciding where to put Ubuntu, let us know.

---

### Post by Hartismere on 2012-02-19
Hi. Thanks for the reply. Can do the partitioning, but, being only familiar with Windows, uncertain about "mounting" and supplying partitions with either "/home" or other. These are not Windows procedures or naming routines.

How about the rest? What should I have chosen chosen during Installation so as not to get the error message? And what is Mount Point?

Think I'm OK with the rest. Everything worked fine while running it from CD - just slow due to constant access of CD drive. Never got online so easily ever.

I'm sure I'll come across other curiosities that need advice.in the future.

Thanks again.

---

### Post by darkod on 2012-02-19
Linux works with two basic partitions. The main system partition is called root and the mount point is /. The second partition is called swap and is simply a partition used when the RAM gets full, or during hibernation to save the system state.

Apart from those, it is good practice to have a third partition with mount point /home which will include the Home folders for all users on it.

If you don't create it, it will simply be a folder inside / so the resulting location is the same, /home. But the difference is that when it is separate partition, you can do a clean install of ubuntu in the future and leave /home without formatting it, so all your data is kept. Something similar like in windows when you have a second partition D:, you can do a reinstall and format C: but all your data on D: is untouched.

As for the no root filesystem message, you are trying to continue the install without telling it which partition to use as /.

The first thing you should check, do you have unpartitioned space on the disk you want to use. In windows most disks are full with ntfs partitions. Linux doesn't install on ntfs so you need unpartitioned space where it will create its own partitions. If such space doesn't exist, you need to shrink (or delete) one of your ntfs partitions. If using vista or 7 it's always best to shrink with Disk Management.

Second problem that might occur, if you ever used any disk in raid, it might have raid meta data leftovers. Windows ignores these but linux doesn't. If something like that exists, ubuntu might ignore the disk not showing any partitions on it. Have you noticed something like this?

If you get that problem, and you ARE NOT using raid, you can remove meta data in live mode with:
sudo dmraid -E -r /dev/sda (change /dev/sda with the correct device disk)

---

