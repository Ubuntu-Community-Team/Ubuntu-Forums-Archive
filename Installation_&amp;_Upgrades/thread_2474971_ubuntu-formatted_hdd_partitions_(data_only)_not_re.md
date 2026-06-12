---
title: "ubuntu-formatted hdd partitions (data only) not recognized by W2Ksp4"
date: 2022-05-12
forum: Installation &amp; Upgrades
---

### Post by legg2 on 2022-05-12
A new Ubuntu 64bit machine was used to create partitions on a new HDD and a data library 
was copied to it in the Ubuntu environment.

This HDD is intended to be physically redeployed to other machines for data access.

I can't get W2Ksp4 machine to recognize the new partitions, whether split up into 
smaller NTFS, or lumped onto single FAT32. It sees only a healthy unpartitioned HDD.

It has had no recent trouble working with NTFS partitions >250G , FAT32 partions >500G 
in other HDD storage media - the data originated in the W2K system, but a lower POH HDD 
is now needed.

What's missing from the new HDD format?

RL

---

### Post by TheFu on 2022-05-12
> **legg2 said:**
>  What's missing from the new HDD format?

Some facts please?
Run these commands and paste the EXACT command with the EXACT  output back here, then use the forum code-tags so the columns line up correctly.  Without the columns lined up, it is too easy to make mistakes.  code-tags use the '#' button in the advanced editor.
```

lsblk -e 7 -o name,size,type,fstype,mountpoint
df -hT -x squashfs -x tmpfs -x devtmpfs
sudo parted -lm
```
Please and thank you.
I used 'code-tags' for the commands above. If your post doesn't have that code box, please fix it.

---

### Post by legg2 on 2022-05-13
```
owner@500Gubuntu:~$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                      SIZE TYPE  FSTYPE      MOUNTPOINT
sda                     465.8G disk              
&#9500;&#9472;sda1                    731M part  ext4        /boot
&#9500;&#9472;sda2                      1K part              
&#9492;&#9472;sda5                    465G part  crypto_LUKS 
  &#9492;&#9472;sda5_crypt            465G crypt LVM2_member 
    &#9500;&#9472;ubuntu--vg-root   464.1G lvm   ext4        /
    &#9492;&#9472;ubuntu--vg-swap_1   976M lvm   swap        [SWAP]
sdb                     931.5G disk              
&#9492;&#9472;sdb2                  850.8G part  vfat        
sdc                       960M disk              
&#9492;&#9472;sdc1                    959M part  vfat        /media/owner/USB 1G A
sr0                      1024M rom               
owner@500Gubuntu:~$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root ext4  456G   13G  420G   3% /
/dev/sda1                   ext4  704M  214M  440M  33% /boot
/dev/sdc1                   vfat  955M  200M  756M  21% /media/owner/USB 1G A
owner@500Gubuntu:~$ sudo parted -lm
```
......

code tags and code box are greek to me.
The font selected here was courier in order to get text columns in-line 
per a 'terminal' display, however, unfortunately, this is not conveyed 
in the displayed posting's html. ('Courier new' isn't fixed spacing?)
[IMG]http://ve3ute.ca/query/220513c_parted.png[/IMG]

The disk in question is listed as sdb. There is 18G 'free space' before the sdb2 partition.
[IMG]http://ve3ute.ca/query/220513c_disks.png[/IMG]

There is no issue with accessibility of data in this partition of this drive in Ubuntu 18.04.
The disk is seen as basic, 931.51G, 'healthy', with 931.51G unformatted,  no volume name, in W2K.

[IMG]http://ve3ute.ca/query/220512_LIB_unseen_on_W2K.jpg[/IMG]

(OT - Is a fact only a fact if it's terminal output or an image?)

RL

---

### Post by TheFu on 2022-05-13
_Code tags_ please.  [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) The columns aren't lining up.

Pasting images isn't necessary 99% of the time. Some people here by for internet by the byte. Please make them into attachments (not inline) to help us out. Also, people using screen readers can't use images.

Also, the **parted -lm** output is missing which could be the most important.

---

### Post by TheFu on 2022-05-13
```
owner@500Gubuntu:~$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                      SIZE TYPE  FSTYPE      MOUNTPOINT
sda                     465.8G disk              
&#9500;&#9472;sda1                    731M part  ext4        /boot
&#9500;&#9472;sda2                      1K part              
&#9492;&#9472;sda5                    465G part  crypto_LUKS 
  &#9492;&#9472;sda5_crypt            465G crypt LVM2_member 
    &#9500;&#9472;ubuntu--vg-root   464.1G lvm   ext4        /
    &#9492;&#9472;ubuntu--vg-swap_1   976M lvm   swap        [SWAP]
sdb                     931.5G disk              
&#9492;&#9472;sdb2                  850.8G part  vfat        
sdc                       960M disk              
&#9492;&#9472;sdc1                    959M part  vfat        /media/owner/USB 1G A
sr0                      1024M rom               
owner@500Gubuntu:~$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root ext4  456G   13G  420G   3% /
/dev/sda1                   ext4  704M  214M  440M  33% /boot
/dev/sdc1                   vfat  955M  200M  756M  21% /media/owner/USB 1G A
owner@500Gubuntu:~$ sudo parted -lm
.....
```
I got this thanks to email notification ...

---

### Post by TheFu on 2022-05-13
So, your Ubuntu system is using LVM on sda inside a LUKS encrypted partition. LVM is an enterprise volume manager. To my knowledge, Windows will not get direct access to those file systems - ever.  You can setup a CIFS share using samba, but that won't be helpful on a dual boot system, though every other computer on the same LAN could have access. I use LUKS and LVM on my laptops. Good solution.

As for sdb2 and sdc1, without the parted output, I don't know which file system is really used.
FAT32 is about the worst choice and should be avoided for anything that isn't mandated by the other device - perhaps a 10+ yr old camera? Newer devices support exFAT, which is a better file system, but doesn't have journalling. That's not good. We want journaled file systems when we can get them for data safety reasons. ext3/4, xfs, ntfs are all journaled file systems.

For any SSD or HDD that you want to share storage between 2 different computers by physical connection (not networked), then NTFS would be best if 1 of those was running Windows. If it is a Linux system, then use ext4.

If the SSD or HDD will be physically connected to a device that doesn't support NTFS (that would be odd), then it will probably support exFAT.  exFAT is the replacement for FAT32 and much better than FAT32. Linux has excellent support for exFAT. Just need to install the **exfat-utils** package, if it isn't already installed. Most phones support exFAT, as does Windows8+ and Linux.

BTW, the Ubuntu package for NTFS support is **ntfs-3g**. Install that if it isn't already installed.

Lastly, and this is just a recommendation, set a useful LABEL on sdb2 and sdc1 file systems.  That LABEL shouldn't have any white-space. I'd use **sudo -H gparted** to create a new GPT partition table, then create as many partitions as you'd like, format each to NTFS (better) or exFAT, and add a 1-word, useful, LABEL to each file system.  

Labels are used at mount time to create the directory name for the mount location. If we want to control exactly where the mount gets placed, we can use the unique LABEL to recognize a file system and mount it to a specific location like it was a UUID or device name.  Spaces cause hassles for us. Best to avoid them anywhere it would/could turn into a directory name or file name.

BTW, I haven't seen a 1G device in yrs.  I would assume that 1G is a flash drive and about the die.
sdb2 doesn't have a label or wasn't mounted when you ran the commands.

---

### Post by ajgreeny on 2022-05-13
@ legg2 

I have added code tags to your post for the lsblk terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. 

See my signature below for a **How-to**

---

### Post by legg2 on 2022-05-13
> **TheFu said:**
> 

Also, the **parted -lm** output is missing which could be the most important.


That's all she wrote.

Ran it a few times with different HDDs in that physical position, and vacant, previously.
All terminated on that line.

RL

---

### Post by TheFu on 2022-05-13
If **parted** doesn't return anything, that's a huge issue. It means the drives aren't connected. NONE of them and I'd look at the controllers in the system for problems. I'm surprised any other tools are able to see the drives at all.

Try 
```
sudo fdisk -l /dev/sd[a-z]
```
parted is newer than fdisk and had native support for more partition table types.

And code-tags are definitely needed with the output.

---

### Post by The Cog on 2022-05-13
It needs to be ```
sudo parted -lm
```without sudo it prints nothing.

---

### Post by legg2 on 2022-05-13
> **TheFu said:**
> So, your Ubuntu system is using LVM on sda inside a LUKS encrypted partition. LVM is an enterprise volume manager. To my knowledge, Windows will not get direct access to those file systems - ever.  You can setup a CIFS share using samba, but that won't be helpful on a dual boot system, though every other computer on the same LAN could have access. I use LUKS and LVM on my laptops. Good solution.

As for sdb2 and sdc1, without the parted output, I don't know which file system is really used.

sdb2 and sdc1 are both fat32. 
sdb2 formatted in Ubuntu using 'disks'. 
sdc1 formatted and reformatted, whenever Windoze complains.

> **TheFu said:**
> FAT32 is about the worst choice and should be avoided for anything that isn't mandated by the other device - perhaps a 10+ yr old camera? Newer devices support exFAT, which is a better file system, but doesn't have journalling. That's not good. We want journaled file systems when we can get them for data safety reasons. ext3/4, xfs, ntfs are all journaled file systems.

For any SSD or HDD that you want to share storage between 2 different computers by physical connection (not networked), then NTFS would be best if 1 of those was running Windows. If it is a Linux system, then use ext4.

This is not the first attempt to get this specific HDD hardware to carry LIB files in a manner readable by the 
remote W2K machine. A previous disk with separate, smaller NTFS partions was similarly ignored.

Both were expected to work - being aware of partition count limitations of W2K machine.

> **TheFu said:**
> If the SSD or HDD will be physically connected to a device that doesn't support NTFS (that would be odd), then it will probably support exFAT.  exFAT is the replacement for FAT32 and much better than FAT32. Linux has excellent support for exFAT. Just need to install the **exfat-utils** package, if it isn't already installed. Most phones support exFAT, as does Windows8+ and Linux.

BTW, the Ubuntu package for NTFS support is **ntfs-3g**. Install that if it isn't already installed.

I used the Ubuntu 18.04 default 'Disks' utility - its option is to select the 'appropriate' file system, by 
application/OS category.

> **TheFu said:**
> Lastly, and this is just a recommendation, set a useful LABEL on sdb2 and sdc1 file systems.  That LABEL shouldn't have any white-space. I'd use **sudo -H gparted** to create a new GPT partition table, then create as many partitions as you'd like, format each to NTFS (better) or exFAT, and add a 1-word, useful, LABEL to each file system.  

Labels are used at mount time to create the directory name for the mount location. If we want to control exactly where the mount gets placed, we can use the unique LABEL to recognize a file system and mount it to a specific location like it was a UUID or device name.  Spaces cause hassles for us. Best to avoid them anywhere it would/could turn into a directory name or file name.

The partitions are named - visible in the 'Disks' window, in the Ubuntu navigation panes and in 
working W2k media.

> **TheFu said:**
> BTW, I haven't seen a 1G device in yrs.  I would assume that 1G is a flash drive and about the die.
sdb2 doesn't have a label or wasn't mounted when you ran the commands.

Oh yeah? . . . and your mother wears army boots, so there.

These 1G USB sticks are increasingly hard to come by, but are invaluable in any 
lab running older western or any eastern lab equipment, which tend to have 
specific and inviolable limits on USB drive size. I treasure them like gold.

sdb2 doesn't have to be actually mounted to serve its purpose here.
As stated, Ubuntu has no issues accessing the data on sdb2 partitions.

W2k can't see them.

RL

---

### Post by legg2 on 2022-05-13
> **ajgreeny said:**
> @ legg2 

I have added code tags to your post for the lsblk terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. 

See my signature below for a **How-to**

Thanks for the link.

RL

---

### Post by legg2 on 2022-05-13
> **TheFu said:**
> If **parted** doesn't return anything, that's a huge issue. It means the drives aren't connected. NONE of them and I'd look at the controllers in the system for problems. I'm surprised any other tools are able to see the drives at all.

Try 
```
sudo fdisk -l /dev/sd[a-z]
```
parted is newer than fdisk and had native support for more partition table types.

And code-tags are definitely needed with the output.


It seems that the terminal was waiting for operator input, so that 
it could process a user password, before proceeding. 
~ Required for both query methods.

```
owner@500Gubuntu:~$ sudo fdisk -l /dev/sd[a-z]
[sudo] password for owner: 
Disk /dev/sda: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk model: TOSHIBA MQ02ABF0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xf284e298

Device     Boot   Start       End   Sectors  Size Id Type
/dev/sda1  *       2048   1499135   1497088  731M 83 Linux
/dev/sda2       1501182 976771071 975269890  465G  5 Extended
/dev/sda5       1501184 976771071 975269888  465G 83 Linux

Partition 2 does not start on physical sector boundary.


Disk /dev/sdb: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000NM0011    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: DCB78AFA-F8A5-4DFE-A9BF-5C4913C1585E

Device        Start        End    Sectors   Size Type
/dev/sdb2  35715072 1819908095 1784193024 850.8G Microsoft basic data


owner@500Gubuntu:~$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                      SIZE TYPE  FSTYPE      MOUNTPOINT
sda                     465.8G disk              
&#9500;&#9472;sda1                    731M part  ext4        /boot
&#9500;&#9472;sda2                      1K part              
&#9492;&#9472;sda5                    465G part  crypto_LUKS 
  &#9492;&#9472;sda5_crypt            465G crypt LVM2_member 
    &#9500;&#9472;ubuntu--vg-root   464.1G lvm   ext4        /
    &#9492;&#9472;ubuntu--vg-swap_1   976M lvm   swap        [SWAP]
sdb                     931.5G disk              
&#9492;&#9472;sdb2                  850.8G part  vfat        
sr0                      1024M rom               
owner@500Gubuntu:~$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root ext4  456G   13G  420G   3% /
/dev/sda1                   ext4  704M  214M  440M  33% /boot
owner@500Gubuntu:~$ sudo parted -lm
[sudo] password for owner: 
BYT;
/dev/sda:500GB:scsi:512:4096:msdos:ATA TOSHIBA MQ02ABF0:;
1:1049kB:768MB:767MB:ext4::boot;
2:769MB:500GB:499GB:::;
5:769MB:500GB:499GB:::;

BYT;
/dev/sdb:1000GB:scsi:512:512:gpt:ATA ST1000NM0011:;
2:18.3GB:932GB:914GB:fat32::msftdata;

BYT;
/dev/mapper/ubuntu--vg-root:498GB:dm:512:4096:loop:Linux device-mapper (linear):;
1:0.00B:498GB:498GB:ext4::;

BYT;
/dev/mapper/ubuntu--vg-swap_1:1023MB:dm:512:4096:loop:Linux device-mapper (linear):;
1:0.00B:1023MB:1023MB:linux-swap(v1)::;

Error: /dev/mapper/sda5_crypt: unrecognised disk label
BYT;                                                                      
/dev/mapper/sda5_crypt:499GB:dm:512:4096:unknown:Linux device-mapper (crypt):;

owner@500Gubuntu:~$ 
```

The 1G USB stick was needed elsewhere, this time around.

RL

---

### Post by TheFu on 2022-05-13
Whoa .... this is a _***[COLOR="#B22222"]Windows 2000[/COLOR]***_ machine that you are trying to get to work?  I know you said it, clearly, but my brain inserted Win 2012 for some reason.

MSFT has changed the standard on NTFS and FAT32 over the decades since 2001.  Being forwards compatible may not be supported.
Win2000 won't support GPT. Ever. You have to stick with 'DOS' partition tables.
FAT32 used to be limited to 32G. Could that be part of the issue?

And, yes, my mother DOES where army boots! ;)
Images still don't work with screen readers. Disks and other images won't help me. I don't trust them.

I can only guess that the best solution would be to format all storage on the Win2000 machines and hope that read/writes on other machines (of any other OS) don't use an incompatible version of the file system. If that doesn't work, I haven't any clue.

I might find an old MB+CPU+RAM for an Athon 2000+ and perhaps an Athon 1800, if you need spares (for a price). I don't recall if either have USB or not. May have a Pentium 90 around - but it definitely doesn't have USB.  All worked when they were put into storage.

---

### Post by legg2 on 2022-05-13
> **TheFu said:**
> Whoa .... this is a _***[COLOR=#B22222]Windows 2000[/COLOR]***_ machine that you are trying to get to work?  I know you said it, clearly, but my brain inserted Win 2012 for some reason.

MSFT has changed the standard on NTFS and FAT32 over the decades since 2001.  Being forwards compatible may not be supported.
Win2000 won't support GPT. Ever. You have to stick with 'DOS' partition tables.
FAT32 used to be limited to 32G. Could that be part of the issue?

I can only guess that the best solution would be to format all storage on the Win2000 machines and hope that read/writes on other machines (of any other OS) don't use an incompatible version of the file system. If that doesn't work, I haven't any clue.

I stuck the offending HDD into the optical disk slot of a 'toy' W7pro machine and used 
the drive mfr's (Seagate DiscWizard) to reformat it. (yeah - another half day re-transferring files).
This was recognized by both W2K and Ubuntu.

[http://ve3ute.ca/query/220513_LIB_f-W7_ubuntu_Disks.png](http://ve3ute.ca/query/220513_LIB_f-W7_ubuntu_Disks.png)

 ```
owner@500Gubuntu:~$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME                      SIZE TYPE  FSTYPE      MOUNTPOINT
sda                     465.8G disk              
&#9500;&#9472;sda1                    731M part  ext4        /boot
&#9500;&#9472;sda2                      1K part              
&#9492;&#9472;sda5                    465G part  crypto_LUKS 
  &#9492;&#9472;sda5_crypt            465G crypt LVM2_member 
    &#9500;&#9472;ubuntu--vg-root   464.1G lvm   ext4        /
    &#9492;&#9472;ubuntu--vg-swap_1   976M lvm   swap        [SWAP]
sdb                     931.5G disk              
&#9500;&#9472;sdb1                     40G part  ntfs        
&#9500;&#9472;sdb2                      1K part              
&#9492;&#9472;sdb5                  830.6G part  vfat        
sr0                      1024M rom               
owner@500Gubuntu:~$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root ext4  456G   13G  420G   3% /
/dev/sda1                   ext4  704M  214M  440M  33% /boot
owner@500Gubuntu:~$ sudo parted -lm
[sudo] password for owner: 
BYT;
/dev/sda:500GB:scsi:512:4096:msdos:ATA TOSHIBA MQ02ABF0:;
1:1049kB:768MB:767MB:ext4::boot;
2:769MB:500GB:499GB:::;
5:769MB:500GB:499GB:::;

BYT;
/dev/sdb:1000GB:scsi:512:512:msdos:ATA ST1000NM0011:;
1:1049kB:43.0GB:43.0GB:ntfs::boot;
2:43.0GB:1000GB:957GB:::lba;
5:43.0GB:935GB:892GB:fat32::;

BYT;
/dev/mapper/ubuntu--vg-swap_1:1023MB:dm:512:4096:loop:Linux device-mapper (linear):;
1:0.00B:1023MB:1023MB:linux-swap(v1)::;

BYT;
/dev/mapper/ubuntu--vg-root:498GB:dm:512:4096:loop:Linux device-mapper (linear):;
1:0.00B:498GB:498GB:ext4::;

Error: /dev/mapper/sda5_crypt: unrecognised disk label
BYT;                                                                      
/dev/mapper/sda5_crypt:499GB:dm:512:4096:unknown:Linux device-mapper (crypt):;
```

```
 owner@500Gubuntu:~$ sudo fdisk -l /dev/sd[a-z]
[sudo] password for owner: 
Disk /dev/sda: 465.78 GiB, 500107862016 bytes, 976773168 sectors
Disk model: TOSHIBA MQ02ABF0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xf284e298

Device     Boot   Start       End   Sectors  Size Id Type
/dev/sda1  *       2048   1499135   1497088  731M 83 Linux
/dev/sda2       1501182 976771071 975269890  465G  5 Extended
/dev/sda5       1501184 976771071 975269888  465G 83 Linux

Partition 2 does not start on physical sector boundary.


Disk /dev/sdb: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000NM0011    
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x622bc19c

Device     Boot    Start        End    Sectors   Size Id Type
/dev/sdb1  *        2048   83941375   83939328    40G  7 HPFS/NTFS/exFAT
/dev/sdb2       83941376 1953525167 1869583792 891.5G  f W95 Ext'd (LBA)
/dev/sdb5       83943424 1825851391 1741907968 830.6G  b W95 FAT32


``` 

After files are reloaded, I'll take it for a spin in the W2Ksp4 environment.
Partition sizes don't seem to be an issue with the last revs and reg tweaks 
available for W2K, though it still cannot create them using resident tools.

> **TheFu said:**
> I might find an old MB+CPU+RAM for an Athon 2000+ and perhaps an Athon 1800, if you need spares (for a price). I don't recall if either have USB or not. May have a Pentium 90 around - but it definitely doesn't have USB.  All worked when they were put into storage.

W2K supported chipsets could be extended to include MCP61, which 
includes a number of venerable motherboards (Athlon/Sempron). 
At present, the motherboard is from an Acer Aspire T180(~ECS MCP61PM-HM)
a change required when the original PC Chips (A13G+) became unobtanium.
. . . and yes, it does support USB2(enhanced)

The last PCC MB was exhibiting erratic power-off faults that eventually killed 
the HDD (<6000POH), it's back-up and an optical drive, simultaneously with an 
attempt to set up a dual boot W2K / LXLE. Can't blame LXLE, but be I'll postponing 
similar attempts until there's a lot of free time, or no other choice. Never did 
get LXLE to print, though all the hardware was recognized . . . . LXLE also 
doesn't think USB drives need safe dismounting . . . 

Going to mark this one as solved, if only because the chicken hard drive is 
being counted in both OSs. Anything else will be W2K's problem.

RL

---

