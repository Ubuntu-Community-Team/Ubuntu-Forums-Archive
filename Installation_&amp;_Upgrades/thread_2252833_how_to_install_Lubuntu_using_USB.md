---
title: "how to install Lubuntu using USB?"
date: 2014-11-15
forum: Installation &amp; Upgrades
---

### Post by flaymond on 2014-11-15
Hi, actually i already installed 2-3 Ubuntu flavours on my pc (swapping and testing). Now, i dont have have the ISO file (the installation file with wubi .exe in it), i have the content in NTFS...how change it to bootable file back.....I already using disk apps to change partition from FAT32( I can view the file) to hidden NTFS (I can't view it, but i can boot it).

I forgot how to make the whole file to bootable file.
I made it a few times, but after couple of days...i forgot how to make it a 'bootable USB'.

Anyone can help me how to change the USB to bootable USB?

---

### Post by Topsiho on 2014-11-15
Hello InterProg,

You mention wubi.exe and some strange filesystem formats :)
I don't think that wubi installs are supported in the newer Ubuntu versions.

Topsiho

---

### Post by ajgreeny on 2014-11-15
You need the .iso image file to be able to make a bootable USB, so you will have to get that from the [Lubuntu]("http://lubuntu.net/") website if you don't have it backed up somewhere.

There is no point using wubi any more as it is not being developed and almost no-one on this forum will be able to help you with it.  It is, however, possible to migrate a wubi installation to a proper partitioned installation.
See [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354) 
I have no idea how successful this might be and have no real info apart from this about wubi, which as I say, is now dead and best forgotten.

---

### Post by sudodus on 2014-11-15
1. Download the iso file

2. Check it with md5sum

3. Use a suitable tool to make a boot USB drive from it.

There is a lot of detailed information in the following link and links from it

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

-o-

It is easiest to start from the iso file and use a dedicated tool. It is also possible to use the files, that you have already extracted (if it is a complete set of files), and you would learn a lot, but it is much more difficult.

*Edit*: and wubi is deprecated.

---

### Post by flaymond on 2014-11-17
I try the third party installer (unetbootin,pendrivelinux,UUI etc.) and find out those failed to detect my USB. using Startup Disk Creator (14.10 had bug, that's the problem I can't set it up from there)....but yeah...nevermind....my OS is still doing well....I just wanna prepare for the future in case I need to reinstall for particular reasons...Thanks for your advise everyone! I appreciate that!

---

### Post by sudodus on 2014-11-18
Please insert the USB drive into a port of your computer. Open a terminal window, run the following commands and post the output of each of the commands. Type your password and finish with the Enter key (it is normal the the text is *not* echoed to the screen). Put the output text within code tags. (Go Advanced mark the text and click on the **#** icon above the editing window.)

```
sudo parted -l
```
'space minus ell' at the end of the command line
```
sudo lsblk -f
```
```
sudo lsblk -m
```
```
df
```

This will give us information about how the USB drive is recognized, and it will be easier to help you make some tool recognize it and make it bootable from a Lubuntu or another flavour of Ubuntu.

---

### Post by flaymond on 2014-11-19
I'm posting step by step -

1. sudo parted -l

```
Model: ATA ST980811AS (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  79.0GB  79.0GB  primary   ext4
 2      79.0GB  80.0GB  1062MB  extended
 5      79.0GB  80.0GB  1062MB  logical   linux-swap(v1)  boot


Model: UFD 2.0 Silicon-Power32G (scsi)
Disk /dev/sdb: 32.3GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  32.3GB  32.3GB  primary  fat32        lba


```

2. sudo lsblk -f

```
NAME   FSTYPE LABEL UUID                                 MOUNTPOINT
sda                                                      
&#9500;&#9472;sda1 ext4         740e8ecf-7603-4c1b-9e4d-e14712404283 /
&#9500;&#9472;sda2                                                   
&#9492;&#9472;sda5 swap         e5803a18-ef2d-4fbc-ae7d-f6f9c0fe69be [SWAP]
sdb                                                      
&#9492;&#9472;sdb1 vfat         72E2-220B                            /media/user/72E2-220B
sr0                             

```

3. sudo lsblk -m

```
NAME    SIZE OWNER GROUP MODE
sda    74.5G root  disk  brw-rw----
&#9500;&#9472;sda1 73.6G root  disk  brw-rw----
&#9500;&#9472;sda2    1K root  disk  brw-rw----
&#9492;&#9472;sda5 1013M root  disk  brw-rw----
sdb      30G root  disk  brw-rw----
&#9492;&#9472;sdb1   30G root  disk  brw-rw----
sr0    1024M root  cdrom brw-rw----
```

4. df

```
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1       75768928 4786320  67110660   7% /
none                   4       0         4   0% /sys/fs/cgroup
udev              498836       4    498832   1% /dev
tmpfs             101808     996    100812   1% /run
none                5120       4      5116   1% /run/lock
none              509036       0    509036   0% /run/shm
none              102400      20    102380   1% /run/user
/dev/sdb1       31483872      16  31483856   1% /media/user/72E2-220B


```


* How should I do to install it with no problems? (No problems in 14.04 using Disk Image Writer to set it up)

---

### Post by sudodus on 2014-11-19
What we normally do, when we install, is to download an iso file, make a  USB boot drive from the downloaded file, boot and install from the USB  boot drive. If I understand correctly from your first post in this  thread, you want to build an iso file from files, that have been  extracted. It is possible but quite difficult. I don't understand why  you want to do that, when it is much easier to download a Lubuntu iso  file.

-o-

Please tell us exactly what you want! There are many alternatives. Do you want to

- install an independent Lubuntu system alongside the current system in **/dev/sda1** (is that Ubuntu?). - Easy

- overwrite the current system in **/dev/sda1** with Lubuntu? - Easier

- make an iso file from the current installed system, and install it somewhere else? - Difficult

- change the current system in **/dev/sda1** (is that Ubuntu?) to Lubuntu? - Easy to add lubuntu-desktop, hard to remove all parts of the current desktop environment

- make a ***backup*** of the current system? - There are easy and more difficult alternatives

Or do you want something else, that I could not think of? In this case, please explain :-)

-o-

Your USB drive seems good, the FAT file system is mounted, and it should be possible to use any of several tools to make it bootable with Lubuntu. The Startup Disk Creator has some bugs. ***Unetbootin*** works, ***mkusb*** works ...

---

### Post by flaymond on 2014-11-19
Actually, I have downloaded the .iso file for 3x times (3 type). First is, the regular one, second is the non-GUI installer (My connection is too slow to download a really big file), and third minimal installer and I failed somehow on this version. I tried UnetBootin and the the app don't have any issue to detect the iso. But, the main issue here, the Unetbootin and PenDriveLinux cannot detect my drive.....I already formatted it to FAT32 format..and tried again and again for 2 days....and the weird thing about this.....I always pass to make these task using Disk Image Writer (to try different flavours) without any problems. Unfortunately, I can't open the iso file with the Disk Image Writer like currently I do on previous installation on several distros....

---

### Post by sudodus on 2014-11-19
I don't know which software you mean by ***Disk Image Writer***, is that the exact name of it or something similar? Is it a linux, Windows or MacOS tool? Is it one of the following tools?

 [https://launchpad.net/win32-image-writer](https://launchpad.net/win32-image-writer)
[http://sourceforge.net/projects/win32diskimager/](http://sourceforge.net/projects/win32diskimager/)

If you have a Lubuntu iso file and the download was successful (check  that it matches the listed string with md5sum), I think you will succeed  with ***mkusb***, which copies/clones/flashes the  iso file (an exact copy of each byte) to the pendrive (the block device  representing the pendrive). See this link

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
or in particular here
[https://help.ubuntu.com/community/mkusb/v9#from_phillw.net](https://help.ubuntu.com/community/mkusb/v9#from_phillw.net)

And I think that ***Unetbootin*** should work too. It worked for me two weeks ago (in 12.04.5 and 14.04.1 also to create 14.10)

-o-

If you have problems downloading big files, I suggest that you use a ***torrent***. The torrent method is designed to work reliably even if the internet connection is slow, interrupted and has transfer errors.

If you have really big problems with the internet connection, maybe you can download the iso file somewhere else (for example at a friend's place), or even try to find someone via the Ubuntu Forums, who lives fairly near-by and can download it and send it as a boot CD/DVD (if that would work for you) otherwise as a file on a data-DVD file for transfer to a USB drive.

---

### Post by flaymond on 2014-11-19
Yes, it was exact the name...***Disk Image Writer***. (I think its a  part of the disk ulities for create and restore disk image). mkusb? never tried that yet, maybe i should use that tomorrow. Torrent? Ohh, I think its a dangerous way because others said that it can track you or the data sent unencrypted....(not the Ubuntu torrent file i meant, its others companies....well, that make me believe that torrent file is unsafe and not should not be used. Fortunately, with your help and knowledge that you shared....I can have a good downloading speed now...without compromise,,:D )

---

