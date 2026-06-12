---
title: "Installing or recover Unbuntu witht no working System &amp; a defected CD"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by ka3sem on 2010-10-12
Hi everybody,

I have only a ubuntu 8.10 in my computer, and trying to desinstall some tools and make more free space to do the update to ubuntu 9, I have deleted some system-files (python), and my OS become defected, no internet connexion, no graphic interface, ...

my ubuntu CD is defected too and shows an error like: 'ubiquited error ...'. I can only boot from it, but can not install the install packet which is in the desktop.

I have downloaded the .iso version 10.04 but the grub failed

I have followed this link:
[https://help.ubuntu.com/community/Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux")

but in step3, I founded /etc/grub.d/20_memtest86+ instead of /etc/grub.conf or /boot/grub/menu.lst or /etc/grub.d/40_custom and I have added the following files in my 20_memtest86+

menuentry "installer" {
insmod ext2
set root=(hd0,1)
linux /casper/vmlinuz boot=casper root=/dev/ram1 ramdisk_size=1048576 rw
initrd /casper/initrd.lz
}


Thanks for help!

```


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7e227e22

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       979,964       979,902  82 Linux swap / Solaris
/dev/sda2             979,965   124,166,384   123,186,420  83 Linux
/dev/sda3         124,166,385   312,576,704   188,410,320  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        9824c022-89b4-4caf-940a-5a5f3d2e29d0   swap                                     
/dev/sda2        6ea89aac-06b8-4586-8c91-44245035ff9f   ext3       /                             
/dev/sda3        e00cb457-274f-4d92-aa80-8bf475ea0d0b   ext3       /home                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/disk              ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sda3        /media/_home             ext3       (rw,nosuid,nodev,uhelper=hal)
/dev/sda2        /mnt                     ext3       (rw)
/dev/sda3        /mnt                     ext3       (rw)
/dev/sda2        /mnt                     ext3       (rw)


```

---

### Post by drs305 on 2010-10-12
The results do not show any installation on the drive, including boot files. This may be why the files are always empty. Your boot files, if they exist, would be on sda2. It appears when you are running the CD and the boot script the system drive is also mounted on /media/disk. That partition may only be mounted while the script runs, but you could check that location with a file browser.

Your /home partition is on sda3 and you might try mounting that to see if you can get your data files back.

There are utilities such as TestDisk and Photorec which help recover files but it is not an easy process (especially Photorec).

I would try to mount sda2 (system partition) and sda3 (home) and inspect the entire partition to see if any files are recoverable.

If you don't have a boot partition and can't edit it's files you aren't going to be able to follow the procedure in the link. It is based on a working Ubuntu system.

Without a working system, a fully functioning CD, or an Internet connection I am not sure what your options are. You need at least one of those three things. 

I think I'd start a new thread with a title like: Install without Internet? or something like that.
 
Explain in the first post:
No Internet
Which CD you have (Jaunty, Karmic, Lucid, etc) can boot but can't install.
You have a non-working installation of ... (version).
Results.txt

Perhaps someone will have a solution.

---

### Post by oldfred on 2010-10-12
It looks like you deleted more than just a few programs but the entire system. The boot script does not show anything in /boot neither kernels nor grub. Or /boot looks like it was deleted. At this point trying to recover looks difficult or impossible. Fortunately you have a separate /home so you should be able to do a manual reinstall using your existing /home (unformated) and at least have all your user settings & data.

What is the problem using the liveCD to install. It seems like it is working well enough for you to get online.

---

### Post by ka3sem on 2010-10-12
the with the cd is after runing the packet on the desktop, after same steps, I receive a error like: ubiquited error ...

/media/_home & /media/disk are created through the Partition Editor gparted (with the CD).

So, I have no working system, no working CD, but I have internet connection. How can I proceed?

---

### Post by ka3sem on 2010-10-12
Duplicate post.

---

### Post by drs305 on 2010-10-12
I think your best option, aside from getting another CD, is to get the CD you have to boot? You mentioned Ubiqity but we dont' really know what the error is.

When you first boot the LiveCD, you can press ESC from the Language selection page, spacebar or F6. It probably differs with CD versions. On recent CDs, if you press F6 it may pop up some boot options. You might try "noapic" and "acpi=off" which I believe are preset options. If you don't see them, try pressing F6 again. The linux line should show and you can manually type those options at the end of the line and then boot.

Which version of Ubuntu is your CD? Also, did you accomplish a CD check? Again, the more recent CDs have this option.

---

### Post by ka3sem on 2010-10-13
When I boot the LiveCD and I press F2, F6,... from the Language selection page, or I want to change the language, nothing changes or would be displayed.
I should wait to the end of 20s, 19s, 18s, .... and then I will be in the showed desktop.
So I think that ESC doesn't work too.

---

### Post by ka3sem on 2010-10-13
@oldfred

which solution do you have for this situation?

---

### Post by oldfred on 2010-10-13
Do you have the ISO file (not installed on CD) and can you run gparted? Is ISO current version?

If so you can create a 1GB partition on your hard drive and install grub2 to the new partition and loopmount the ISO and then install from that. Confirm you have ISO and can run gparted and I can give details.

---

### Post by ka3sem on 2010-10-13
thanks oldfred, a friend had given me the Ubuntu 9.10-CD und I will try with it.

---

### Post by ka3sem on 2010-10-14
I have installed ubuntu 9  and then upgraded to 10. The problem is resolved now. But I have lost some data & files which were in my system Ubuntu 8 :( .

@oldfred
can you tell me more details about the solution (which commands to use, ...): "install grub2 to the 1GB partition and loopmount the ISO and then install from that"?

and how can I recover my lost data?


Thanks anyway

---

### Post by oldfred on 2010-10-14
Once a partition has new data written to it, it is about impossible to recover data. These programs will scan a drive and look for what may be a file and let you save it.

Testdisk & photorec
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
Foremost
[http://www.howtoforge.com/recover-deleted-files-with-foremost](http://www.howtoforge.com/recover-deleted-files-with-foremost)
[http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html](http://www.ubuntugeek.com/recover-deleted-files-with-foremostscalpel-in-ubuntu.html)


What I suggest is to create a separate install partition on hard drive. You allocate 1GB and install grub to it, create a folder /boot/ISO and copy the ISO to that folder. Then you created a grub.cfg that loop mounts the ISO. You then can install to other partitions on hard drive. But if you have a working liveCD or USB you do not need to use hard drive.

Direct boot on hard drive:
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)
Says you can install from same partition you boot from with workarounds.
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

---

### Post by ka3sem on 2010-10-15
ok, thanks.

---

