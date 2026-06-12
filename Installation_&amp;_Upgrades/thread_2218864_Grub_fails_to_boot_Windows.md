---
title: "Grub fails to boot Windows"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by palimmo on 2014-04-22
Hi.
Finally yesterday I convinced a friend to install Linux on his machine, alongside with the old Windows XP.
By the way, he asked me to install it in dual boot.

Linux works correctly, but Windows XP fails to boot. Even its partition is not mountable.
When I select it on Grub, this is the screen that I get and on which the pc remains stuck. I can just press ctrl-alt-canc to reboot.
[ATTACH=CONFIG]252363[/ATTACH]

This is the command in Grub for the Win XP selection:
[ATTACH=CONFIG]252364[/ATTACH]

And this is the output that I obtain in Linux with sudo update-grub:
[ATTACH=CONFIG]252365[/ATTACH]

I'm quite sure that something went wrong during the Xubuntu installation and partitioning process.
I had to shrink the Win XP (FAT32) partition to create an ext4 and swap partition.

Now I can't access the Windows partition (FAT32; sda1) with File Manager and even with a linux live-usb. :cry:
This is the situation in Gparted:
[ATTACH=CONFIG]252366[/ATTACH]

I've tried **Gparted -> Check and Repair filesystem** but I received this error:
```
GParted 0.18.0 --enable-libparted-dmraid --enable-online-resize

Libparted 2.3
Check and repair file system (fat32) on /dev/sda1  00:00:31    ( ERROR )
       
calibrate /dev/sda1  00:00:00    ( SUCCESS )
       
path: /dev/sda1
start: 63
end: 205217791
size: 205217729 (97.86 GiB)
check file system on /dev/sda1 for errors and (if possible) fix them  00:00:00    ( SUCCESS )
       
fsck.fat -a -w -v /dev/sda1
       
fsck.fat 3.0.26 (2014-03-07)
fsck.fat 3.0.26 (2014-03-07)
Checking we can access the last sector of the filesystem
Seek to 157291996672:Invalid argument
grow file system to fill the partition  00:00:31    ( ERROR )
       
using libparted
libparted messages    ( INFO )
       
The file system is bigger than its volume!
Bad FAT: unterminated chain for \FOUND.000\FILE0000.CHK. You should run dosfsck or scandisk.

========================================
```

Thanks to Testdisk I have copied most of the files (just a few, fortunately) I had on that FAT32 partition in another device.
But now for me (and for the owner of this pc) is vital to have a functioning WIN XP alongside Xubuntu.
How can I solve this **The file system is bigger than its volume!** ?
Could Testdisk or other tools be useful? (please note that we do not have Win XP CD here available)

Please help!:confused:

---

### Post by fantab on 2014-04-22
That sounds to me like a filesystem error. It could also mean 'bad sectors' in the HDD. You may want to run '[chkdsk]("https://kb.wisc.edu/helpdesk/page.php?id=5097")' on your windows partitions.
It is always recommended that you run 'chkdsk' on Windows partitions, esp. C: after we shrink/resize windows partition to make space for Ubuntu.
You may find this useful as well, [https://superuser.com/questions/193899/how-to-run-chkdsk-if-i-cant-boot-to-windows](https://superuser.com/questions/193899/how-to-run-chkdsk-if-i-cant-boot-to-windows)

Edit: OP has also posted the same issue on[ http://forums.linuxmint.com/viewtopic.php?f=46&t=165530&p=850919]("http://forums.linuxmint.com/viewtopic.php?f=46&t=165530&p=850919")

---

### Post by palimmo on 2014-04-22
> **fantab said:**
> That sounds to me like a filesystem error. It could also mean 'bad sectors' in the HDD. You may want to run '[chkdsk]("https://kb.wisc.edu/helpdesk/page.php?id=5097")' on your windows partitions.
It is always recommended that you run 'chkdsk' on Windows partitions, esp. C: after we shrink/resize windows partition to make space for Ubuntu.
You may find this useful as well, [https://superuser.com/questions/193899/how-to-run-chkdsk-if-i-cant-boot-to-windows](https://superuser.com/questions/193899/how-to-run-chkdsk-if-i-cant-boot-to-windows)
[/URL]

thanks fantab.
Unfortunately I can't run Win XP and I do not have any Win XP CD available

---

### Post by oldfred on 2014-04-22
I have run chkdsk on my XP install from my Windows 7 repair flash drive. But it converted PBR or partition boot sector to Win7 type and I had to also reinstall a XP type PBR with bootsec.exe. But Windows 7 chkdsk did work better than my XP chkdsk. My XP was in NTFS not FAT32.

Some third party Windows partition tools can run chkdsk.
       EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)

 Third party chkdsk tools
Hiren's Boot CD, and do a chkdsk on the XP
[http://www.hirensbootcd.org/](http://www.hirensbootcd.org/)

---

### Post by palimmo on 2014-04-24
no steps forward so far :(

What do you think if I try to shrink a little bit the partition in Gparted?
Because *The file system is bigger than its volume!*
Or do I risk to worsen tje situation?

---

### Post by oldfred on 2014-04-24
That sounds more like a partition table error.
IF not overlapping partitions you can try fixparts.

       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

---

