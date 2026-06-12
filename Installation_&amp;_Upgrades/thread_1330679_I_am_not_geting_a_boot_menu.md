---
title: "I am not geting a boot menu"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by techforay on 2009-11-18
I installed ubuntu inside windows using this method.
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

My windows boots from a G:drive but when I installed ubuntu 9.10 I selected my H:drive because it had more space.  After all was installed I was asked to reboot and I expected to get a menu to select ubuntu or windows like the tutorial says.  I did not.  I do not know how to launch ubuntu.

---

### Post by wrgb2 on 2009-11-18
With Wubi, you need to install Ubuntu on the same drive your pc boots from.  The problem you have now is that the boot manager is on the H: drive and your booting from the G: drive.

---

### Post by darkod on 2009-11-18
Go into Add/Remove programs, there should be Ubuntu there. Remove it and try again. Maybe it just didn't work the first time.

---

### Post by darkod on 2009-11-18
No, you don't. I've had wubi (ubuntu) on F: while my windows was on C:. Something else went wrong. Try second time, then we'll see.

PS. Why do you need wubi anyway? Boot with the ubuntu cd and select the option Try Ubuntu. It will run from the cd and will not make any changes to your hdd. You can look around, even surf the web, try applications, and see if you like it and whether all hardware will work fine. Graphics, sound, network, etc.

Then when you decide to install again boot with the cd and select option Install Ubuntu, etc...

You don't really need to bother with wubi especially if it didn't work.

---

### Post by techforay on 2009-11-18
Thanks for your help.  I already have played with it and know that I like it.  The only reason I used WUBI is my primary drive G: is getting full.  I have a huge secondary drive H:  I am a Linux novice so I thought that WUBI would do all the linking for me.  I am willing and would like to dual boot but should I clean some stuff off my primary drive and dual boot there.  Is there a novice type tutorial for dual booting with XP?

---

### Post by darkod on 2009-11-18
No need for any special tutorial, if you google you will probably find loads.
The most important thing to consider is that you need FREE SPACE to install ubuntu obviously. But not free space just like unused in a windows partition.
Linux works with different type of filesystem and partitions. You actually need free unpartitioned space.
It can be a whole hdd, it can be just a part of hdd. You need at least 30GB outside of a windows partition.
For example if you have 100GB and 150GB windows partitions on a 250GB drive, you would have to shrink the second from 150GB to 100GB and you will get 50GB free unpartitioned space to create linux partitions.

So just sit down and make a plan how you want your drives to look like.

---

### Post by techforay on 2009-11-18
On my secondary drive I have lots of space to shrink a partition.  I would like to install ubuntu on that drive.  Using dual boot on a secondary drive how do I get it to boot? By going into bios each time and changing the hard drive order?

---

### Post by darkod on 2009-11-18
I definitely wouldn't do it like that, although some people give that advice. It's much more complicated to select drives in BIOS every time, than entries in the grub menu right?

It's best to shrink a partition with Gparted. Boot with the ubuntu CD, select Try Ubuntu option, that should not mount your hdds. Open System -> Admin -> Gparted and select the correct drive, the correct partition and shrink it how much you want. If by any chance that drive is mounted just click on that partition and unmount it.

The shrinking will create unpartitioned space. Then again boot with the CD, select Install Ubuntu option and proceed. When asked where to install select Manual Partitioning, select the correct drive, the empty space and create your ubuntu partitions.

You need at least / (root) and swap. Optional /home as separate partition. If you want to read more about that, google is your best friend. :)

IMPORTANT: On the last screen of the installer, just before you click Install button, there is Advanced. Click there and it will offer choice where to install grub2, the bootloader. I would select your other (first) drive, the one where windows is installed because BIOS is already set up to look for the boot sector there. So, if your ubuntu drive is your second one for example, and called /dev/sdb, then tell grub2 to install on /dev/sda. Be careful, not on a specific partition like /dev/sda1, but on the whole drive, /dev/sda.

And that's it. Enjoy your new Ubuntu.

---

### Post by techforay on 2009-11-18
Thank you very much for your help.

---

### Post by techforay on 2009-11-18
I figured out why I was not seeing the boot menu.  The system seting in control pannel was set to on second.  Now I have a different problem.  I can see the menu but the arrows on my keyboard wont work untill after windows loads.  The default "windows" is selected.  I know how to change the default in windows but can I change the default back to windows from ubuntu?

---

