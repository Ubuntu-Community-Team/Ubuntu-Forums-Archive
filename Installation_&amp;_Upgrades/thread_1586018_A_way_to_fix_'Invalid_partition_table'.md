---
title: "A way to fix 'Invalid partition table'"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by emonti on 2010-10-01
Hi,

I have had a problem whilst trying to rewrite the MBR on a NTFS-only harddisk which has one partition.

I'm wondering if I can do anything to fix the problem from my ubuntu CD which gives me access to a shell - using the trial/demo mode.

The problem is that I can't boot into WinXP since using the XP boot cd to go into recovery mode and typing in 'fixmbr \Device\Harddisk0\Partition1'.

All I get is the message

>  "Press any key to boot from CD ..." followed by > "Invalid partition table."

I tried to mount as ntfs but I get :

> 
"NTFS signature missing" 

Failed to mount '/dev/sda': Invalid argument. The device '/dev/sda' doesn't seem to have a valid NTFS. 


Thought perhaps there may be a way to restore the missing signature or something, from ubuntu. Anyone have any ideas?

Regards
Jim

---

### Post by psusi on 2010-10-01
Open a terminal and run sudo fdisk -l and post the results.

---

### Post by emonti on 2010-10-01
Hi psusi,

Here is the output you requested:

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x10981097

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4997    40138371    7  HPFS/NTFS

Disk /dev/sdb: 1998 MB, 1998585344 bytes
4 heads, 16 sectors/track, 60991 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x584ec45d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60992     1951735+   b  W95 FAT32
ubuntu@ubuntu:~$ 


Jim

---

### Post by srs5694 on 2010-10-01
Which disk is the problem one, /dev/sda or /dev/sdb? It looks like /dev/sdb is one cylinder too big for the disk; however, that's really impossible to tell using cylinder units; you'd need to re-run the fdisk command as "sudo fdisk -lu" rather than "sudo fdisk -l". If you do and post the results, please post them between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings to improve legibility.

---

### Post by emonti on 2010-10-01
Okay, here we go:


```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders, total 80293248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x10981097

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    80276804    40138371    7  HPFS/NTFS
ubuntu@ubuntu:~$ 
```

/dev/sda(or should I say sda1?) is the only drive in the machine and it has Windows XP Home on it. sdb was the usb pendrive I was using to transfer fdisk output between machines.

Jim

---

### Post by psusi on 2010-10-01
Did you have the usb stick plugged in at the time you got the error?  Because it looks like that one is messed up and the hard disk is fine.

---

### Post by emonti on 2010-10-01
Gee... it could've been plugged in but I will reboot without any usb drives and see if there is still a problem. I'll take out the ubuntu cd too and see what happens.

Jim

---

### Post by emonti on 2010-10-01
Did that and got:


> Searching for Boot Record from CDROM .. Not Found
Searching for Boot Record from Floppy .. Not Found
Searching for Boot Record from IDE-0 .. OK

Invalid partition table


That time there were no drives plugged in and no cd-rom/floppy disks inserted.

Jim

---

### Post by psusi on 2010-10-01
You can try running testdisk on it, but otherwise all I've got is Windows is stupid.  It doesn't look like there's anything wrong with your partition table.

---

### Post by emonti on 2010-10-01
Hmm .... that is good news and bad news at the same time.

Strange I can't mount it from linux, then. If the partition was okay, shouldn't I be able to do that? 

I mean this was originally a problem trying to erase the prompt for boot up into winxp/mandriva flash. That was only a problem with the boot sector. I assume the partition is on the main harddisk sector and the table... where is the partition table?

And what is testdisk? 

Jim

---

### Post by psusi on 2010-10-01
The partition table is in the first sector of the hard disk.  testdisk is a program that attempts to fix various problems with disks.  Your attempt to mount it failed because you tried to mount the entire drive ( sda ), instead of the partition in it ( sda1 ).

---

### Post by emonti on 2010-10-01
No. 

sda, sda1 - neither will mount. Same msg as before. NTFS signature is missing.

Tell me about testdisk. Where is it?

Jim

---

### Post by psusi on 2010-10-01
In the repositories: sudo apt-get install testdisk

---

### Post by srs5694 on 2010-10-01
I don't see anything wrong with the partition table, either; however, there are a few partition table details that fdisk doesn't routinely report. It's conceivable that one of these is subtly messed up. If so, you might be able to fix it by following this procedure (but be aware there are risks):


[list=1]
[*]Type "sudo fdisk -u /dev/sda" to enter fdisk's interactive mode on the disk.
[*]Type "o" to wipe the partition table and create a new one.
[*]Type "n" to create a new partition. Answer the prompts to create a primary partition, number 1, that begins at sector 63 and ends at sector 80276804.
[*]Type "p" to view the partition table and verify that the start and end points are *exactly* correct -- 63 and 80276804. If not, type "q" to quit and try again.
[*]Type "a" to flag the new partition as active.
[*]Type "t" to change the partition's type code. Enter "07" for the code.
[*]Type "x" to enter the experts' menu.
[*]Type "i" to change the disk identifier. Type "0x10981097" as the identifier.
[*]Type "r" to return to the main menu.
[*]Type "p" to display the partition table. It should look *exactly* like what you posted earlier. Pay particular attention to the number of heads, the number of sectors/track, the disk identifier, and the partition's start and end sector numbers. If these don't all match, type "q" to quit without saving. If they all match, type "w" to save your changes.
[/list]


The fact that you got an "NTFS signature is missing" message when you tried to mount /dev/sda1 suggests that there's a problem with the filesystem *inside* that partition. This doesn't explain the "invalid partition table" message, though. It could be the two are related -- if the partition table is corrupt in some way that's not obvious from the fdisk output, the OS might be looking at the wrong location to mount the filesystem.

---

### Post by emonti on 2010-10-01
Thanks, gentlemen. I'll give your suggestions a go in the morning. It's late here in London.

Jim

---

### Post by emonti on 2010-10-02
This may sound lame but I haven't a clue where to find Testdisk on the ultimatebootcd. It says it is part of part magic which is a bootable version of linux but there is no mention of testdisk anywhere on the menus. So I'm trying to download it using ubuntu install/dem cd. 

Taking ages to load ubuntu from cd, having only 250mg RAM.

As I understand testdisk is an executable. Is that right?

Jim
P.S. if testdisk doesn't work, I'll do the partition table stuff from srs, above.

---

### Post by emonti on 2010-10-02
Ran testdisk and it looked at the structure and came back without detecting any problems. Apparently it compares what it finds with what is in the partition table so it looks fine as you both said.

It's funny, you know, I don't even know what I'm trying to do with testdisk. I don't see any menu items that fit the problem. Anyway, I re-wrote the MBR from testdisk and rebooted but I get exactly the same message.

So I tried following the instructions to change the partition table and got the following when entering 63 for the first sector:


```
Command (m for help): o
Building a new DOS disklabel with disk identifier 0xf3f84078.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First sector (2048-80293247, default 2048): 63
Value out of range.
First sector (2048-80293247, default 2048):
```

Now what?

Jim

---

### Post by psusi on 2010-10-02
Switch off dos compatibility mode with the c command.

---

### Post by emonti on 2010-10-02
Done. I made sure I did that before I reached this step.

Why is it coming up with 2048? Is it possible it is conflicting with another pendrive? There is a wireless usb device still plugged in.

Jim

---

### Post by emonti on 2010-10-02
Ha!

Problem solved. Problem**s** should I say - both problems fixed.

The second problem 'Invalid partition table' on startup was fixed by me running 'fixboot c:' from 'R' mode after booting up from the winXP cd.

This took me back to the first problem... trying to get rid of the dual boot prompt seeing as there was only one partition and OS to boot anyway. This I removed by running the uninstaller (who'd have thought?). Actually I had already run an uninstaller before but from the start mandriva GUI option that's why I thought I had cover that option. This folder which I stumbled onto, by accident almost, had an uninstall.exe in it.

Thanks to psusi and srs5694 for your time. Hopefully this post will be of some help to other in future ;-)

Jim

---

### Post by srs5694 on 2010-10-02
I realize the problem is solved; however, just to answer some lingering side questions....

> **psusi said:**
> Switch off dos compatibility mode with the c command.

Actually, for this specific task, DOS compatibility mode would need to be turned *on,* not off.

[quote=emonti]Why is it coming up with 2048? Is it possible it is conflicting with another pendrive? There is a wireless usb device still plugged in.[/quote]

There's no device conflict. In the 1980s, and to some extent through much of the 1990s, hard disks used cylinder/head/sector (CHS) addressing, and partitions had to begin on cylinder boundaries. Starting in the 1990s, though, CHS addressing was phased out in favor of logical block addressing (LBA). This also did away with the need to align partitions on cylinder boundaries. Today, new issues have become important: For some types of RAID arrays and disks with the new 4096-byte physical sectors but 512-byte logical sectors, it's important that partitions be aligned on boundaries that are multiples of 4 KiB, 16 KiB, or higher, commonly up to 128 KiB. To ensure that this is done, and to give some wiggle room for extreme cases, Microsoft now aligns partitions on 1 MiB boundaries -- that is, every 2048 sectors.

Two independent switches in fdisk adjust how it aligns partitions by default, and what values it permits:


[LIST]
[*]**Entry units** -- By default, fdisk accepts partition start and end points, and displays this information, in terms of cylinders. This is good for 1980s hard disks but is meaningless at best today. You can change to sector units by starting fdisk with the -u switch, or by typing "u" at its main menu prompt.
[*]**Partition alignment** -- By default, fdisk lets you enter any value greater than or equal to the sectors/track value for the start of the first partition (when in sectors mode). This is "DOS compatibility mode". If you turn this off (via the -c command-line switch or by typing "c" at its main menu), fdisk enforces the Microsoft-style value of 2048 as the minimum sector value.
[/LIST]


So basically, by disabling DOS compatibility mode, you were reducing the flexibility of fdisk and making it impossible for it to re-create your original partition, which used the DOS-style sector 63 as the first partition's starting point.

---

### Post by psusi on 2010-10-03
> **srs5694 said:**
> 
Actually, for this specific task, DOS compatibility mode would need to be turned *on,* not off.

No, it is on by default and caused the minimum 2048 start sector, so it needed turned off.

> **srs5694 said:**
> 
So basically, by disabling DOS compatibility mode, you were reducing the flexibility of fdisk and making it impossible for it to re-create your original partition, which used the DOS-style sector 63 as the first partition's starting point.

I'm afraid you have it backwards.  Compatibility mode = restrictions on where you can put things, which these days means starting at sector 2048.  No compatibility mode = put it wherever you want.

---

### Post by srs5694 on 2010-10-03
> **psusi said:**
> No, it is on by default and caused the minimum 2048 start sector, so it needed turned off.

I'm afraid you have it backwards.  Compatibility mode = restrictions on where you can put things, which these days means starting at sector 2048.  No compatibility mode = put it wherever you want.

There have been significant changes in fdisk along these lines with recent versions. Here's what happens for me, using a USB flash drive for testing and fdisk from util-linux 2.17.2:

```

$ sudo fdisk -u /dev/sdc

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c').
```

Note that it's starting up with DOS compatibility mode enabled.

```
Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First sector (32-31576063, default 32): 32
Last sector, +sectors or +size{K,M,G} (32-31576063, default 31576063): 
Using default value 31576063
```

With DOS compatibility mode disabled (the default), I was able to create a partition starting at sector 32 (the sectors/track value for this small drive).

```
Command (m for help): p

Disk /dev/sdc: 16.2 GB, 16166944768 bytes
64 heads, 32 sectors/track, 15418 cylinders, total 31576064 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd81e4170

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              32    31576063    15788016   83  Linux

Command (m for help): d
Selected partition 1
```

Now, disable DOS compatibility mode and see what happens....

```
Command (m for help): c
DOS Compatibility flag is not set

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 1
First sector (2048-31576063, default 2048): 32
Value out of range.
First sector (2048-31576063, default 2048): 63
Value out of range.
First sector (2048-31576063, default 2048): 2048
Last sector, +sectors or +size{K,M,G} (2048-31576063, default 31576063): 
Using default value 31576063

```

With DOS compatibility mode disabled, fdisk refuses to create a partition that starts below sector 2048.

This behavior is not the same in the older util-linux-2.16-1ubuntu5 on my Ubuntu 9.10 system, though; in that system, DOS compatibility mode works much like above, whereas disabling it enables entry of any value, as you suggest. Enabling DOS compatibility mode, though, will never result in a refusal to create a partition that starts at sector 63 on a blank disk; since that's the maximum permitted sectors/track value, it will always be legal.

Note that emonti claimed to have disabled DOS compatibility mode before creating the partition, and the snippet of output he showed matches what I showed above, in terms of fdisk refusing to create a partition that starts below sector 2048. Therefore, it's clear he's got a more recent version that enforces a minimum starting sector number of 2048 when DOS compatibility mode is disabled.

---

