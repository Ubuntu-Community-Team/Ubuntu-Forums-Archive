---
title: "Dual boot Ubuntu and Windows 7 - does not detect disk!"
date: 2013-02-02
forum: Installation &amp; Upgrades
---

### Post by savishy on 2013-02-02
Hi all,

I have a Dell Inspiron 14z (5423) Ultrabook that came pre-installed with the stock Windows 7 64-bit.
For those that are unaware here is the way its setup:
[LIST]It has a 32GB mSATA cache + 500GB disk in a RAID configuration
[/LIST]
[LIST]Windows is pre-installed on the 500GB disk
[/LIST]
[LIST]The 32GB disk is all but invisible; it is merely for caching the operating system in such a way that the boot time reduces dramatically.
[/LIST]

I wanted to do the following: 
[LIST]replace the optical drive with a 128GB SSD
[/LIST]
[LIST]partition that into 90GB for Windows-7 64-bit, 30GB for Ubuntu 12.04 64-bit
[/LIST]
[LIST]Use the 500GB + 32GB for storage.
[/LIST]

I followed instructions on links such as [http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121). I was able to successfully install Ubuntu and Windows 7 on the SSD. The 500GB data drive is also visible.

*However, upon boot, the 128GB disk is not recognized!*
It loads a "grub rescue" prompt that does not recognize any commands. 
To fix this, every time I boot I have to press F12 and choose "boot from hard disk". It then shows the bootloader. 

**What I have tried**
[LIST]Try reordering the boot order in BIOS. Out of the available choices I have tried putting "HDD", "Second HDD", "CD/DVD drive" first. No luck.
[/LIST]

I am willing to clean-install Ubuntu if necessary, but not Windows 7 if possible. Lots of data there.

Ubuntu is crazy fast with the SSD, and I feel like I'm almost there! Any advice to fix this?

---

### Post by oldfred on 2013-02-02
Some of those have SSD's built into mother board. It is not really two drives.

Just to see what Linux sees. Install Boot-Repair to your live flash installer or DVD.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by savishy on 2013-02-02
Here is the Boot-Info:
[http://paste.ubuntu.com/1603365/](http://paste.ubuntu.com/1603365/)

Also, earlier I mentioned that it boots automatically to grub rescue. Here is the error:
```

error: no such device: ff50e06d-.....
grub rescue> set
prefix=(hd0,6)/boot/grub
root=hd0,6
```

And ff50 is the UUID of /dev/sdc6, as evidenced by ```
ls -l /dev/disk/by-uuid/
```

Looks like one problem is that there are two grubs and the wrong one gets loaded? I may have done some weird stuff during the initial stages of getting things to work. It was a while ago so I forgot exactly what I did.

---

### Post by serpantman on 2013-02-03
Could we get your grub config file.


There is no need to re-install a OS. Re-installing a boot loader might be easier. In which case i would recommend lilo. But post your config file and we will go from there.

---

### Post by savishy on 2013-02-03
> **serpantman said:**
> Could we get your grub config file.


Thanks for the reply. I am trying to learn as I go along; what's the thinking behind that? 

Also, am I correct when I wonder that maybe there are two grubs installed, and the wrong one gets loaded? 

Attached: foo.txt is my grub.cfg.

---

### Post by darkod on 2013-02-03
From other threads seen here, I think a disk installed into a dvd-rom is not sued to boot from. It all looks normal, but it can't boot a bootloader from it.

I suggest to try putting grub2 to another disk, like /dev/sda. Also, make sure the hdd and ssd, sda and sdb are separated, and you are not using them in any sort of special relationship like Intel SRT or similar.

Use the ubuntu cd in live mode in terminal try something like:
```
sudo mount /dev/sdc6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Then set in BIOS to boot from sda, the 500GB disk. And see how it goes.

The combination of hdd+ssd cache disk is usually configured as some sort of raid array. Depending how yours was configured and whether you did something about it, like disabling the raid setting in bios, you might also need to delete raid meta data from sda and sdb so that linux can correctly see them as separate and not as raid. From the bootinfo they do seem correctly recognized as separate, so you might not need to do anything about this.

---

### Post by savishy on 2013-02-03
> **darkod said:**
> From other threads seen here, I think a disk installed into a dvd-rom is not sued to boot from. It all looks normal, but it can't boot a bootloader from it.I suggest to try putting grub2 to another disk, like /dev/sda. 

@Darkod I think there is a grub2 installed in MBR of /dev/sda as well as the MBR of /dev/sdc. See the Boot-Info at [http://paste.ubuntu.com/1603365/](http://paste.ubuntu.com/1603365/)

> Also, make sure the hdd and ssd, sda and sdb are separated, and you are not using them in any sort of special relationship like Intel SRT or similar.


sda is the 500GB hard disk.
sdb is the 32GB mSATA SSD.
sdc is the 128GB SSD I replaced the opticaldrive with.

sda and sdb are indeed in Intel SRT, but my operating system is in Sdc. Do you think that affects matters?

---

### Post by darkod on 2013-02-03
I saw there is grub2 in /dev/sda but we have to make sure it is connected to /dev/sdc6, so running the above commands can't hurt.

Yes, I think Intel SRT can affect things. This is my logic:
1. Grub2 from /dev/sdc will not be able to boot because that disk is in a dvd caddy. We have seen that on other threads.
2. /dev/sda and /dev/sdb are shown separately by ubuntu and bootinfo, and there is grub2 on /dev/sda, but if the machine/bios considers the hdd+ssd as "one device" due to Intel SRT, it might not even try to boot the grub2 from /dev/sda correctly.

The above is only my assumption but I think it's worth considering.

First reinstall grub2 on /dev/sda with the commands I gave you and try booting from /dev/sda.

If that still doesn't work, you have to consider whether Intel SRT is affecting your boot process.

---

### Post by oldfred on 2013-02-03
In addition to Darko's comments so far.

You have installed grub2's boot loader to the Windows PBR or partition boot sector. Normally grub in not installed to a PBR and never to a NTFS PBR as that has to have Windows boot code. It has a backup that can be used to restore if only written once. Testdisk will say if backup is ok or not.

```
sdc1: _______________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sdc1 
                       and looks at sector 222239264 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos6)/boot/grub on this drive. No errors found 
                       in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

```

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:

[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
Also check for /boot/grub in addition to /Boot 
Since ntfs partitions are case insensitive this leads to confusions between "/boot" and the already existing folder "/Boot" 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

---

### Post by savishy on 2013-02-17
Hi darkod,

Sorry for going invisible without warning - got suddenly busy at work. 

I got some spare time again and did the following things:

> **darkod said:**
> I saw there is grub2 in /dev/sda but we have to make sure it is connected to /dev/sdc6, so running the above commands can't hurt.
* Disabled the RAID Coupling between the 32-GB SSD and the 500GB HDD through Windows. (This is possible using the Intel Rapid Storage Technology software package)
* I *did not change boot controller*. Currently it's set to "Intel RST", and if I change it to AHCI, I get blue-screens.
* I booted from an Ubuntu liveUSB and did the grub-install commands you mention. This did not work, i.e I saw the same behavior as earlier.

> 
If that still doesn't work, you have to consider whether Intel SRT is affecting your boot process.

At this point I have to consider that this could be an issue.

So, any next steps?
* I am willing to reinstall my Ubuntu if needed - will that help?

---

### Post by oldfred on 2013-02-17
The drive still retains RAID meta-data.
        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it. 

       
 sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

    > 

You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.
    

---

