---
title: "Re: No space on the disk"
date: 2016-06-07
forum: Installation &amp; Upgrades
---

### Post by Juan_Fiorenzano on 2016-06-07
Hello everybody, I am having the same problem when I'm going to install Ubuntu 16.04. I want to install Ubuntu in my laptop which is an Asus x555u and has Windows 10(Windows came already installed in the laptop) I don't want to get rid off Windows, I want to install Ubuntu alongside it. When I am in the installation wizard appear a error message telling me that I don't have space on the disk.
[[Image with error message 1]("https://drive.google.com/open?id=0BxNi9b3FMfkdRFlyaVZManE4SVk")]
[[Image with error message 2]("https://drive.google.com/open?id=0BxNi9b3FMfkdM3VGSm05TE1zSTg")]

If you see the images are very similar the only difference is in the ubi-partman error code, I reviewed the /var/log/syslog file and the error is that I don't have space on the disk. After some research, some people has had this error but during the update process. I was reading that this error can happen when you hard drive is not in IDE mode, my hard drive is a SATA drive in AHCI mode and I can't change it.
[[BIOS image]("https://drive.google.com/open?id=0BxNi9b3FMfkdajRiZ0oxalhwcjA")] 

I was following the recommendation that you advised to carlosestefano in this post and these are the outputs of the three commands:

```

[COLOR=#000000][FONT=Ubuntu Mono]sudo fdisk -lu
[/FONT][/COLOR]
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/loop0: 1.4 GiB, 1526194176 bytes, 2980848 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 6B235324-3BC4-4E60-84DB-3181560B72F6


Device         Start        End   Sectors   Size Type
/dev/sda1       2048     534527    532480   260M EFI System
/dev/sda2     534528     567295     32768    16M Microsoft reserved
/dev/sda3     567296  780388351 779821056 371.9G Microsoft basic data
/dev/sda4  780388352  781410303   1021952   499M Windows recovery environment
/dev/sda5  781410304 1748721663 967311360 461.3G Microsoft basic data








Disk /dev/sdb: 28.7 GiB, 30752000000 bytes, 60062500 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000


Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *       32 60062499 60062468 28.7G  c W95 FAT32 (LBA)



```

```

[COLOR=#000000][FONT=Ubuntu Mono]sudo parted -l
[/FONT][/COLOR]Model: ATA HGST HTS721010A9 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 




                                                                          
Number  Start   End    Size    File system  Name                          Flags
 1      1049kB  274MB  273MB   fat32        EFI system partition          boot, esp
 2      274MB   290MB  16.8MB               Microsoft reserved partition  msftres
 3      290MB   400GB  399GB   ntfs         Basic data partition          msftdata
 4      400GB   400GB  523MB   ntfs         Basic data partition          hidden, diag
 5      400GB   895GB  495GB   ntfs                                       msftdata




Model: SanDisk Ultra USB 3.0 (scsi)
Disk /dev/sdb: 30.8GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  30.8GB  30.8GB  primary  fat32        boot, lba





```

```

sudo blkid

/dev/sda1: LABEL="SYSTEM" UUID="BEBD-7545" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="1f364185-8aa6-42d7-8264-c8d3e155f811"
/dev/sda3: LABEL="OS" UUID="CC36C02436C0117E" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="f439206f-04b3-454a-86ac-818ebb06f46f"
/dev/sda4: LABEL="RECOVERY" UUID="60BE0EB5BE0E83AE" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="9060aa3c-6684-492c-8bc1-8fd8e5536576"
/dev/sda5: LABEL="DATA" UUID="40DEE5E2DEE5D068" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="3ec2c7f3-672f-4d19-9c64-df665286916b"
/dev/sdb1: LABEL="UUI" UUID="B80D-4B13" TYPE="vfat"
/dev/loop0: TYPE="squashfs"
/dev/sda2: PARTLABEL="Microsoft reserved partition" PARTUUID="8d67c444-ab75-47e1-8aec-0b452989df53"



```

And this is a picture of how my partition table looks in Windows
[[Partition table image]("https://drive.google.com/open?id=0BxNi9b3FMfkdMDd1N0paR0dTRjg")]

If you can help with this I will be very grateful. Thanks in advance.

---

### Post by QDR06VV9 on 2016-06-07
@ Juan_Fiorenzano Please do not hijack others Threads it dilutes the thread.
I have started another thread for you.
Thanks and Good Luck :grin:

---

### Post by Juan_Fiorenzano on 2016-06-07
Oh, sorry I didn't know that it would be a problem I didn't want to hijack anybody, I thought that is better write in the same post with the same problem than post a new one

---

### Post by lisati on 2016-06-07
> **Juan_Fiorenzano said:**
> Oh, sorry I didn't know that it would be a problem I didn't want to hijack anybody, I thought that is better write in the same post with the same problem than post a new one

That's OK.

Sometimes what looks like the same (or similar) problems turn out to have very different solutions.

---

### Post by QDR06VV9 on 2016-06-07
No it is always better to start your own thread no matter how close to identical they may seem.
Gets very confusing when replying to multiple posters.
Thanks for your understanding.;)
Ninja'd by lisati

---

### Post by yancek on 2016-06-07
Are you booting Ubuntu in UEFI?  You need to do that and install Ubuntu UEFI as windows is UEFI.  Mixing an MBR install with UEFI will make one system unbootable.  Use the "Something Else" option  to install.

---

### Post by Juan_Fiorenzano on 2016-06-07
> **yancek said:**
> Are you booting Ubuntu in UEFI?  You need to do that and install Ubuntu UEFI as windows is UEFI.  Mixing an MBR install with UEFI will make one system unbootable.  Use the "Something Else" option  to install.
 
The message appear before I can to select something else option.

---

### Post by oldfred on 2016-06-07
Did you leave Windows fast start up on? That is always on hibernation and Linux cannot mount NTFS partition.
In addition it is generally better to use Windows own partitioning tools to shrink the Windows NTFS partition and reboot immediately so it can run chkdsk.
If it needs chkdsk or is hibernated the Linux NTFS driver cannot mount it or make any changes to it.

More details in link below in my signature.

---

### Post by Juan_Fiorenzano on 2016-06-08
> **oldfred said:**
> Did you leave Windows fast start up on? That is always on hibernation and Linux cannot mount NTFS partition.
In addition it is generally better to use Windows own partitioning tools to shrink the Windows NTFS partition and reboot immediately so it can run chkdsk.
If it needs chkdsk or is hibernated the Linux NTFS driver cannot mount it or make any changes to it.

More details in link below in my signature.

Yes I turned off the windows fast start up option before the installation process, it is not the problem.

---

### Post by Juan_Fiorenzano on 2016-06-10
I don't know what it's happening with this installation or this laptop,jajaja , I changed the usb table partition scheme to GPT for avoid conflicts and used the Gparted for make a swap partition and a primary partition with ext4 format and I'm still having the same problem.

---

### Post by oldfred on 2016-06-10
Are you then using Something Else and selecting the / partition you created in advance with the change button?

 Asus M32CD desktop - Skylake several boot parameters  pci=nomsi  i915.preliminary_hw_support=1
[http://ubuntuforums.org/showthread.php?t=2312977](http://ubuntuforums.org/showthread.php?t=2312977)
ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)
ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)

---

### Post by Juan_Fiorenzano on 2016-06-10
> **oldfred said:**
> Are you then using Something Else and selecting the / partition you created in advance with the change button?

The error appear before I can select any option of instalation, it appear when I am in the dialog before it.

---

### Post by oldfred on 2016-06-10
You say dialog before.
Have you booted in UEFI mode?
Are you seeing grub menu?
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Does your system have nVidia and you are using nomodeset? Or is it booting with Intel video in control?
Some Skylake systems need a different boot parameter for Intel video.

---

### Post by Juan_Fiorenzano on 2016-06-11
Yes I am booting in UEFI mode I can see the GRUP menu screen, I have a nVidia card but I think my primary card is the Intel video card, in the bios options doesn't appear anything about nvidia and when I am in Windows the active video card is the intel's except when I am running a game, all the games run in my nvidia video card. My processor it's a Skylake what are this special boot parameter you've been talking about? I don't understand what does my video card have to do with the problem of the space?

---

### Post by oldfred on 2016-06-11
I thought maybe you were not getting correctly to the install options.

Does system boot into live mode ok?
You said you added partitions for Ubuntu, post this:
sudo parted -l

You should then be using the Something Else install option and choose partition(s) you created. Use change button, ext4 and / (root). Same if you created partition for /home. If you have swap already, it should just auto find & use it.

---

### Post by Juan_Fiorenzano on 2016-06-11
> **oldfred said:**
> I thought maybe you were not getting correctly to the install options.

Does system boot into live mode ok?

The system boot into live mode, but in the same way it send me the error message that I don't have space on the disk, but in this case I can ignore the message and continue with my work.

> **oldfred said:**
> You said you added partitions for Ubuntu, post this:
sudo parted -l

this is my partition table right now:
```
[COLOR=#000000][FONT=&amp]Model: ATA HGST HTS721010A9 (scsi)[/FONT][/COLOR]Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  274MB   273MB   fat32           EFI system partition          boot, esp
 2      274MB   290MB   16.8MB                  Microsoft reserved partition  msftres
 3      290MB   400GB   399GB   ntfs            Basic data partition          msftdata
 4      400GB   400GB   523MB   ntfs            Basic data partition          hidden, diag
 5      400GB   895GB   495GB   ntfs            Basic data partition          msftdata
 6      895GB   982GB   87.0GB  ext4
 7      982GB   1000GB  17.8GB  linux-swap(v1)


Model: SanDisk Ultra USB 3.0 (scsi)
Disk /dev/sdb: 30.8GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags [COLOR=#000000][FONT=&amp] 1      1049kB  30.8GB  30.8GB  fat32        Microsoft Basic Data  msftdata
[/FONT][/COLOR]
```

> **oldfred said:**
> You should then be using the Something Else install option and choose partition(s) you created. Use change button, ext4 and / (root). Same if you created partition for /home. If you have swap already, it should just auto find & use it.

I can not move to the step where I select the Something Else install option, the error occur in the step before
[Install Dialog]("https://drive.google.com/open?id=0BxNi9b3FMfkdRFlyaVZManE4SVk")

---

### Post by oldfred on 2016-06-11
Is  drive set for AHCI, not RAID nor IDE? Or some Intel SRT type things that interfere?
Also some drives get locked in UEFI/BIOS. But since you were able to add the partitions that should not be the issue.

Did you verify download was correct?
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Juan_Fiorenzano on 2016-06-11
> **oldfred said:**
> Is  drive set for AHCI, not RAID nor IDE? Or some Intel SRT type things that interfere?
Also some drives get locked in UEFI/BIOS. But since you were able to add the partitions that should not be the issue.

Yes, the drive is set for AHCI and is the only option available.

> **oldfred said:**
> 
Did you verify download was correct?
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Yes I already verify the MD5 sum and it is correct.

---

### Post by oldfred on 2016-06-12
I am out of ideas.

Perhaps something mentioned in these similar Asus systems.
 ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)
ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Installing 15.04 on Asus N550JX, boot parameters required
[http://ubuntuforums.org/showthread.php?t=2293394](http://ubuntuforums.org/showthread.php?t=2293394)

---

### Post by Juan_Fiorenzano on 2016-06-12
> **oldfred said:**
> 
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)

This post has the same problem that I am, I am trying to use the boot option pci=nomsi, but I don't know where I have to put this command, when the boot screen appear I type c and I write pci=nomsi in the command line after that I press esc and select install ubuntu, but I still having the same problem, so I don't know If I am doing well.

---

### Post by Juan_Fiorenzano on 2016-06-12
Ok, at last I could install Ubuntu, instead of type "c" in the boot menu I type "e" and write pci=nomsi before the "quite slash" option, and everything works, but after install I still having problems, now is another problem but I think that is for other thread, now when I select boot for Ubuntu this appear in my screen : [screen image]("https://drive.google.com/open?id=0BxNi9b3FMfkdY3J3UloyNkRoUmM") when this happens I have to reboot and when the system start is painfully slow and others error messages are shows.

---

### Post by bamhamyt on 2016-06-12
Hi i may know how to solve that, you should create a bootable usb for linux there are many tutorials on youtube to do that but that might be more time consuming i failed once and had to restart ;)

---

### Post by Juan_Fiorenzano on 2016-06-12
> **bamhamyt said:**
> Hi i may know how to solve that, you should create a bootable usb for linux there are many tutorials on youtube to do that but that might be more time consuming i failed once and had to restart ;)

I don't understand what do you mean, I already have a bootable usb for linux.

---

### Post by Juan_Fiorenzano on 2016-06-12
Ok I still have the same problem I dont have enough space on the disk, the disk has 80gb and only the var folder has 77gb occupied how is this possible? is it normal that the system fill 77gb during the installation? look at this [image ]("https://drive.google.com/open?id=0BxNi9b3FMfkdVEYxSVRGY0pHU2M")the space distribution, I didn't mark the option of install third party software and I didn't install any software so, what is happening?
When I shutdown the system this [screen]("https://drive.google.com/open?id=0BxNi9b3FMfkdb185U2ptLWlmVTg") appear and I have to press the shutdown button on the laptop.

---

### Post by lisati on 2016-06-12
> **bamhamyt said:**
> Hi i may know how to solve that, you should create a bootable usb for linux there are many tutorials on youtube to do that but that might be more time consuming i failed once and had to restart ;)

Have a look here: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by lliseil on 2016-06-12
OK it's late thought a couple words shoudn't hurt.

1) The NTFS partition wa *consistent* right?

2) Reading other threads with the same issue it appears adding the following option at boot did solve the 'no space' issue.

> I am trying to use the boot option pci=nomsi, but I don't know where I have to put this command, when the boot screen appear I type c and I write pci=nomsi in the command line

Press [F6] during boot so you can see additional options. Choose `nodmraid`. At this point you can also write whatever you want to test eg. `nomsi`. See the community [BootOptions page]("https://help.ubuntu.com/community/BootOptions") on Ubuntu.com.

---

### Post by oldfred on 2016-06-12
If you needed pci=nomsi to install, you may need it all the time.
On first boot into your install you can add it they same way with e on grub menu and replace quiet splash.

If you do not get grub menu, then if UEFI install press escape key or if BIOS boot press and hold shift key from BIOS screen until grub menu appears. 

If that entry is the correct one, then we can make it a permanent part of grub.

       GRUB_CMD_LINUX_DEFAULT="quiet splash"
[URL="http://www.kernel.org/doc/Documentation/kernel-parameters.txt"]http://www.kernel.org/doc/Documentation/kernel-parameters.txt
[/URL]
 sudo nano /etc/default/grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)

GRUB_CMD_LINUX
Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel.
 
GRUB_CMD_LINUX_DEFAULT="quiet splash"
This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only.     
o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash".  

[URL="http://www.kernel.org/doc/Documentation/kernel-parameters.txt"]
[/URL]

---

### Post by Juan_Fiorenzano on 2016-06-12
I solved the problem finally, I had to modify the grup for always use pci=nomsi and after that I cleaned the logs, when I boot using pci=nomsi my logs files doesn't grow so alarmingly. The messages in the logs was the same that appeared in the terminal when I shutdown/restart the pc, with pci=nomsi all my problems with the space has gone. Thank you everyone for your help, especially to oldfred. This thread was solved :).

---

### Post by lisati on 2016-06-12
> **Juan_Fiorenzano said:**
> I solved the problem finally,.

I've marked your thread "solved" for you. This can usually be done by clicking on Thread Tools -> Mark thread as solved.

---

