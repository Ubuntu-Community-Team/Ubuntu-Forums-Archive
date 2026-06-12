---
title: "Major Partition Problem"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by TrevT93 on 2009-12-26
First off, my partition structure was something like this before:

/dev/sda1 was my built-in Vista RECOVERY partition.  NTFS, about 10GB of space.
/dev/sda2 was my Windows Vista partition.  NTFS, about 74 GB.
/dev/sda3 was my Windows 7 Beta partition.  NTFS, about 40 GB.
/dev/sda4 was an extended partition.
/dev/sda5 was my copy of Xubuntu.  EXT4, about 10 GB.
/dev/sda6 was an old copy of Debian I was going to remove soon.  EXT3, about 13 GB.
/dev/sda7 was a SWAP space of capacity 1 GB.
/dev/sda8 was a SWAP space of capacity 1 GB.

Yesterday, I upgraded my Windows Vista copy to Windows 7.  In classic Windows fashion, the upgrade itself would not work, so a reinstall was necessary to get it to work.

The Windows bootloader overwrote GRUB2, just as I had expected.  I went to restore the bootloader but I found that Windows messed with the partitions.  They now read:

/dev/sda1 (Recovery)
/dev/sda2 (Vista, now Windows 7)
/dev/sda3 (Windows 7 beta)
/dev/sda4 (Extended space with a lot of gigabytes but no distinct partitions)
/dev/sda5 (Linux SWAP, it looks like it lumped the two swaps together)

I used TestDisk to restore the partitions to their correct structure (removed Debian from the picture, it seemed to make TestDisk not want to write the partition).  Wrote it back to the drive then rebooted into Kubuntu Karmic.  Used a set of instructions to restore the GRUB2 bootloader and rebooted.  All seemed well.

That is, until I revisited Xubuntu.  I opened up GParted to remove the old Windows 7 Beta.  But GParted showed me something troubling: the partition structure seemed to have ceased to exist.  It showed my hard disk as unallocated space through and through.

I installed TestDisk on Xubuntu, re-wrote the partition structure and rebooted.  I never saw Xubuntu again.

No amount of reinstalling the bootloader or using the Windows one got ANY of my partitions back.  I tried to mount the Xubuntu partition in live Kubuntu and got a journaling superblock error.

Now I'm in a bad situation.  I reinstalled Windows 7, and although Windows can see all the partitions, GParted still can't.  Which means my Xubuntu partition is lost.  If I try to use TestDisk again, I'm afraid it'll get me back in the same situation.  And worse, I can't correctly partition the disk to get a new copy of Xubuntu running!

---

### Post by oldfred on 2009-12-26
If grub cannot see your partitions I do not know if the script will work or not. You can download from the liveCD and run.

Boot Info Script 0.42 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 
Instructions:  louieb's 
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 
or as example if on desktop or  downloads directory from liveCD download: 
sudo bash ~/Desktop/boot_info_script*.sh
or depending on where it downloaded
sudo bash ~/Downloads/boot_info_script*.sh 
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here, it can be big. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text, to make it easier to view.

---

### Post by TrevT93 on 2009-12-27
Thanks for the quick reply.

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:     BootPart in the file 
                       /NST/nst_grub-40056727F539F2DCC9D702336A749ABE.mbr is 
                       trying to chain load sector #261393741 on boot drive #1
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda3 has 
                       94350935 sectors, but according to the info from 
                       fdisk, it has 94365810 sectors.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5cb4fa98

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    21,478,904    21,478,842   7 HPFS/NTFS
/dev/sda2          21,478,905   167,027,804   145,548,900   7 HPFS/NTFS
/dev/sda3         167,027,805   261,393,614    94,365,810   7 HPFS/NTFS
/dev/sda4         261,393,615   312,592,769    51,199,155   f W95 Ext d (LBA)
/dev/sda5         261,393,678   310,199,084    48,805,407  83 Linux
/dev/sda6         310,199,148   312,576,704     2,377,557  82 Linux swap / Solaris

/dev/sda4 ends after the last sector of /dev/sda

blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="FE7E736B7E731B99" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda2: UUID="74A695FBA695BE54" LABEL="WVISTA" TYPE="ntfs" 
/dev/sda3: UUID="30B81F9DB81F60A0" LABEL="WSEVEN" TYPE="ntfs" 
/dev/sda5: UUID="07e7670f-51d9-4082-867c-3de051507221" TYPE="ext4" 
/dev/sda6: TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
```

---

### Post by SecretCode on 2009-12-27
"Major" problem is right. Not to say it can't be fixed though ... even if we have to get a hex editor onto the MBR! (The author of GParted has been doing a bit of that to recover from some bugs.)

I am not convinced that any one tool tells us everything - and I'm not familiar enough with boot_info_script to see if it covers these (or just fdisk): so please install disktype, sfdisk and cfdisk (or just download PartedMagic) (looks like sfdisk and cfdisk are in the standard Karmic CD), and give the outputs of
```
sudo disktype /dev/sda
sudo cfdisk -Pt /dev/sda
sudo cfdisk -Ps /dev/sda
sudo sfdisk -luS /dev/sda
```

From what you've posted so far, sda3 is somehow the wrong size ... and sda4 extends beyond the end of the drive ... maybe sda4 has been shifted along in the partition table but the data on the disk hasn't, so sda5 can no longer be read.

By the way, why did you have two swap partitions? I didn't think that was ever necessary.

---

### Post by TrevT93 on 2009-12-27
You know what?  I think I have a major complaint to write to Microsoft.  It was completely unnecessary to modify the partition table to this extent.  Windows needs to act as an OS, not a program that domineers every aspect of a computer and modifies whatever it wants for whatever reason it comes up with!

Thanks, by the way, for joining in on my case.  I'll run those later and get back to you.

I had two SWAPs because I had Xubuntu and Debian running at the same time for a while.  When I would use Debian and then restart into Xubuntu, though, Xubuntu would boot into a recovery shell with the message that the SWAP space was still in use.  I made the second SWAP space for Xubuntu to use without throwing me exceptions.

---

### Post by SecretCode on 2009-12-27
I have learned something about swap spaces!

---

### Post by TrevT93 on 2009-12-28
Here you go.

```

ubuntu@ubuntu:~$ sudo disktype /dev/sda

--- /dev/sda
Block device, size 149.1 GiB (160041885696 bytes)
DOS/MBR partition map                            
Partition 1: 10.24 GiB (10997167104 bytes, 21478842 sectors from 63, bootable)
  Type 0x07 (HPFS/NTFS)                                                       
  NTFS file system                                                            
    Volume size 10.24 GiB (10997166592 bytes, 21478841 sectors)               
Partition 2: 69.40 GiB (74521036800 bytes, 145548900 sectors from 21478905)   
  Type 0x07 (HPFS/NTFS)
  NTFS file system
    Volume size 69.40 GiB (74521034240 bytes, 145548895 sectors)
Partition 3: 45.00 GiB (48315294720 bytes, 94365810 sectors from 167027805)
  Type 0x07 (HPFS/NTFS)
  NTFS file system
    Volume size 44.99 GiB (48307678720 bytes, 94350935 sectors)
Partition 4: 24.41 GiB (26213967360 bytes, 51199155 sectors from 261393615)
  Type 0x0F (Win95 Ext'd (LBA))
  Partition 5: 23.27 GiB (24988368384 bytes, 48805407 sectors from 261393615+63)
    Type 0x83 (Linux)
    Ext3 file system
      UUID 07E7670F-51D9-4082-867C-3DE051507221 (DCE, v4)
      Volume size 23.27 GiB (24988364800 bytes, 6100675 blocks of 4 KiB)
  Partition 6: 1.134 GiB (1217309184 bytes, 2377557 sectors from 310199085+63)
    Type 0x82 (Linux swap / Solaris)
    Linux swap, version 2, subversion 1, 4 KiB pages, little-endian
      Swap size 1.134 GiB (1217298432 bytes, 297192 pages of 4 KiB)

ubuntu@ubuntu:~$ sudo cfdisk -Pt /dev/sda
FATAL ERROR: Bad primary partition 3: Partition ends after end-of-disk
ubuntu@ubuntu:~$ sudo cfdisk -Ps /dev/sda
FATAL ERROR: Bad primary partition 3: Partition ends after end-of-disk
ubuntu@ubuntu:~$ sudo sfdisk -luS /dev/sda

Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  21478904   21478842   7  HPFS/NTFS
/dev/sda2      21478905 167027804  145548900   7  HPFS/NTFS
/dev/sda3     167027805 261393614   94365810   7  HPFS/NTFS
/dev/sda4     261393615 312592769   51199155   f  W95 Ext'd (LBA)
/dev/sda5     261393678 310199084   48805407  83  Linux
/dev/sda6     310199148 312576704    2377557  82  Linux swap / Solaris

```

Looks like cfdisk doesn't want to deal with me because of the whole extended-partition-is-too-big thing.

---

### Post by gradinaruvasile on 2009-12-28
Use fdisk from command line for partitioning. 
I dont trust gparted, it is weird sometimes and cant complete seemingly trivial tasks at times.

Oh yes, and Windows Vista, and especially Windows 7 is a big pain in the @$$ when it comes to multiple partitioning. It seems Microsoft thinks people are more stupid than they were when XP was around... 
Like it was said before, it should be a program for Gods sake that does what is told to do, not what Microsoft wants...   Especially when it is about whole partitions that can contain valuable data. 
Microsoft should be directly responsible for these damages. But:

From the Vista EULA:

"LIMITATION ON AND EXCLUSION OF DAMAGES. You can recover from Microsoft and its suppliers only direct damages up to the amount you paid for the software. You cannot recover any other damages, including consequential, lost profits, special, indirect or incidental damages."

As i see it, if you lose stuff that its worth a truckload of money, you are kinda screwed...

---

### Post by gradinaruvasile on 2009-12-28
From the Windows 7  EULA:

"25. LIMITATION ON AND EXCLUSION OF DAMAGES. Except for any refund the manufacturer
    or installer [COLOR="Red"]may[/COLOR] provide, you cannot recover any other damages, including consequential,
    lost profits, special, indirect or incidental damages.
    This limitation applies to
    ·   anything related to the software, services, content (including code) on third party Internet sites,
        or third party programs; and
·    claims for breach of contract, breach of warranty, guarantee or condition, strict liability,
     negligence, or other tort to the extent permitted by applicable law.
[COLOR="Red"]It also applies even if[/COLOR]
·    repair, replacement or a refund for the software does not fully compensate you for any losses; or
·    [COLOR="red"]Microsoft knew or should have known about the possibility of the damages.[/COLOR]"

Nice work Microsoft...

---

### Post by SecretCode on 2009-12-28
I don't really know what to do about it (yet...) but this is what I think has happened.

[LIST]
[*]sda1 and sda2 are fine.


[*]sda3 (WSEVEN) has been expanded a bit but the filesystem in it hasn't: the boot_info_script section on sda3 mentions this, and the disktype output shows that the filesystem (volume) is 94,350,935 sectors but the partition is 94,365,810 - a difference of 14,785.


[*]sda4 (the extended partition) has been moved along the drive (incorrectly: both the beginning and end have moved, so the end is beyond the physical end of the drive) but - my theory - the contents haven't. So testdisk could only find the second ext4 partition that used to be there and the first swap file.

sda4 is marked to end at sector 312,592,769, which is 10,961 more than the number of sectors there are supposed to be on the drive.
[/LIST]
So ... if you could write a new partition table in the MBR, without writing any data into the extended partition, the logical partitions might be recoverable. The details of the logical partitions aren't in the MBR but at the beginning of the extended partition and we can hope that that bit of the drive hasn't been written over. 

It's unclear where the original start of sda4 was. So you might need to try a few different values, and test until sensible logical partitions appear. But you can safely make its end be the end of the physical drive.

And you can safely reduce sda3 to the volume size + 1 sector.

What I'm not sure of is how to write the MBR partition table without touching any logical partition data ... except by using a hex editor on the MBR itself ... which we can do.

Q1: Can you boot the machine from a USB stick? This would enable us to save some data persistently (using an Ubuntu live USB with a 'persistence' area). Or else, can you attach a USB drive / stick and boot from a Live CD, so we can save data onto the USB stick?

---

### Post by oldfred on 2009-12-28
I do not consider myself knowledgeable enough to do this but here is an example to directly edit the partition table example only applies to that OPs partition table:

Caljohnsmith using sfdisk to edit partition table from text file
[http://ubuntuforums.org/showthread.php?t=1036600](http://ubuntuforums.org/showthread.php?t=1036600)

---

### Post by TrevT93 on 2009-12-28
My computer currently is bootable, and it still runs Windows 7 which I installed after this whole mess took place (overwriting the Windows 7 copy which previously was Windows Vista on sda2).  It also runs the Windows 7 Beta which is on sda3.

I have a 2 GB flash drive which is empty and a 4 GB one that all my important data was backed up onto.  It has about 1 GB of space left on it.

So you're basically saying that you believe that Windows accidentally expanded one partition and that the other ones beyond it shifted to accommodate it, and that because of it one of the partitions was written incorrectly to read as being beyond the capacity of the hard disk?

---

### Post by SecretCode on 2009-12-28
1GB of flash drive will be plenty to save a few MBR copies.

> **TrevT93 said:**
> So you're basically saying that you believe that Windows accidentally expanded one partition and that the other ones beyond it shifted to accommodate it, and that because of it one of the partitions was written incorrectly to read as being beyond the capacity of the hard disk?

I'm saying that **something** expanded one partition, etc. The EULA that I implicitly signed when launching my first copy of Windows 95 binds me not to implicate Microsoft in anything of any kind whatsoever. :P

---

### Post by TrevT93 on 2009-12-28
Lol...my high school's head of the tech department is an all-Microsoft person.  I can't imagine how he's able to do _anything_ for the school.

(FYI, I'll keep implicating Microsoft because if they're seen suing a teenager over implicating them for a computer crash their product so obviously caused, they won't get anywhere and they'll lose a lot of the credibility they already don't have!)

---

### Post by SecretCode on 2009-12-28
OK ... can you boot the machine from a live CD and attach a USB drive to save the output of this:

```
sudo dd if=/dev/sda of=~/Desktop/TrevT93-original.mbr bs=512 count=1
```

This saves a binary copy of your MBR. If you type this wrong you are liable to wipe out your MBR. 

Have you backed up all important data from the partitions you can still access?

Then, I don't think you can upload a binary file as an attachment, but either zip it (even though it will only be 512 bytes) or upload to a filesharing service.

And/or run 
```
hexdump -C ~/Desktop/TrevT93-original.mbr
```
and post the output here.

Keep the .mbr file safe in case we mess it up even more than it is!

---

### Post by TrevT93 on 2009-12-28
Out of ease, I went with the hexdump option:

```

ubuntu@ubuntu:~$ hexdump -C ~/Desktop/TrevT93-original.mbr
00000000  33 c0 8e d0 bc 00 7c 8e  c0 8e d8 be 00 7c bf 00  |3.....|......|..|
00000010  06 b9 00 02 fc f3 a4 50  68 1c 06 cb fb b9 04 00  |.......Ph.......|
00000020  bd be 07 80 7e 00 00 7c  0b 0f 85 0e 01 83 c5 10  |....~..|........|
00000030  e2 f1 cd 18 88 56 00 55  c6 46 11 05 c6 46 10 00  |.....V.U.F...F..|
00000040  b4 41 bb aa 55 cd 13 5d  72 0f 81 fb 55 aa 75 09  |.A..U..]r...U.u.|
00000050  f7 c1 01 00 74 03 fe 46  10 66 60 80 7e 10 00 74  |....t..F.f`.~..t|
00000060  26 66 68 00 00 00 00 66  ff 76 08 68 00 00 68 00  |&fh....f.v.h..h.|
00000070  7c 68 01 00 68 10 00 b4  42 8a 56 00 8b f4 cd 13  ||h..h...B.V.....|
00000080  9f 83 c4 10 9e eb 14 b8  01 02 bb 00 7c 8a 56 00  |............|.V.|
00000090  8a 76 01 8a 4e 02 8a 6e  03 cd 13 66 61 73 1c fe  |.v..N..n...fas..|
000000a0  4e 11 75 0c 80 7e 00 80  0f 84 8a 00 b2 80 eb 84  |N.u..~..........|
000000b0  55 32 e4 8a 56 00 cd 13  5d eb 9e 81 3e fe 7d 55  |U2..V...]...>.}U|
000000c0  aa 75 6e ff 76 00 e8 8d  00 75 17 fa b0 d1 e6 64  |.un.v....u.....d|
000000d0  e8 83 00 b0 df e6 60 e8  7c 00 b0 ff e6 64 e8 75  |......`.|....d.u|
000000e0  00 fb b8 00 bb cd 1a 66  23 c0 75 3b 66 81 fb 54  |.......f#.u;f..T|
000000f0  43 50 41 75 32 81 f9 02  01 72 2c 66 68 07 bb 00  |CPAu2....r,fh...|
00000100  00 66 68 00 02 00 00 66  68 08 00 00 00 66 53 66  |.fh....fh....fSf|
00000110  53 66 55 66 68 00 00 00  00 66 68 00 7c 00 00 66  |SfUfh....fh.|..f|
00000120  61 68 00 00 07 cd 1a 5a  32 f6 ea 00 7c 00 00 cd  |ah.....Z2...|...|
00000130  18 a0 b7 07 eb 08 a0 b6  07 eb 03 a0 b5 07 32 e4  |..............2.|
00000140  05 00 07 8b f0 ac 3c 00  74 09 bb 07 00 b4 0e cd  |......<.t.......|
00000150  10 eb f2 f4 eb fd 2b c9  e4 64 eb 00 24 02 e0 f8  |......+..d..$...|
00000160  24 02 c3 49 6e 76 61 6c  69 64 20 70 61 72 74 69  |$..Invalid parti|
00000170  74 69 6f 6e 20 74 61 62  6c 65 00 45 72 72 6f 72  |tion table.Error|
00000180  20 6c 6f 61 64 69 6e 67  20 6f 70 65 72 61 74 69  | loading operati|
00000190  6e 67 20 73 79 73 74 65  6d 00 4d 69 73 73 69 6e  |ng system.Missin|
000001a0  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
000001b0  65 6d 00 00 00 63 7b 9a  98 fa b4 5c 00 00 80 01  |em...c{....\....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 ba bd 47 01 00 fe  |......?.....G...|
000001d0  ff ff 07 fe ff ff f9 bd  47 01 64 e6 ac 08 00 fe  |........G.d.....|
000001e0  ff ff 07 fe ff ff 5d a4  f4 09 72 e8 9f 05 00 fe  |......]...r.....|
000001f0  ff ff 0f fe ff ff cf 8c  94 0f b3 3c 0d 03 55 aa  |...........<..U.|
00000200

```

Yes, everything is still backed up to my 4 GB flash drive.

---

### Post by SecretCode on 2009-12-28
OK! But in my timezone it's way past bedtime so I won't look at this for a few hours. :D

---

### Post by TrevT93 on 2009-12-28
Fine by me, my computer just needs to be ready by next Monday.

---

### Post by SecretCode on 2009-12-29
Here's what I suggest, then.

Check again that your saved original mbr is safe somewhere. 

Then make a copy of the file (say, "yourcopyof.mbr") and make sure you have **hexedit** installed. Run ```
hexedit --sector --color yourcopyof.mbr
```

Use the cursor to go to the row 000001e0. Type in the following changes...
You should have:
```

000001e0  ff ff 07 fe ff ff 5d a4  f4 09 72 e8 9f 05 00 fe  
000001f0  ff ff 0f fe ff ff cf 8c  94 0f b3 3c 0d 03 55 aa
```
And you want:
```

000001e0  ff ff 07 fe ff ff 5d a4  f4 09 **_58 ae_** 9f 05 00 fe
000001f0  ff ff 0f fe ff ff **_b5 52_**  94 0f b3 3c 0d 03 55 aa
```

This changes the size of partition sda3 and the start of the extended partition sda4.

Save the file using Ctrl-X

Apply the new mbr as follows - don't mistype; you could irretrievably erase other data:
```
sudo dd if=yourcopyof.mbr of=/dev/sda bs=512 count=1
```

Now reboot the live CD (to make sure the OS reads the new partition table) and get the output of 
```
sudo disktype
sudo sfdisk -luS /dev/sda
```
and post it here.

If disktype says that Partition is anything other than 94350936 sectors - and the volume size is 94350935 - 
```
Partition 3: ??.?? GiB (??????????? bytes, 94350936 sectors from 167027805)
  Type 0x07 (HPFS/NTFS)
  NTFS file system
    Volume size 44.99 GiB (48307678720 bytes, 94350935 sectors)
```
- don't reboot windows! Instead recover the original MBR with
```
sudo dd if=TrevT93-original.mbr of=/dev/sda bs=512 count=1
```
- You might need to give the full path to TrevT93-original.mbr.

On the other hand, if this works, it's worth running **testdisk** again. It should now see all of the extended partition, and be able to detect the partitions in it - provided the relevant disk sectors have not been written over, which may unfortunately have happened.

Also save a copy of yourcopyof.mbr.

---

### Post by TrevT93 on 2009-12-29
Okay, that's one problem solved...and another created, I fear.

```

ubuntu@ubuntu:~$ sudo disktype /dev/sda

--- /dev/sda
Block device, size 149.1 GiB (160041885696 bytes)
DOS/MBR partition map
Partition 1: 10.24 GiB (10997167104 bytes, 21478842 sectors from 63, bootable)
  Type 0x07 (HPFS/NTFS)
  NTFS file system
    Volume size 10.24 GiB (10997166592 bytes, 21478841 sectors)
Partition 2: 69.40 GiB (74521036800 bytes, 145548900 sectors from 21478905)
  Type 0x07 (HPFS/NTFS)
  NTFS file system
    Volume size 69.40 GiB (74521034240 bytes, 145548895 sectors)
Partition 3: 44.99 GiB (48307679232 bytes, 94350936 sectors from 167027805)
  Type 0x07 (HPFS/NTFS)
  NTFS file system
    Volume size 44.99 GiB (48307678720 bytes, 94350935 sectors)
Partition 4: 24.41 GiB (26213967360 bytes, 51199155 sectors from 261378741)
  Type 0x0F (Win95 Ext'd (LBA))
  Signature missing

ubuntu@ubuntu:~$ sudo sfdisk -luS /dev/sda

Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

sfdisk: ERROR: sector 261378741 does not have an msdos signature
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  21478904   21478842   7  HPFS/NTFS
/dev/sda2      21478905 167027804  145548900   7  HPFS/NTFS
/dev/sda3     167027805 261378740   94350936   7  HPFS/NTFS
/dev/sda4     261378741 312577895   51199155   f  W95 Ext'd (LBA)

```

Where are sda's 5, 6, and 7?  And why does sda4 seem to be missing a signature of some kind?

To be on the safe side, I'm reverting the mbr to the original I took.  Unless you happen to reply before I do so.

---

### Post by SecretCode on 2009-12-29
That's actually fine, so far. I just guessed where the sda4 partition might start - not really surprising that the sector it points to doesn't contain a extended partition sector. So disktype doesn't find a signature there, and so doesn't see any logical partitions. Nor will fdisk, etc.

But **testdisk** ought to scan sectors starting with sector 261378741 and pick out any that look like partition sectors and recreate the correct extended partition layout. Did you try testdisk?

I didn't take account of the cylinder boundary issue - that at least means the original extended partition sector will be a little further along the disk (if it wasn't overwritten already).

By the way, the MBR you saved does point to a valid extended partition sector, but it will be one that your earlier run of testdisk created - not the original one that has your original partitions in.

---

### Post by TrevT93 on 2009-12-29
I don't know whether this is right or not...but here's what TestDisk is reporting as the "correct" partition structure:

```

Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  1336 254 63   21478842 [RECOVERY]
P HPFS - NTFS           1337   0  1 10396 254 63  145548900 [WVISTA]
P HPFS - NTFS          10397   0  1 16270 254 63   94365810 [WSEVEN]
L Linux                16271   1  1 19308 254 63   48805407
L Linux Swap           19309   1  1 19456 254 63    2377557

```

I'm not going to write it unless you give me a thumbs up, though.  It's reporting sda3's size in sectors as 94365810, not the 94350936 we came up with earlier.  TestDisk wants to extend sda3 to the same position Windows had it earlier...why?

And, by the way: if I were to reboot my computer right now and try to get into Windows, would it go through?  (I'm not going to for the moment, but I thought I would find out now.)

EDIT: hold that thought, I'm doing a deep search now for partitions.  Can't wait to see what this thing digs up...

---

### Post by TrevT93 on 2009-12-29
Okay, here's what the TestDisk deep scan reveals...

```

D HPFS - NTFS              0   1  1  1336 254 63   21478842 [RECOVERY]
D HPFS - NTFS           1336 254 63  2673 254 63   21478906
D HPFS - NTFS           1337   0  1 10396 254 63  145548900 [WVISTA]
D HPFS - NTFS           1337   0  1 10396 254 63  145548900 [WVISTA]
D HPFS - NTFS          10396 254 59 19456 254 63  145548905
D HPFS - NTFS          10396 254 63 19456 254 63  145548901
D HPFS - NTFS          10397   0  1 16270 254 63   94365810 [WSEVEN]
D HPFS - NTFS          10397   0  1 19456 254 63  145548900 [WSEVEN]
D Linux                16271   1  1 19308 254 63   48805407
D Linux                16271   2  1 17576 254 63   20980764
D Linux                17576   2  1 19177 254 63   25736004 [DEBIAN]
D Linux Swap           19178   1  1 19308 254 63    2104452
D Linux Swap           19309   1  1 19456 254 63    2377557

```

Now, how do they all fit together?

I would assume this:

```

[COLOR="Lime"]* HPFS - NTFS              0   1  1  1336 254 63   21478842 [RECOVERY][/COLOR]
D HPFS - NTFS           1336 254 63  2673 254 63   21478906
[COLOR="lime"]P HPFS - NTFS           1337   0  1 10396 254 63  145548900 [WVISTA][/COLOR]
D HPFS - NTFS           1337   0  1 10396 254 63  145548900 [WVISTA]
D HPFS - NTFS          10396 254 59 19456 254 63  145548905
D HPFS - NTFS          10396 254 63 19456 254 63  145548901
[COLOR="lime"]P HPFS - NTFS          10397   0  1 16270 254 63   94365810 [WSEVEN][/COLOR]
D HPFS - NTFS          10397   0  1 19456 254 63  145548900 [WSEVEN]
D Linux                16271   1  1 19308 254 63   48805407
[COLOR="lime"]L Linux                16271   2  1 17576 254 63   20980764[/COLOR]
D Linux                17576   2  1 19177 254 63   25736004 [DEBIAN]
[COLOR="lime"]L Linux Swap           19178   1  1 19308 254 63    2104452
L Linux Swap           19309   1  1 19456 254 63    2377557[/COLOR]

```

...but then again I know comparatively very little when it comes to partitioning!

(The structure I picked out fits together according to TestDisk...but will it work?

---

### Post by SecretCode on 2009-12-29
That first testdisk output looks much like your original report - so I don't think my shifting of sda4 has done much (yet).
> **TrevT93 said:**
> It's reporting sda3's size in sectors as 94365810, not the 94350936 we came up with earlier.  TestDisk wants to extend sda3 to the same position Windows had it earlier...why?
Perhaps because that's the offset where it finds the next partition sector. Don't know

> **TrevT93 said:**
> And, by the way: if I were to reboot my computer right now and try to get into Windows, would it go through?  (I'm not going to for the moment, but I thought I would find out now.)
I'm 90% confident Windows would boot fine, both from the sda2 partition WVISTA (because we didn't alter it) and the sda3 WSEVEN, if that's still got a working OS on it, because although we changed the partition size we didn't touch the *volume* size.

Now, your next post looks interesting...

---

### Post by SecretCode on 2009-12-29
> **TrevT93 said:**
> Okay, here's what the TestDisk deep scan reveals...
...
Now, how do they all fit together?

I would assume this:
```

a) [COLOR="Lime"]* HPFS - NTFS              0   1  1  1336 254 63   21478842 [RECOVERY][/COLOR]
b) D HPFS - NTFS           1336 254 63  2673 254 63   21478906
c) [COLOR="lime"]P HPFS - NTFS           1337   0  1 10396 254 63  145548900 [WVISTA][/COLOR]
d) D HPFS - NTFS           1337   0  1 10396 254 63  145548900 [WVISTA]
e) D HPFS - NTFS          10396 254 59 19456 254 63  145548905
f) D HPFS - NTFS          10396 254 63 19456 254 63  145548901
g) [COLOR="lime"]P HPFS - NTFS          10397   0  1 16270 254 63   94365810 [WSEVEN][/COLOR]
h) D HPFS - NTFS          10397   0  1 19456 254 63  145548900 [WSEVEN]
i) D Linux                16271   1  1 19308 254 63   48805407
j) [COLOR="lime"]L Linux                16271   2  1 17576 254 63   20980764[/COLOR]
k) D Linux                17576   2  1 19177 254 63   25736004 [DEBIAN]
l) [COLOR="lime"]L Linux Swap           19178   1  1 19308 254 63    2104452
m) L Linux Swap           19309   1  1 19456 254 63    2377557[/COLOR]

```

...but then again I know comparatively very little when it comes to partitioning!

(The structure I picked out fits together according to TestDisk...but will it work?

(I added letters for reference.)

I agree with a) and c) (although c/WVISTA might need the boot flag not a/RECOVERY). 

g) starts in the right place but I still suspect that it shouldn't be that large - probably the partition sector at the beginning of the partition is giving that size and testdisk believes that, not me.

Working from the end, m) and l) look fine (there are your two swap partitions). You should **include** k) as a logical partition - its start and end fit neatly between j) and l), and it's a valid partition, picking up the DEBIAN label.

Partition j) probably ends in the right place, but its start position isn't right (so it hasn't seen its label).

Time for some more calculation...

---

### Post by SecretCode on 2009-12-29
Wait, there's another problem. Partition k), which I'm fairly confident of, starts before the end of partition j). And because of the rounding to cylinders thing that Windows requires, partition g/WSEVEN is actually the right size ... at least according to Windows rules.

Maybe when you installed Xubuntu, you didn't round to cylinders (which Linux doesn't care about) - everything worked until Windows got its next chance to update the partition table and re-applied its own rules.

---

### Post by SecretCode on 2009-12-29
Anyway, here's a couple of possible layouts:

1 - Just changed the end cylinder of j) so everything fits. If this is right, then the beginning of j) - your lost Xubuntu partition - has probably been overwritten, hence testdisk not seeing a volume label. I'm not sure how to recover from that, but something should be possible.

```
      Type            C  H  S     C    H   S       Size  Label           Start        End
a  *  HPFS-NTFS       0  1  1  1336  254  63   21478842  [RECOVERY]         63   21478904 
c  P  HPFS-NTFS    1337  0  1 10396  254  63  145548900  [WVISTA]     21478905  167027804 
g  P  HPFS-NTFS   10397  0  1 16270  254  63   94365810  [WSEVEN]    167027805  261393614 
j  L  Linux       16271  2  1 _17575_  254  63   _20964699_  _XUBUNTU?_    261393741  282358439 
k  L  Linux       17576  2  1 19177  254  63   25736004  [DEBIAN]    282358566  308094569 
l  L  Linux Swap  19178  1  1 19308  254  63    2104452              308094633  310199084 
m  L  Linux Swap  19309  1  1 19456  254  63    2377557              310199148  312576704 
```

2 - As I've been thinking all along, I compressed g) as much as possible and made j) start after that (allowing for the extended partition sector/track). If this layout turns out to work, you should soon clone the Xubuntu partition and rebuild the partitions with 'round to cylinders' on, and restore the clone.
```
      Type            C   H   S      C    H   S       Size  Label           Start        End
a  *  HPFS-NTFS       0   1   1   1336  254  63   21478842  [RECOVERY]         63   21478904
c  P  HPFS-NTFS    1337   0   1  10396  254  63  145548900  [WVISTA]     21478905  167027804
g  P  HPFS-NTFS   10397   0   1  16270   _18_  _57_   _94350936_  [WSEVEN]    167027805  261378740
j  L  Linux       16270  _20_  _58_  _17575_  254  63   _20979573_  _XUBUNTU?_    261378867  282358439
k  L  Linux       17576   2   1  19177  254  63   25736004  [DEBIAN]    282358566  308094569
l  L  Linux Swap  19178   1   1  19308  254  63    2104452              308094633  310199084
m  L  Linux Swap  19309   1   1  19456  254  63    2377557              310199148  312576704
```

---

### Post by TrevT93 on 2009-12-29
Wow, four in a row.

Well, before you go off on the Xubuntu-partition-is-wrong theorem, let me just mention that there was no volume label on Xubuntu.  I was going to add that shortly before my computer crashed...

I do need to get back into Windows, that's why I asked.

---

### Post by SecretCode on 2009-12-30
> **TrevT93 said:**
> Well, before you go off on the Xubuntu-partition-is-wrong theorem, let me just mention that there was no volume label on Xubuntu.

:!:
Right, I'll stop thinking about that then!

---

I've been messing with gparted and testdisk in a virtual machine ... and I have got errors like gparted showing all the space as unallocated and cfdisk saying the end of the extended partition is after the end of the drive, as you found. Worrying, because I don't know what caused it.

There may be a problem with the disk geometry.

Can I have the output of 
```
sudo sfdisk -gG /dev/sda
```

Also 
```
sudo testdisk /list /dev/sda
```

---

### Post by TrevT93 on 2009-12-30
Okay.

```

ubuntu@ubuntu:~$ sudo sfdisk -gG /dev/sda
/dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

sfdisk: ERROR: sector 261378741 does not have an msdos signature
/dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
ubuntu@ubuntu:~$ sudo testdisk /list /dev/sda
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
Please wait...
Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63, sector size=512

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition            Start        End    Size in sectors
 1 * HPFS - NTFS              0   1  1  1336 254 63   21478842 [RECOVERY]
 2 P HPFS - NTFS           1337   0  1 10396 254 63  145548900 [WVISTA]
 3 P HPFS - NTFS          10397   0  1 16270  18 57   94350936 [WSEVEN]
 4 E extended LBA         16270  18 58 19457  18 57   51199155

test_logical: 
Partition sector doesn't have the endmark 0xAA55

```

Oh, and I thought I might throw this one in here:

```

ubuntu@ubuntu:~$ gksudo gparted
======================
libparted : 1.8.8.1.159-1e0e
======================
Invalid partition table on /dev/sda -- wrong signature e09.

```

---

### Post by SecretCode on 2009-12-30
That lack of a partition table signature is a puzzle. Can you post the MBR again:

```
sudo dd if=/dev/sda of=~/TrevT93-current.mbr bs=1 count=512
```

Zip this file and attach it, or run 
```
hexdump -C ~/TrevT93-current.mbr
```
and post the output here.

--
Also, what error are you getting from *sudo cfdisk /dev/sda* and *sudo sfdisk -luS /dev/sda* (if any)?

---

### Post by TrevT93 on 2009-12-30
MBR:

```

ubuntu@ubuntu:~$ hexdump -C ~/TrevT93-current.mbr
00000000  33 c0 8e d0 bc 00 7c 8e  c0 8e d8 be 00 7c bf 00  |3.....|......|..|
00000010  06 b9 00 02 fc f3 a4 50  68 1c 06 cb fb b9 04 00  |.......Ph.......|
00000020  bd be 07 80 7e 00 00 7c  0b 0f 85 0e 01 83 c5 10  |....~..|........|
00000030  e2 f1 cd 18 88 56 00 55  c6 46 11 05 c6 46 10 00  |.....V.U.F...F..|
00000040  b4 41 bb aa 55 cd 13 5d  72 0f 81 fb 55 aa 75 09  |.A..U..]r...U.u.|
00000050  f7 c1 01 00 74 03 fe 46  10 66 60 80 7e 10 00 74  |....t..F.f`.~..t|
00000060  26 66 68 00 00 00 00 66  ff 76 08 68 00 00 68 00  |&fh....f.v.h..h.|
00000070  7c 68 01 00 68 10 00 b4  42 8a 56 00 8b f4 cd 13  ||h..h...B.V.....|
00000080  9f 83 c4 10 9e eb 14 b8  01 02 bb 00 7c 8a 56 00  |............|.V.|
00000090  8a 76 01 8a 4e 02 8a 6e  03 cd 13 66 61 73 1c fe  |.v..N..n...fas..|
000000a0  4e 11 75 0c 80 7e 00 80  0f 84 8a 00 b2 80 eb 84  |N.u..~..........|
000000b0  55 32 e4 8a 56 00 cd 13  5d eb 9e 81 3e fe 7d 55  |U2..V...]...>.}U|
000000c0  aa 75 6e ff 76 00 e8 8d  00 75 17 fa b0 d1 e6 64  |.un.v....u.....d|
000000d0  e8 83 00 b0 df e6 60 e8  7c 00 b0 ff e6 64 e8 75  |......`.|....d.u|
000000e0  00 fb b8 00 bb cd 1a 66  23 c0 75 3b 66 81 fb 54  |.......f#.u;f..T|
000000f0  43 50 41 75 32 81 f9 02  01 72 2c 66 68 07 bb 00  |CPAu2....r,fh...|
00000100  00 66 68 00 02 00 00 66  68 08 00 00 00 66 53 66  |.fh....fh....fSf|
00000110  53 66 55 66 68 00 00 00  00 66 68 00 7c 00 00 66  |SfUfh....fh.|..f|
00000120  61 68 00 00 07 cd 1a 5a  32 f6 ea 00 7c 00 00 cd  |ah.....Z2...|...|
00000130  18 a0 b7 07 eb 08 a0 b6  07 eb 03 a0 b5 07 32 e4  |..............2.|
00000140  05 00 07 8b f0 ac 3c 00  74 09 bb 07 00 b4 0e cd  |......<.t.......|
00000150  10 eb f2 f4 eb fd 2b c9  e4 64 eb 00 24 02 e0 f8  |......+..d..$...|
00000160  24 02 c3 49 6e 76 61 6c  69 64 20 70 61 72 74 69  |$..Invalid parti|
00000170  74 69 6f 6e 20 74 61 62  6c 65 00 45 72 72 6f 72  |tion table.Error|
00000180  20 6c 6f 61 64 69 6e 67  20 6f 70 65 72 61 74 69  | loading operati|
00000190  6e 67 20 73 79 73 74 65  6d 00 4d 69 73 73 69 6e  |ng system.Missin|
000001a0  67 20 6f 70 65 72 61 74  69 6e 67 20 73 79 73 74  |g operating syst|
000001b0  65 6d 00 00 00 63 7b 9a  98 fa b4 5c 00 00 80 01  |em...c{....\....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 ba bd 47 01 00 fe  |......?.....G...|
000001d0  ff ff 07 fe ff ff f9 bd  47 01 64 e6 ac 08 00 fe  |........G.d.....|
000001e0  ff ff 07 fe ff ff 5d a4  f4 09 58 ae 9f 05 00 fe  |......]...X.....|
000001f0  ff ff 0f fe ff ff b5 52  94 0f b3 3c 0d 03 55 aa  |.......R...<..U.|
00000200

```cfdisk says:

```

FATAL ERROR: Bad primary partition 3: Partition ends in the final partial cylinder
                             Press any key to exit cfdisk

```sfdisk says:

```

Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

sfdisk: ERROR: sector 261378741 does not have an msdos signature
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  21478904   21478842   7  HPFS/NTFS
/dev/sda2      21478905 167027804  145548900   7  HPFS/NTFS
/dev/sda3     167027805 261378740   94350936   7  HPFS/NTFS
/dev/sda4     261378741 312577895   51199155   f  W95 Ext'd (LBA)

```

---

### Post by SecretCode on 2009-12-30
OK, now try this!

Run ```
hexedit --sector --color ~/TrevT93-current.mbr
```

Use the cursor to go to the row 000001e0. Type in the following changes...
You should have:
```

000001e0  ff ff 07 fe ff ff 5d a4  f4 09 58 ae 9f 05 00 fe  
000001f0  ff ff 0f fe ff ff b5 52  94 0f b3 3c 0d 03 55 aa 
```
And you want:
```

000001e0  ff ff 07 fe ff ff 5d a4  f4 09 58 ae 9f 05 00 fe  
000001f0  ff ff 0f fe ff ff _cf 8c_  94 0f _f2 fd oc_ 03 55 aa 
```

This should bring the end of sda4 within range so cfdisk stops objecting, and put the start where testdisk reckons it should be and we may have some chance of finding the extended partition sector. Perhaps.

Save the file using Ctrl-X

Apply the new mbr as follows - don't mistype; you could irretrievably erase other data:
```
sudo dd if=~/TrevT93-current.mbr of=/dev/sda bs=512 count=1
```

Now reboot the live CD (to make sure the OS reads the new partition table) and get the output of 
```
sudo disktype
sudo sfdisk -luS /dev/sda
sudo cfdisk -Pt /dev/sda
```
and post it here.

If they give no error, give gparted a whirl (but don't make any more partitioning changes yet). If that sees partitions, try booting into windows.

---

### Post by TrevT93 on 2009-12-30
I think we are now officially getting somewhere...

```

ubuntu@ubuntu:~$ sudo disktype /dev/sda

--- /dev/sda
Block device, size 149.1 GiB (160041885696 bytes)
DOS/MBR partition map
Partition 1: 10.24 GiB (10997167104 bytes, 21478842 sectors from 63, bootable)
  Type 0x07 (HPFS/NTFS)
  NTFS file system
    Volume size 10.24 GiB (10997166592 bytes, 21478841 sectors)
Partition 2: 69.40 GiB (74521036800 bytes, 145548900 sectors from 21478905)
  Type 0x07 (HPFS/NTFS)
  NTFS file system
    Volume size 69.40 GiB (74521034240 bytes, 145548895 sectors)
Partition 3: 44.99 GiB (48307679232 bytes, 94350936 sectors from 167027805)
  Type 0x07 (HPFS/NTFS)
  NTFS file system
    Volume size 44.99 GiB (48307678720 bytes, 94350935 sectors)
Partition 4: 24.41 GiB (26205742080 bytes, 51183090 sectors from 261393615)
  Type 0x0F (Win95 Ext'd (LBA))
  Partition 5: 23.27 GiB (24988368384 bytes, 48805407 sectors from 261393615+63)
    Type 0x83 (Linux)
    Ext3 file system
      UUID 07E7670F-51D9-4082-867C-3DE051507221 (DCE, v4)
      Volume size 23.27 GiB (24988364800 bytes, 6100675 blocks of 4 KiB)
  Partition 6: 1.134 GiB (1217309184 bytes, 2377557 sectors from 310199085+63)
    Type 0x82 (Linux swap / Solaris)
    Linux swap, version 2, subversion 1, 4 KiB pages, little-endian
      Swap size 1.134 GiB (1217298432 bytes, 297192 pages of 4 KiB)

ubuntu@ubuntu:~$ sudo sfdisk -luS /dev/sda

Disk /dev/sda: 19457 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  21478904   21478842   7  HPFS/NTFS
/dev/sda2      21478905 167027804  145548900   7  HPFS/NTFS
/dev/sda3     167027805 261378740   94350936   7  HPFS/NTFS
/dev/sda4     261393615 312576704   51183090   f  W95 Ext'd (LBA)
/dev/sda5     261393678 310199084   48805407  83  Linux
/dev/sda6     310199148 312576704    2377557  82  Linux swap / Solaris

ubuntu@ubuntu:~$ sudo cfdisk -Pt /dev/sda
Partition Table for /dev/sda

         ---Starting----      ----Ending-----    Start     Number of
 # Flags Head Sect  Cyl   ID  Head Sect  Cyl     Sector    Sectors
-- ----- ---- ---- ----- ---- ---- ---- ----- ----------- -----------
 1  0x80    1    1     0 0x07  254   63  1336          63    21478842
 2  0x00    0    1  1337 0x07  254   63 10396    21478905   145548900
 3  0x00    0    1 10397 0x07   18   57 16270   167027805    94350936
 4  0x00    0    1 16271 0x0F  254   63 19456   261393615    51183090
 5  0x00    1    1 16271 0x83  254   63 19308          63    48805407
 6  0x00    1    1 19309 0x82  254   63 19456          63     2377557

```No more messing with me, no more errors, no more mount issues.  And GParted is actually displaying the partition table!

But...

```

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /media
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```Xubuntu doesn't want to make a reappearance.  Or at least not yet.  Maybe it's time for another TestDisk deep scan?

EDIT: just so you know, I seem to be getting filesystem errors from GParted concerning the WSEVEN partition.  It's telling me to run "chkdsk /f" in Windows...I don't think this pertains to the problem at hand here but I wanted to be sure.

---

### Post by SecretCode on 2009-12-31
:D

Re the WSEVEN partition: it's normally a good practice to run chkdsk after any ntfs resizing operation. Gparted sets a flag for that, I think. Not necessarily a problem. 

Re sda5 ... either we just haven't found the right location yet, or (worst case) the relevant sector was actually overwritten. 

There's still only 2 logical partitions showing, where there should be 4. 

Yes, run testdisk deep scan (... but don't apply any changes just yet).

---

### Post by TrevT93 on 2009-12-31
Alright, I will.

However, please just note these things:


[LIST]
[*]First, I'm running out of time before my PC needs to be totally up and running.  Should worst come to worst, I can overwrite Xubuntu, the old Debian, and the swap spaces and start over.  Most of the important information is, as I mentioned, backed up.
[*]Second, I was planning to get rid of the Debian partition.  If it doesn't squeeze in exactly right, we can do away with it.
[*]Third, the NTFS partitions are all operating as they should.  In fact, I'm typing this from Windows 7.  Both drives are accessible.
[/LIST]

So, I'll run TestDisk now, but if it doesn't help much, then I can work with wiping out the old partitions and reinstalling Xubuntu.

---

### Post by TrevT93 on 2009-12-31
Okay, TestDisk says:

```

D HPFS - NTFS              0   1  1  1336 254 63   21478842 [RECOVERY]
D HPFS - NTFS           1336 254 63  2673 254 63   21478906
D HPFS - NTFS           1337   0  1 10396 254 63  145548900 [WVISTA]
D HPFS - NTFS           1337   0  1 10396 254 63  145548900 [WVISTA]
D HPFS - NTFS          10396 254 59 19456 254 63  145548905
D HPFS - NTFS          10396 254 63 19456 254 63  145548901
D HPFS - NTFS          10397   0  1 16270 254 63   94365810 [WSEVEN]
D HPFS - NTFS          10397   0  1 19456 254 63  145548900 [WSEVEN]
D Linux                16271   1  1 19308 254 63   48805407
D Linux                16271   2  1 17576 254 63   20980764
D Linux                17576   2  1 19177 254 63   25736004 [DEBIAN]
D Linux Swap           19178   1  1 19308 254 63    2104452
D Linux Swap           19309   1  1 19456 254 63    2377557

```I would think:

```

[COLOR=Lime]* HPFS - NTFS              0   1  1  1336 254 63   21478842 [RECOVERY][/COLOR]
D HPFS - NTFS           1336 254 63  2673 254 63   21478906
[COLOR=Lime]P HPFS - NTFS           1337   0  1 10396 254 63  145548900 [WVISTA][/COLOR]
D HPFS - NTFS           1337   0  1 10396 254 63  145548900 [WVISTA]
D HPFS - NTFS          10396 254 59 19456 254 63  145548905
D HPFS - NTFS          10396 254 63 19456 254 63  145548901
[COLOR=Lime]P HPFS - NTFS          10397   0  1 16270 254 63   94365810 [WSEVEN][/COLOR]
D HPFS - NTFS          10397   0  1 19456 254 63  145548900 [WSEVEN]
D Linux                16271   1  1 19308 254 63   48805407
[COLOR=Lime]L Linux                16271   2  1 17576 254 63   20980764[/COLOR]
[COLOR=Lime]L Linux                17576   2  1 19177 254 63   25736004 [DEBIAN][/COLOR]
[COLOR=Lime]L Linux Swap           19178   1  1 19308 254 63    2104452[/COLOR]
[COLOR=Lime]L Linux Swap           19309   1  1 19456 254 63    2377557[/COLOR]

```

There's a problem:

```

...
[COLOR=Lime]L Linux                16271   2  1 175_76_ 254 63   20980764[/COLOR]
[COLOR=Lime]L Linux                175_76_   2  1 19177 254 63   25736004 [DEBIAN]
[COLOR=Black]...

```

The Xubuntu and Debian partitions appear to be sharing a cylinder, which isn't helping me because TestDisk won't let me write the partition structure back like this.

So...what do we do about that?
[/COLOR][/COLOR]

---

### Post by SecretCode on 2009-12-31
> **TrevT93 said:**
> However, please just note these things:
[LIST]
[*]First, I'm running out of time before my PC needs to be totally up and running.  Should worst come to worst, I can overwrite Xubuntu, the old Debian, and the swap spaces and start over.  Most of the important information is, as I mentioned, backed up.
[*]Second, I was planning to get rid of the Debian partition.  If it doesn't squeeze in exactly right, we can do away with it.
[*]Third, the NTFS partitions are all operating as they should.  In fact, I'm typing this from Windows 7.  Both drives are accessible.
[/LIST]
Noted!

You mentioned that the Debian pt was old - but how important is the Xubuntu one? I was under the impression that it had some stuff in it you really need to keep. If we can't make it bootable but we can access some of the files, is that worthwhile?

> **TrevT93 said:**
> Okay, TestDisk says:
...

There's a problem:
...
The Xubuntu and Debian partitions appear to be sharing a cylinder, which isn't helping me because TestDisk won't let me write the partition structure back like this.

So...what do we do about that?

That **is** a problem, and afaics testdisk doesn't have any ability to edit the address details of its recommendations. This is where we would have to use **sfdisk**.

---

### Post by SecretCode on 2009-12-31
sfdisk then ...

Run ```
sudo sfdisk -d /dev/sda > ~/sfd-pt.txt
```

Copy the file to e.g. sfd-pt-edit.txt and edit it with a text editor (are you doing this from the Xubuntu live cd?). It should have a set of lines like ```
/dev/sda1 : start=       63, size= 52436097, Id= 7
```

- And it'll probably only go up to sda6.

Don't change sda1 sda2 or sda3! And I'm pretty sure sda4 is OK.

You need to change or add lines like this: 
```
/dev/sda5 : start= 261393741, size= 20964699, Id=83
/dev/sda6 : start= 282358566, size= 25736004, Id=83
/dev/sda7 : start= 308094633, size=  2104452, Id=82
/dev/sda8 : start= 310199148, size=  2377557, Id=82
```
(numbers taken from my post [here]("http://ubuntuforums.org/showpost.php?p=8577959&postcount=27"))

Then apply the changes to the disk using
```
sudo sfdisk /dev/sda -O ~/sda-partition-sectors.save < ~/sfd-pt-edit.txt
```

- and see what cfdisk and gparted etc think of the disk. You may still have a "bad superblock" on sda5 (xubuntu) but if we get all the partitions back there should be other ways of addressing that.

You may need to reboot to get the new partition table recognised by all tools, but I don't think so.

---

Post your sfd-pt.txt and sfd-pt-edit.txt here. I'm not around this evening but if you get it nearly right, I'm sure someone else can chip in :)

---

And as usual, make sure you **_save_** the sfd...txt files and especially the ~/sda-partition-sectors.save somewhere permanent like a flash drive!

---

### Post by TrevT93 on 2009-12-31
Let's hope we can get this done by the end of today.  And I don't think there will be anyone else joining in on this discussion, seeing that over the last few days of discussion, only a few other people have been around, and none of them have posted since we've gotten deep into this.

sfdisk is checking to make sure all the drives are unmounted, and for some reason the check fails:

```

ubuntu@ubuntu:~$ sudo sfdisk /dev/sda -O ~/sda-partition-sectors.save < ~/sfd-pt-edit.txt
Checking that no-one is using this disk right now ...
BLKRRPART: Device or resource busy

This disk is currently in use - repartitioning is probably a bad idea.
Umount all file systems, and swapoff all swap partitions on this disk.
Use the --no-reread flag to suppress this check.
Use the --force flag to overrule all checks.

```Weird, just after it I "sudo umount"'ed all the sda drives and got that all of them were never mounted in the first place.

sfd-pt:

```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 21478842, Id= 7, bootable
/dev/sda2 : start= 21478905, size=145548900, Id= 7
/dev/sda3 : start=167027805, size= 94350936, Id= 7
/dev/sda4 : start=261393615, size= 51183090, Id= f
/dev/sda5 : start=261393678, size= 48805407, Id=83
/dev/sda6 : start=310199148, size=  2377557, Id=82

```

sfd-pt-edit:

```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 21478842, Id= 7, bootable
/dev/sda2 : start= 21478905, size=145548900, Id= 7
/dev/sda3 : start=167027805, size= 94350936, Id= 7
/dev/sda4 : start=261393615, size= 51183090, Id= f
/dev/sda5 : start=261393741, size= 20964699, Id=83
/dev/sda6 : start=282358566, size= 25736004, Id=83
/dev/sda7 : start=308094633, size=  2104452, Id=82
/dev/sda8 : start=310199148, size=  2377557, Id=82

```

---

### Post by SecretCode on 2009-12-31
Not sure how to do this from the command line, but launch gparted, right click the visible swap partition, and click 'swapoff' (if it's enabled)

---

### Post by SecretCode on 2009-12-31
Your edited pt looks fine. 

If you can't get past the 'currently in use' error, just use the --no-reread flag it suggests. You need to get this done!

Also ... Happy New Year!

---

### Post by TrevT93 on 2009-12-31
Okay, I'll do it all either tomorrow or tonight after the New Year's party.

Happy New Years to you too, and to anyone who might happen to come upon this thread and read this post!

---

### Post by TrevT93 on 2010-01-01
I just used "sudo swapoff -a" to turn off the swaps and it worked...

...that is, until sfdisk chimed in at the end of the partition structure I wanted it to use, saying:

```

New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *        63  21478904   21478842   7  HPFS/NTFS
/dev/sda2      21478905 167027804  145548900   7  HPFS/NTFS
/dev/sda3     167027805 261378740   94350936   7  HPFS/NTFS
/dev/sda4     261393615 312576704   51183090   f  W95 Ext'd (LBA)
/dev/sda5     261393741 282358439   20964699  83  Linux
/dev/sda6     282358566 308094569   25736004  83  Linux
/dev/sda7     308094633 310199084    2104452  82  Linux swap / Solaris
/dev/sda8     310199148 312576704    2377557  82  Linux swap / Solaris
Warning: partition 3 does not end at a cylinder boundary

sfdisk: I don't like these partitions - nothing changed.
(If you really want this, use the --force option.)

```

Just one last "I'm making sure" moment.

---

### Post by SecretCode on 2010-01-01
Since partition 3 isn't changing, I think it's safe to ignore that warning and use --force.

---

### Post by SecretCode on 2010-01-01
Any luck yet?

---

### Post by TrevT93 on 2010-01-01
Yeah, but...

GParted notes that the Xubuntu journal superblock is bad.  The Debian superblock is just fine, and mounting it works.

Worst comes to worst, I think my teacher can get me back my non-backed-up history notes.

Do tell me if you want to try something else, though.

---

### Post by SecretCode on 2010-01-01
Oh well. I suspect all bits of the partition table are now pointing to the right places. The sda5 superblock probably did get corrupted

> **TrevT93 said:**
> Do tell me if you want to try something else, though.

Hey - it's your data - your call!

If you want to keep on trying, try this: boot the live CD (or the Debian partition, I suppose) and enter
```
sudo dumpe2fs /dev/sda5 | grep Block size
sudo dumpe2fs /dev/sda5 | grep superblock
```
(Will probably give nothing.)

```
sudo fsck.ext4 /dev/sda5
```
(Will probably give an error)

```
sudo fsck.ext4 -b 32786 /dev/sda5
```

```
sudo fsck.ext4 -b 98304 /dev/sda5
```

---

### Post by TrevT93 on 2010-01-01
Let's keep going until Sunday night.  I'd like to see the return of all my precious data, if possible.

Don't count out your commands too soon:

```

ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sda5 | grep Block size
grep: size: No such file or directory
dumpe2fs 1.41.9 (22-Aug-2009)
ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sda5 | grep superblock
dumpe2fs 1.41.9 (22-Aug-2009)
  Primary superblock at 0, Group descriptors at 1-1
  Backup superblock at 32768, Group descriptors at 32769-32769
  Backup superblock at 98304, Group descriptors at 98305-98305
  Backup superblock at 163840, Group descriptors at 163841-163841
  Backup superblock at 229376, Group descriptors at 229377-229377
  Backup superblock at 294912, Group descriptors at 294913-294913
  Backup superblock at 819200, Group descriptors at 819201-819201
  Backup superblock at 884736, Group descriptors at 884737-884737
  Backup superblock at 1605632, Group descriptors at 1605633-1605633
ubuntu@ubuntu:~$ sudo fsck.ext4 /dev/sda5
e2fsck 1.41.9 (22-Aug-2009)
The filesystem size (according to the superblock) is 2620603 blocks
The physical size of the device is 2620587 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? yes

ubuntu@ubuntu:~$ sudo fsck.ext4 -b 32786 /dev/sda5
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext4: Bad magic number in super-block while trying to open /dev/sda5

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo fsck.ext4 -b 98304 /dev/sda5
e2fsck 1.41.9 (22-Aug-2009)
The filesystem size (according to the superblock) is 2620603 blocks
The physical size of the device is 2620587 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? yes

```There were a few times it asked me to abort, and so I did to see if you could use the feedback and make a decision from there.

Helpful at all?

---

### Post by SecretCode on 2010-01-02
Slight error in my typing there ... could you try
```
sudo dumpe2fs /dev/sda5 | grep 'Block size'
```The result is bound to be 4096.

But if the disk sector we're pointing at is recognised by 
```
sudo fsck.ext4 /dev/sda5
```then we have made progress!

Run that command again, but don't abort on the size error. However, if it offers to fix errors, say no.

We probably need to resize the filesystem:
```
sudo resize2fs -p
```
```
sudo resize2fs -p 2620603
```
Enter the first command. Try the second if the first reports an error. If they seem to work, run the fsck command again.

I'd prefer to check the filesystem before resizing it, but if fsck objects, it might be necessary to resize first.

---

### Post by TrevT93 on 2010-01-02
```

ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sda5 | grep 'Block size'
dumpe2fs 1.41.9 (22-Aug-2009)
Block size:               4096
ubuntu@ubuntu:~$ sudo fsck.ext4 /dev/sda5
e2fsck 1.41.9 (22-Aug-2009)
The filesystem size (according to the superblock) is 2620603 blocks
The physical size of the device is 2620587 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? no

/dev/sda5 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda5: 191661/655360 files (0.3% non-contiguous), 1572520/2620603 blocks
ubuntu@ubuntu:~$ sudo resize2fs -p
resize2fs 1.41.9 (22-Aug-2009)
Usage: resize2fs [-d debug_flags] [-f] [-F] [-M] [-P] [-p] device [new_size]

```

Block size is correct, but was I supposed to put /dev/sda or /dev/sda5 on the end of the resize2fs commands?  (Remember, I'm still a bit of a beginner!)

---

### Post by SecretCode on 2010-01-02
> **TrevT93 said:**
> Block size is correct, but was I supposed to put /dev/sda or /dev/sda5 on the end of the resize2fs commands?  (Remember, I'm still a bit of a beginner!)

Right - that would have been a good idea :)
sudo resize2fs -p /dev/sda5

---

### Post by TrevT93 on 2010-01-02
Sweet, the drive mounts again!

```

ubuntu@ubuntu:~$ sudo fsck.ext4 /dev/sda5
e2fsck 1.41.9 (22-Aug-2009)
/dev/sda5: clean, 191661/655360 files, 1572520/2620587 blocks
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda5 /media
ubuntu@ubuntu:~$ 

```

So then, is it time to reinstall GRUB2?  I know how to do it (having done it a few times before).

---

### Post by SecretCode on 2010-01-02
If you have an external drive, I would really like to recommend making a clone (using clonezilla or something like that) of the Xubuntu partition, and probably the important windows partitions.

What does your boot menu look like at the moment - is it Windows or grub? Can you boot into xubuntu? Or the debian install?

---

### Post by TrevT93 on 2010-01-02
I don't have anything other than my two flash drives...I think I'll just grab anything of importance and work with that.

The boot menu is Windows' own right now, but let me get a copy of Super Grub Disk going and see if I can't boot to Xubuntu from there...

---

### Post by SecretCode on 2010-01-02
Reinstalling grub2 should be safe now. You'll have to run it from the live cd and there are a couple of parameters to remember - see [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by TrevT93 on 2010-01-02
Thank you so much!  It seems as though my system is back the way it should be, almost as though none of this ever happened.  Xubuntu is back, it boots, it works, and I'm using Firefox on Xubuntu to get you this status report!

GParted is also reporting the right structure.

All right, mission accomplished!

You might find this crazy (and maybe a little funny), but now I'm about to more or less restructure the partitions on my drive again to do away with the old Windows 7 Beta partition, and probably remove Xubuntu to give it a little more space (you can't take free space before a partition and extend that partition using that free space, can you?).

---

### Post by SecretCode on 2010-01-02
Awesome! For a while I thought this wasn't going to work. 

Not crazy to repartition. I was thinking you should probably clean up the partitions once you've rescued your data - there may be still one or two oddities.

Just don't use Vista or W-Seven to do any of the partitioning - there are some rules that have changed, which tools like parted and testdisk are probably not up to date with - whereas it's safe to partition using gparted and then install windows (if you need to reinstall, that is). See [Multibooters, Vista Dual and Multibooting - Vista's New Partitioning Rules](http://www.multibooters.co.uk/partitions.html).

If your budget will extend to an external hard drive, even 160GB / 250GB, that would be incredibly useful for making partition clones to avoid future data loss.

> **TrevT93 said:**
> (you can't take free space before a partition and extend that partition using that free space, can you?)

Actually you can ... although you'll need a few steps.

After deleting the wseven partition (sda3?) you'll have to move and resize the extended partition (sda4) to the left. Then you could move and resize the xubuntu partition (sda5) within the extended partition. It might take tens of minutes, even hours, but you could give it a try and if it takes too long abort it and create new partitions and do a fresh install.

Or you could clone the xubuntu partition to an external drive, create new  partitions as required and restore the image into the new larger partition. If you had an external drive.

---

### Post by TrevT93 on 2010-01-07
Just to check in, all's well, my old WSEVEN partition has been successfully deleted and overwritten with XUBUNTU's data.  The hard disk has been greatly freed up so that I have room for experimenting with other Linux distros.  And the only casualty of this fiasco was a saved game from Secret Maryo Chronicles (which, to be honest, is a very small price to pay!).

Thanks for all the help, I don't know what I would have done without you!

(I marked the thread SOLVED.)

---

### Post by SecretCode on 2010-01-08
Good news, and no problem!

---

