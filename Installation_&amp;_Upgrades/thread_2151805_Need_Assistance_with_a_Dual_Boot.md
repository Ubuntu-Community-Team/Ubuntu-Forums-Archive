---
title: "Need Assistance with a Dual Boot"
date: 2013-06-05
forum: Installation &amp; Upgrades
---

### Post by parkernathan on 2013-06-05
I'm running into a little ordeal and I'm hoping the community can assist. 

I'm attempting to dual boot Windows and Ubuntu on the same machine.

I have just performed a clean install of Windows.

However, instead of the normal process where Ubuntu detects Windows and offers to run them side by side, Ubuntu is not detecting Windows and is asking me to either wipe my drive entirely clean, or something else, where I can specify how and where I wish to install Ubuntu.

Here's the details of my setup:

Hardware is VIA Artigo A1250 (see [http://www.viaembedded.com/en/products/systems/1990/1/ARTiGO_A1250_(Pico-ITX).html)](http://www.viaembedded.com/en/products/systems/1990/1/ARTiGO_A1250_(Pico-ITX).html)). It's a cute little machine and will give me a lot of Windows and Ubuntu power in a tiny little box.

Hard drive is Samsung SSD 840 Series 500 GB.

Windows OS is Windows 7 Professional 64 Bit (I have the ability to upgrade to 8 Pro if need be).

Ubuntu OS is Ubuntu (Christian Edition) 12.04 LTS 64 Bit.

I created two partitions when installing Windows (basically splitting my drive in half).

Here's where the issue probably lies. My machine boots over EFI instead of a regular BIOS. So there's probably something I need to do to kick in the dual boot working with an EFI instead of a BIOS.

Here are screenshots of what I'm seeing at the Ubuntu installation (look at them from right to left, the order reversed when uploading them):

[ATTACH=CONFIG]243537[/ATTACH][ATTACH=CONFIG]243538[/ATTACH][ATTACH=CONFIG]243539[/ATTACH]

Here's a picture of my EFI boot screen (when I boot up and hold down delete):

[ATTACH=CONFIG]243540[/ATTACH]

I'd prefer to ditch dual booting and use virtualization, and while my processor supports hardware virtualization, the manufacturer hasn't fully baked it into the EFI, so I can only run VM's with a single processor at a time and very low video memory, which wouldn't do for my applications. I need Windows and Ubuntu to have the full power of the hardware.

Any help would be much appreciated.

Thanks a bunch!

---

### Post by ahallubuntu on 2013-06-05
~

---

### Post by fantab on 2013-06-06
also post the output of:

```
sudo parted -l
```

---

### Post by parkernathan on 2013-06-06
@allhallubuntu

I created the partitions using my Windows Installation CD. When I originally created them in GPARTED, Windows balked at it and gave me an error message about not being able to install on a GPT partition.

Here's the output of fdisk:

sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x21c408f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   512002047   255897600    7  HPFS/NTFS/exFAT
/dev/sda3       512002048   976771071   232384512    7  HPFS/NTFS/exFAT

I've just pulled up File Manager under Ubuntu off the Live CD, and the File Manager is seeing both partitions and all the Windows files.

I'm posting this message from the Live CD, but I'm getting pictures of all of this anhd will post them from my other machine shortly.

I formatted the other partition inside Windows after finishing the installation so it'd at least be a recognizable partition.

When I boot from GPARTED now,n GPARTED iis not seeing tw0 partitions. Only one glob of unalllocated space like the Ubuntu installer (screen shot coming).

@fantab

Here's the output of parted:

sudo parted -l
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No?               

This same message appears in GPARTED.

In Terminal, if I type yes, here's the output:

yes                                                               
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label

If I type no, here's the output:

no                                                                

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label

BTW, everything is a clean install and I have no personal data installed yet, so I can do anything need be to my drive.

Thanks again for all your help!

---

### Post by parkernathan on 2013-06-06
Here's what I see off the Ubuntu Live CD under file manager:

[ATTACH=CONFIG]243579[/ATTACH]

Here's what I see in GPARTED:

[ATTACH=CONFIG]243580[/ATTACH]

---

### Post by oldfred on 2013-06-06
It looks like drive was gpt, but you installed Windows in BIOS mode with MBR(msdos). Windows then converts to MBR, but does not delete the backup gpt partition table and Linux tools see both and get confused.

Both Windows & Ubuntu have to be both BIOS mode or UEFI mode to easily dual boot. If drive is MBR then you have to boot in BIOS mode. Windows only boots in UEFI mode from gpt drives. Or from gpt partitioned drives with UEFI.

You can remove the extra gpt data with fixparts, then gparted or installer should correctly see drive.
 Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by parkernathan on 2013-06-06
Sounds good. I'm chatting with the developer of FixParts to get the recommended method for doing this, then I'll give it a spin and see how it goes.

---

### Post by parkernathan on 2013-06-06
I think it's all going to kick in now and that's going to do the trick. Giving something else a spin first to ensure, then we'll see how it goes! I'll post an update here once I know for sure. Thanks a bunch for your help!

---

### Post by parkernathan on 2013-06-07
That did the trick! Thank you, Thank you, Thank you oldfred! I am so thrilled! 

BTW do I need to do something to mark this topic solved?

---

### Post by oldfred on 2013-06-07
Glad that worked. :)

See my signature for our temp workaround on Solved. We will be getting an add-in to our new vB4 forum "Real Soon Now" to make it easier.

---

