---
title: "dual harddrive 2 dual boot"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by LordCla on 2007-09-18
So I have this dual booting idea and I want your professional opinions. I have 2 hard drives and one of them has ubuntu 7.04 installed on it (works fine). Is it a good ideea to use Gparted to format /partition the other hard disk to use with Windows. I would select it (hard no 2) as 1st bootable in bios . install win to the new partition .and then i could select what OS load up from the bios (by setting the hard drive boot order)

  What do you think of this? Will it work?

---

### Post by dabl on 2007-09-18
No.

Well, not exactly.  The problem is, if you do what you are proposing, Windows will be the only OS that you can boot, and it will boot automatically. So, the hard drive that has Linux will be spinning away and you won't have any option to boot it.  Windows will set the "boot" flag on the hard drive where you install it, and even when you change the BIOS sequence, that is the partition that is going to be booted.

It is easy to set up your two hard drives to be a real dual boot system, but you have to approach it differently. Here is the high-level process:

1. Set the BIOS boot sequence the way you want it for the long term, i.e. CD ROM, HDD#1, HDD#2.

2. Install Windows to the hard drive where you want it.

3. Partition the other drive the way you want it (I use the GParted Live CD) for Linux, and install Ubuntu.  At the end of that process, let it install Grub to the MBR on the Windows drive (this is what it will automatically want to do).

4. Now you'll have a boot menu, that will allow you to boot whichever OS you choose.

:guitar:

---

### Post by LordCla on 2007-09-18
Thank you for your advice! But I need to install windows after installing ubuntu. I found a tutorial that explains this . I tried it once and it messed up all my partitions. so I'm looking for alternatives.

---

### Post by dabl on 2007-09-18
> **LordCla said:**
> 

Thank you for your advice!

You are welcome.

>  But I need to install windows after installing ubuntu. 

I completely disagree.  I don't know what tutorial you found, or why it says that.  It is certainly possible to install Ubuntu first and Windows second, but it is FAR easier, in my experience of many times, to let Windows be the first OS installed, and then let Ubuntu install Grub on the MBR where the Windows bootloader is.  So, I would call the Ubuntu-first method the "hard way", and not the best for new Linux users.

  :)

---

