---
title: "XP / Ubuntu 6.06 dual boot via BIOS"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by Philder on 2007-01-05
Hi all

For the past few months I've had my machine set up with XP as master with a Linux partition on a second hard drive. Rather than writing GRUB to MBR, I've been using a boot floppy (distros were Kanotix and more recently BFX2006.1). I'm now happy enough with Linux to want it as my main OS, and am going to install Ubuntu 6.06 from a liveCD, but for now I want to leave XP and the MBR alone. Current plan is to install Ubuntu on the slave drive, then set BIOS to boot from that, leaving the option to boot back into XP but without touching the Windows boot loader. Only problem is that the first partition on the source Ubuntu drive is an encrypted FAT32 partition (using TrueCrypt) for private data. 

Partitions look like this :-

hda1 = XP
hdb1 = 20gb Encrypted partition
hdb2 = Linux Swap
hdb3 = Target for Ubuntu > GRUB to go here

I can set the BIOS to boot from HDD-1 rather than HDD-0, but not sure if that will work due to the first partition on HDD-1 being encrpyted? Going to try it anyway, but just wondered if anyone had any wisdom they could impart?

---

### Post by bulldog on 2007-01-05
Can't say anything about the encrypted partition,but if you install ubuntu on the second hdd,and you want your windows disk untouched,I recommend to disconnect the windows disk,because if you won't do that,you get GRUB installed on that disk.

I think you can safely install ubuntu next to the encrypted partition.
The only thing what can happen is,GRUB pointing to the wrong disk and partition to boot from,and that's easily to repair with the ubuntu live cd.
Let GRUB install in the MBR of the second disk [your ubuntu] this will happen if the other disk is disconnected.

Of course you have to add an entry for your windows manually.
This is also a simple thing to do.

---

### Post by Philder on 2007-01-05
Hadn't occured to unhook the Windows hard drive - I'll give it a go. What would the GRUB config need to look like to "see" the reattached Windows disk? I've not really delved too deep into GRUB until now.

Would the BIOS trick work if GRUB went to the root of the Ubuntu partition, or does it have to be loaded to MBR on that hard drive?

---

### Post by bulldog on 2007-01-05
The best and simplest way is put it into the MBR.
Another thing you should be aware of,if GRUB is installed on the second hdd,you have to make it the master boot device to see the GRUB menu.

You can do so by either set it in the BIOS or switch the hdd's from place at the flat cable.
Otherwise you will be booting right into windows without seeing the GRUB menu.

The advantage of doing it this way is,you can boot windows and ubuntu from GRUB,but if there's going something wrong,you can always boot windows from it's own boot loader,by switching the back.
If you give me the output of ```
 sudo fdisk -l (l as in like)
``` after you switch the disks from place,I can give you the exact entry for your windows.

---

### Post by louieb on 2007-01-05
You should be ok if you do what Bulldog suggested and unplug the windows drive before stating the Ubuntu install. 
By using the manual partitioning option you will have no problem using hdb3 for Ubuntu and hdb2 for swap. 
Ubuntu is just like all the other Linux distributions I have tried in that the boot loader last thing installed. Just let it install to the MBR.
The first 466 byte of the [MBR]("http://www.cpqlinux.com/mbr.html") of hdb2 is what GRUB modifies. What it does is place some code in there to run the program /boot/grub/stage2.  The Grub installer knows which partition to look to find it. 
The thing that I am not sure of is how your BIOS is going to report the second drive with the first drive unplugged. If the manual partitioner show it to be hdb then your ok. If not then you may have to do some post installation tweaking of you menu.lst and /etc/fstab in order to get Ubuntu (or some other Linux) to work.

Or you can do what Bulldog suggested in his last post and make the windows drive the slave and the Ubuntu drive the master and use GRUB instead of BIOS to dual boot. I have done exactly that on a couple of my PC's.
But it looks like either way your windows drive and the encrypted partition remain untouched.

---

