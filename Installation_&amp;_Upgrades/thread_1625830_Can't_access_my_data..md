---
title: "Can't access my data."
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by jdocop on 2010-11-19
I put the ubuntu install onto a jump drive, and then, when I asked it to install, it installed onto my external HDD (my mistake).  Now, if I boot to Windows 7, I can't access that external HDD where I have all of my data, documents, videos, music, etc.  Likewise, I can't seem to import either my address book from my Windows Outlook, or my bookmarks from Firefox, and - of course - I can't access my data from where it is on that external HDD.  I thought it was supposed to be easy to put my contacts and bookmarks into this system, but I guess I was wrong.  I just want to uninstall ubuntu and go back to things the way they were, but can't seem to progress in any direction.  Oh, yeah, the computer will not boot from the original hard drive at all, only if the external HDD is connected, and then, well........
what else can I say?
Can anyone help?

---

### Post by Joe of loath on 2010-11-19
Basically, installing to the external HDD has wiped it of all your previous data. It's a risk you run when you leave it plugged in during the installation, I'm afraid.

RE the bookmarks and outlook contacts, do some googling for a tutorial, there should be a few around.

---

### Post by ajgreeny on 2010-11-19
Your problem seems to be that all your data is now on a partition formatted as one of the linux file types.  Unfortunately windows is not clever enough to read those partitions without an external third person utility, and most of those if not all, do not work with the default ext4 file system of Ubuntu.  Also you can not boot to windows without the external drive attached as all the grub config files are on the ubuntu external drive

If you can backup your data files to another USB drive (format fat32) you can then copy them to the windows partition from within windows.  Better still make a new partition on the windows drive, using windows own disk management utility, format as NTFS, and put all the data in that, not in the windows OS partition.

You also need to sort out the boot managers of the two systems, firstly to put grub onto the USB disk with ```
sudo grub-install /dev/sdx
```where sdx is your USB disk.  If you are not sure of your device names run ubuntu and use the terminal command sudo fdisk -l which will tell you all the disks and partitions.  You can do this from the live USB as the output should be the same.
You then need to install a Windows equivalent MBR to your sda drive by doing the following from your Live USB:
```
sudo apt-get install lilo
```Ignore the warning then 
```
sudo lilo -M  /dev/sda mbr

```This assumes that windows is on the first disk of your system, /dev/sda.  Then you should be able to boot directly into Windows again if all goes well without needing the USB drive attached.

Now in the machine BIOS set the USB to be the first device to boot and the internal hard disk as the second device.  Now when you boot up you should go straight to windows when the USB is missing, but get grub when the USB is attached.

EDIT:  Whoops!  I missed the detail of what you had done.
I hope *Joe of loath* is not correct, or that you have a good backup of those files somewhere, but if you let ubuntu install to the whole of the external drive, I fear he is probably right.

---

### Post by jdocop on 2010-11-19
I, too, hope that it did indeed partition that external HDD, and I am pretty sure that is what it did, because I do recall there being mention of partitioning when the install began........meanwhile, my problem is that I cannot access any part of the external drive, other than where the ubuntu is installed.......  just seemed to me that the logical way to do this is to somehow restore what used to work, in order to delete the ubuntu entirely....

---

### Post by jdocop on 2010-11-19
Meanwhile, I have managed to repair my MBR so that the PC will boot to Windows 7, but the external HDD is no longer recognized as anything other than a MBR for ubuntu that cannot be used in any way........it does not show up as a disk drive at all, now......so, it does look as if all my data is gone.......

---

### Post by jdocop on 2010-11-21
fwiw, I got things back the way they were, no thanks to Windows.  I found a little utility called testdisk, or something like that, and in order to use it, I was reminded why I want to get away from Windows.  It would not install in Windows7 'cause it was "not a valid Win32 application/file/whatever," so I had to use my laptop, which runs XP........Meanwhile, I guess I need to start a new thread  to find out if I'll be able to import my Contacts and bookmarks, if I try Ubuntu again.....

---

