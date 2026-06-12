---
title: "Grub2 can't find windows XP"
date: 2012-10-12
forum: Installation &amp; Upgrades
---

### Post by marineBoy on 2012-10-12
Hi,
I upgraded to 12.04 Kubuntu (clean install) a couple of months ago and today needed to boot into my XP install to record some screencasts for work, but the entry (or menu) wasn't there.
I fixed the display of the menu but still no entry for XP.
The XP partition wasn't being mounted by default so I modified the fstab settings to fix that.
I've tried creating a custom entry in /etc/grub.d/40_custom with:

```
#menuentry "Microsoft Windows XP" {
    insmod part_msdos
    insmod ntfs
    insmod search_fs_uuid
    insmod ntldr
    set root '(hd0,1)'
    search --fs-uuid --no-floppy --set=root BE4C3C2F4C3BE0B7
    ntldr /ntldr
}
```
and 
```
menuentry "Microsoft Windows XP 2" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root '(hd0,1)'
    search --fs-uuid --no-floppy --set=root BE4C3C2F4C3BE0B7
    chainloader +1
}
```
and ran:
```
sudo grub-mkconfig
sudo update-grub2
```
but with no success.

There's two disks: sda with win xp, and sdb with 12.04.
My output from the boot info script is:
```

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and uses an 
    embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid f0926f11-4b43-49b6-a3e5-afac9aca9268 root 
    set prefix=($root)/grub
    ---------------------------------------------------------------------------
    -----.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sdb1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sdb5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 7998. But according to the info from fdisk, 
                       sdb5 starts at sector 1855868928.
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   155,171,834   155,171,772   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1          30,275,582 1,953,523,711 1,923,248,130   5 Extended
/dev/sdb5       1,855,868,928 1,953,523,711    97,654,784   7 NTFS / exFAT / HPFS
/dev/sdb6          47,364,096 1,855,860,735 1,808,496,640  83 Linux
/dev/sdb7          30,275,584    38,086,655     7,811,072  82 Linux swap / Solaris
/dev/sdb8          38,088,704    47,357,951     9,269,248  83 Linux
/dev/sdb2    *          2,048    30,273,535    30,271,488  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        BE4C3C2F4C3BE0B7                       ntfs       
/dev/sdb2        d4cc4d13-a68e-4e46-827c-8f935c849a5b   ext4       
/dev/sdb5        665023215022F787                       ntfs       
/dev/sdb6        96ed2045-5297-4f9c-9774-9fd6c363bc2b   ext4       
/dev/sdb7        dda0489b-322f-48ba-af3a-5ec0d495de58   swap       
/dev/sdb8        37ee0ab5-1453-44a7-b6ed-9cb652b605b2   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /mnt/Windows             fuseblk    (rw,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb2        /                        ext4       (rw,errors=remount-ro)
/dev/sdb6        /home                    ext4       (rw)
/dev/sdb8        /var                     ext4       (rw)

```


From the output it appears I might have grub installed to two locations. 
How do I fix this? I'm a little reluctant to bork the system further :)
And just to make life interesting, I don't have an XP disk, but I do have an XP to copy files off if necessary (I seem to recall you can copy boot sectors with a dd command?)

Regards,
Duncan

---

### Post by darkod on 2012-10-12
First of all, the XP partition doesn't need to be mounted for the dual boot to work. On the contrary, windows often doesn't like other OSs to touch its system partition, so you might as well undo the change in Gparted.

Yes, you have grub2 on both disks, and it might make a difference which are you booting. I would try booting the 1TB disk, the /dev/sdb, where ubuntu is. Go into bios and set it as first option.

The results are missing lots of info, either the script didn't produce it or you didn't paste all of it. But in any case, unless you have the automatic os-prober disabled, you don't need to bother with any custom entries, it will detect XP by itself.

So, make sure you boot from sdb, boot into ubuntu and run in terminal:
sudo update-grub

See whether that detects XP or not.

About your manual entries, the first one looks wrong, I don't know if you can boot XP with ntldr command. The second entry with chainaloder +1 looks correct, only the set root command needs to be:
set root=(hd0,1)

But anyhow, in a working grub2 situation you don't need any of this, as mentioned. See what the above suggestion will do and whether the update-grub will detect it.

---

### Post by YannBuntu on 2012-10-12
Please indicate your Boot-Info URL. [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
 This will provide relevant information to help you.

---

### Post by oldfred on 2012-10-12
Since you have multiple drives, you also need the drivemap command. The drive you boot is always hd0 in grub. But Windows has to see itself as hd0 so the drive locations have to be switched.

Add this just before the chainloader entry:

drivemap -s (hd0) ${root}


Also you should just install a Windows boot loader to the Windows drive. Boot-Repair can put syslinux boot loader which works just like the Windows boot loader (MBR only part of boot loader). Then you can also use BIOS to choose to boot the Windows drive with the one time boot key (f12 on my system).

---

### Post by marineBoy on 2012-10-14
@oldfred I've added the drivemap command so the entry now looks like:
```

menuentry "Microsoft Windows XP 2" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root=(hd0,1)
    search --fs-uuid --no-floppy --set=root BE4C3C2F4C3BE0B7
    drivemap -s (hd0) ${root}
    chainloader +1
}

```

On booting from the second hard disk and trying to boot win xp I get an error
```
Error: not an assignment
press any key to continue

```
but it will then boot.

From this [thread]("http://ubuntuforums.org/showthread.php?t=2000951"), post 7 I also seem to have some raid entries left over:
```
sudo dmraid --raid_devices -v
INFO: RAID device discovered:

/dev/sda: ddf1, ".ddf1_disks", GROUP, ok, 155189248 sectors, data@ 0

```

but trying to remove the raid entry gives errors:
```
sudo dmraid -Er /dev/sda
Do you really want to erase "ddf1" ondisk metadata on /dev/sda ? [y/n] :y
ERROR: ddf1: seeking device "/dev/sda" to 40959999737856
ERROR: writing metadata to /dev/sda, offset 79999999488 sectors, size 0 bytes returned 0
ERROR: erasing ondisk metadata on /dev/sda

```

So, it looks I've found the reason why os_prober is ignoring the windows drive (It's a second user system that was a server in a previous life).

If anyone knows how to get rid of the old raid entry that would be great, otherwise, I can live with it, especially considering how often I boot into windows anyway :)

---

### Post by oldfred on 2012-10-14
the command I have for removing RAID meta-data:

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

---

