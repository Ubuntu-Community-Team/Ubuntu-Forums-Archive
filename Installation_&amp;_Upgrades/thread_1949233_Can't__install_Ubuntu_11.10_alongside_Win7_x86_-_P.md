---
title: "Can't  install Ubuntu 11.10 alongside Win7 x86 - Partition not found"
date: 2012-03-29
forum: Installation &amp; Upgrades
---

### Post by superkato on 2012-03-29
Hi,

I'm using Ubuntu 9.x alongside Win7 on my old PC.

Now I bought up a new Thinkpad and installed Win7 Enterprise (I need it for some Applications).

My Problem is that I can't get Ubuntu 11.10 x86 installed on the system. 

The HDD has a size of 320GB. First of all I installed Win7

100MB EFI for Win7
290GB for Win7 (NTFS)
and the rest for Ubuntu.
Screenshot (german windows): [http://media.cdn.ubuntu-de.org/forum/attachments/52/13/4166637-win.PNG](http://media.cdn.ubuntu-de.org/forum/attachments/52/13/4166637-win.PNG)

When the partitioning tool starts (because it does not show me the "install alongside windows" option, it only shows me one drive with one big partition - no ntfs no windows:
[U][I]
SDA and 320000 unlocated free size
[/I][/U]

So I started the live CD and typed fdisk -l:

```
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1c204861

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   580081663   289937408    7  HPFS/NTFS/exFAT
ubuntu@ubuntu:~$ 
```


```
ubuntu@ubuntu:~$ sudo parted -l

Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? 

if yes 


Yes/No? yes                                                               
Model: ATA ST9320325ASG (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!    


If no

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!  
```


Seems that Windows created a GPT signature..
Could my Thinkpad BIOS Harddisk protection cause this ? 

If I try to install it with WUBI (what I dont really want) it says - no root partition - 

seems that Ubuntu 11.10 can't handle my existing Filesystem :(

Is their anysolution?

Kind Regards
Sam from Germany

---

### Post by Paddy Landau on 2012-03-30
I see one problem immediately.

The first is that you have reserved just 695Mb for Ubuntu. You really need 20Gb at an absolute minimum (including space for swap). I would recommend at least 30Gb.

Try fixing that first. Use Windows's computer disk management to shrink the Windows partition, leaving enough space to expand the Ubuntu partition. You want the following:

[LIST=1]
[*]System-reserviert (do not change this): 100Mb
[*]Ubuntu 11.10: 20Gb (or more if you want)
[*]Linux swap: 4Gb (adjust this to equal the size of your RAM)
[*]Win7 [noparse](C:)[/noparse]: The remainder of the disk
[/LIST]

---

### Post by darkod on 2012-03-30
If you use EFI boot, windows has no other option except to work on gpt table. It can't work on efi/msdos combination.

Also, in your parted command, did you notice towards the end the message "can't have a partition outside the disk"? Somehow, the program that was creating the partitions created it ending outside the disk.

Try parted again whether it will show you the partitions list this time, so you can figure out if there really is a partition outside the disk.

Alternatively, see what windows disk management says.

And be advised, ubuntu grub2 also has a bug when dual booting with EFI, sometimes it can delete the windows boot files on the EFI system partition. Investigate for solutions before you continue.

If you don't mind, and your laptop has the option, it's probably best to boot with BIOS boot, not EFI boot. Then you can have the older type msdos table if you want. And makes things little simpler.

---

### Post by darkod on 2012-03-30
PS. You got me confused a bit in your first post when you mentioned a 100MB EFI partition. Now thinking about it, you might have created your hdd with msdos table, the 100MB system reserved partition is created during installation of win7, it's not an EFI partition.

And because when you try to change gpt disk into msdos disk with windows, it changes only the primary table, but gpt has a backup table. This is what parted detected, and you should have said NO when it asked you if it is gpt disk. All of this under the assumption you created new msdos table earlier.

So, do you have msdos or gpt disk?

The best way to get rid of the gpt backup table, if you want to use the disk as msdos, is fixparts. it detects correctly the msdos disk with backup gpt table and asks you if you want to remove it.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by superkato on 2012-03-30
> I see one problem immediately.

The first is that you have reserved just 695Mb for Ubuntu. You really need 20Gb at an absolute minimum (including space for swap). I would recommend at least 30Gb.

No thats the Ubuntu CD ... The Space for Ubuntu are the 20GB in the black square at the right corner.

> PS. You got me confused a bit in your first post when you mentioned a 100MB EFI partition. Now thinking about it, you might have created your hdd with msdos table, the 100MB system reserved partition is created during installation of win7, it's not an EFI partition.


yes you're right, thats the 100Mb that windows7 setup creates at the beginning.


- ok I will try fixparts but what happens when I'm saving an Image of my windows7 and re-create alle partitions with gparted:
win7 100mb, win7 main, ubuntu, ubuntu swap etc.
could that work ? because I would creating everything with gparted?

After that I would copy my win7 image back to the disk and installing ubuntu? what do you think?


kind regards

---

### Post by darkod on 2012-03-31
I don't understand, why win7 imaging back?

You can make an image of your win7 to be safe, but fixparts can fix the backup gtp issue without data loss. In that case the disk will be recognized properly as msdos disk with two primary partitions, system reserved and win7 C: .

When you start the ubuntu installation, if you are using the manual method, just create all partitions that you want as logical and you can create as many as you want, for example /, /home and swap. If they are logical they will all form a single extended partition and in that case you will have total of three partitions which is still under the 4 limit. If that is what you are worried about.

---

### Post by superkato on 2012-03-31
> Re: natty narwhal doesnt detect my windows7
If you run FixParts in Windows, the device filename is "0:". You would open an Administrator command prompt window and type:

Code:

fixparts 0:

You must run the program as Administrator.

Once the program is running, do this:

Code:

FixParts 0.7.1

Loading MBR data from /dev/sdc

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 15654912 sectors (7.5 GiB)
MBR disk identifier: 0x000721DC
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1                    62      6125599   primary     Y        Y      0x83
   5               6125662     15650907   logical     Y        Y      0x83

MBR command (? for help): w

Final checks complete. About to write MBR data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!

Do you want to proceed? (Y/N): y
Done writing data!

I've put what you type in bold. The "p" command displays the partition table. In this example, I've got two partitions, one primary and one logical. (FixParts does not display extended partitions.) Your display will obviously be different, but you should use "p" to verify that all your partitions are present and marked as either "primary" or "logical" (not "omitted") in the "Status" column. If everything looks OK, type "w" to save your changes. If you see anything suspicious, type "q" to quit without saving and post the output here for advice.


works fine ! problem solved!!!

---

### Post by Paddy Landau on 2012-03-31
> **superkato said:**
> works fine ! problem solved!!!
Excellent. Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by RJARRRPCGP on 2012-04-01
> **Paddy Landau said:**
> I see one problem immediately.

 You really need 20Gb at an absolute minimum (including space for swap). I would recommend at least 30Gb.



Ubuntu don't even require 8 GB much less 20 GB! (Hint: It's not Windows 7!) 

And I assume swap the same size as the RAM when using hibernation.

---

### Post by Paddy Landau on 2012-04-02
> **RJARRRPCGP said:**
> Ubuntu don't even require 8 GB much less 20 GB!
I know. I was assuming that the OP might want to store data on his partition.

> **RJARRRPCGP said:**
> I assume swap the same size as the RAM when using hibernation.
Yes, that is correct. If you have very low RAM (in which case you should be using Lubuntu or another light distro), many say that you should have at least 1Gb swap.

Actually, it is possible to need more than the RAM for hibernation. If you have used all your RAM and some of your swap, you'll need all the swap and more for hibernation. But that would be be likely on a modern computer only if you are doing massive data manipulation.

---

