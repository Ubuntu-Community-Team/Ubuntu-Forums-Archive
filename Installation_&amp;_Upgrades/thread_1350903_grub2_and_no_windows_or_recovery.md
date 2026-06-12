---
title: "grub2 and no windows or recovery"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by busmechanic on 2009-12-09
Installed 9.10 it has grub 2 running but I can not access windows xp or the recovery partion to restore to orginal from factory that one says missing ntldr missing and if I choose windows all i get is a black screen with a cursor blinking.

been all over looking for a fix, Sure are a lot of problems with the new grub 2

here is my results 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11a8ba38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         638     5117994   12  Compaq diagnostics
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         638       16764   129538455    7  HPFS/NTFS
/dev/sda3           16765       19457    21631522+   5  Extended
/dev/sda5           16765       19339    20683656   83  Linux
/dev/sda6           19340       19457      947803+  82  Linux swap / Solaris

Disk /dev/sdb: 1031 MB, 1031798784 bytes
16 heads, 32 sectors/track, 3936 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0xe6675836

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3936     1007600    b  W95 FAT32
  

and BLkid

/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="PQSERVICE" UUID="0159-6699" TYPE="vfat" 
/dev/sda2: UUID="0CD46CB3D46CA126" LABEL="ACER" TYPE="ntfs" 
/dev/sda5: UUID="6a44755a-fa01-4210-bd23-eb4592024c30" TYPE="ext4" 
/dev/sda6: UUID="12ad9f7c-46b6-4537-8d06-9fa0e9393705" TYPE="swap" 
/dev/sdb1: UUID="1C0A-E4A7" TYPE="vfat" 


Thanks for any help with this

---

### Post by shredder12 on 2009-12-10
Have you tried reinstalling grub2 using live CD.
try this [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If this problem is because of grub2 this should resolve it.

---

### Post by busmechanic on 2009-12-10
I think I have tried every suggestion out there I would like to find one just one thread that details a sussuccfull work around, I am still plugin have been trying suggestions from another thread that darkod is working on too.

---

### Post by presence1960 on 2009-12-10
> **busmechanic said:**
> I think I have tried every suggestion out there I would like to find one just one thread that details a sussuccfull work around, I am still plugin have been trying suggestions from another thread that darkod is working on too.

your fdisk & blkid output are no where near enough to hopefully diagnose your problem. 

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by busmechanic on 2009-12-11
I scrubed the entire Project going back to windows for now until they get this GRUB 2 fixed.

---

### Post by darkod on 2009-12-11
> **busmechanic said:**
> I scrubed the entire Project going back to windows for now until they get this GRUB 2 fixed.

You have to be careful with blaming only grub2. While it may be the issue, there is also the possibility of the recovery partition creating confusion. Some computer manufacturers even modify the bootloader to include an entry for their partition, etc. Also, recently it turned out that some HP tools actually slice part of the MBR and destroy part of grub2 with that. Some sort of autorepair windows boot tool which doesn't even ask you if anything is wrong. As if you should have no other OS than windows.
These manufacturers put loads of stuff you don't even know on there, unfortunately. Not to mention that those recovery partitions destroy the whole hdd data and recreate it like coming from factory. You would call that nice solution? You pay for win license and you don't even get media to reinstall your system without the recovery partition procedure wiping all your data. And do you have a choice? Did they ask you if you prefer windows media or recovery partition?
I am running grub2 just fine on both my desktop and netbook.

---

### Post by presence1960 on 2009-12-11
> **darkod said:**
> You have to be careful with blaming only grub2. While it may be the issue, there is also the possibility of the recovery partition creating confusion. Some computer manufacturers even modify the bootloader to include an entry for their partition, etc. Also, recently it turned out that some HP tools actually slice part of the MBR and destroy part of grub2 with that. Some sort of autorepair windows boot tool which doesn't even ask you if anything is wrong. As if you should have no other OS than windows.
These manufacturers put loads of stuff you don't even know on there, unfortunately. Not to mention that those recovery partitions destroy the whole hdd data and recreate it like coming from factory. You would call that nice solution? You pay for win license and you don't even get media to reinstall your system without the recovery partition procedure wiping all your data. And do you have a choice? Did they ask you if you prefer windows media or recovery partition?
I am running grub2 just fine on both my desktop and netbook.

I hear you Darko. But let busmechanic go his merry way. He claims to have tried all sorts of solutions, but in here his post count is 4. At least with us in this community he didn't try at all as far as I am concerned. He didn't even take the time to download and run the script. People like that I don't waste my precious time on them. There are plenty others who want help and are willing to try things to fix their issues and maybe learn about Linux in doing so.

**_The above is my opinion and not necessarily fact_**

---

### Post by darkod on 2009-12-12
> **presence1960 said:**
> I hear you Darko. But let busmechanic go his merry way. He claims to have tried all sorts of solutions, but in here his post count is 4. At least with us in this community he didn't try at all as far as I am concerned. He didn't even take the time to download and run the script. People like that I don't waste my precious time on them. There are plenty others who want help and are willing to try things to fix their issues and maybe learn about Linux in doing so.

**_The above is my opinion and not necessarily fact_**

Thanks. That was more for other people stumbling upon the thread in future searches because "until they get grub2 fixed" sounded really bad and it would make me worried if I read it somewhere.

---

### Post by shredder12 on 2009-12-14
> **presence1960 said:**
> I hear you Darko. But let busmechanic go his merry way. He claims to have tried all sorts of solutions, but in here his post count is 4. At least with us in this community he didn't try at all as far as I am concerned. He didn't even take the time to download and run the script. People like that I don't waste my precious time on them. There are plenty others who want help and are willing to try things to fix their issues and maybe learn about Linux in doing so.

**_The above is my opinion and not necessarily fact_**

Well said ...

---

### Post by dj4mc on 2009-12-14
Hey guys I am on sort of the same fix. I am building a new PC and am at the point I can wipe the whole thing if needed. Here is where I am:
Loaded Win 7, split the partition of main drive (1T) into an additional 500 gig for Ubuntu, loaded 9.10 and while doing so partitioned out from the new partition a scratch disk of 24 gig. Then set the install to use the 470ish gig partition, formated it for ext3 and load onto that. I know it all worked because I can boot back in to the Live CD and see all the drives and partitions (with data) post install etc. I lost or misplaced the boot loader. After switching to boot from HD, it comes up and just says GRUB. I can't type a command or anything. I don't really care which boot loader I use and I just figured out that GRUB2 exists. Should I recover from Win 7 and reinstall the MBR or slug it out on GRUB2? (I know I dont have a lot of posts but I am persistent and like a good challenge, you learn from them)

Thanks!

---

### Post by presence1960 on 2009-12-14
> **dj4mc said:**
> Hey guys I am on sort of the same fix. I am building a new PC and am at the point I can wipe the whole thing if needed. Here is where I am:
Loaded Win 7, split the partition of main drive (1T) into an additional 500 gig for Ubuntu, loaded 9.10 and while doing so partitioned out from the new partition a scratch disk of 24 gig. Then set the install to use the 470ish gig partition, formated it for ext3 and load onto that. I know it all worked because I can boot back in to the Live CD and see all the drives and partitions (with data) post install etc. I lost or misplaced the boot loader. After switching to boot from HD, it comes up and just says GRUB. I can't type a command or anything. I don't really care which boot loader I use and I just figured out that GRUB2 exists. Should I recover from Win 7 and reinstall the MBR or slug it out on GRUB2? (I know I dont have a lot of posts but I am persistent and like a good challenge, you learn from them)

Thanks!

I need more specific info before I can tell you what needs to be done.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by goldfish88 on 2009-12-14
presence1960,

Do you mind taking a look at my setup?

I royally messed up Ubuntu by deleting a bunch of things. (*zlib1g-dev, zlib1g, libpng and tcl/tk)*

I'm loading into Ubuntu via the live cd and trying to install grub from scratch.
No luck so far and I'm pretty bummed about it as I've tried quite a few codes

My initial setup was via Wubi and I think that might be giving me some difficulty as folders are probably tossed all over the place. Here are my results. Thanks for any help!

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   173,871,494   173,871,432   7 HPFS/NTFS
/dev/sda2    *    173,871,495   315,179,234   141,307,740   7 HPFS/NTFS
/dev/sda3         800,792,055   976,768,064   175,976,010   7 HPFS/NTFS
/dev/sda4         315,179,235   800,792,054   485,612,820  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="01361EFE1761BEF4" TYPE="ntfs" 
/dev/sda2: UUID="113E8BBE7E8421D4" TYPE="ntfs" 
/dev/sda3: UUID="2AD79922521B5ECC" TYPE="ntfs" 
/dev/sda4: UUID="41e10733-1124-46a3-aaf0-fb3b93790026" TYPE="ext2" 

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


================================== sda1Wubi: ==================================

Operating System: "Ubuntu 9.10"

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by presence1960 on 2009-12-14
> **goldfish88 said:**
> presence1960,

Do you mind taking a look at my setup?

I royally messed up Ubuntu by deleting a bunch of things. (*zlib1g-dev, zlib1g, libpng and tcl/tk)*

I'm loading into Ubuntu via the live cd and trying to install grub from scratch.
No luck so far and I'm pretty bummed about it as I've tried quite a few codes

My initial setup was via Wubi and I think that might be giving me some difficulty as folders are probably tossed all over the place. Here are my results. Thanks for any help!

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /wubildr.mbr /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/disks/root.disk

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   173,871,494   173,871,432   7 HPFS/NTFS
/dev/sda2    *    173,871,495   315,179,234   141,307,740   7 HPFS/NTFS
/dev/sda3         800,792,055   976,768,064   175,976,010   7 HPFS/NTFS
/dev/sda4         315,179,235   800,792,054   485,612,820  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="01361EFE1761BEF4" TYPE="ntfs" 
/dev/sda2: UUID="113E8BBE7E8421D4" TYPE="ntfs" 
/dev/sda3: UUID="2AD79922521B5ECC" TYPE="ntfs" 
/dev/sda4: UUID="41e10733-1124-46a3-aaf0-fb3b93790026" TYPE="ext2" 

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


================================== sda1Wubi: ==================================

Operating System: "Ubuntu 9.10"

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

Your initial setup still is your setup. You do not have a dedicated partition with a linux installation. You have a partition sda4 which is a linux filesystem (ext2) but no OS is installed there.

Maybe I don't understand the question, what exactly are you trying to do?

---

### Post by goldfish88 on 2009-12-14
As I understand, my Linux installation is on sda1, Windows 7 is on sda2 and sda3.
I'm not sure why the script is concluding Windows is on all 3. Perhaps because sda1 is a ntfs or because I installed via Wubi?

I'm simply trying to recover my Ubuntu installation, as when I try to boot, it tells me I first need to load the kernel.

Im not even able to get into a command prompt or grub when booting normally, thus Im trying to install grub via the live cd.

Hope this helps.

---

### Post by presence1960 on 2009-12-14
> **goldfish88 said:**
> As I understand, my Linux installation is on sda1, Windows 7 is on sda2 and sda3.
I'm not sure why the script is concluding Windows is on all 3. Perhaps because sda1 is a ntfs or because I installed via Wubi?

I'm simply trying to recover my Ubuntu installation, as when I try to boot, it tells me I first need to load the kernel.

Im not even able to get into a command prompt or grub when booting normally, thus Im trying to install grub via the live cd.

Hope this helps.

Yes you used wubi. Unfortunately I know very little about wubi. Wubi is not meant to be a permanent installation, although I understand more people are trying to use it as such. Wubi is meant to be a trial period to see if you like Ubuntu before you commit to partitioning your hard disk. It is installed inside windows file system and as such has it's problems and quirks. I really wish I had something to help you but I do not. If you like Ubuntu I would suggest that you do a full, dedicated installation to a partition(s) on your hard disk rather than using wubi- just for the sheer fact of lack of support. There are some in here who know wubi, but most of us do not use it.

[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

P.S. when you used "initial setup" to me that implied there was at least a second setup. That is why I thought you tried to install Ubuntu to sda4.

---

### Post by goldfish88 on 2009-12-14
I wish I had not used Wubi although I did not have a physical Ubuntu cd at the time.

It does indeed feel like Ubuntu is installed as a stand alone. It was installed with Wubi although it was into its own partition that was already previously created.

I'd like to get it back working as I have some data in there

Thanks again

---

### Post by darkod on 2009-12-14
> **goldfish88 said:**
> I wish I had not used Wubi although I did not have a physical Ubuntu cd at the time.

It does indeed feel like Ubuntu is installed as a stand alone. It was installed with Wubi although it was into its own partition that was already previously created.

I'd like to get it back working as I have some data in there

Thanks again

And what exactly is your problem with wubi? You just posted results.txt and said look at my setup.
Is it the now already famous sh:grub prompt at boot when nothing is booting?

PS. I saw now, it's asking to load the kernel. But still, give us more info.

---

### Post by darkod on 2009-12-14
This is one of the ways to boot wubi manually, if the boot stops at command prompt only. Execute the commands one by one:

sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot

Your wubi is on /dev/sda1 so just use them as they are. It should allow you to boot into wubi. If the sh:grub was the issue, once you load wubi open terminal and execute:
sudo update-grub2

---

### Post by goldfish88 on 2009-12-14
> **darkod said:**
> And what exactly is your problem with wubi? You just posted results.txt and said look at my setup.
Is it the now already famous sh:grub prompt at boot when nothing is booting?

PS. I saw now, it's asking to load the kernel. But still, give us more info.

darkod,

The problem was caused by myself this time. Wubi is just making it difficult to fix or recover.

I did get the sh:grub problem when I first installed (last week) but I've been using Ubuntu fine until I decided to delete everything. (*zlib1g-dev, zlib1g, libpng and tcl/tk)*

When I boot Ubuntu I am prompted that I need to load the kernel first and it does not give me any option to put in any commands.

So now Im using the live cd trying to fix everything.

I thought a good start would be to get grub back, but I cant get it to work because I'm not sure which folder or sda to use.. ect..

---

### Post by darkod on 2009-12-14
> **goldfish88 said:**
> darkod,

The problem was caused by myself this time. Wubi is just making it difficult to fix or recover.

I did get the sh:grub problem when I first installed (last week) but I've been using Ubuntu fine until I decided to delete everything. (*zlib1g-dev, zlib1g, libpng and tcl/tk)*

When I boot Ubuntu I am prompted that I need to load the kernel first and it does not give me any option to put in any commands.

So now Im using the live cd trying to fix everything.

I thought a good start would be to get grub back, but I cant get it to work because I'm not sure which folder or sda to use.. ect..

If you installed wubi I don't think you can just use the standard grub recovery procedures like that. Remember, grub2 is not on your hdd MBR, it's just a virtual grub. You don't have grub at all in fact. With wubi ubuntu is virtual.
One option would be to check if the kernels are really in /boot folder. I'm not using wubi too, like Presence, and have no idea how to search for the files, just guesses. You need to find out what is the virtual /. Is it ubuntu/disks folder on the /dev/sda1 partition? If there is boot folder inside, check for the vmlinuz and initrd files.
Also, if wubi files are just put like that in the ubuntu folders, you can try to get your data from windows (if it's working ok). Depending what you need to get out, and whether the files are just saved there unpacked (as opposed to in one big disk image file), you might be able to pull it off.

---

### Post by goldfish88 on 2009-12-14
darkod, 

Thanks. Yes there is an ubuntu/disks folder in the sda1 partition, with a boot folder in there, and inside the boot folder there is a root.disk and swap.disk files as well as a grubs folder but the grubs folder is empty.

(ubuntu/disks/boot/grub)

Unfortunately, all my data seems to be packed into the Wubi installer or something so its not accessible.

I've followed the code in the first post here to install grub, but no luck.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by darkod on 2009-12-14
> **goldfish88 said:**
> darkod, 

Thanks. Yes there is an ubuntu/disks folder in the sda1 partition, with a boot folder in there, and inside the boot folder there is a root.disk and swap.disk files as well as a grubs folder but the grubs folder is empty.

(ubuntu/disks/boot/grub)

Unfortunately, all my data seems to be packed into the Wubi installer or something so its not accessible.

I've followed the code in the first post here to install grub, but no luck.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

That's procedure to restore grub1 not grub2, and for full ubuntu install. It would restore it to your MBR. I guess it's better that it didn't work.
As I said, almost all things in wubi is virtual. You're right, root.disk is your virtual / packed as an image, single file. So you can't access the kernels or folders inside.
And the virtual grub is I guess in wubildr.mbr which is on C: (I assume). Not sure if you can read that .mbr file, really not an expert on it.
Also, not sure if copying wubildr.mbr from another pc can help you. But it's worth a try.
Put wubi on another pc, get C:wubildr.mbr and put it on your pc. Before that rename your wubildr.mbr to keep it, do not delete it.

---

### Post by goldfish88 on 2009-12-14
darkod,

The wubildr.mbr file is only 8kb. Are you sure that I removed any info from there?

I think the damage was done in the .disk files.. but what do I know?

Should I attempt to install what I removed? ie. (*zlib1g-dev, zlib1g, libpng and tcl/tk)*

---

### Post by darkod on 2009-12-14
> **goldfish88 said:**
> darkod,

The wubildr.mbr file is only 8kb. Are you sure that I removed any info from there?

I think the damage was done in the .disk files.. but what do I know?

Should I attempt to install what I removed? ie. (*zlib1g-dev, zlib1g, libpng and tcl/tk)*

I didn't say you removed any files from there. My assumption is that the virtual grub2 is in there, and maybe that's why the name wubildr.mbr to simulate a hdd MBR.

---

