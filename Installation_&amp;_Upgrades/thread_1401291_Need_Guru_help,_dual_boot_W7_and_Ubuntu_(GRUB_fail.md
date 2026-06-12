---
title: "Need Guru help, dual boot W7 and Ubuntu (GRUB fail issue)"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by d3mncln3r on 2010-02-07
Hey I posted this in the beginner forum, and I had someone give me a lot of time and help to try and install Ubuntu on my machine, but even after several days, we could not figure out the problem together. I thought I would ask in this forum because maybe it would get more exposure from an even more experienced user. For reference here is a link to the original post, though I will explain my problem in detail here. 

[http://ubuntuforums.org/showthread.php?t=1393066]("http://ubuntuforums.org/showthread.php?t=1393066")

I followed some advice on how to do a fresh install of windows 7 and ubuntu for a dual booting machine. The tutorial had me use Gparted to create partitions for each OS plus another one for storage space. GParted did not work for me, so I ended up partitioning using Windows 7.

I made one 20GB NTFS partition for W7, and one 20GB unformatted partition for Ubunutu, and another NTFS partition using the rest of my HD as my storage space.

Windows 7 installed fine and works smoothly with the storage space, but when I try to install ubuntu (using the live disc) it will get to 95% of the install and then fail due to a GRUB issue.

The user that was guiding me in the previous post helped me quite a bit and we did many things (much of which I didn't understand) but to no avail.

If someone out there wants to test their mettle, and help me on my way to becoming a happy ubuntu-W7 dual booter I would be very grateful!

I am happy to answer any questions, but much of the information is in the aforementioned post. Thanks in advance, can't wait to get this solved!

---

### Post by d3mncln3r on 2010-02-09
Hmm... no one wants to help tackle this problem? Somebody's got to know what they're doing out there.

---

### Post by drs305 on 2010-02-09
Just to point out to helpers, it looks like from the previous thread, you are using Grub legacy and RAID. Is that correct?

---

### Post by d3mncln3r on 2010-02-09
> **drs305 said:**
> Just to point out to helpers, it looks like from the previous thread, you are using Grub legacy and RAID. Is that correct?

Sadly, I couldn't tell you. I'm using Ubuntu 9.10 I downloaded the iso from the website, burned to a dvd and went from there.

---

### Post by darkod on 2010-02-09
Well, you can help with the raid part of the question. I also read the linked thread and it really seems you are running raid.
Wouldn't you know about that? Even if the computer came with raid without you setting it up, maybe you can see it in the specification or something.
It matters because you actually need to use different ISO for raid, called alternate install cd, as opposed to the standard desktop livecd.
In theory, you could manage with the desktop livecd too, but the alternate one is recommended for raid setup.

---

### Post by oldfred on 2010-02-09
Most of us (me included) do not know raid, that is more of a server configuration not a desktop. I believe the desktop install did not be default include grub raid add ins. You should be using the alternate install or a server install and add the gui after the install. There may be ways to use the desktop and add the extras for raid but I do not know.

---

### Post by oshunluvr on 2010-02-09
9.10 iso uses GRUB2. 9.04 uses GRUB-Legacy

I can't imagine why your having trouble with GPARTED unless you've got a bad burn. You did use the gparted bootable disk and not from a distro live cd right???

If you wish you can install GRUB-Legacy by downloading SuperGrubDisk and setting it up yourself.

Also - it's impossible to determine what's going wrong unless you post the exact (or nearly so) error messages you're getting.

---

### Post by darkod on 2010-02-09
PS. Fakeraid howto:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by d3mncln3r on 2010-02-09
Ok, I don't believe I am using RAID, if I am it is against my knowledge. What I do know is that my laptop uses two 115GB hard drives that acts as a single 230GB. Is that considered a RAID configuration? I thought this set up was pretty standard for laptops but maybe not. Here is a copy of the boot info script that I posted for the last helper, ```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/mapper/isw_dghcgdcbcb_Volume0
isw_dghcgdcbcb_Volume01: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

isw_dghcgdcbcb_Volume02: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

isw_dghcgdcbcb_Volume03: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

isw_dghcgdcbcb_Volume04: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, 
                       isw_dghcgdcbcb_Volume04 starts at sector 0. But 
                       according to the info from fdisk, 
                       isw_dghcgdcbcb_Volume04 starts at sector 81915435.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: isw_dghcgdcbcb_Volume0 ___________________ _____________________________________________________

Disk /dev/mapper/isw_dghcgdcbcb_Volume0: 240.1 GB, 240063348736 bytes
255 heads, 63 sectors/track, 29186 cylinders, total 468873728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x4138620b

Partition  Boot         Start           End          Size  Id System

/dev/mapper/isw_dghcgdcbcb_Volume01   *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/mapper/isw_dghcgdcbcb_Volume02            206,848    40,962,047    40,755,200   7 HPFS/NTFS
/dev/mapper/isw_dghcgdcbcb_Volume03         40,965,750    81,915,434    40,949,685  83 Linux
/dev/mapper/isw_dghcgdcbcb_Volume04         81,915,435   468,873,089   386,957,655   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/isw_dghcgdcbcb_Volume01 521AC5421AC523B7                       ntfs       System Reserved               
/dev/mapper/isw_dghcgdcbcb_Volume02 AA98E0D998E0A4D3                       ntfs                                     
/dev/mapper/isw_dghcgdcbcb_Volume03 9f397d66-fd8c-49bf-a3d8-d06ae5506496   ext4                                     
/dev/mapper/isw_dghcgdcbcb_Volume04 19794AB4737CD798                       ntfs       Storage                       
/dev/sda                                                isw_raid_member                               
/dev/sdb                                                isw_raid_member                               

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
isw_dghcgdcbcb_Volume0
isw_dghcgdcbcb_Volume01
isw_dghcgdcbcb_Volume02
isw_dghcgdcbcb_Volume03
isw_dghcgdcbcb_Volume04

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


====================== isw_dghcgdcbcb_Volume03/etc/fstab: ======================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/isw_dghcgdcbcb_Volume03 /               ext4    errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

========== isw_dghcgdcbcb_Volume03: Location of files loaded by Grub: ==========


  20.9GB: boot/initrd.img-2.6.31-14-generic
  20.9GB: boot/vmlinuz-2.6.31-14-generic
  20.9GB: initrd.img
  20.9GB: vmlinuz
```

I will copy the error message later when I try the install again tonight.

---

### Post by X-Rated on 2010-02-09
Hi, I can't say I'm a guru, but I'll try the best I can.
As already mentioned, I think you do have RAID running.
..................
[COLOR=Red]/dev/sda            isw_raid_member
/dev/sdb            isw_raid_member[/COLOR]
..................

 > What I do know is that my laptop uses two 115GB hard drives that acts  as a single 230GB. Is that considered a RAID configuration?

Yes, that is considered a raid config.

If you didn't setup raid then maybe it was setup in the bios. Check your system bios and see if raid is enabled on the motherboard.

If you are sure you don't have raid enabled, then sorry,  I don't know what the problem is, and I would have failed to increase my Ubuntu Guru status.

Otherwise, if you can confirm you are running raid, then you have 2 options.

Option 1) 
try to get ubuntu to boot from the raid array.  A link was provided in a previous post on how to do this. If it was me, I wouldn't bother with raid for your setup. It's not worth the headache. I would opt for option 2.

Option 2) 
disable the raid and run the disks as 2 separate disks.
Install Windows then Ubuntu on your first disk, use your 2nd disk as a data disk.

** but first, backup your important stuff.

---

### Post by Mark Phelps on 2010-02-10
> **d3mncln3r said:**
> ... What I do know is that my laptop uses two 115GB hard drives that acts as a single 230GB. Is that considered a RAID configuration? 

Yes -- that is a RAID configuration.  

And, as others have already mentioned, you need to use the Alternate CD to install to a RAID config,

---

