---
title: "Unable to Dual boot Ubuntu with windows 10. Not detecting existing HDD &amp; Windows 10"
date: 2018-12-15
forum: Installation &amp; Upgrades
---

### Post by murali0206 on 2018-12-15
I am trying to install Ubuntu 18.04.1 parallel to my existing windows 10 OS. 

Please find the attachment with name Disk_Space.png for disk partition configuration.

[ATTACH=CONFIG]281929[/ATTACH]
 
I have downloaded ISO file and write it on to a USB flash stick using [https://etcher.io](https://etcher.io) . 

Then restarted the system by continuously typing F12 and choose my USB device from boot menu. After that when I try to install ubuntu OS, it is not showing alongside windows option/ something else option. Even it is not showing my unallocated memory of Hard disk. Instead it is showing my USB memory capacity.

I am unable to install dual boot ubuntu with windows10.

Please find the attachments for further info.

---

### Post by Autodave on 2018-12-15
Have you disabled *fast boot *in the BIOS?  Win10 does not shut down: it hibernates.  When it hibernates, it holds the entire drive hostage.  You will have to disable fast boot and then shut Windows down. Then, when you restart the machine, you again want to get to the boot order and choose your USB to boot from. Then you should see the space that you allocates and it should also tell you that it found Win10.

---

### Post by oldfred on 2018-12-15
I cannot tell for sure if the FAT32 partition at beginning of drive is an ESP for UEFI or a recovery partition and your install is BIOS.
Windows only installs in UEFI mode to gpt partitioned drives and only in BIOS boot mode from MBR(msdos) partitioned drives.
Post this and it will say if gpt or dos:
sudo parted -l

If BIOS/MBR, then you have used all 4 primary partitions.

IF BIOS or UEFI, you may have Windows fast start up on and then the Linux NTFS driver cannot see the NTFS partition.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by murali0206 on 2018-12-16
I have already disbled the fast boot settings in my system.

---

### Post by jeremy31 on 2018-12-16
Have you disabled the hybrid shutdown in Windows?

---

### Post by yancek on 2018-12-16
The Disk Management output in your initial post shows that partition 1 and partition 5 are empty which seems odd to me.
You neglected to post the output of the command:  sudo parted -l from a terminal when booted to the Ubuntu install media.
If you have done any updates on windows since disabling fastboot, it was probably turned back on.

---

### Post by murali0206 on 2018-12-16
Partition 1 and partition 5 in disk partition are for healthy recovery which are not in my control.
I tried sudo parted -| in Ubuntu terminal. But it is showing blank. It is not throwing any error.

---

### Post by oldfred on 2018-12-16
Best to copy & paste command to avoid confusion. Different fonts look different, and it is -l or lower case el, not capital I nor 1 nor |.

sudo parted -l

---

### Post by murali0206 on 2018-12-17
Here is the output

ubuntu@ubuntu:~$ sudo parted -l
Warning: Not all of the space available to /dev/sda appears to be used, you can
fix the GPT to use all of the space (an extra 4544 blocks) or continue with the
current setting? 
Fix/Ignore? ^C                                                            
Model: ATA ST1000LM035-1RK1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  274MB   273MB   fat32        EFI system partition          boot, esp
 2      274MB   290MB   16.8MB               Microsoft reserved partition  msftres
 3      290MB   701GB   701GB   ntfs         Basic data partition          msftdata
 4      972GB   999GB   26.8GB  ntfs         Basic data partition          msftdata
 5      999GB   1000GB  1047MB  ntfs         Basic data partition          hidden, diag


Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel? ^C                                                         
Model: SanDisk Cruzer Blade (scsi)
Disk /dev/sdb: 15.7GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:

---

### Post by murali0206 on 2018-12-17
Based on the above output from sudo parted -l, it looks like unpartitioned space is not getting listed here. And also my C drive where the Windows 10 is installed is listed here

---

### Post by oldfred on 2018-12-17
You can ignore error on flash drive, that seems to be common with most tools to create flash drives.

I would let parted or gdisk fix any errors before proceeding. Errors often prevent partitioning tools in installer from working. And that may be issue.

But some systems also need UEFI update and if SSD, SSD firmware update. And all systems need drives set to AHCI, not RAID nor Intel SRT or similar.
What brand/model system? What video card/chip?

You do have UEFI install of Windows, since you have both gpt partitioning & typical UEFI partitions for Windows in UEFI boot mode.
So back up Windows, only use Windows to shrink the NTFS partition where you want to create space for Ubuntu, make sure Windows fast start up is off and be sure to boot Ubuntu live installer in UEFI boot mode to install in UEFI mode.

       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 10 screens or similar to Windows 8
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)  & 
[https://askubuntu.com/questions/221835/how-do-i-install-ubuntu-alongside-a-pre-installed-windows-with-uefi](https://askubuntu.com/questions/221835/how-do-i-install-ubuntu-alongside-a-pre-installed-windows-with-uefi) 
    
Lots more details on UEFI install with many links to even more useful info if you do not understand some things.

---

### Post by murali0206 on 2018-12-18
Mine is Lenovo IdeaPad 330s model with Intel i5 8th gen processor

---

### Post by oldfred on 2018-12-18
Check if Lenovo has newer UEFI for your system.

Most vendors use similar or same UEFI with many models with just options implemented. But Lenovo seems to have many models and I am not sure if any of these are similar or not. Bigger differences if AMD or Intel based system.
       Lenovo y50-70 use rEFInd
[https://askubuntu.com/questions/987409/ubuntu-boot-failed-cant-modify-bios-setup-to-remove-secure-boot](https://askubuntu.com/questions/987409/ubuntu-boot-failed-cant-modify-bios-setup-to-remove-secure-boot)
Lenovo boot screen can be accessed by Fn + F2 keys, boot device selection by Fn + F12.
Ubuntu on Lenovo ThinkPad E470  Pre-installed Ubuntu
[https://certification.ubuntu.com/hardware/201609-25122/](https://certification.ubuntu.com/hardware/201609-25122/)
Lenovo Y700 Ideapad Windows 10 & Ubuntu SSD & HDD
[http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html](http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html)
Lenovo Legion Y520-15I  Installer does not detect SSD and HDD: Ubuntu 16.04 LTS
[URL="https://ubuntuforums.org/showthread.php?t=2359208"]https://ubuntuforums.org/showthread.php?t=2359208
[/URL]
 Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715) 

[URL="https://ubuntuforums.org/showthread.php?t=2359208"]
[/URL]

---

