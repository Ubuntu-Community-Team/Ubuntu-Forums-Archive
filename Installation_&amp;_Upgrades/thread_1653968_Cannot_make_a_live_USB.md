---
title: "Cannot make a live USB"
date: 2010-12-27
forum: Installation &amp; Upgrades
---

### Post by zeating on 2010-12-27
Using windows 7 32bit ultimate edition, I downloaded Universal USB Installer 1.8.2.0, downloaded the ubuntu 10.10 32bit iso, when i try to make a live usb with it it says "Syslinux402.exe has stopped working" then "An error (255) occured while executing syslinux. Your USB drive won't be bootable" Anyone famillar with this problem? what can i do? thanks

---

### Post by presence1960 on 2010-12-27
[http://old.linuxliveusb.com/](http://old.linuxliveusb.com/)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Try these.

---

### Post by zeating on 2010-12-27
ubootin hangs at 11%, gonna try the other one

---

### Post by zeating on 2010-12-27
exact same problem with linux live usb creator :(

---

### Post by presence1960 on 2010-12-27
> **zeating said:**
> exact same problem with linux live usb creator :(

The problem is with the iso you downloaded then. Did you MD5SUM the iso and make sure the hashes match exactly? if the hashes are off by even one charcter the iso is no good. See [here]("https://help.ubuntu.com/community/UbuntuHashes")

---

### Post by zeating on 2010-12-28
I really dont think its the ISO as i've downloaded downloaded it twice, once directly from the ubuntu site and one from the torrent

---

### Post by zeating on 2010-12-29
bump, happens on 2 different computers :S
the characters are not off and the program says number of known md5 hashes found in md5sum files: 0

---

### Post by presence1960 on 2010-12-29
> **zeating said:**
> bump, happens on 2 different computers :S

Maybe your flash drive is faulty. Did you try another flash drive formatted as FAT32?

---

### Post by ~XiX~ on 2011-06-19
I searched the internet and the reason it seems is a bad filename. The workaround is to install syslinux before the USB installer and then run USB installer. 
Here is wat I do and it works well all the time.
 
1. Download the required syslinux files from the net
 
or the easy way,
- run universal USB installer and let it fail.
- Before u close the installer, copy the list of instructions/commands the installer ran.
- Find the temporary folder it is using.
- Navigate to the temporary folder and copy the contents to another folder. This folder has the necessary syslinux files.
 
2. Format the USB
 
3. Open command prompt in administrator mode and navigate to the folder where u have syslinux files. Itu open the command in administrator mode else syslinux command will not work
 
4. Run the command 
"syslinux -maf [*driveletter:*]" where drive letter is the pendrive
eg: "syslinux -maf F:"
If no error msg is displayed, then the syslinux installation is done.
 
5. Run the universal USB installer again. 
 
6. This time, when the installer runs the syslinux command, it will not fail.
 
This works for other installers too.

---

### Post by pgn674 on 2012-11-07
Thank you for the instructions, ~XiX~. I actually found that I only had to format the drive myself by right clicking on it in Computer. I was then able to run the Universal USB Installer without trouble, with the message "Syslinux Errors 0".

---

