---
title: "Trouble with my Ubuntu Boot."
date: 2013-09-20
forum: Installation &amp; Upgrades
---

### Post by Seaford_Linton on 2013-09-20
I didnt want to bother anyone but im confused now and i'm feeling defeated. for two days now i been trying to get Ubuntu to boot.
The Install went flawlessly I partitioned my drives the way it was supposed to go and made sure everything was set, no errors or anything. after the install Ubuntu told me that i should reboot. fine.

I completely Deleted Windows 7 for Ubuntu, I dont have any Windows CD, and i Burned Ubuntu to my USB Flash Drive,


[Ubuntu 13.04]
I hit Shutdown and then Restart. after the screen rebooted and i know it was safe to finally pull out my USB Drive, I did so.
Then waiting for something to happen i was hit with this.

"This is not a bootable disk. Please insert a bootable floopy and press any key to try again"

Please tell me i dont need my USB or floopy to boot ubuntu. Im really stuck here. and I would like to get this working. i kinda narrowed it down to the HDD and Grub2 for the life of me i cant seem to get my computer to see Ubuntu. its almost as if the Computer cant see the Boot Partition. Please help me..im willing to try anything to get my only operating system working.

I dont have any Windows CD so any chance to Reinstalling that is out the Window. All i have is this Flash Drive of Ubuntu 13.04.
I will be keep my eye on this post..i really need help.

---

### Post by Bashing-om on 2013-09-20
Seaford_Linton; Hi ! Welcome to the forum.

Not a bother ! We are here to help.

Try this:
Boot the USB ->try ubuntu mode ->key combo ctl+alt+t yields a terminal.
Let's see if your problem is that grub (Grand Unified Bootloader) is not properly installed. We will install grub to the 1st hard drive .. assuming that there is only the one hard drive installed in your box.
Terminal code:
```

sudo grub-install /dev/sda

```
exit out of all and 
Reboot.

Can you now boot your install ?
[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Seaford_Linton on 2013-09-20
ok i will try that and respond with my findings
ok i tried to run the code and i get this.

ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.

---

### Post by Bashing-om on 2013-09-20
Seaford_Linton; Well ..
That says we have to mount that partition in order in install grub, OK
Mount your OS partition:
```

sudo mount /dev/sda1 /mnt

```
Next, install GRUB2:
```

sudo grub-install --root-directory=/mnt /dev/sda

```
Now unmount:
```

sudo umount /mnt

```
reboot ..

How now ?
[INDENT][INDENT]ubuntu, always more than one way
[/INDENT][/INDENT]

---

### Post by Seaford_Linton on 2013-09-20
ok i'll let you know my progress shortly after restart

---

### Post by Seaford_Linton on 2013-09-20
ok I got an Update that seems Promising.

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo umount /mnt
ubuntu@ubuntu:~$ sudo reboot

After I restarted I was Greeted with this message, alot different from my last message

"GNU GRUB Version 2.00-13Unbuntu3

Minimal BASH-like line editing is supported, for the first word, TAB  lists possible command completions. Anywhere else TAB lists possible  device or file completions"

grub> _

What do i do now?

---

### Post by Bashing-om on 2013-09-20
Seaford_Linton; 
Well, now grub is telling us that it cannot find the remainder of the boot code, or maybe it is corrupt.
There are means to direct grub in booting from that prompt but a bit technical.
Ok, do you know the partition that you installed "/" on ? 
Did you install /boot to it's own partition ?

Let's see how you have your hard disk partitioned.
From the liveUSB, terminal code:
```

sudo fdisk -lu

```

we will see

---

### Post by Seaford_Linton on 2013-09-20
Here's the results of that code

ubuntu@ubuntu:~$ **sudo fdisk -lu**

Disk /dev/sda: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe47aa92a

   Device Boot      Start         End      Blocks   Id  System
[B]/dev/sda1   *        2048     1048575      523264   83  Linux                             <------Boot
/dev/sda2         1048576     5238783     2095104   82  Linux swap / Solaris
/dev/sda3         5238784   652394495   323577856   83  Linux                 <-------/home
/dev/sda4       652394496   781422591    64514048   83  Linux[/B]               **<-------/ (Root)**

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
16 heads, 63 sectors/track, 775221 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0822074a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   781422767   390711352+  42  SFS

Disk /dev/sdc: 4004 MB, 4004511744 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *         128     7821311     3910592    b  W95 FAT32
ubuntu@ubuntu:~$

---

### Post by Bashing-om on 2013-09-20
Seaford_Linton; Shucks.

You do have a separate /boot partition. The former commands places the boot code in the wrong place for such a configuration.
Let me have a bit of time to confirm how to place the boot code to the /boot partition. (sda1 NOT to sda !)

I will be back

---

### Post by Seaford_Linton on 2013-09-20
ok i'll be waiting

---

### Post by Bashing-om on 2013-09-20
Never mind this one .. I re thought it .. did not seem correct .. still 

[INDENT]look'n for a solution
[/INDENT]

---

### Post by Seaford_Linton on 2013-09-21
i appreciate your help. this cant be easy so im paitently waiting.

---

### Post by Bashing-om on 2013-09-21
Seaford_Linton; I think I have a means to install grub to sda1 partition.

However, may I ask why you want a separate boot partition ? Now-a-days that practice is highly discouraged:
And I knew I pulled my separate boot partition when I redid my system for reason:
I ran across these:
> 
However, sharing /boot is more complex and generally not a good idea, especially as Ubuntu defaults to using no separate boot partition. A separate /boot is something of an anachronism, dating back to limited PC BIOSes that could only handle small disks, so the boot files had to be at the start of the disk. Nowadays, this is no longer applicable and I don't use a boot partition on anything. You have a couple of options. The best in the long term, but the most work, is to back up your install, using either a second drive or a pile of DVDs, and repartition the disk from scratch.
&&

If you want to install GRUB2 to the boot sector of a partition for some strange reason, you may use something like /dev/sda1 or /dev/sda2 for writing GRUB's boot.img to a partition boot sector. The practice of installing GRUB2 to partition boot sectors is not encouraged. It reduces GRUB's reliability and it could be dangerous to other operating systems if users use the grub-install command carelessly or ill-informed and write GRUB to the wrong boot sector.


How about taking the time to do as the article advises and (re)partition and (re-)install without the separate boot partition ??

The call is yours .. what ever you want to do in light of the information. 

[INDENT][INDENT]here to help
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-09-21
Seaford_Linton; Hey .

In the event you decide to go ahead with a separate /boot partition (waste of disk space also), try this modified code:
Once more from the liveUSB:
```

sudo mount /dev/sda4 /mnt/boot
sudo grub-install --root-directory=/mnt/boot /dev/sda
sudo umount /mnt/boot

```
I still have some reservations in respect to the mount point, but, I think it is as we need it to be (??)
sda4 as root on the install, and should now install the boot code to the MBR of sda and point the loader to the look for those remaining files in sda1 (/boot) as per [/mnt/boot].

[INDENT][INDENT]maybe yes, maybe not so yes
[/INDENT][/INDENT]

---

### Post by Seaford_Linton on 2013-09-21
Thank you for Responding

I should probably mention i'm new to linux and before even thinking  about installing i decided to do some research on how to install
everyone always say to make a seprate partition. I never asked questions  i just followed along. Im willing to try anything to get my Ubuntu  working. i'm Willing to learn Linux for i got seriously fed up with  windows. sorry for my delay, i went to sleep waiting.

I will try this and let you know the results.

---

### Post by Seaford_Linton on 2013-09-21
I am back and **SUCCESS**
I am **Officially** in **Ubuntu 13.04** the Boot loaded, I got to put in my password.
Everything is working fine. You are a Genius 

**Thanks so much for helping me.**

---

### Post by Bashing-om on 2013-09-21
Seaford_Linton; Outstanding !

Again, welcome to our world of open source; ubuntu in particular !
Do not be a stranger, come back often and share with others.

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

