---
title: "Windows 7 Dual boot Grub2 doesn't install"
date: 2010-04-26
forum: Installation &amp; Upgrades
---

### Post by tnine on 2010-04-26
Hi all,
  I've just installed the 64 bit edition of 9.10 on my workstation.  My raid drivers worked without any custom installation, which is very impressive!  I am however having a problem installing grub2. I boot to the live CD, run the install process, resize and partition my free space as an ext4 primary partition with mount point /.  Everything installs except grub, so I'm always booting in to windows.  This seems to be a bit off as I've never had this occur with dual booting before.  Any ideas why grub didn't install, and how I can get it on my machine?

Thanks,
Todd

---

### Post by limey_rick on 2010-04-26
So can you clarify what you mean by RAID drivers? Perhaps some more information on your setup. For example, do you have raid setup from the BIOS? How many hard drives on your system? IDE or SATA or RAID? Is Windows 7 installed across a few drives (striped or mirrored)? 

When the 9.10 installation finishes, does it report any errors or as far as you are concerned or does it appear as though it has completed correctly?

Check out this post: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) if you are using a raid setup. 

I have had problems where GRUB2 (on 9.10) has not honoured the order of my disks as defined in the PC BIOS, so it installs itself on another disk. If you don't boot from this disk in the BIOS though you won't see GRUB. If you have more than one disk, try changing the boot order in the BIOS as maybe GRUB2 installed on the other disk.

---

### Post by wilee-nilee on 2010-04-26
You might also post the ubiquitous boot script this will show exactly whats going on post it with code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by tnine on 2010-04-27
Hey guys,
  I've made it a bit of progress on this issue.  My previous statements were incorrect, my RAID drivers did not work properly. What I was actually doing was blitzing the data off of my /dev/sda device.  Thankfully with my RAID 1+0 I was able to rebuild the underlying data on the disk after I booted back into Windows 7.


Unfortunately I have a FRAID card.  Specifically a Rocket Raid 2302.  While I fully understand the software RAID built into Ubuntu performs the same task as highpoint's software with less bugs, I cannot run the linux RAID since I need to keep my existing Windows 7 installation which was installed on top of the highpoint drivers.  

My driver page downloads is here.

[http://www.highpoint-tech.com/usa/bios_rr2300.htm](http://www.highpoint-tech.com/usa/bios_rr2300.htm)

As you can see, none of the precompiled options will work.  So, I've downloaded the source, then run the usual 

```
sudo make && sudo make install
```After the installation I run

```

 sudo modprobe rr2310_00

```Now, my module is loaded.  However the partition manager and installation helper still shows me 4 SATA disks, not the 2 devices defined by the RAID Bios setup.  I have 2 raided paritions, 1 raid 1+0 for data and 1 RAID 0 for swap.  I know Ubuntu can see my hardware.  Here is my output from inspecting PCI cards.

```
ubuntu@ubuntu:~$ sudo lspci |grep Rocket
05:00.0 SCSI storage controller: HighPoint Technologies, Inc. RocketRAID 230x 4 Port SATA-II Controller (rev 02)

```However, when I check the status of my kernel modules, it's not loaded.

```
ubuntu@ubuntu:~$ sudo lsmod|grep rr
rr2310_00             240864  0 
```I'm running the Live CD pre-install.  How can I force ubuntu to use the scsci device to install everything?  Also, how can I get the driver installed so it boots properly after the installation?

Thanks,
Todd

---

### Post by wilee-nilee on 2010-04-27
I would not force anything and post the boot script, you are otherwise flailing in the dark and may lose everything, or end up in a longer harder working situation.

---

### Post by tnine on 2010-04-27
Which script do I need to post?

---

### Post by wilee-nilee on 2010-04-27
> **wilee-nilee said:**
> You might also post the ubiquitous boot script this will show exactly whats going on post it with code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

This one.

---

### Post by tnine on 2010-04-27
Thanks for the help.  Here is my output.  /dev/sda through /dev/sdd are the hard drives in my FRAID card.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
 => No boot loader is installed in the MBR of /dev/sdc
 => No boot loader is installed in the MBR of /dev/sdd
 => Syslinux is installed in the MBR of /dev/sde

sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sde1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sde1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sde1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1c8ddb3f

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    78,123,007    78,120,960   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sdd ___________________ _____________________________________________________

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sde ___________________ _____________________________________________________

Disk /dev/sde: 8127 MB, 8127512576 bytes
251 heads, 62 sectors/track, 1020 cylinders, total 15874048 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00021fbc

Partition  Boot         Start           End          Size  Id System

/dev/sde1    *             62    15,873,239    15,873,178   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sde1        ED56-BC7C                              vfat       Todd                          

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


```

---

### Post by oldfred on 2010-04-27
The script is not really designed for raid as that is not common for desktops.  So the script did not get to see the partitions inside the raid. Server raid systems often have a separate boot drive and some desktops also where we have been able to help.

Without seeing the Ubuntu partitions and knowing how your raid works makes it difficult to help. I do not know raid.

Someone with raid experience may be able to help.

---

### Post by tnine on 2010-05-09
Ok, some follow up.  When I use 10.04 I can compile and modprobe my driver from the live cd.  After that all my drives defined my the FRAID Bios appear.  However as soon as I start the installation process, my drives disappear.  It seems the module is getting unloaded.  Any ideas on what's going on?

Thanks,
Todd

---

