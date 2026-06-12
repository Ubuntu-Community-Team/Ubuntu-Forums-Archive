---
title: "Can't access 2nd hard drive after install"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by merlinus23 on 2010-05-31
After not listening to the age old advice of making a back up before proceeding I lost my Windows 7 OS after trying to install a duel boot of Win 7 and Ubuntu.  My 2 identical hard drives were in a RAID (Stripe) configuration and I was trying to install Ubuntu to my second hard drive.  After failing at this a couple of times I reconfigured my hard drives as IDE drives and was able to install Ubuntu 10.04 to the second drive.  The installation went well and since I was a complete newbie at Linux I explored Ubuntu for a couple of days before trying to reinstall a fresh installation of Windows 7 with my HP recovery disks and a Windows 7 upgrade disk.  After my Windows 7 reinstall on my first drive I am totally unable to access my second drive.  I tried to use mbrfix on the drive from the command line but I just get an error message stating "drive not ready". :confused:

---

### Post by darkod on 2010-05-31
Few points, for some of them it's too late:

1. You don't install ubuntu on RAID with the standard desktop cd (live cd). You use the Alternate Install CD (image).

2. Windows can't see linux and does not offer a way to boot it. It seems your grub2 bootloader was on the first disk, not on the ubuntu disk, and installing win7 now overwrote it.

You should be able to fix that by simply reinstalling grub2 to the ubuntu disk MBR. It takes only two commands run from ubuntu live mode (the cd booted in Try Ubuntu mode).

However, to make sure this is the case, boot into live mode and run the boot info script and post the results as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by merlinus23 on 2010-05-31
I know i really messed up but I appreciate your quick response.  Here are the results.

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOT/BCD

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders, total 703282608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   682,719,231   682,719,169   7 HPFS/NTFS
/dev/sda2         682,719,232   703,279,103    20,559,872   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 360.1 GB, 360080695296 bytes
255 heads, 63 sectors/track, 43777 cylinders, total 703282608 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        58BA438DBA43669A                       ntfs       HP                            
/dev/sda2        DA86472F86470B87                       ntfs       FACTORY_IMAGE                 
/dev/sda: PTTYPE="dos" 
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf

---

### Post by darkod on 2010-05-31
You can see yourself, there are 2 partitions listed under /dev/sda but no partitions for /dev/sdb.
Are you sure the win7 "install" didn't wipe all disks, including the ubuntu disk? Unfortunately, in the past few years, more and more restore partitions/CDs are designed to wipe everything, and create the factory setup on your computer.

If you open in win7 Disk Management, does it show the second disk with partitions or fully unallocated?

PS. I asked about Disk Management info because even though windows can't recognize linux and offer to boot it with its bootloader, it will still see the partitions usually with correct size, but reported as unknown type, or similar. The script seems to say you have no partitions on /dev/sdb, the second disk. If Disk Management says the same, I guess it's safe to assume the win7 restore process wiped everything out.

---

### Post by merlinus23 on 2010-05-31
Again, thanks for your quick reply.  You were right, Windows Disk Management showed the drive as totally unallocated.  I was able to use disk management to create a new volume and now it shows up in windows.  Will i be able to use the live CD now to reinstall Ubuntu on the second drive or do i need to use another method.

---

### Post by darkod on 2010-05-31
> **merlinus23 said:**
> Again, thanks for your quick reply.  You were right, Windows Disk Management showed the drive as totally unallocated.  I was able to use disk management to create a new volume and now it shows up in windows.  Will i be able to use the live CD now to reinstall Ubuntu on the second drive or do i need to use another method.

If you plan to install ubuntu on it, actually creating a partition on the whole disk is a mistake. While it's still empty (I guess), go back in Disk Management and delete that partition. Then create a partition with the size you want for ntfs, leave the rest as unallocated for ubuntu. You can't create partitions for linux in windows.

Depending how you want to plan your disks and partitions, I recommend giving ubuntu at least 30-35GB, even more if you can. If you plan to keep large videos/music/photos there, you need even more.

I suggest you allocate lets say 50GB for ubuntu. So, create a ntfs partition on the second disk which is 360GB - 50GB. On that partition you can keep data which you can "see" from both windows and ubuntu. Leave the 50GB as unallocated.

Restart and go into BIOS, and set the ubuntu disk to be first option in hdd boot options (that way you will be able to keep windows bootloader on the windows disk). Boot with the ubuntu cd, and start the installer. In step 4 tell it to Use Largest Available Free space option. It will install into the 50GB unallocated space.

In that step you can see one color bar on top, and one on bottom. The one on bottom shows you how the disk will look after the procedure. If it looks weird, cancel the install process until you figure things out.

In the last screen of the install, click the Advanced button and double check the bootloader (grub2) to go to the same disk, note the name of the disk in step 4. Lets say /dev/sdb. So make sure grub2 goes to /dev/sdb. It should not have a number in it, a number means partition.

That's it. It sounds like a lot written like this but actually it's pretty straightforward.

---

### Post by merlinus23 on 2010-05-31
I did what you suggested and it worked fine except that when I clicked on the restart button the system hung and I had to shut it down with the power button.  When I restarted my system it opened into the grub boot menu but all that it showed was 4 options for Linux.  Two for Linux and two for Linux with mem test.  There was no option for Win 7.   Is there a way of removing the two extra options on menu and adding one for Win 7.

---

### Post by darkod on 2010-05-31
Hmmm... win7 should have been detected.

Can you boot ubuntu and in terminal try:

sudo update-grub

See if that reports it as found. The additional ubuntu entries are recovery mode entries, usually they should be kept around if the normal mode entry fails.

The memtest you can remove from the grub menu with:

sudo chmod -x /etc/grub.d/20_memtest86+
sudo update-grub

---

### Post by merlinus23 on 2010-05-31
The update grub command worked perfectly.  Thanks for everything. :)

---

