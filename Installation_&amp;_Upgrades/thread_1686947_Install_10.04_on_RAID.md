---
title: "Install 10.04 on RAID"
date: 2011-02-13
forum: Installation &amp; Upgrades
---

### Post by Steve Moss on 2011-02-13
Hi

Hope someone clever out there can help me

I am trying to install Ubuntu 10.04 32-bit from live CD (wubi doesn't work)so that I can dual boot windows XP or Ubuntu

The installation proceeds OK until I get a screen that has the following options

[COLOR=red]Erase and use the entire disk
Specify partitions manually (advanced)[/COLOR]

However all the tutorials say there should be a third option 

[COLOR=Red]Install alongside other operating systems ( dual booting[/COLOR])

I don't have this third option and don't know how to proceed

Any help would be much appreciated

Below is boot script info

           ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/mapper/nvidia_dacfdfjj

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

nvidia_dacfdfjj1: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows XP
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 300.1 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders, total 586072368 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   586,051,199   586,051,137   7 HPFS/NTFS


Drive: nvidia_dacfdfjj ___________________ _____________________________________________________

Disk /dev/mapper/nvidia_dacfdfjj: 600.1 GB, 600138055680 bytes
255 heads, 63 sectors/track, 72962 cylinders, total 1172144640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/mapper/nvidia_dacfdfjj1   *             63   586,067,264   586,067,202   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/mapper/nvidia_dacfdfjj: PTTYPE="dos" 
/dev/sda                                                nvidia_raid_member                               
/dev/sdb                                                nvidia_raid_member                               
error: /dev/sda1: No such file or directory

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
nvidia_dacfdfjj
nvidia_dacfdfjj1

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
```

---

### Post by YesWeCan on 2011-02-13
See: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by ronparent on 2011-02-13
The last time I looked that FaleRaid reference had not been updated. It wasn't straight forward but is very doable.

Unless the fixes to gparted have reached 10.04, gparted will not find the raid partitions so in that case you have to employ a workaround. To do this you boot to a 10.04 live cd session. Install kpartx to that session (software center, synaptics or 'sudo apt-get install kpartx' in a terminal. At this point you click the install icon on the desktop and start the installation. In the partitioning step select 'Specify partitions manually (advanced)'. With winXP you can use the partitioner to shrink one of your windows partitions to make room for installing (8 Gb is minimum for '/' and probably 2Gb for swap). Select 'create' to create the partition to install to and in that window select the format for your filesystem (either ext3 or ext4), check to format, and. select '/' for your mount point. Close that box and open one to create  the 2Gb swap. Then step through the remaining install step. In the final step (I believe step 8 of 8, I haven't looked at this in a while) you select a box called 'advanced' and pick or select '/dev/mapper/nvidia_dacfdfjj' as the location to put the grub boot loader on. 

Sometimes this last step doesn't work right. Don't panic if you system is unbootable - it is fixable. You just do a grub reinstall from a live cd terminal per this: [https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

In the two step process outlined just be sure to mount the partition you installed to (/dev/mapper/nvidia_dacfdfjj# where # is your raid partition for the install) and designate the location for the boot record in the second step ('/dev/mapper/nvidia_dacfdfjj' in place of /dev/sda illustrated). Good luck. Post if you run into problems.

---

### Post by Steve Moss on 2011-02-14
Hi Ronparent

Thanks for your reply

Sorry but I am having trouble following your instructions (please bear in mind all of this is very new to me)

I have 2 hard drives

Looking in windows I have a C: drive (disk 0) which is the entire first hard disk and a D: drive (disk 1)which is the entire second hard disk

The C: drive has windows XP installed the D: drive is empty

Using disk management in XP I see the following
C: Partition Basic NTFS Healthy (System) 279GB capacity 253GB free
d: Partition basic NTFS Healthy (Active) 279GB capacity 279GB free

I now boot up Ubuntu 10.4 using Live CD and fire up Gparted and get a drop down menu with 2 options

The first is /dev/sda1 which I am certain is the C: drive so I will leave this alone

The second is dev/sdb1 and looks like the D: drive so I select this

This says partition /dev/sdb1 file system ntfs size 279GB

Please advise how I proceed from here

---

### Post by ronparent on 2011-02-14
That clarify's a lot. You are not using raid. The raid meta data is still on your drives and should first be erased before you do anything. In a live cd terminal write 'sudo dmraid -rE /dev/sda' and then the same thing for sdb. If you leave the meta data in place you are courting disaster because you will likely be offered the option to partition the raid, and, in the process wipe out your non raid partitions!

Then you should probably still elect the 'Specify partitions manually (advanced)' option. In the screen that follows selecting that option you would then elect to shrink the sdb1 (which corresponds to the d: drive) as I previously described. What is left after that operation is now unallocated space. Now you select 'change' twice to create in turn a partition to install to (designated '/') and a swap partition. The sizes depend on how much space you want to allocate for them - a minimum being 10Gb for '/' and 2Gb for swap. 

You need not change the default for installing grub unless you want to retain the windows boot sector on sda. If you do want to retain it (conservative but understandable) then you best option would probably be to disconnect that drive before starting the install! Then you could select the easier side by side option. To do this you should be comfortable with changing the hd boot order in bios.

I don't have time right now to explain all of the ramification but installtion will be much simpler once the raid meta data is erased. Do post if you need more info.

---

### Post by YesWeCan on 2011-02-14
The output you showed is a little weird because sdb is not listed.

As a precaution, disconnect the D: drive and try to boot Windows. Make sure this works. If it does then your RAID artefacts are redundant and Ron's advice to remove the superblocks is good. Also, go into the bios and disable anything related to RAID. If you cannot boot off the sda/C: drive then we need to think again.

Regarding installing Ubuntu, I always disconnect my Windows drive first. It just makes the install simpler and less dangerous if I make a goof. After the install it is simple to add the Windows OS to the Grub boot menu. We'll come to that later. I think it is a good contingency to be able to independently boot Windows so I don't install any grub stuff on the Windows disk.

---

### Post by Steve Moss on 2011-02-14
Hi guys

Thanks for the replies

Before I got these replies I got impatient and took a chance and installed under "side by side" option from live CD

All seems to be working although I get a boot option of 4 x Linux loads and 1 x Windows load. If I take the Windows load I get a further 2 boot options Ubuntu or Windows

I tried the command

sudo dmraid -rE /dev/sdb

and got this message

sudo: dmraid: command not found

Please advise if I should take any further action

---

### Post by ronparent on 2011-02-14
Fortunately in your case dmraid was not installed since you were not installing to a raid - that is normal. Since dmraid is not installed and apparently raid is not turned on in bios everything should work normally and you don't urgently need to do any thing. Many people suggest that as the solution to rid yourself of any problems caused by the raid meta data.

I suggest erasing the raid meta data because it persists despite not being used and often comes back to haunt you in the future when you forget it is there. Although you can leave it alone and the future to itself, if you want to rid that data once and for all you could boot to a live cd and use the commands I gave you in a terminal window. The choice is entirely yours. In any case you have a working system now regardless of what you do. Enjoy and good luck.

---

### Post by Steve Moss on 2011-02-14
Thanks again Ronparent

> if you want to rid that data once and for all you could boot to a live cd and use the commands I gave you in a terminal window.

You have been so helpful already but could you just remind me exactly what commands these are

Sorry to be a nusiance

---

### Post by ronparent on 2011-02-14
> I tried the command

sudo dmraid -rE /dev/sdb

and got this message

sudo: dmraid: command not foundYou got that result because dmraid was not installed with your system. It is on the live cd however and will remove the meta data from sda and sdb if run from the live cd for each drive.

---

### Post by Steve Moss on 2011-02-15
Thanks that did the trick!!!

This is what sdb now looks like in KDE

/dev/sdb1 ntfs size 139GB used 68GB boot
/dev/sdb2 extended size 139GB used 139GB
     /dev/sdb5 ext4 mount point /  size 133GB used 4GB
     /dev/sdb6 linux swap size 5.7GB used 0GB 

Does this look OK?

Can I change partition sizes without losing data (I have 130GB spare space on the drive)

Thanks again for all your help

---

### Post by ronparent on 2011-02-15
Your swap might be a bit larger than you need - but you otherwise have plenty of room so this is not material. As long as you have plenty of empty space in each partition changing partition size is no problem in itself. Anything that requires moving the front end of a partition can become time consuming - but still doable at will.

Disks have become so cheap that acquiring additional space is trivial as long as your mother board and case can handle it or you can augment with an external. If you know of a specific future need you can plan for it. Otherwise just relax and go with it. Glad I could help. Enjoy.

---

