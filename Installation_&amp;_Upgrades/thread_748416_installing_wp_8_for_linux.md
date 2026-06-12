---
title: "installing wp 8 for linux"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by harryliddic on 2008-04-07
I have an old but dear copy of wordperfect 8 for linux and the instructions read as follows

1) log in as *root* where you have accessto the CD-ROM drive

2)Create a Wordperfect installation directory
    ** _Important_**if you are planning a *non-root* installation, make sure the WOrdperfect directory grants write permission to the planned primary wordperfect adminstrator

3) Insert the wordperfect CD-ROM into the drive

4)Use the *mount* command to access the wordperfect CD-ROM. to use the *mount* command successfully, you must know the correct device name and options for your linux system and device.  Mount command: mount  /dev/cdrom/cdrom.
 ***Important*** if you are planning a *non-root* installation of WP you can log out as root at this time and log back in as the primary WP administor.

5) Type *cd/CDROMdir*(where CDROMdir is the full pathname of the directory where the CD-ROM is mounted) then press Enter to change the *root* directory on the CD*ROM

6) type *pwd*, the ENTER to verify that you are in the correct directory.

7)Type ./install.wp, then press ENTER to access the cD-ROM.

8) if you are asked, select Linux, then choose OK

well that is it.is there any way to install WP 8 in the Kubuntu age?

---

### Post by oldos2er on 2008-04-07
Pop the cd in your cd drive. Open konqeror, change to the root directory of the cd, open a terminal there, and type in "kdesu ./install.wp"

---

### Post by harryliddic on 2008-04-08
I did as  you said and kept getting this message

harry@harry-desktop:~$ kdesu install ./install.wp
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
install: 
missing destination file operand after `./install.wp'

harry@harry-desktop:~$ kdesu install ./install.wp /home/wpinstall
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
install: 
cannot stat `./install.wp'
: No such file or directory

any suggestions?

---

### Post by PmDematagoda on 2008-04-08
Unfortunately you are not only entering the wrong command but you are also in the wrong directory.

First of all move to the CD-ROM directory(I am assuming that the mount point is /media/cdrom):-
```
cd /media/cdrom0
```

Then execute the installer:-
```
kdesu ./install.wp
```

But before doing anything like that, did you make the destination directory for the application as mentioned in the instructions?

---

### Post by oldos2er on 2008-04-08
The "X Error: BadDevice, invalid or uninitialized input device" is an error within xorg.conf--usually a wacom tablet device that doesn't exist.

---

