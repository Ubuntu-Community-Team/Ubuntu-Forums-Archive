---
title: "My GRUB Oddysey"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by Sporkmaster on 2007-10-17
Well, I've so far encountered many errors in this thing but here goes

TRIAL ONE: Got a GRUB ERROR 18

-created a 16MiB hda1 FAT16 partition with Windows stuff

TRIAL TWO: Got GRUB ERROR 17

-changed hda1 file format to ext3

TRIAL THREE: Got GRUB ERROR 15

-followed[This guy]("http://users.bigpond.net.au/hermanzone")'s instructions to set up the hda1 partition for GRUB

TRIAL FOUR: Now I have the GRUB command-line boot thing here, but the command boot does nothing but boot the same GRUB screen.

```
grub> root (hd0,1)
Error 18: Selected cylinder exceeds maximum supported by BIOS
grub> root (hd0,0)
kernel /vmlinuz root=/dev/hda2
Error 15: File not found
grub>  find /boot/grub/menu.lst
 (hd0,0)
grub> configfile (hd0,0)/boot/grub/menu.lst
#The screen clears, as GRUB seems to have ONCE AGAIN booted itself
grub> configfile (hd0,X)/boot/grub/menu.lst #Where X is any number above 0
Error 18...

```

-changed Hard Disk Detect to Auto

TRIAL FIVE: Got GRUB menu, after selecting an OS got GRUB ERROR 15

-changed (hd0,2) to (hd0,0) in /boot/grub/menu.lst

TRIAL SIX: Got Grub menu, selected OS, Xubuntu logo and bar comes up, sudden crash with error:

```
BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(intramfs) _
```

---

### Post by Gen2ly on 2007-10-17
Grubs a bitch.  Usually it's fixbable.

The best start would be to start from your Ubuntu-LiveCD and chroot into your existing installation:

```
sudo bash
mkdir /mnt/osname
mount /dev/sda3 /mnt/osname
mount -t proc none /mnt/osname/proc
mount -o bind /dev /mnt/osname/dev
chroot /mnt/osname /bin/bash
```

Start "grub"

and use find to discover you hard-disk (hopefully)

```
find /boot/grub/stage1
```

If you see (hd0,0) define the grub partition:

```
setup (hd0,0)
root (hd0,0)
```

If this doesn't seem to work, Step 2:

In the Grub boot menu, try to use auto-complete (i.e. tab) to discover your partition.  You may beable to discover your partition with this.  Just choose 'e' and try it.

if that doesn't seem to work, you may have hosed your boot sectors.   They are possible to wipe and later restore.  This section will have a few details...  USE WITH UTMOST CARE.

[http://gentoo-wiki.com/MBR](http://gentoo-wiki.com/MBR)

Good Luck

---

### Post by Herman on 2007-10-17
> Well, I've so far encountered many errors in this thing but here goes
TRIAL ONE: Got a GRUB ERROR 18
-created a 16MiB hda1 FAT16 partition with Windows stuff
TRIAL TWO: Got GRUB ERROR 17
-changed hda1 file format to ext3
TRIAL THREE: Got GRUB ERROR 15
-followed[This guy]("http://users.bigpond.net.au/hermanzone")'s instructions to set up the hda1 partition for GRUB
TRIAL FOUR: Now I have the GRUB command-line boot thing here, but the command boot does nothing but boot the same GRUB screen.
What is it you are trying to do, set up a Dedicated GRUB Partition or something?
Here is a link about that if that will help you, [         How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_"), or what is it you are trying to do exactly? 

Regards, Herman :)

---

### Post by AustinMarton on 2007-10-17
Hey I'm not sure if it's completely relivant, but everytime I have a grub issue the 'Super Grub Disk' has been a fantastic help.

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

---

### Post by Sporkmaster on 2007-10-17
Thanks, guys.

OK the reason I'm making a new GRUB partition is because the rest of the hard drive is on a cylinder too far away for the BIOS to find.

Also, if you have any other recommendations, please make them, even if they could break the OS, because this is a brand new installation on a blank HD. It's a computer made of spare parts and it seems they don't like eachother. I'll try your stuff now and see what happens...

---

### Post by Sporkmaster on 2007-10-17
Ironic, as the page I was using was, in fact, Herman's all along.

OK I copied the /boot folder from my laptop onto this new computer and deleted the entries for Windows.

Now I can see the good old menu sitting there, but attempts to boot any of the five operating systems listed result in Error 18.

Note: This is not a conflict of OS difference, as I am using the SAME DISK to install to this new computer that I used about six months ago when I dual-booted my laptop. I checked and the partition numbers seem to match, but I'm still presented with this awful error 18.

The hard drive is the only component in this computer that is actually new, and it seems to have more cylinders than GRUB can handle...

Any help on the next step?

---

### Post by Herman on 2007-10-17
> OK the reason I'm making a new GRUB partition is because the rest of the hard drive is on a cylinder too far away for the BIOS to find.
Oh, okay, you don't want just a 'dedicated GRUB partition' for that, what you need is a 'separate /boot partition'. 
A 'separate /boot partition' contains not only GRUB, but your Linux kernel and initrd.img files and can help computers with hard drive BIOShard drive size limits boot past the                                        8.45 GB Standard INIT13 limitation (CHS[1024x256x512).found in most BIOSes made around late 1990s.

Proabaly the easiest way to do that would be to re-install again and make your separate /boot partition right at teh start of your hard disk, before you make the rest of your partitions ('/' (root) and swap area, and possibly /home if you believe a separate /home is necessary).

Regards, Herman :)

---

### Post by Herman on 2007-10-17
If you still have trouble, check the way you have your hard drive plugged in and jumpered. 
If you have a plain IDE cable,  (with black plugs), you should have your hard drive jumpered as master, and possibly your CD/DVD drive jumpered as slave.

If you have a 'cable select' IDE cable, (with a blue plug to the motherboard socket, a black plug for the master hard drive, and a grey plug for the slave), then you need to set the jumpers on your drives to 'cable select'. Check the stickers on top of your drives for instructions about how to set the jumper settings for your particular drives.

I'm not saying that's your problem or not, just giving general advice, a lot of people who assemble their own computers have the same problems.

I'm am another person who likes to fix old computers or make them into new computers and generally mess around with hardware. I'm pleased to meet someone else with similar interests.  :)

Regards, Herman :)

---

### Post by Sporkmaster on 2007-10-17
Well, I've been poking around in the BIOS and the Error 18s are gone, now replaced with Error 15s

I copied the entire /boot directory from my laptop onto this thing, and the laptop boots fine.

Did I forget something?

---

### Post by Sporkmaster on 2007-10-17
YES! I've found it! 

All of the entries in GRUB were set to look on hd0,2

I just changed all of them to hd0,0 and it BOOTED!

Unfortunately, I now seem to have a completely different boot error outside of GRUB :(

I'll try re-reinstalling xubuntu, as I did mess with that partition alot

---

