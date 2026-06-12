---
title: "Windows disappeared..."
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by Azotus on 2009-12-16
I'm having a problem getting dual boot to work on my machine, plus I'm new to Ubuntu. I have Windows 7 64-bit installed on a machine and I've partitioned the drives and installed Ubuntu 9.10 64-bit, that all worked fine. When I restart and the grub menu loads it only shows the Ubuntu OS and not Windows. I've checked and the Windows partition is still available but it seems that the Ubuntu install did not recognize the Windows OS on the other partition. Is there a change I can make to get the windows os to show in the grub menu?

---

### Post by ers11121 on 2009-12-16
Inital boot screen should have option to boot Windows, yoy should be able to scroll down to it, if you get back into windows Download EasyBCD that should be able to reset the boot order
Ed

---

### Post by darkod on 2009-12-16
Download the script from my signature, move it to desktop for example and run it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with lots of info about your boot process. Copy the content of that file here and please wrap it in CODE tags (with the text sepected hit the # button in the toolbar above).

---

### Post by Azotus on 2009-12-16
I believe this is the relevant part. I should also note that sdb is a back-up of sda.

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda2 starts at sector 1090877760.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: /dev/sda5 already mounted or sda5 busy

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdb2 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb2 starts at sector 1090877760.
    Mounting failed:
fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: /dev/sdb5 already mounted or sdb5 busy

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2568b488

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   978,233,343   978,231,296   7 HPFS/NTFS
/dev/sda2       1,090,877,760 1,953,503,999   862,626,240   7 HPFS/NTFS
/dev/sda3         978,246,045 1,090,877,759   112,631,715   5 Extended
/dev/sda5         993,202,560 1,090,877,759    97,675,200  83 Linux
/dev/sda6         978,246,171   993,186,494    14,940,324  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2568b488

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   978,233,343   978,231,296   7 HPFS/NTFS
/dev/sdb2       1,090,877,760 1,953,503,999   862,626,240   7 HPFS/NTFS
/dev/sdb3         978,246,045 1,090,877,759   112,631,715   5 Extended
/dev/sdb5         993,202,560 1,090,877,759    97,675,200  83 Linux
/dev/sdb6         978,246,171   993,186,494    14,940,324  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="5C6EB7456EB7172C" LABEL="Windows 7" TYPE="ntfs" 
/dev/sda2: UUID="1E10A4F466330945" LABEL="Storage" TYPE="ntfs" 
/dev/sda5: UUID="730fe46e-529a-4a5d-974c-1a71cc7607b2" TYPE="ext4" 
/dev/sda6: UUID="aafc4b15-6149-49a9-b111-15cf77b76c1e" TYPE="swap" 
/dev/sdb1: UUID="5C6EB7456EB7172C" LABEL="Windows 7" TYPE="ntfs" 
/dev/sdb2: UUID="1E10A4F466330945" LABEL="Storage" TYPE="ntfs" 
/dev/sdb5: UUID="730fe46e-529a-4a5d-974c-1a71cc7607b2" TYPE="ext4" 
/dev/sdb6: UUID="aafc4b15-6149-49a9-b111-15cf77b76c1e" TYPE="swap" 
/dev/mapper/isw_dajbhgijge_Volume01: UUID="5C6EB7456EB7172C" LABEL="Windows 7" TYPE="ntfs" 
/dev/mapper/isw_dajbhgijge_Volume02: UUID="1E10A4F466330945" LABEL="Storage" TYPE="ntfs" 
/dev/mapper/isw_dajbhgijge_Volume05: UUID="730fe46e-529a-4a5d-974c-1a71cc7607b2" TYPE="ext4" 
/dev/mapper/isw_dajbhgijge_Volume06: UUID="aafc4b15-6149-49a9-b111-15cf77b76c1e" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/mapper/isw_dajbhgijge_Volume05 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/azotus/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=azotus)

=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

---

### Post by darkod on 2009-12-16
Are you running raid?

---

### Post by Azotus on 2009-12-16
Yes I am.

---

### Post by darkod on 2009-12-16
Did you install using the alternate install cd? For raid you need to use that cd.
Also, 9.10 should come with grub2 and on your drives you have grub1 (official version 0.97). The top of the results file clearly says grub 0.97 installed.
For grub1 you need to manually add windows entry in /boot/grub/menu.lst but I'm not sure how would it work with raid. Basically, after the ubuntu titles in menu.lst you need to add something like:

title Windows 7
rootnoverify (hd0,0)
savedefault
chainloader +1

But I'm not sure if modification for raid is needed in the above entry.

---

### Post by Azotus on 2009-12-16
I used the alternate CD for 64-bit. I did not see any options for a raid specific set-up.

I downloaded 9.10 yesterday, it is unclear to me why I would not have grub2. I can try your suggestion but if I would be better off reinstalling, I would rather do that.

---

### Post by darkod on 2009-12-16
> **Azotus said:**
> I used the alternate CD for 64-bit. I did not see any options for a raid specific set-up.

I downloaded 9.10 yesterday, it is unclear to me why I would not have grub2. I can try your suggestion but if I would be better off reinstalling, I would rather do that.

I can't really advise you for raid, I don't know enough about it. Actually I'm saving money for second hdd and then I'll play with raid myself. :)
If you used the alternate cd then maybe grub1 is used on it on purpose. I haven't used it and maybe it doesn't come with grub2.
If you are using the so called fakeraid (from motherboard onboard raid) look here, it might give you some ideas or something you missed:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

There is another option for ubuntu (you also need the alternate cd) called software raid, or softraid. In that case you create the identical partitions on both drives but actually ubuntu is creating the raid, a software raid. Some info here:
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

