---
title: "Updated Ubuntu which removed MBR and Grub following successful dualboot installation"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by shayno90 on 2010-08-09
Ok I ran into a problem now, I updated Ubuntu now and the updated kernel has removed the EasyBCD settings for dual booting and now once the system boots up, a cursor flashes in the top right hand corner and then boots straight into Ubuntu without showing any options for booting into Ubuntu or Windows!

Has this problem being fixed yet or are there any solutions to retrieve the original EasyBCD bootloading setup?

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   337,010,687   336,601,088   7 HPFS/NTFS
/dev/sda3         337,012,734   598,984,703   261,971,970   5 Extended
/dev/sda5         337,012,736   588,257,279   251,244,544  83 Linux
/dev/sda6         588,259,328   598,984,703    10,725,376  82 Linux swap / Solaris
/dev/sda4         598,984,704   625,139,711    26,155,008   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        122656F62656D9F5                       ntfs       SYSTEM                        
/dev/sda2        BE26AE8326AE3C71                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda4        488E0E1C8E0E0364                       ntfs       RECOVERY                      
/dev/sda5        bf00db6b-11e7-442c-b27b-7e508a37c0cc   ext4                                     
/dev/sda6        63fc54eb-ccbe-43ae-aabe-7785981c2d56   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)

Coutesy of  sudo bash [path/to/the/download_folder]/boot_info_script*.sh the boot info script.

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
Found Windows Vista (loader) on /dev/sda4
done

So if I cannot boot into Windows I cannot configure EasyBCD settings. Any idea how I can get the Grub2 boot menu to appear and not just boot straight into Ubuntu?

Do I need to reinstall GRUB 2 since it doesn't appear then change the grub config to boot into Windows 7 partition and then configure the MBR with EasyBCD?

---

### Post by oldfred on 2010-08-09
I do not know about easyBCD.

Have you tried this to get grub to find windows?

```
sudo update-grub
```

It should find your windows and let you boot it.

If you do not want grub to update, choose no drives, use spacebar to unchoose also. Does easyBCD require an install to a partition?

to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose drive, enter to accept, do not choose partitions

If you install to a partition understand that you are using blocklists which are less reliable. They are hardcoded address to find boot files. Any movement of files by partition movement, file updates or filechecks may move files and require grub to be reinstalled to boot.

---

### Post by shayno90 on 2010-08-09
No the system boots straight into Ubuntu so can only access Easy BCD in WIndows.

The dual boot was fine until I updated the Ubuntu system which updated the kernel and changed the grub setting i had configured.

I tried the sudo grub update but those partitions for each OS only appear in terminal and not when I reboot the system 

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Windows Vista (loader) on /dev/sda2
Found Windows Vista (loader) on /dev/sda4
done

Yet this doesnt appear when I reboot the system!! 

Any ideas otherwise I will have to reinstall the grub2?!

Plus when I ran this sudo dpkg-reconfigure grub-pc

 &#9474; The following Linux command line was extracted from /etc/default/grub or the `kopt' parameter in GRUB Legacy's menu.lst.  Please verify that it is correct, and   &#9474; 
 &#9474; modify it if necessary.                                                                                                                                           &#9474; 
 &#9474;                                                                                                                                                                   &#9474; 
 &#9474; Linux command line:     

It did not give me an option to pick a drive as it prompts for one to be manually written, the Ubuntu Ext 4 is on /dev/sda5, do I enter this?

---

### Post by oldfred on 2010-08-09
Are you sure you do not have the windows entries. Sometimes if you have a lot of lines, all do not show in the grub menu box and you have to scroll down to see them. One of your Vista's is just the recovery.

I do not know easyBCD and do not think you should add any settings from old grub unless you know you need them.

---

### Post by shayno90 on 2010-08-09
The problem is  the Grub boot menu box doesn't appear with a selection of Ubuntu and WIndows 7 partitions so it is not possible so either I need to change the grub config file to not make an automatic timed selection by extending it to 10 seconds or so,  or reinstall grub2 after which i boot into windows and redo the easybcd configuration as it is a much tidier option for dual booting.

first i installed grub2 to the MBR, then reinstalled the Windows boot  loader to the MBR, then i booted Windows and installed EasyBCD to configure the settings. (the previous procedure for booting)

Also what do i enter into the command line for reconfiguring the packages in grub-pc?

---

### Post by shayno90 on 2010-08-09
Ok I downloaded startupmanager and changed the selection in the boot menu to 10 seconds (essentially it edited the configuration file for grub where the default time is) (it was set to 0 from the previous boot configuration) and there you go the boot menu appeared with all the Ubuntu and Window partitions. 

When i selected the windows 7 mbr it presented me with my previous EasyBCD bootup configuration. So I will configure it now to boot with the new Ubuntu kernel which was installed.

Will update later.

---

### Post by HealingMindOS on 2010-08-09
I'm watching this thread very closely. I consider it a master selling point for Ubuntu. 

I am deeply considering a dual boot config w/ Ubuntu / WinXP. Unfortunately, I do not understand the instructions under the heading: Master Boot Record and Boot Manager at [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot), then I found this thread.

Since I am a linux newbie, I'm not sure what goes into updating Ubuntu. When Xandros had an update (long ago) my whole dual boot system got whacked and I had to start everything from scratch again. I thought Ubuntu had tons of support for these kinds of problems.

---

### Post by shayno90 on 2010-08-09
Well I configured the EasyBCD to organize the booting process. The oiriginial problem for not seeing the boot up grub menu was the time in /etc/default/grub and was set to 0 from the previous EasyBCD configuration. I would recommend not to change this 0 and leave it at the original as once the updated Ubuntu starts the changes to the kernel cause the grub to override the EasyBCD dualbooting settings and thus it would boot straight into Ubuntu 10.04 if the GRUB _TIMEOUT=0 so better leave it at 10. I have a guide for dualbooting WIndows 7 and Ubuntu 10.04 below, the only thing to be careful of is when you update the newly installed system you will have repeat the EasyBCD process as the GRUB from the new updated Ubuntu overrides the MBR containing the EasyBCD setup.

Hint download startupmanager to handle the /boot/grub/grub.cfg and /etc/default/grub settings

~$ sudo apt-get install startupmanager

[http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html](http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html)

This is 

~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

Installation Guide:

Ok, I have successfully installed Ubuntu 10.04 with Windows 7.

Make sure you back up your important files and have the recovery discs or Windows 7 cd ready!

Step 1
I defragmented the Windows 7 hard disk and then partitioned it with the Windows disk manager by shrinking the main NTFS volume.
Guide at this link [https://help.ubuntu.com/community/Ho...dowsPartitions]("https://help.ubuntu.com/community/HowtoResizeWindowsPartitions")

Step 2
Downloaded Ubuntu 10.04 from [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
the x86 version or 32bit

Step 3
Downloaded Infrarecorder at [http://infrarecorder.org/?page_id=5](http://infrarecorder.org/?page_id=5)
Burn the ISO image at the lowest speed of 4x and used a Memorex 700MB CD-R on an external CD-ROM Drive

Step 4
Checked the MD5Sum by downloading [http://www.nullriver.com/products/winmd5sum](http://www.nullriver.com/products/winmd5sum) to check the ubuntu hash matches the mirror version.
The guide for windows is here [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Step 5
Once verified installation begins by placing the burnt ISO CD image into  the external CD-ROM drive and booted into it using F9 key
Follow the on screen instructions once the Live CD boots up, make sure  to select the largest continuous space for the Ubuntu partition
 this guide gives more detail [http://members.iinet.net.au/~herman546/p23.html]("http://members.iinet.net.au/%7Eherman546/p23.html")

Step 6
Following the install you may get an I/O error as the external device  has ejected the Live CD following the reboot, so just type 'shutdown -r  now' which restarts the bootloader

Step 7
Boot into Windows 7 and download EasyBCD to configure the bootloaders for Windows and Ubuntu at [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)
This guide shows how to configure it [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Step 8
Once the bootloader has been set up, if you log into Windows 7 and all  your desktops icons are missing, infrarecorder has somehow removed them  but the can be restored by right clicking the desktop and select show  desktop icons.

Step 9 
Hint download startupmanager to handle the /boot/grub/grub.cfg and /etc/default/grub settings as once you update Ubuntu this will make it easier to make changes to those sensitive files.

~$ sudo apt-get install startupmanager

[http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html](http://www.ubuntugeek.com/startup-manager-change-settings-in-grub-grub2-and-usplash.html)

Dual boot complete!! :)

---

