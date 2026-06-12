---
title: "Destroyed My OS"
date: 2016-03-29
forum: Installation &amp; Upgrades
---

### Post by utnubu4 on 2016-03-29
Hey folks,

I have been running ubuntu live straight from my USB flash drive, i managed to get my wireless internet working with an update and driver installation. After roaming around ubuntu i made the decision to install ubuntu permanently as my main and only OS. Within a very short period of beginning the installation it failed, this happened on numerous occasions afterwards, it stated that my disk may be damaged or my CD/DVD drive, as you know i was attempting to install from my live USB. After rebooting my laptop and removing the flash drive i realized that my windows OS had been destroyed. I currently have no OS now and this worries me a lot, my only OS is a live version of ubuntu through my USB flash drive. Please help me guys, i need a HDD OS. How can i install ubuntu to my HDD. Do i need a disk with ubuntu on and if so will the disk function from the live flash drive version?

---

### Post by sudodus on 2016-03-29
If there are important files that you want to save from the internal hard disk drive, you should start by cloning it with ddrescue, and do the repair work on a cloned copy. This reduces the risk of destroying what is left.

If there is nothing to save from the internal hard disk drive, I suggest that you use the option **'Erase disk and install Ubuntu'** at the window 'Installation type' of the installer.

So this is the first thing you have to decide and tell us.

-o-

Next we can start talking about installing Ubuntu:

Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Also: while booted into the live Ubuntu system, please run the following commands in a terminal window and post the result in a reply.

```
df
sudo parted -ls  #space minus ell ess
sudo lsblk -fm
```

Knowing this makes it easier to help.

---

### Post by utnubu4 on 2016-03-29
Thank you for the reply!

That is the option i picked when i attempted to install ubuntu 'erase disk and install ubuntu', i picked this option because i did not want windows anymore. The installation failed very quickly but my HDD still got wiped including windows OS.

My laptop: Toshiba Satellite C55-C-1M9
CPU: Intel Celeron N2830 2.16 GHz
RAM: 4GB
Graphics chip/card: Intel  HD Graphics (integrated)
WIFI chip/card: Broadcom BCM43142

This is all of the information retrieved from the terminal commands.

 df:

Filesystem     1K-blocks    Used Available Use% Mounted on
udev             1951580       4   1951576   1% /dev
tmpfs             392684    1208    391476   1% /run
/dev/sdb1       15170560 1045968  14124592   7% /cdrom
/dev/loop0        999296  999296         0 100% /rofs
/cow             1963420   48200   1915220   3% /
none                   4       0         4   0% /sys/fs/cgroup
tmpfs            1963420    1028   1962392   1% /tmp
none                5120       0      5120   0% /run/lock
none             1963420      76   1963344   1% /run/shm
none              102400      64    102336   1% /run/user



sudo parted -ls #space minus ell ess:

Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  538MB   537MB   fat32                 boot
 2      538MB   996GB   995GB   ext4
 3      996GB   1000GB  4171MB  linux-swap(v1)


Model: SanDisk Ultra (scsi)
Disk /dev/sdb: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.6GB  15.6GB  primary  fat32        boot, lba



sudo lsblk -fm:

NAME   FSTYPE   LABEL       MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                                    sda    931.5G root  disk  brw-rw----
&#9500;&#9472;sda1 vfat                            &#9500;&#9472;sda1   512M root  disk  brw-rw----
&#9500;&#9472;sda2 ext4                            &#9500;&#9472;sda2 927.1G root  disk  brw-rw----
&#9492;&#9472;sda3 swap                 [SWAP]     &#9492;&#9472;sda3   3.9G root  disk  brw-rw----
sdb                                    sdb     14.5G root  disk  brw-rw----
&#9492;&#9472;sdb1 vfat     UBUNTU 14_0 /cdrom     &#9492;&#9472;sdb1  14.5G root  disk  brw-rw----
sr0                                    sr0     1024M root  cdrom brw-rw----
loop0  squashfs             /rofs      loop0  975.9M root  disk  brw-rw----

---

### Post by sudodus on 2016-03-29
Your computer is powerful enough for Ubuntu :-)

The graphics should work, but I think you will have to install a proprietary driver for the Broadcom wifi.

Install ***without*** trying to download or update any files. You should fix that later on.
[hr][/hr]
I have a similar Toshiba computer, but soon 3 years old. Ubuntu works in UEFI as well as in BIOS mode in that computer. BIOS mode is called CSM in the boot menus.

I know that there are problems installing linux into some new Toshibas, but I think it is in UEFI mode, necessary when you want to keep Windows. If there is an option to select BIOS alias CSM mode, it might be easier to install Ubuntu. (I suggest that you select CSM mode if you can find it.)
[hr][/hr]
You have a GUID partition table, GPT, in the installed disk. I suggest that you install and use mkusb to wipe the first megabyte and after that create a new partition table. That way you should get rid of data, that might disturb the installation.

[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

You need to 'toggle USB only' to be able to 'see and be able to select' your internal drive in mkusb.

1. If you want to keep using the modern GPT, you can use "Advanced: create GUID partition table (skeleton for installing an OS)". In this case you should not erase the disk, but create partitions with ***gparted***, say 5 GB swap, and the rest of the unallocated drive space for the root partition with ext4 file system.

After that start the installer. Select ***'Something else'*** at the partitioning page and select the partitions that you created with gparted. (In UEFI mode you must use GPT, in BIOS alias CSM mode it is an option.)

2. If you want to use the old style MSDOS partition table, you can use "Standard: create MSDOS partition table with FAT32 partition". After that it should work to install Ubuntu in BIOS alias CSM mode, and 'erase disk and install ubuntu'. (This is the easiest option.)
[hr][/hr]
***Edit:*** Ubuntu is installed in the same mode as you are booting from the USB pendrive. You can find out by running the following command

```
test -d /sys/firmware/efi && echo efi || echo bios
```

See more at the following link:

[Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

---

### Post by retr02 on 2016-03-29
Not my best area but:

Boot into the live environment

If you want it as full OS, run gparted

Select your disk, probably /dev/sda

Right click and remove all of the partitions

Now apply the changes and open the installer.

It should say "Erase disk and install ubuntu"

Choose that option, it will now install.

GL ~ :D

---

### Post by kansasnoob on 2016-03-29
> Within a very short period of beginning the installation it failed, this happened on numerous occasions afterwards, it stated that my disk may be damaged or my CD/DVD drive

Boot the live USB and run Check disc for defects from the advanced boot menu:

[https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options](https://help.ubuntu.com/community/BootOptions#Ubuntu_CD_Advanced_Welcome_Page_Options)

Don't blink because you have about 3 seconds after the keyboard=human icon appears to press a key. If that test shows any defects then you need to create a new live USB/DVD before proceeding.

I wouldn't bother enabling wireless on the live DE. You won't be able to download updates or install 3rd party software during installation but that can be sorted out later. Or you could use a wired network connection for the installation if possible.

---

### Post by utnubu4 on 2016-03-29
Hey guys,

I have tried the method provided from sododus with no luck. But i did manage to change to CSM Bios.

I have tried the method from retr02 with no luck either.

I did Boot the live USB and run Check disc for defects and 1 defect was shown, but i think i know what this defect is... after installing the ISO to the flash drive using Rufus i created a folder in the flash drive with all of my files and documents on, could this be the source of my issue?

I have attempted to remove the file i created but as i have no root permission access i can not delete the folder, i can not make a new ISO because i do not have any permissions to remove anything from the flash drive. When i attempted to give the folder access to be able to delete i get this message 'net usershare' returned error 255: net usershare add: cannot share path /cdrom/My Stuff as we are restricted to only sharing directories we own. Ask the administrator to add the line "usershare owner only = false" to the [global] section of the smb.conf to allow this.

---

### Post by kansasnoob on 2016-03-29
Any errors at all are likely preventing the live installer from functioning properly. I've never used Rufus but I see the downloads are .exe so I assume it's software for Windows? So you'll be using Windows to create a new live USB?

I've only created live USB's in Linux for the last 9 years or so, so I don't know about Windows, but in Ubuntu I typically have to use Gparted to create a new partition table on the flash drive and then create a FAT 32 partition. I have no idea what Windows utilities are available for creating a new partition table and reformatting the flash drive so it can be reused :redface:

---

### Post by utnubu4 on 2016-03-29
> **kansasnoob said:**
> Any errors at all are likely preventing the live installer from functioning properly. I've never used Rufus but I see the downloads are .exe so I assume it's software for Windows? So you'll be using Windows to create a new live USB?

I've only created live USB's in Linux for the last 9 years or so, so I don't know about Windows, but in Ubuntu I typically have to use Gparted to create a new partition table on the flash drive and then create a FAT 32 partition. I have no idea what Windows utilities are available for creating a new partition table and reformatting the flash drive so it can be reused :redface:


That is my issue, windows was destroyed and removed from my hard drive the first time i attempted to install ubuntu. I have no other access to a pc or laptop so i am unsure how i can remove the files from my flash drive and create a new ISO. do you please know the command line for this 'net usershare' returned error 255: net usershare add: cannot share path  /cdrom/My Stuff as we are restricted to only sharing directories we  own. Ask the administrator to add the line "usershare owner only =  false" to the [global] section of the smb.conf to allow this.

---

### Post by kansasnoob on 2016-03-29
I don't think you can fix a borked .iso. Can you get someone with another computer to help you create a new live USB? Sometimes libraries have live DVD's that can be borrowed.

---

### Post by utnubu4 on 2016-03-29
I can try but it's not going to be any time soon and i really wanted the issue fixed as soon as possible.

I am certain that i know what the ISO defect is though, a folder i created with my files in. Surly if i remove that folder and i run a defect test and everything is okay it should install, right?

The ubuntu live runs with no issues whatsoever.

---

### Post by kansasnoob on 2016-03-29
I have serious doubts that will work, but I suppose it's possible :confused:

My fear is that you'll render that live USB totally unusable and then be stuck with no means to communicate :(

If you know the path to the file you can possibly using sudo rm whatever_file_path. Sometimes it's easier change directory using cd to simplify the path_to_file, eg;

I want to delete the file ubi_crash.JPG from my Desktop so I cd to Desktop, use ls to list the files/folders, and then use rm:

```
lance@lance-desktop:~$ cd Desktop
lance@lance-desktop:~/Desktop$ ls
bad~            failed_upgrade_2                         ubi_crash.JPG
BugsRUs~        gut.abw                                  Untitled Document~
Edubuntu        paint                                    Untitled Document 1
failed_upgrade  Screenshot from 2016-03-18 07:21:21.png  Which_Ubuntu~
lance@lance-desktop:~/Desktop$ rm ubi_crash.JPG
lance@lance-desktop:~/Desktop$ ls
bad~            failed_upgrade_2                         Untitled Document~
BugsRUs~        gut.abw                                  Untitled Document 1
Edubuntu        paint                                    Which_Ubuntu~
failed_upgrade  Screenshot from 2016-03-18 07:21:21.png

```

Of course since Desktop is in home no sudo is needed which will likely not be the case in your situation.

---

### Post by sudodus on 2016-03-29
Am I understanding things correctly: You *can* boot from your USB drive and run a live Ubuntu system.

In that case, fine :-) Don't try to fix the USB drive!

Boot again. Directly after booting, in the menu that starts with 'Try Ubuntu ...', select 'Check disc for defects' and check if all the installed packages are good.

Boot once more, this time into Ubuntu and use the tools that are available in the live session. If it is live-only, it means that you lose mkusb (but it can be re-installed if necessary). At this moment I suppose that your internal drive has a new partition table. Please run the following commands (again)

```
df
sudo parted -ls  #space minus ell ess
sudo lsblk -fm
test -d /sys/firmware/efi && echo efi || echo bios
```

This time, please click on the big red button [COLOR="#FF0000"]Go Advanced[/COLOR], copy the output of the commands to the reply window, mark it and click on the **#** icon above the reply window to put it within [noparse]```
tags
```[/noparse], and we have better chances to help you take the next steps:

- Are you running in BIOS alias CSM mode now?
- Is your partition table good for installing in this mode?

Also, please reply with a detailed description what happens, when the installations fails :-)

---

### Post by kansasnoob on 2016-03-29
> Boot again. Directly after booting, in the menu that starts with 'Try Ubuntu ...', select 'Check disc for defects' and check if all the installed packages are good.

They already did that and it said one defect found:

[http://ubuntuforums.org/showthread.php?t=2318774&p=13462481#post13462481](http://ubuntuforums.org/showthread.php?t=2318774&p=13462481#post13462481)

AFAIK a borked live USB is just borked.

---

### Post by sudodus on 2016-03-29
Let us wait for *utnubu4* to tell us what is the current status of this issue. What is the known defect?

Until then we can hope the best or fear the worst or both at the same time :-P

---

### Post by kansasnoob on 2016-03-29
> **sudodus said:**
> Let us wait for *utnubu4* to tell us what is the current status of this issue. What is the known defect?

Until then we can hope the best or fear the worst or both at the same time :-P

Check disc for defects never tells you what the defect is, just the number of defects found.

---

### Post by utnubu4 on 2016-03-29
I have tried to make a partition but i am unsure if its correct. Here are the results you asked for.


df

Filesystem     1K-blocks    Used Available Use% Mounted on
udev             1953200      12   1953188   1% /dev
tmpfs             393008    1232    391776   1% /run
/dev/sdb1       15170560 1047136  14123424   7% /cdrom
/dev/loop0        999296  999296         0 100% /rofs
/cow             1965040  252280   1712760  13% /
none                   4       0         4   0% /sys/fs/cgroup
tmpfs            1965040    1132   1963908   1% /tmp
none                5120       4      5116   1% /run/lock
none             1965040      80   1964960   1% /run/shm
none              102400      76    102324   1% /run/user




sudo parted -ls  #space minus ell ess


Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      27.9GB  996GB   968GB   primary   fat32
 2      996GB   1000GB  4173MB  extended
 5      996GB   1000GB  4173MB  logical   linux-swap(v1)


Model: SanDisk Ultra (scsi)
Disk /dev/sdb: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.6GB  15.6GB  primary  fat32        boot, lba




sudo lsblk -fm

NAME   FSTYPE   LABEL       MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                                    sda    931.5G root  disk  brw-rw----
&#9500;&#9472;sda1 vfat                            &#9500;&#9472;sda1 901.7G root  disk  brw-rw----
&#9500;&#9472;sda2                                 &#9500;&#9472;sda2     1K root  disk  brw-rw----
&#9492;&#9472;sda5 swap                 [SWAP]     &#9492;&#9472;sda5   3.9G root  disk  brw-rw----
sdb                                    sdb     14.5G root  disk  brw-rw----
&#9492;&#9472;sdb1 vfat     UBUNTU 14_0 /cdrom     &#9492;&#9472;sdb1  14.5G root  disk  brw-rw----
sr0                                    sr0     1024M root  cdrom brw-rw----
loop0  squashfs             /rofs      loop0  975.9M root  disk  brw-rw----



The last command gives me nothing in the terminal.

---

### Post by sudodus on 2016-03-29
> **kansasnoob said:**
> Check disc for defects never tells you what the defect is, just the number of defects found.

If the live system works, you can do it 'manually' like this (the commands are [COLOR="#0000FF"]blue[/COLOR])


```

lubuntu@lubuntu:~$ [COLOR="#0000FF"]cd /cdrom[/COLOR]
lubuntu@lubuntu:/cdrom$ [COLOR="#0000FF"]ls[/COLOR]
boot/    dists/    isolinux/   pics/  preseed/            ubuntu@
casper/  install/  md5sum.txt  pool/  README.diskdefines
lubuntu@lubuntu:/cdrom$ [COLOR="#0000FF"]md5sum -c md5sum.txt[/COLOR] 
./pics/red-upperleft.png: OK
./pics/red-lowerleft.png: OK
./pics/blue-lowerleft.png: OK
./pics/logo-50.jpg: OK
./pics/blue-upperright.png: OK
./pics/blue-lowerright.png: OK
./pics/red-lowerright.png: OK
./pics/blue-upperleft.png: OK
./pics/debian.jpg: OK
./pics/red-upperright.png: OK
./preseed/lubuntu.seed: OK
./preseed/cli.seed: OK
./pool/restricted/s/sl-modem/sl-modem-daemon_2.9.11~20110321-12_i386.deb: OK
./pool/universe/libc/libcapi20-3/libcapi20-3_3.27-1_i386.deb: OK
./pool/universe/libc/libcapi20-3/libcapi20-dev_3.27-1_i386.deb: OK
./pool/universe/c/caspar/caspar_20140919-1_all.deb: OK
./pool/universe/i/isdnutils/capiutils_3.25+dfsg1-3.7ubuntu1_i386.deb: OK
./pool/universe/i/isdnutils/isdnutils-xtools_3.25+dfsg1-3.7ubuntu1_i386.deb: OK
./pool/universe/i/isdnutils/isdnutils-base_3.25+dfsg1-3.7ubuntu1_i386.deb: OK
./pool/universe/i/isdnutils/pppdcapiplugin_3.25+dfsg1-3.7ubuntu1_i386.deb: OK
./pool/multiverse/d/drdsl/drdsl_1.2.0-3_i386.deb: OK
./pool/main/m/mouseemu/mouseemu_0.16-0ubuntu9_i386.deb: OK
./pool/main/m/manpages/manpages-dev_4.04-2_all.deb: OK
./pool/main/m/make-dfsg/make_4.1-6_i386.deb: OK
./pool/main/l/linux/linux-libc-dev_4.4.0-15.31_i386.deb: OK
./pool/main/l/lupin/lupin-support_0.57_i386.deb: OK
./pool/main/g/gcc-defaults/g++_5.3.1-1ubuntu1_i386.deb: OK
./pool/main/g/gcc-defaults/gcc_5.3.1-1ubuntu1_i386.deb: OK
./pool/main/g/glibc/libc-dev-bin_2.23-0ubuntu2_i386.deb: OK
./pool/main/g/glibc/libc6-dev_2.23-0ubuntu2_i386.deb: OK
./pool/main/g/gcc-5/libmpx0_5.3.1-12ubuntu4_i386.deb: OK
./pool/main/g/gcc-5/libcc1-0_5.3.1-12ubuntu4_i386.deb: OK
./pool/main/g/gcc-5/libitm1_5.3.1-12ubuntu4_i386.deb: OK
./pool/main/g/gcc-5/libstdc++-5-dev_5.3.1-12ubuntu4_i386.deb: OK
./pool/main/g/gcc-5/libcilkrts5_5.3.1-12ubuntu4_i386.deb: OK
./pool/main/g/gcc-5/libasan2_5.3.1-12ubuntu4_i386.deb: OK
./pool/main/g/gcc-5/g++-5_5.3.1-12ubuntu4_i386.deb: OK
./pool/main/g/gcc-5/libgcc-5-dev_5.3.1-12ubuntu4_i386.deb: OK
./pool/main/g/gcc-5/libubsan0_5.3.1-12ubuntu4_i386.deb: OK
./pool/main/g/gcc-5/libatomic1_5.3.1-12ubuntu4_i386.deb: OK
./pool/main/g/gcc-5/gcc-5_5.3.1-12ubuntu4_i386.deb: OK
./pool/main/b/build-essential/build-essential_12.1ubuntu2_i386.deb: OK
./pool/main/liba/libalgorithm-diff-xs-perl/libalgorithm-diff-xs-perl_0.04-4build1_i386.deb: OK
./pool/main/liba/libalgorithm-merge-perl/libalgorithm-merge-perl_0.08-3_all.deb: OK
./pool/main/liba/libalgorithm-diff-perl/libalgorithm-diff-perl_1.19.03-1_all.deb: OK
./pool/main/libf/libfile-fcntllock-perl/libfile-fcntllock-perl_0.22-3_i386.deb: OK
./pool/main/u/user-setup/user-setup_1.63ubuntu2_all.deb: OK
./pool/main/u/ubiquity/oem-config-gtk_2.21.52_all.deb: OK
./pool/main/u/ubiquity/oem-config_2.21.52_all.deb: OK
./pool/main/d/dpkg/dpkg-dev_1.18.4ubuntu1_all.deb: OK
./pool/main/d/dpkg/libdpkg-perl_1.18.4ubuntu1_all.deb: OK
./pool/main/f/fakeroot/fakeroot_1.20.2-1ubuntu1_i386.deb: OK
./pool/main/f/fakeroot/libfakeroot_1.20.2-1ubuntu1_i386.deb: OK
./.disk/info: OK
./.disk/base_installable: OK
./.disk/casper-uuid-generic: OK
./.disk/cd_type: OK
./.disk/release_notes_url: OK
./boot/grub/loopback.cfg: OK
./casper/filesystem.size: OK
./casper/filesystem.manifest: OK
./casper/filesystem.squashfs: OK
./casper/initrd.lz: OK
./casper/filesystem.manifest-remove: OK
./casper/vmlinuz: OK
./README.diskdefines: OK
./dists/xenial/restricted/binary-i386/Release: OK
./dists/xenial/restricted/binary-i386/Packages.gz: OK
./dists/xenial/Release: OK
./dists/xenial/Release.gpg: OK
./dists/xenial/universe/binary-i386/Release: OK
./dists/xenial/universe/binary-i386/Packages.gz: OK
./dists/xenial/multiverse/binary-i386/Release: OK
./dists/xenial/multiverse/binary-i386/Packages.gz: OK
./dists/xenial/main/binary-i386/Release: OK
./dists/xenial/main/binary-i386/Packages.gz: OK
./install/mt86plus: OK
./install/sbm.bin: OK
./install/README.sbm: OK
lubuntu@lubuntu:/cdrom$ 

```

And you will be able to inspect the output of the command **md5sum -c md5sum.txt** to find which package is bad (if any).

---

### Post by sudodus on 2016-03-29
> **utnubu4 said:**
> I have tried to make a partition but i am unsure if its correct. Here are the results you asked for.


```
[COLOR="#0000FF"]df[/COLOR]
Filesystem     1K-blocks    Used Available Use% Mounted on
udev             1953200      12   1953188   1% /dev
tmpfs             393008    1232    391776   1% /run
/dev/sdb1       15170560 1047136  14123424   7% /cdrom
/dev/loop0        999296  999296         0 100% /rofs
/cow             1965040  252280   1712760  13% /
none                   4       0         4   0% /sys/fs/cgroup
tmpfs            1965040    1132   1963908   1% /tmp
none                5120       4      5116   1% /run/lock
none             1965040      80   1964960   1% /run/shm
none              102400      76    102324   1% /run/user

[COLOR="#0000FF"]sudo parted -ls[/COLOR]  #space minus ell ess
Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      27.9GB  996GB   968GB   primary   fat32
 2      996GB   1000GB  4173MB  extended
 5      996GB   1000GB  4173MB  logical   linux-swap(v1)


Model: SanDisk Ultra (scsi)
Disk /dev/sdb: 15.6GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  15.6GB  15.6GB  primary  fat32        boot, lba

[COLOR="#0000FF"]sudo lsblk -fm[/COLOR]
NAME   FSTYPE   LABEL       MOUNTPOINT NAME     SIZE OWNER GROUP MODE
sda                                    sda    931.5G root  disk  brw-rw----
&#9500;&#9472;sda1 vfat                            &#9500;&#9472;sda1 901.7G root  disk  brw-rw----
&#9500;&#9472;sda2                                 &#9500;&#9472;sda2     1K root  disk  brw-rw----
&#9492;&#9472;sda5 swap                 [SWAP]     &#9492;&#9472;sda5   3.9G root  disk  brw-rw----
sdb                                    sdb     14.5G root  disk  brw-rw----
&#9492;&#9472;sdb1 vfat     UBUNTU 14_0 /cdrom     &#9492;&#9472;sdb1  14.5G root  disk  brw-rw----
sr0                                    sr0     1024M root  cdrom brw-rw----
loop0  squashfs             /rofs      loop0  975.9M root  disk  brw-rw----

```

The last command gives me nothing in the terminal.

You *have* changed the partition table :-) It is an MSDOS partition table now, and if you are running in BIOS mode, it should be possible to 'erase disk and install ubuntu'. (This is the easiest option.)

But please run the '[COLOR="#0000FF"]blue[/COLOR] commands' in my previous post to find which package is bad. Maybe we can help you replace it with a good one.

The last command should give you either

```
$ [COLOR="#0000FF"]test -d /sys/firmware/efi && echo efi || echo bios[/COLOR]
efi
```
or
```
$ [COLOR="#0000FF"]test -d /sys/firmware/efi && echo efi || echo bios[/COLOR]
bios
```

otherwise you did not type it correctly.

---

### Post by utnubu4 on 2016-03-29
Here are the results from ls

bin    dev   initrd.img  media  proc  run   sys     usr
boot   etc   lib         mnt    rofs  sbin  target  var
cdrom  home  lib64       opt    root  srv   tmp     vmlinuz


When i do the **md5sum -c md5sum.txt command it says, no such file or directory?**

---

### Post by utnubu4 on 2016-03-29
Ah right i thought i was not getting a command, this is what i get. test -d /sys/firmware/efi && echo efi || echo bios
bios


There is one defect but i believe i know what it is.. i have a folder full of files and documents also on the USB flash drive, maybe this folder is confusing the installation, what do you think?

---

### Post by sudodus on 2016-03-29
You are running in BIOS mode. Good :-)

I don't know yet about the bad package. Please run the [COLOR="#0000FF"]blue commands[/COLOR] of post #18 and try to find the package that is 'not OK'. Then we need not guess.

---

### Post by utnubu4 on 2016-03-29
Every time i run [COLOR=#0000FF]md5sum -c md5sum.txt it says no such file or directory?
[/COLOR]

---

### Post by sudodus on 2016-03-29
You need all the blue commands. The first one changes the current directory to /cdrom, where you should run the md5sum command line. The second one lists the files in the directory, and you should see for example md5sum.txt. The third command does the job, and lists the result :-)

```
[COLOR="#0000FF"][SIZE=3]cd /cdrom

ls

md5sum -c md5sum.txt[/SIZE][/COLOR]
```

---

### Post by utnubu4 on 2016-03-29
Oh my bad... i was running them separately! here are the results.


```

 ./pics/red-upperleft.png: OK
./pics/red-lowerleft.png: OK
./pics/blue-lowerleft.png: OK
./pics/logo-50.jpg: OK
./pics/blue-upperright.png: OK
./pics/blue-lowerright.png: OK
./pics/red-lowerright.png: OK
./pics/blue-upperleft.png: OK
./pics/debian.jpg: OK
./pics/red-upperright.png: OK
./wubi.exe: OK
./autorun.inf: OK
./preseed/ubuntu.seed: OK
./preseed/ltsp.seed: OK
./preseed/cli.seed: OK
./pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu0.2_amd64.deb: OK
./pool/main/m/mouseemu/mouseemu_0.16-0ubuntu9_amd64.deb: OK
./pool/main/l/lupin/lupin-support_0.55_amd64.deb: OK
./pool/main/s/secureboot-db/secureboot-db_1.1_amd64.deb: OK
./pool/main/s/shim-signed/shim-signed_1.9+0.8-0ubuntu2_amd64.deb: OK
./pool/main/s/shim/shim_0.8-0ubuntu2_amd64.deb: OK
./pool/main/s/setserial/setserial_2.17-48_amd64.deb: OK
./pool/main/g/grub2/grub-efi-amd64-bin_2.02~beta2-9ubuntu1.7_amd64.deb: OK
./pool/main/g/grub2/grub-efi-amd64_2.02~beta2-9ubuntu1.7_amd64.deb: OK
./pool/main/g/grub2/grub-efi_2.02~beta2-9ubuntu1.7_amd64.deb: OK
./pool/main/g/grub2-signed/grub-efi-amd64-signed_1.34.8+2.02~beta2-9ubuntu1.7_amd64.deb: OK
./pool/main/b/b43-fwcutter/b43-fwcutter_018-2_amd64.deb: OK
./pool/main/e/efibootmgr/efibootmgr_0.5.4-7ubuntu1.2_amd64.deb: OK
./pool/main/w/wvstreams/libwvstreams4.6-base_4.6.1-7_amd64.deb: OK
./pool/main/w/wvstreams/libuniconf4.6_4.6.1-7_amd64.deb: OK
./pool/main/w/wvstreams/libwvstreams4.6-extras_4.6.1-7_amd64.deb: OK
./pool/main/w/wvdial/wvdial_1.61-4.1_amd64.deb: OK
./pool/main/u/user-setup/user-setup_1.48ubuntu2_all.deb: OK
./pool/main/u/ubiquity/oem-config_2.18.8.12_all.deb: OK
./pool/main/u/ubiquity/oem-config-gtk_2.18.8.12_all.deb: OK
./pool/main/u/ubiquity-slideshow-ubuntu/oem-config-slideshow-ubuntu_83.1_all.deb: OK
./pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu5.14.04.5_all.deb: OK
./pool/main/f/fakeroot/libfakeroot_1.20-3ubuntu2_amd64.deb: OK
./pool/main/f/fakeroot/fakeroot_1.20-3ubuntu2_amd64.deb: OK
./.disk/info: OK
./.disk/base_installable: OK
./.disk/casper-uuid-generic: OK
./.disk/cd_type: OK
./.disk/release_notes_url: OK
./EFI/BOOT/BOOTx64.EFI: OK
./EFI/BOOT/grubx64.efi: OK
./boot/grub/x86_64-efi/chain.mod: OK
./boot/grub/x86_64-efi/blocklist.mod: OK
./boot/grub/x86_64-efi/spkmodem.mod: OK
./boot/grub/x86_64-efi/loopback.mod: OK
./boot/grub/x86_64-efi/pata.mod: OK
./boot/grub/x86_64-efi/echo.mod: OK
./boot/grub/x86_64-efi/lsacpi.mod: OK
./boot/grub/x86_64-efi/gcry_sha256.mod: OK
./boot/grub/x86_64-efi/cbls.mod: OK
./boot/grub/x86_64-efi/part_acorn.mod: OK
./boot/grub/x86_64-efi/videotest.mod: OK
./boot/grub/x86_64-efi/gettext.mod: OK
./boot/grub/x86_64-efi/iorw.mod: OK
./boot/grub/x86_64-efi/acpi.mod: OK
./boot/grub/x86_64-efi/part_sun.mod: OK
./boot/grub/x86_64-efi/terminfo.mod: OK
./boot/grub/x86_64-efi/minix3_be.mod: OK
./boot/grub/x86_64-efi/ohci.mod: OK
./boot/grub/x86_64-efi/gcry_arcfour.mod: OK
./boot/grub/x86_64-efi/raid6rec.mod: OK
./boot/grub/x86_64-efi/gfxmenu.mod: OK
./boot/grub/x86_64-efi/xnu_uuid_test.mod: OK
./boot/grub/x86_64-efi/morse.mod: OK
./boot/grub/x86_64-efi/efi_uga.mod: OK
./boot/grub/x86_64-efi/part_apple.mod: OK
./boot/grub/x86_64-efi/video_bochs.mod: OK
./boot/grub/x86_64-efi/dm_nv.mod: OK
./boot/grub/x86_64-efi/gcry_camellia.mod: OK
./boot/grub/x86_64-efi/multiboot2.mod: OK
./boot/grub/x86_64-efi/bitmap.mod: OK
./boot/grub/x86_64-efi/part_plan.mod: OK
./boot/grub/x86_64-efi/usb_keyboard.mod: OK
./boot/grub/x86_64-efi/efifwsetup.mod: OK
./boot/grub/x86_64-efi/part_amiga.mod: OK
./boot/grub/x86_64-efi/parttool.lst: OK
./boot/grub/x86_64-efi/boot.mod: OK
./boot/grub/x86_64-efi/hfs.mod: OK
./boot/grub/x86_64-efi/eval.mod: OK
./boot/grub/x86_64-efi/partmap.lst: OK
./boot/grub/x86_64-efi/adler32.mod: OK
./boot/grub/x86_64-efi/btrfs.mod: OK
./boot/grub/x86_64-efi/gcry_serpent.mod: OK
./boot/grub/x86_64-efi/setjmp_test.mod: OK
./boot/grub/x86_64-efi/cpio_be.mod: OK
./boot/grub/x86_64-efi/tftp.mod: OK
./boot/grub/x86_64-efi/lsefi.mod: OK
./boot/grub/x86_64-efi/xnu_uuid.mod: OK
./boot/grub/x86_64-efi/test.mod: OK
./boot/grub/x86_64-efi/syslinuxcfg.mod: OK
./boot/grub/x86_64-efi/test_blockarg.mod: OK
./boot/grub/x86_64-efi/part_msdos.mod: OK
./boot/grub/x86_64-efi/datetime.mod: OK
./boot/grub/x86_64-efi/keystatus.mod: OK
./boot/grub/x86_64-efi/password.mod: OK
./boot/grub/x86_64-efi/lsefimmap.mod: OK
./boot/grub/x86_64-efi/halt.mod: OK
./boot/grub/x86_64-efi/luks.mod: OK
./boot/grub/x86_64-efi/video.lst: OK
./boot/grub/x86_64-efi/macbless.mod: OK
./boot/grub/x86_64-efi/geli.mod: OK
./boot/grub/x86_64-efi/gcry_tiger.mod: OK
./boot/grub/x86_64-efi/gcry_rmd160.mod: OK
./boot/grub/x86_64-efi/part_sunpc.mod: OK
./boot/grub/x86_64-efi/raid5rec.mod: OK
./boot/grub/x86_64-efi/lspci.mod: OK
./boot/grub/x86_64-efi/terminal.lst: OK
./boot/grub/x86_64-efi/crypto.lst: OK
./boot/grub/x86_64-efi/jpeg.mod: OK
./boot/grub/x86_64-efi/video_fb.mod: OK
./boot/grub/x86_64-efi/datehook.mod: OK
./boot/grub/x86_64-efi/cbtable.mod: OK
./boot/grub/x86_64-efi/mpi.mod: OK
./boot/grub/x86_64-efi/gcry_rijndael.mod: OK
./boot/grub/x86_64-efi/videoinfo.mod: OK
./boot/grub/x86_64-efi/file.mod: OK
./boot/grub/x86_64-efi/testload.mod: OK
./boot/grub/x86_64-efi/gcry_twofish.mod: OK
./boot/grub/x86_64-efi/lsefisystab.mod: OK
./boot/grub/x86_64-efi/usbserial_usbdebug.mod: OK
./boot/grub/x86_64-efi/xfs.mod: OK
./boot/grub/x86_64-efi/minix3.mod: OK
./boot/grub/x86_64-efi/ntfscomp.mod: OK
./boot/grub/x86_64-efi/minix2.mod: OK
./boot/grub/x86_64-efi/uhci.mod: OK
./boot/grub/x86_64-efi/testspeed.mod: OK
./boot/grub/x86_64-efi/jfs.mod: OK
./boot/grub/x86_64-efi/help.mod: OK
./boot/grub/x86_64-efi/offsetio.mod: OK
./boot/grub/x86_64-efi/videotest_checksum.mod: OK
./boot/grub/x86_64-efi/video_colors.mod: OK
./boot/grub/x86_64-efi/usb.mod: OK
./boot/grub/x86_64-efi/zfscrypt.mod: OK
./boot/grub/x86_64-efi/setpci.mod: OK
./boot/grub/x86_64-efi/diskfilter.mod: OK
./boot/grub/x86_64-efi/cat.mod: OK
./boot/grub/x86_64-efi/minicmd.mod: OK
./boot/grub/x86_64-efi/msdospart.mod: OK
./boot/grub/x86_64-efi/part_bsd.mod: OK
./boot/grub/x86_64-efi/gcry_rsa.mod: OK
./boot/grub/x86_64-efi/exfctest.mod: OK
./boot/grub/x86_64-efi/lvm.mod: OK
./boot/grub/x86_64-efi/progress.mod: OK
./boot/grub/x86_64-efi/gcry_sha512.mod: OK
./boot/grub/x86_64-efi/romfs.mod: OK
./boot/grub/x86_64-efi/gfxterm_menu.mod: OK
./boot/grub/x86_64-efi/ufs1_be.mod: OK
./boot/grub/x86_64-efi/newc.mod: OK
./boot/grub/x86_64-efi/true.mod: OK
./boot/grub/x86_64-efi/aout.mod: OK
./boot/grub/x86_64-efi/gfxterm_background.mod: OK
./boot/grub/x86_64-efi/gcry_md4.mod: OK
./boot/grub/x86_64-efi/verify.mod: OK
./boot/grub/x86_64-efi/ehci.mod: OK
./boot/grub/x86_64-efi/video.mod: OK
./boot/grub/x86_64-efi/http.mod: OK
./boot/grub/x86_64-efi/gcry_des.mod: OK
./boot/grub/x86_64-efi/cryptodisk.mod: OK
./boot/grub/x86_64-efi/usbserial_common.mod: OK
./boot/grub/x86_64-efi/backtrace.mod: OK
./boot/grub/x86_64-efi/fat.mod: OK
./boot/grub/x86_64-efi/xnu.mod: OK
./boot/grub/x86_64-efi/lssal.mod: OK
./boot/grub/x86_64-efi/efinet.mod: OK
./boot/grub/x86_64-efi/div_test.mod: OK
./boot/grub/x86_64-efi/grub.cfg: OK
./boot/grub/x86_64-efi/crc64.mod: OK
./boot/grub/x86_64-efi/pcidump.mod: OK
./boot/grub/x86_64-efi/date.mod: OK
./boot/grub/x86_64-efi/parttool.mod: OK
./boot/grub/x86_64-efi/ldm.mod: OK
./boot/grub/x86_64-efi/gcry_sha1.mod: OK
./boot/grub/x86_64-efi/memrw.mod: OK
./boot/grub/x86_64-efi/gcry_crc.mod: OK
./boot/grub/x86_64-efi/png.mod: OK
./boot/grub/x86_64-efi/hfspluscomp.mod: OK
./boot/grub/x86_64-efi/hexdump.mod: OK
./boot/grub/x86_64-efi/ntfs.mod: OK
./boot/grub/x86_64-efi/keylayouts.mod: OK
./boot/grub/x86_64-efi/gcry_md5.mod: OK
./boot/grub/x86_64-efi/gcry_dsa.mod: OK
./boot/grub/x86_64-efi/bfs.mod: OK
./boot/grub/x86_64-efi/usbserial_ftdi.mod: OK
./boot/grub/x86_64-efi/sleep_test.mod: OK
./boot/grub/x86_64-efi/efi_gop.mod: OK
./boot/grub/x86_64-efi/gcry_whirlpool.mod: OK
./boot/grub/x86_64-efi/lzopio.mod: OK
./boot/grub/x86_64-efi/at_keyboard.mod: OK
./boot/grub/x86_64-efi/gptsync.mod: OK
./boot/grub/x86_64-efi/minix2_be.mod: OK
./boot/grub/x86_64-efi/relocator.mod: OK
./boot/grub/x86_64-efi/hashsum.mod: OK
./boot/grub/x86_64-efi/usbserial_pl2303.mod: OK
./boot/grub/x86_64-efi/mdraid09.mod: OK
./boot/grub/x86_64-efi/ata.mod: OK
./boot/grub/x86_64-efi/ufs1.mod: OK
./boot/grub/x86_64-efi/procfs.mod: OK
./boot/grub/x86_64-efi/elf.mod: OK
./boot/grub/x86_64-efi/gfxterm.mod: OK
./boot/grub/x86_64-efi/cpio.mod: OK
./boot/grub/x86_64-efi/ls.mod: OK
./boot/grub/x86_64-efi/mmap.mod: OK
./boot/grub/x86_64-efi/odc.mod: OK
./boot/grub/x86_64-efi/hfsplus.mod: OK
./boot/grub/x86_64-efi/crypto.mod: OK
./boot/grub/x86_64-efi/gcry_idea.mod: OK
./boot/grub/x86_64-efi/net.mod: OK
./boot/grub/x86_64-efi/gcry_rfc2268.mod: OK
./boot/grub/x86_64-efi/legacycfg.mod: OK
./boot/grub/x86_64-efi/pbkdf2_test.mod: OK
./boot/grub/x86_64-efi/cpuid.mod: OK
./boot/grub/x86_64-efi/bsd.mod: OK
./boot/grub/x86_64-efi/part_dvh.mod: OK
./boot/grub/x86_64-efi/sleep.mod: OK
./boot/grub/x86_64-efi/fixvideo.mod: OK
./boot/grub/x86_64-efi/setjmp.mod: OK
./boot/grub/x86_64-efi/read.mod: OK
./boot/grub/x86_64-efi/macho.mod: OK
./boot/grub/x86_64-efi/gcry_blowfish.mod: OK
./boot/grub/x86_64-efi/squash4.mod: OK
./boot/grub/x86_64-efi/multiboot.mod: OK
./boot/grub/x86_64-efi/password_pbkdf2.mod: OK
./boot/grub/x86_64-efi/ext2.mod: OK
./boot/grub/x86_64-efi/bitmap_scale.mod: OK
./boot/grub/x86_64-efi/archelp.mod: OK
./boot/grub/x86_64-efi/moddep.lst: OK
./boot/grub/x86_64-efi/mdraid1x.mod: OK
./boot/grub/x86_64-efi/reiserfs.mod: OK
./boot/grub/x86_64-efi/cmp.mod: OK
./boot/grub/x86_64-efi/fs.lst: OK
./boot/grub/x86_64-efi/loadbios.mod: OK
./boot/grub/x86_64-efi/linuxefi.mod: OK
./boot/grub/x86_64-efi/hdparm.mod: OK
./boot/grub/x86_64-efi/signature_test.mod: OK
./boot/grub/x86_64-efi/cbtime.mod: OK
./boot/grub/x86_64-efi/cbmemc.mod: OK
./boot/grub/x86_64-efi/command.lst: OK
./boot/grub/x86_64-efi/scsi.mod: OK
./boot/grub/x86_64-efi/tr.mod: OK
./boot/grub/x86_64-efi/play.mod: OK
./boot/grub/x86_64-efi/ufs2.mod: OK
./boot/grub/x86_64-efi/mdraid09_be.mod: OK
./boot/grub/x86_64-efi/loadenv.mod: OK
./boot/grub/x86_64-efi/all_video.mod: OK
./boot/grub/x86_64-efi/linux16.mod: OK
./boot/grub/x86_64-efi/xzio.mod: OK
./boot/grub/x86_64-efi/font.mod: OK
./boot/grub/x86_64-efi/ahci.mod: OK
./boot/grub/x86_64-efi/time.mod: OK
./boot/grub/x86_64-efi/part_dfly.mod: OK
./boot/grub/x86_64-efi/appleldr.mod: OK
./boot/grub/x86_64-efi/cs5536.mod: OK
./boot/grub/x86_64-efi/linux.mod: OK
./boot/grub/x86_64-efi/gcry_cast5.mod: OK
./boot/grub/x86_64-efi/reboot.mod: OK
./boot/grub/x86_64-efi/lsmmap.mod: OK
./boot/grub/x86_64-efi/gzio.mod: OK
./boot/grub/x86_64-efi/usbtest.mod: OK
./boot/grub/x86_64-efi/legacy_password_test.mod: OK
./boot/grub/x86_64-efi/bufio.mod: OK
./boot/grub/x86_64-efi/udf.mod: OK
./boot/grub/x86_64-efi/pbkdf2.mod: OK
./boot/grub/x86_64-efi/video_cirrus.mod: OK
./boot/grub/x86_64-efi/nativedisk.mod: OK
./boot/grub/x86_64-efi/disk.mod: OK
./boot/grub/x86_64-efi/cbfs.mod: OK
./boot/grub/x86_64-efi/cmdline_cat_test.mod: OK
./boot/grub/x86_64-efi/regexp.mod: OK
./boot/grub/x86_64-efi/minix_be.mod: OK
./boot/grub/x86_64-efi/priority_queue.mod: OK
./boot/grub/x86_64-efi/trig.mod: OK
./boot/grub/x86_64-efi/tga.mod: OK
./boot/grub/x86_64-efi/usbms.mod: OK
./boot/grub/x86_64-efi/terminal.mod: OK
./boot/grub/x86_64-efi/gcry_seed.mod: OK
./boot/grub/x86_64-efi/exfat.mod: OK
./boot/grub/x86_64-efi/serial.mod: OK
./boot/grub/x86_64-efi/probe.mod: OK
./boot/grub/x86_64-efi/part_gpt.mod: OK
./boot/grub/efi.img: OK
./boot/grub/grub.cfg: OK
./boot/grub/loopback.cfg: OK
./boot/grub/font.pf2: OK
./casper/filesystem.size: OK
./casper/filesystem.manifest: OK
./casper/filesystem.squashfs: FAILED
./casper/initrd.lz: OK
./casper/vmlinuz.efi: OK
./casper/filesystem.manifest-remove: OK
./README.diskdefines: OK
./dists/trusty/restricted/binary-i386/Release: OK
./dists/trusty/restricted/binary-i386/Packages.gz: OK
./dists/trusty/restricted/binary-amd64/Release: OK
./dists/trusty/restricted/binary-amd64/Packages.gz: OK
./dists/trusty/Release: OK
./dists/trusty/Release.gpg: OK
./dists/trusty/main/binary-i386/Release: OK
./dists/trusty/main/binary-i386/Packages.gz: OK
./dists/trusty/main/binary-amd64/Release: OK
./dists/trusty/main/binary-amd64/Packages.gz: OK
./install/mt86plus: OK
md5sum: WARNING: 1 computed checksum did NOT match
ubuntu@ubuntu:/cdrom$
```

---

### Post by sudodus on 2016-03-29
**./casper/filesystem.squashfs: FAILED**

This is the biggest file, and it contains the main part of the live system (it contains a compressed file system, which is extracted into RAM for the live system). We don't know what is wrong or missing, only that it does not match the checksum. Obviously the basic system works live, so maybe there is only a minor defect in the file.

The standard advice in this situation would be to download the iso file again, or even better, to get it via a torrent, which has a built in check for transfer errors. And then to flash that good iso file into the pendrive. But I understand that you can't do it now. Instead you would like to get only the bad file. and it is a big and very important file.

```
sdb                                    sdb     14.5G root  disk  brw-rw----
&#9492;&#9472;sdb1 vfat     UBUNTU 14_0 /cdrom     &#9492;&#9472;sdb1  14.5G root  disk  brw-rw----
```

**/cdrom** has a vfat file system which might or might not have write permissions, depending on if it is a live-only or persistent live system. If it is a persistent live system (with a casper-rw file) it should have write permissions, but I don't think it is. It is possible to solve by creating manually a casper-rw file (or partition) and add the boot option **persistent**. Then it should be possible to download a good version of the file filesystem.squashfs and go ahead. But it is really too much harder than to start from the beginning with a good iso file (and another computer).

One alternative, obviously, is to wait until you can borrow a computer.

Another alternative is to use a second USB pendrive. Running from this pendrive you can get a good iso file (download or get via torrent) and check its md5sum so that you are sure. Then you can install it into the second USB pendrive, and reboot into that pendrive, which should have a complete system.

By the way, from the output (above) 'UBUNTU 14_0' (which is cut off), I guess that you have downloaded Ubuntu 14.04.x LTS. Which point version x is it?

---

### Post by utnubu4 on 2016-03-30
I have just bought a USB flash drive from amazon with ubuntu already installed on it, so i should have no issues with that.. hopefully!

Thank you very much for all of your hard work and trying to solve my issue. I really do appreciate your deliberation to helping me!

I am not really sure which ubuntu i downloaded but i got it from their main website, i think it was ubuntu 14.04.4 LTS. I am not sure about the point x version sorry.

Once again thank you very much sododus :)

---

### Post by sudodus on 2016-03-30
You are welcome :-)

I was thinking about getting the same version, if you want to download it again, because the version on your current pendrive is working (even though the file filesystem.squashfs is damaged). You can find out by running the following command line, when booted from the pendrive

```
lsb_release -a
``` and you can find out about the linux kernel with the following command line

```
uname -a
```

Good luck with the new pendrive, and come back to the Ubuntu Forums, if you need more help :-)

[hr][/hr]
Probably there will be a completely different issue, for example with the Broadcom wifi chip, and you should create a new thread with a good descriptive title and a good description of the computer, Ubuntu version and the problem in the first post. That way you have the best chances to attract people who know about it and can help you. If you want to, you can create a link from this thread to that new thread.

---

### Post by RobGoss on 2016-03-30
Hello and welcome, The best thing about Ubuntu there's always a fix. You didn't mention what version of Ubuntu you're trying too install I found from experience just cleaning the disc will make a world of difference.

If you're trying to install Ubuntu 1604 you will get a lot of errors on the Disk Management. I think it's just  a bug I managed to get it install Just about every time I try. Try cleaning the disk and use the correct options to boot Ubuntu and see if that works

Even if you wiped your Windows OS you should still be able to install Ubuntu, when you boot into the live CD there's many options to install Ubuntu.

Are you sure your Windows OS is non-functional? It might be a question of going back into the BIOS and change the boot options

---

### Post by utnubu4 on 2016-03-30
> **sudodus said:**
> You are welcome :-)

I was thinking about getting the same version, if you want to download it again, because the version on your current pendrive is working (even though the file filesystem.squashfs is damaged). You can find out by running the following command line, when booted from the pendrive

```
lsb_release -a
``` and you can find out about the linux kernel with the following command line

```
uname -a
```

Good luck with the new pendrive, and come back to the Ubuntu Forums, if you need more help :-)

[HR][/HR]
Probably there will be a completely different issue, for example with the Broadcom wifi chip, and you should create a new thread with a good descriptive title and a good description of the computer, Ubuntu version and the problem in the first post. That way you have the best chances to attract people who know about it and can help you. If you want to, you can create a link from this thread to that new thread.

Ah right, i am sure this version is great and its my own issue when  installing the ISO to my USB. I really enjoy the live 14.04.4 anyway so i  can not wait to get it installed properly! thank you for the offer of the re-download and the commands provided, but i think i will stick with the live for one more day as the USB should arrive tomorrow. The USB comes with ubuntu and mint but i only want to install ubuntu.

Thank you, i hope i have good luck with the pen drive this time too and yeas i am sure i will be back to get more help and information. I have read that many people have small issues with my wifi chip and linux. I guess i will see you around the forum!

Once again, thank you very much for your effort and kindness.

Have a nice day sudodus :)

---

### Post by utnubu4 on 2016-03-30
Hey RobGoss,

Thanks for your input but there is no way to fix my current situation unless i have another pc/laptop. The ISO on my current USB flash drive has a filesystem.squashfs damage.

Yeas my windows OS has been completely removed from my hard drive, i have attempted to boot up from the hard drive and nothing exists.

---

### Post by RobGoss on 2016-03-30
> **utnubu4 said:**
> Hey RobGoss,

Thanks for your input but there is no way to fix my current situation unless i have another pc/laptop. The ISO on my current USB flash drive has a filesystem.squashfs damage.

Yeas my windows OS has been completely removed from my hard drive, i have attempted to boot up from the hard drive and nothing exists.

Yes I understand that but if you can get a fresh copy of Ubuntu's ISO file and put it on either that USB stick or another one you should be ok. 

You should also be able to format that USB and install the ISO file on it again.

---

### Post by utnubu4 on 2016-03-30
> **sudodus said:**
> You are welcome :-)

I was thinking about getting the same version, if you want to download it again, because the version on your current pendrive is working (even though the file filesystem.squashfs is damaged). You can find out by running the following command line, when booted from the pendrive

```
lsb_release -a
``` and you can find out about the linux kernel with the following command line

```
uname -a
```

Good luck with the new pendrive, and come back to the Ubuntu Forums, if you need more help :-)

[HR][/HR]
Probably there will be a completely different issue, for example with the Broadcom wifi chip, and you should create a new thread with a good descriptive title and a good description of the computer, Ubuntu version and the problem in the first post. That way you have the best chances to attract people who know about it and can help you. If you want to, you can create a link from this thread to that new thread.

Ah right, i am sure this version is great and its my own issue when  installing the ISO to my USB. I really enjoy the live 14.04.4 anyway so i  can not wait to get it installed properly! thank you for the offer of  the re-download and the commands provided, but i think i will stick with  the live for one more day as the USB should arrive tomorrow. The USB  comes with ubuntu and mint but i only want to install ubuntu.

Thank  you, i hope i have good luck with the pen drive this time too and yeas i  am sure i will be back to get more help and information. I have read  that many people have small issues with my wifi chip and linux. I guess i  will see you around the forum!

Once again, thank you very much for your effort and kindness.

Have a nice day sudodus :)

---

