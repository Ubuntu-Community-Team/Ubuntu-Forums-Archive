---
title: "Ubuntu 12.04 (32 bit) won't install on HP Pavilion p6-2003w"
date: 2013-11-19
forum: Installation &amp; Upgrades
---

### Post by stanleytswincher on 2013-11-19
Hello everyone,

I've had trouble trying to install Ubuntu 12.04 from DVD-R.

Here are the details of my computer

OS: Windows 7 (32 bit) Home Premium
HP Pavilion - Desktop
Model No. P6-2003w
RAM: 4GB
Processor: AMD E2-3200 APU with Radeon(tm) HD Graphics 2.40 GHz

For the last several days I've tried to install Ubuntu, I've had no luck.
My  other computer which is custom-built for my father, was running vista  with 2gb RAM, Ubuntu installed correctly, I've also installed Ubuntu  once before earlier this year on an older computer.
Every time I run  it through wubi, my PC will restart, and make it to the first screen  with the rectangle and circle logo at the bottom of the screen,
after  that the screen goes blank and the monitor flashes off. The monitor  then comes back on only to say "Monitor going to sleep",
the monitor  will then stay asleep or it will just keep flashing the going to sleep  message. I have tried disabling UEI settings in BIOS, my friend told me  that might work and it didn't.
I don't know what else I can do.

Please help if you can, I'd greatly appreciate it!

Take care

---

### Post by fantab on 2013-11-19
First of all, why 32bit Ubuntu, your processor supports 64bit, doesn't it? Check if 64bit Ubuntu works.
Are you able to "Try Ubuntu Without Installing" option?

Are you trying to install via WUBI? If you are don't, it not well supported anymore. Consider true dualboot. 
Also if Windows is booting in UEFI then perhaps WUBI will NOT work. Though I am not 100% sure about this. Anyways, WUBI is a bad idea.

From the description you gave of the problem, it sounds to me lika a graphic card issue. Read and use **[NOMODESET]("http://ubuntuforums.org/showthread.php?t=1613132")** at boot.
Are you able to "Try Ubuntu Without Installing" option? Try it with 'nomodeset'. If you are able to reach the desktop, then post the output of:

```
sudo parted -l
sudo fdisk -l
```

---

### Post by stanleytswincher on 2013-11-19
Thanks for the quick reply.

I'm currently out of blank DVDs to burn Ubuntu 64 bit, which I'll be going to buy some later today. That's why I've been trying to install 32bit.
I was using WUBI, thanks for telling me that it's not well supported anymore though.

I will try using nomodeset at boot, then I'll come back and tell you if the problem still occurs. That's if I can try Ubuntu without installing.

Thanks again

EDIT: Can't try without installing, going to try with the 64bit version today of 12.04 or probably just try 13.10.

---

### Post by stanleytswincher on 2013-11-19
So I burned Ubuntu 13.10 64bit and then booted my pc.

I got to a black screen that said

Try Ubuntu without installing
Install Ubuntu
OEM install (for manufacturers)
Check disc for defects

I tried with and without installing Ubuntu.
 I didn't even make it to the first screen with the rectangle and little circle.
The screen was black for a few seconds then my monitor went off came back on and repeated flashing every few seconds with
"Monitor going to sleep".

Any suggestions I can do? Also at the bottom of the screen it said

"Use the ^ and V keys to select which entry is highlighted.
Press enter to boot the selected OS, `e' to edit the commands before booting or `c'
for a command-line. ESC to return previous menu."

Thanks

---

### Post by fantab on 2013-11-19
Does your computer boot in UEFI? If you do then you won't see "*the first screen with the rectangle and the little circle*", The black screen with options is 'the first screen'. [Check THIS]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode") and confirm which Ubuntu screen do you see.
When you boot your DVD/USB make sure you don't load the option with [U]EFI. 32bit Windows won't boot in EFI mode, however since what you describe sounds like the DVD/USB is booting in UEFI mode.
Check in your BIOS under something like 'Boot' or 'Boot configuration' and confirm if you see UEFI. Read the above linked webpage.
Can you post a Screen-Shot of your Hard-disk Partitions from Windows? 
Have you tried the NOMODESET option, as suggested earlier? This option loads the basic opensource Graphic driver and lets you boot with minimum graphics enhancements. If there is a problem with your Graphics card then this should take care of it.

---

### Post by stanleytswincher on 2013-11-19
When I booted the 64bit disc it showed the black screen
When I booted the 32bit disc it showed the purple screen

I am currently running the 32bit installation disc with nomodeset on "Try Ubuntu without installing" now the only problem I have is if I install Ubuntu then restart my pc it will revert back to original and nomodeset will be off again. I don't know how to make it permanent. I saved the boot option with the command

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```But in terminal when I try typing in```
sudo update-grub
```It shows

```
/usr/sbin/grub-probe: error: failed to get canonical path of /cow.
```

I don't know what that means or if it saved or not.

---

### Post by fantab on 2013-11-19
You don't have to worry about making it permanent as yet, also you can't make it permanent on Live DVD. NOMODESET is temporary option, unless really needed, until you install the proper graphic driver.
12.04 has been reporting problems the kind you describe. Try Ubuntu 13.10 64bit.

Also post the output of the the following from the Terminal [Ctrl+Alt+T]:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by stanleytswincher on 2013-11-20
Alright, thanks for all the help.

Running 13.10 64bit with NOMODESET on, try without installing.

I typed the code in and got this, I hope this is what you wanted me to post.

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA Hitachi HDS72101 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name                  Flags
 1      1049kB  512MB  511MB  ntfs         EFI System Partition  boot


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3be13be1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
ubuntu@ubuntu:~$ 


```

---

### Post by fantab on 2013-11-20
There is no Windows installed. Did you remove it? 

You have GPT partition table. From this table Windows can ONLY boot in EFI, and only 64bit OS. 
There is an EFI partition on the HDD. And this is the only partition you have. However, this partition is incorrectly formatted with NTFS, it should be FAT32.

What you want to do? Do you want to install both Windows and Ubuntu as dual-boot or instal only Ubuntu?
Do you have a copy of 64bit Windows?
If you are stuck with 32bit Windows then you CAN'T use your HDD in its current setup, you will need to covert the GPT disk to 'msdos'.

Please clarify the above questions....

---

### Post by stanleytswincher on 2013-11-20
I did remove WIndows earlier when I installed Ubuntu,
when I thought setting nomodeset to be permanent was my only option.

I want to run Ubuntu only.
I do not have a copy of 64bit Windows.

Edit: To be honest I don't know why my pc came with 32bit Windows 7 in the first place.

---

### Post by fantab on 2013-11-20
EDIT: Are you sure that your desktop came with 32bit Windows. Check again and confirm. Because you have GPT table on HDD, Win32 will never have installed there. Only 64bit Windows would. Unless you have changed the partition table from 'msdos' to 'GPT'.

Start with reformatting your First partition on HDD to FAT32 and put a 'boot' flag on it. Then Create partitions on HDD. If I were you I do the following:
> 511Mb FAT32 EFI 'boot' flag
100GB NTFS [In case I decide on installing Windows 64bit at a later date,] Ubuntu can read/write NTFS partition.
25GB EXT4 / Ubuntu system files
25GB EXT4 Free [If in future I decide to try another Linux distro or another version of Ubuntu or flavor]
25GB EXT4 Free ["]
5GB SWAP
All the remaining GB EXT4 [DATA Partition: you can either use this as /home or just plain partition without any mountpoint]

You should use GPARTED from the Ubuntu DVD/USB you have in 'Try Without installing' mode.

Once the HDD is setup, choose to install Ubuntu from the desktop.
At the "Installation Type' screen choose 'Something Else' option. This option lets you manually install Ubuntu to the already created partitions.
At this stage the Installer will open a 'Disk management dialog. Select the first 25GB partition and choose the following settings:
USE AS = Ext4
Mountpoint = /
Format = check the box.

If you want a /home partition then select the Partition with 'All the remaining GB' and:
USE As = Ext4
Mountpoint = /home
Format = check the box.
If you don't want separate /home then skip the above step.

Here's a small note: Make sure when you boot the 13.10 Ubuntu DVD/USB, it boots in UEFI mode. How you boot is how you install. You will be able to install in UEFI mode only if you boot the DVD/USb in EFI mode.
This should help you figure out how you boot: [https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode](https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode) 


Thats it. Continue with installation.

When you boot your installed Ubuntu for the first time use NOMODESET, if you boot to a black screen. Then From update-manager's 'Additional Drivers' find the driver for your Graphics card and install it. Reboot to check.

Good Luck.

---

