---
title: "[SOLVED] Grub. Forcing recognition of XP for dual boot."
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by hundred1906 on 2008-04-14
I have installed Ubuntu (7.10) onto an spare sector on a secondary disk on my windows XP machine. I manually configured the installation to achieve this so as to leave the windows installation un-touched. Now the system boots up straight into Linux.

What I need is a dual boot option but GRUB has no entry for my XP installation. This is probably because my XP is on a Raid 0 drive and I assume the Ubuntu build could not find it.

So how can I either create a manual entry for GRUB (but I do not have access to XP boot parameters). Or force XP to boot. Or should I load up Raid for Ubuntu so that I can get the XP info to put into GRUB, if so how. Or what?

Why am I in this mess - its because XP got a couple of viruses that have proven very difficult to shift and I thought Linux would be a good place from which to work in the future. But first I needed to recover lots of pre-existing pictures and other media files.

Trevor. :confused:

---

### Post by StefAndrew on 2008-04-14
From the terminal:

> 
gksudo gedit /boot/grub/menu.lst
At the bottom is where you can input the following lines, but you'll need to find out what partition number your XP partition is:

> title               Windows XP
  root              (hd0)
  chainloader   +1
hd0 is usually the default for the first partition on the hard drive.  Since you have a RAID 0 going though, I'm not sure how that will affect it.

You can look up the partitions with gparted application as well and see if linux sees a partition for it.

I hope this at least gets your started in the right direction.

---

### Post by logos34 on 2008-04-14
actually your windows entry will need a root line with this format:

root (hdx,y)

If you're booting from linux, then that drive is almost certainly hd0, and the windows hd1 (unless grub overwrote the xp booloader on one of the raid drives)

Post the output of
[B]
sudo fdisk -l[/B]

---

### Post by hundred1906 on 2008-04-15
Perfect. Problem overcome.

I used: 

title		Windows XP
root		(hd0,0)
chainloader +1

Now I just need to sort out how to access my Raid 1 files.

Trevor

---

### Post by StefAndrew on 2008-04-15
Did you set up the raid through your hard drive controller or through Windows disk manager?

I guess if it's your system HD, it'd be pretty hard to do a RAID on it from disk manager.  I don't have any experience with communicating with a raid array in linux, so I really can't help out with that part.  Sorry.

---

