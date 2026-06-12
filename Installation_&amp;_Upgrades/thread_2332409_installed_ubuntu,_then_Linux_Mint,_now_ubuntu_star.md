---
title: "installed ubuntu, then Linux Mint, now ubuntu starts in Emergency Mode."
date: 2016-07-31
forum: Installation &amp; Upgrades
---

### Post by gregconquest2 on 2016-07-31
I partitioned my drive and installed Ubuntu Studio 16.04.1 into two partitions (root and home), and it restarted fine. 

Then I installed Linux Mint 18 into the final two partitions (I had not mounted them under ubuntu during the install). Linux Mint booted fine.

Now, though, Ubuntu Studio goes into Emergency Mode when I try to boot it. I did not alter the ubuntu partitions during the Mint install, though I did overwrite grub.

Can anyone please help me fix this?

Thank you,
Greg Conquest

---

### Post by Bashing-om on 2016-07-31
gregconquest2; Hello;

There can be but one controlling boot authority . Which do you want as your primary operating system ?

Show us presently what the set up is:
```

sudo parted -l

```
which among all the other info, will indicate what method you have for booting.
Then we proceed to insure grub is happy.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gregconquest2 on 2016-07-31
I get:
> Model: ATA Hitachi HTS54321 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  525MB   524MB   primary   ntfs            boot
 2      525MB   53.7GB  53.2GB  primary   ntfs
 3      53.7GB  143GB   89.1GB  extended
 5      53.7GB  79.5GB  25.8GB  logical   ext4
 6      79.5GB  107GB   27.9GB  logical   ext4
 7      107GB   120GB   12.3GB  logical   ext4
 8      120GB   133GB   13.4GB  logical   ext4
 9      133GB   143GB   9658MB  logical   linux-swap(v1)
 4      143GB   160GB   17.2GB  primary   ntfs


I set up the partitions using a linux boot disc, 
then I installed Windows, 
then I installed Ubuntu Studio, grub in sda,
then I tested it all.
Then I booted with the Linux Mint DVD and installed that with grub also going into sda.

FWIW, after the last failed boot into Ubuntu Studio, rebooting into Mint also gave me Emergency Mode, for the first time. I booted Windows. That was fine, and then restarted into Linux Mint. It booted fine.

PS Grub boots into Mint by default since it was the last OS I installed.

---

### Post by Bashing-om on 2016-07-31
gregconquest2; Well ..

so far so good .. we know now that the [s]partitioning is GPT[/s].
edit: Ouch .. I did miss:
> 
3 53.7GB 143GB 89.1GB extended

Tunnel vision .. as this is a MBR partitioned drive.

[s]Now I want to know if this is a UEFI system[/s]. Where the firmware controls what boots.
What returns:
```

[ -d /sys/firmware/efi ] && echo "Installed in EFI mode" || echo "Installed in Legacy mode"

```

Be aware if this is UEFI it is out of my experience range . Others here will have to take up my slack to set and arrange the booting .

[INDENT][INDENT]some things
[INDENT][INDENT]I do not know
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gregconquest2 on 2016-07-31
The results are:
> Installed in Legacy mode

---

### Post by Bashing-om on 2016-07-31
gregconquest2; K ...

So back to the primary question .. with 3 operating systems installed on this hard drive, which do you want as that primary booting system ? And It can not be Windows, as Windows does not speak grub ( GRand Unified Bootloader); but grub will load Windows .

[INDENT][INDENT]proceeding in a forward direction
[/INDENT][/INDENT]

---

### Post by gregconquest2 on 2016-07-31
I want Linux Mint to be the OS in control. I think it installed grub into the mbr (hence sda). I guess I could edit grub at any time to make ubuntu the default, but grub seems to be the master regardless. I'm not sure if I could set Windows to be the default, but I'm not likely to do that anyway.

But, big news: all OSes are booting now!

The original problem, emergency mode on ubuntu, spanned several boot attempts. I'm wondering if a failed boot kicked it into emergency mode instead of safe mode or whatever its called, the one that usually fixes such problems and reboots clean. Emergency mode seems very different.

This might be due to Windows 10 still having Fast Startup enabled. I tell everyone to disable that as a shutdown should be a real shutdown, not a hibernation which is what is does. That caused file fragments on my other dual booting machine till I serendipitously figured out what was going on.

I documented the problem here:
Serendipity! I've found a problem for anyone dual-booting Windows 10 and Linux.
[https://plus.google.com/+GregConquest/posts/RrxWJPEbRvV](https://plus.google.com/+GregConquest/posts/RrxWJPEbRvV)

---

### Post by Bashing-om on 2016-07-31
gregconquest2; K


All ^ great info .. and all now to the good .. Glad you provided what was taking place !

So Mint to be the primary .. what we have to do is make sure that 'buntu can not get control of the boot .
To that end boot up ubuntu and execute:
```

sudo chmod -x /etc/grub.d/30_os-prober

```
And to update the boot code to reflect this change in 'buntu; execute:
```

sudo update-grub

```
such that 'buntu is no longer aware of any other installs and will only deal with it's self .
It is always a good idea not only to comment in the file the reason for the change .. but also keep a log of all changes one makes to the operating system . Such a log will serve you in good stead in the future.

Now make Mint that controlling authority:
boot up into Mint and execute :
```

sudo update-grub

```
Where Mint picks up 'buntu and Windows .. and chainloads them onto it's boot menu .

[INDENT][INDENT]been there
[INDENT][INDENT][INDENT]done that
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gregconquest2 on 2016-07-31
Bashing-om, thanks for your help. I've confirmed that I had not disabled Fast Startup after my most recent Windows reinstall. I'm guessing this was the what happened:
1) I'm using Windows, and I shut down (really hibernated due to Fast Startup being enabled [I](by default!))
[/I]2) I boot ubuntu and the drive is altered in some way. I shut down/restart.
3) I boot back into Windows, which is actually just taking the system out of hibernation, Windows sees some alterations on the disk, perhaps on the shared ntfsDATA partition, and it "fixes" them.
4) I boot ubuntu, and it freaks out because Windows screwed up a disk checksum, removed "file fragments", or some such.
5) Some combination of clean shutdowns clears up the problem. Seeing Linux Mint also go into emergency mode was what made me expand my thinking about what might have been happening.

This is my best guess as to what was happening. I hope I've fixed the problem now. 

The moral of the story is when anyone is having a problem with a Windows 10 computer, the go-to fix is to tell them to restart, not shut down. Then get them to fix the Fast Startup setting to prevent the problem happening again.

Thanks again, Bashing-om :-)

---

### Post by gregconquest2 on 2016-07-31
Bashing-om, what you're suggesting with chmod would prevent a future update of ubuntu from writing to grub, right? I've had this problem before and have dealt with it by applying big updates to my primary system last, but what you say seems to make sense. I'll try this after I get everything running well and an image of the whole hard drive made.

---

### Post by Bashing-om on 2016-07-31
gregconquest2; Yeah ...

I too multi-boot:
```

sysop@1404mini:~$ sudo fdisk -lu
[sudo] password for sysop: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ea65
 Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   102402438    51200195+  83  Linux
/dev/sdb2   *   102404096   204804095    51200000   83  Linux
/dev/sdb3       204806144   266246143    30720000   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   976768064   488384001   83  Linux
sysop@1404mini:~$ 

sysop@1404mini:~$ 

sysop@1404mini:~$ sudo blkid
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="ubie14.04std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdb2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sdb3: LABEL="ubie16.04" UUID="2ec4733f-db40-4db0-aef8-5c54e54085ab" TYPE="ext4" 
/dev/sdc1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
sysop@1404mini:~$

```
And I have had to do some extreme measures such that my sda1 install always has control.
Also, a great thing to do is to label the partitions .. It really helps to keep the confusion factor down.

[INDENT][INDENT]all in system administration
[INDENT][INDENT][INDENT]worth the effort
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

