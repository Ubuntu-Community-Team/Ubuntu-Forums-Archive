---
title: "Stuck on live cd second hdd install"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by twogeo on 2009-11-19
Howdy,

My aim is to install Karmic from the desktop live cd on logical partitions on sdb, to dual boot with an existing XP install that occupies the whole of sda.

Both hdds are recognised by the BIOS and boot priority has sda listed first.
I've partitioned sdb using GParted from the live cd already.

The complication is that I've previously run a play dual-boot install of Win7 on sdb to alternate with the existing XP on sda, then used the Win FIXMBR routine to restore the XP MBR and, as I'd thought, formatted sdb and removed all the Win7 traces.

Sadly, no ;-)  The auto partitioning routine of the Karmic install cd tells me that I have only sda and that is a Win 7 (loader) occupied space.
The advanced partitioner sees both hdds and recognises sda as ntfs but doesn't flag it as the boot disc.
It does see the extended partition that I've created on sdb.
So, I've backed out before installing to find out what kind of precautions I can take before following my dumb instinct that installing on sdb will probably work if I can work out how to get grub installed properly.

Here follows the output of the Boot Info Script
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d97d2

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   488,375,999   488,375,937   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x287d9874

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   5 Extended
/dev/sdb5                 126    40,965,749    40,965,624  83 Linux
/dev/sdb6          40,965,813   204,812,684   163,846,872  83 Linux
/dev/sdb7         204,812,748   209,310,884     4,498,137  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="B0282039281FFCCA" TYPE="ntfs" 
/dev/sdb5: UUID="a06b159d-c06e-45cf-b57e-0034f66c3a7f" TYPE="ext4" 
/dev/sdb6: UUID="446eb26e-3701-4928-80ef-0474298aa4ec" TYPE="ext4" 
/dev/sdb7: LABEL="swap" UUID="0e1aaea8-a133-4a2e-9fd3-973540fe80cf" TYPE="swap" 

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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /NOEXECUTE=OPTIN /FASTDETECT /USEPMTIMER
```
As far as I can see, I have no way of using the live cd install routine to install grub on sda1.
Can I please have a hand with how to install grub to achieve a dual-boot between Karmic on sdb and XP on sda - without having to go the path of a new XP install?

---

### Post by darkod on 2009-11-19
The easiest solution would be to install grub2 on sdb. Note, not on the partition sdb1 but on the MBR, sdb. Then switch the boot disk order in BIOS to have sdb as the first option. Grub2 will pick up your XP installation and create the appropriate entry.

I am no expert in dual booting two win installations, but from the info you supplied I think you should be able to safely delete som files from sda1 that confuse Ubuntu.

If you are sure you restored sda MBR with WinXP disc and not Win7, then what I guess happened is:
The MBR got written with XP mbr info, the sda1 boot sector info clearly states that. But in the boot files list you have both boot.ini and ntldr, used by XP, and /bootmgr and /boot/bcd used by 7. My guess is you could safely delete bootmgr and boot/bcd anyway because you have XP there. But DOUBLE CHECK  that on google or windows forums.

As I said, installing grub2 on sdb would be fine anyway, regardless of what type of boot sector you have on sda. Just don't forget to tell bios to look at sdb first.
With multiple drives you can select where you want grub2 installed on the last screen of the ubuntu installer, just before you click Install. There is button Advanced and that will give you the option to select /dev/sdb.

PS. It is possible that having both boot.ini and bootmgr on sda will confuse grub2 when creating the entries. That's what I hate about win, always doing it the wrong way. So what if you had dual boot of xp/7, after you restored mbr with xp then /bootmgr and /boot/bcd should be gone. I would really google around whether it's safe to delete those files before starting the ubuntu install. It will help ubuntu pick up just XP.

---

### Post by twogeo on 2009-11-19
> **darkod said:**
> 
With multiple drives you can select where you want grub2 installed on the last screen of the ubuntu installer, just before you click Install. There is button Advanced and that will give you the option to select /dev/sdb.

Aha!  That's the missing info.  I'm very grateful for your comprehensive reply.

> PS. It is possible that having both boot.ini and bootmgr on sda will confuse grub2 when creating the entries. That's what I hate about win, always doing it the wrong way. So what if you had dual boot of xp/7, after you restored mbr with xp then /bootmgr and /boot/bcd should be gone. I would really google around whether it's safe to delete those files before starting the ubuntu install. It will help ubuntu pick up just XP.Shall definitely research that before going ahead.  I'm also betting that the 2 orphan files are the culprits.
Thanks once again.  Shall return with whatever results I achieve. I really hope that this is going to be my last Win mess.

And please ignore the inappropriate icon at the header of this post; I didn't intend it. I'm still an IRC baby and often miss seeing all the bells and whistles in these new-fangled web2 places ;-)

Update:  Analysis correct darkod.  Found via MS fora that the Boot *directory* and bootmgr *file*, both in XP's root directory, are left-overs from Win7 dual-booting, having been placed there by the Win7 boot manager,  and needing changes of permissions from within XP to be deleted - not even Safe Mode running would allow them to be touched.
One more count against MS's attitude is that my XP is a Home version, with my needing to boot into the live cd to turf them out - - relaxing the NT Simple File Sharing settings isn't possible without the XP Pro network admin tools - hrmmpf.  
Posting now from a faultlessly dual-booting Karmic/XP:  Grub is on sdb as you advised, the live cd installer's routine correctly id'd XP once the two Win7 files were deleted.
It would be nice to see the Grub install options just a tad more prominent than that very quiet Advanced button on the last install screen though.  :-)

---

