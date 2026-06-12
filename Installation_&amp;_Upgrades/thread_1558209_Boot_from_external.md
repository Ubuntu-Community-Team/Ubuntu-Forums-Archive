---
title: "Boot from external"
date: 2010-08-21
forum: Installation &amp; Upgrades
---

### Post by SplinteredChaos on 2010-08-21
I'm having some issues, and this is my first stop in trying to figure out a solution. My internal hard drive developed a problem (probably from a fall) and needs to be replaced. In the meantime I've decided to use my external hard drive to hold a version of Linux (ubuntu 10.04) until I am able to replace the internal hard drive. For some reason I am unable to get the external drive to accept the recovery disks I have for Windows 7, but that's for another forum, lol. 

What I'm having issues with is that after installing the Ubuntu OS on to the external, I reboot the PC and it tells me it cannot find a boot file, and won't load anything. I have to run the live cd version of the OS to get anything to work right.

Any thoughts?

---

### Post by earthpigg on 2010-08-22
hi,

is the old & semi-busted hard drive still plugged in?

if so, make sure that at the final step of the ubuntu install you select 'advanced' and tell it to put grub on the external hard drive.

---

### Post by presence1960 on 2010-08-22
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by SplinteredChaos on 2010-08-22
I'm running into a few snags with what was posted....I've downloaded the program and followed the instructions you mentioned, but when I first typed in sudo bash ~/Desktop/boot_info_script*.sh it did nothing. The site I downloaded the program from suggested a change in the command to 
su 
     bash ~/Desktop/boot_info_script*.sh

This proceeded to give me an error stating to either use sudo or "root". I 
tried to use "root", but the system said the program did not exist, but to 
type the command and it would install it. I did so, it runs in to an 
error E: Sub-process /usr/bin/dpkg returned an error code (1)....

HELP!!!

---

### Post by presence1960 on 2010-08-22
> **SplinteredChaos said:**
> I'm running into a few snags with what was posted....I've downloaded the program and followed the instructions you mentioned, but when I first typed in sudo bash ~/Desktop/boot_info_script*.sh it did nothing. The site I downloaded the program from suggested a change in the command to 
su 
     bash ~/Desktop/boot_info_script*.sh

This proceeded to give me an error stating to either use sudo or "root". I 
tried to use "root", but the system said the program did not exist, but to 
type the command and it would install it. I did so, it runs in to an 
error E: Sub-process /usr/bin/dpkg returned an error code (1)....

HELP!!!

You must be doing something incorrectly. This boot info script is widely used in our community. Start over. Download the boot info script. Once downloaded move it to the desktop. Then copy and paste this command into terminal ```
sudo bash ~/Desktop/boot_info_script*.sh
```Do not type the command- copy and paste it from here.

---

### Post by SplinteredChaos on 2010-08-22
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda1 starts at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320044269568 bytes
255 heads, 63 sectors/track, 38909 cylinders, total 625086464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   607,354,879   607,352,832  83 Linux
/dev/sda2         607,356,926   625,084,415    17,727,490   5 Extended
/dev/sda5         607,356,928   613,602,306     6,245,379  82 Linux swap / Solaris
/dev/sda6         613,603,328   624,480,255    10,876,928  83 Linux
/dev/sda7         624,482,304   625,084,415       602,112  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        81BF-1700                              vfat       New Volume                    
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d6608860-4763-4ce1-9a43-f756e7858258   swap                                     
/dev/sda6        ddeb98a9-b2d3-4ee8-9527-031263dae4bc   ext4                                     
/dev/sda7        9c609d40-b85c-407a-ade8-9370009a9387   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/ddeb98a9-b2d3-4ee8-9527-031263dae4bc ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1        /media/New Volume        vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=ddeb98a9-b2d3-4ee8-9527-031263dae4bc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=9c609d40-b85c-407a-ade8-9370009a9387 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 318.5GB: boot/initrd.img-2.6.32-24-generic-pae
 318.2GB: boot/vmlinuz-2.6.32-21-generic
 318.3GB: boot/vmlinuz-2.6.32-24-generic-pae
 318.5GB: initrd.img
 318.3GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  17 0d 29 6c 58 03 d0 35  4e 8d d0 10 b2 1c 1d 5e  |..)lX..5N......^|
*
000001b0  17 0d 29 6c 58 03 d0 35  4e 8d d0 10 b2 1c 00 fe  |..)lX..5N.......|
000001c0  ff ff 82 fe ff ff 02 00  00 00 03 4c 5f 00 00 fe  |...........L_...|
000001d0  ff ff 05 fe ff ff 75 4d  5f 00 8d fa a5 00 00 00  |......uM_.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

 
```

---

### Post by SplinteredChaos on 2010-08-22
I'm hoping this is what you were looking for, and presented in the right way. LOL.

---

### Post by oldfred on 2010-08-22
Is sda your external? The grub is looking in partition #1 and the only linux is in sda6 which does not look complete. The script sometimes mis identifies drives but not partitions, so I think you may have Ubuntu in partition one sdb1 of your external.

The install in sda6 seems to be missing the grub files.

If you ran the script without your external please rerun it with the external plugged in.

---

### Post by SplinteredChaos on 2010-08-22
The external was plugged in when the script was run. As for the designation of the external, I couldn't tell you. I let the install software determine all that stuff. Every time I've tried reapplying the installation to the external I get a different "result" in that the desktop will show different bits of information, ie currently it says 5.6 gb file system, and then another disk icon that simply says new volume at 289.5 gb. Which doesn't make much sense to me. The drive is supposed to be a 320 gb drive, I know that some of that is lost because of proprietary software on the drive, however not 30 gb worth.

---

### Post by SplinteredChaos on 2010-08-22
If it helps at all, there was a version of Debian installed on to the external, however I ran in to a similar problem in that I couldn't get things to load. Depending on which option I took I would get a text only screen, and that's it. The other option wouldn't even get me that far. Sprinkle in there the No boot file message and we're about covered. Every time I've reinstalled Ubuntu I tell the system to delete all information on the hard drive.

---

### Post by oldfred on 2010-08-22
The partition sda1 in one place is shown as vfat and the other as linux. So that must be where your new install is but you have a Partition error. The script was not able to parse the vfat file to find the Ubuntu files. 

From the liveCD system, administration, disk utility what does it show sda1 as and will it let you set it to linux. Is it supposed to be ext3 or ext4? If we can be sure it sees it as ext then we could run file checks but the file check will not work if it sees it as vfat.

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sda1
if errors:
sudo e2fsck -f -y -v /dev/sda1

---

### Post by SplinteredChaos on 2010-08-22
I am redoing the installation again. I toggled a different option this time around, so perhaps this is the missing key. Can't say I hold much hope for that though. 

I will continue to post new information here, until I get this figured out.

---

### Post by SplinteredChaos on 2010-08-22
I got it. After nearly 2 days of futzing with it, I got it. I had to max out the partion stuff manually, and then through the advanced menu pick the section with what looked like the lowest number for where the gbur (or whatever it is called) was to go. That seemed to be my entire problem.

Thank you for all of your help guys.

---

