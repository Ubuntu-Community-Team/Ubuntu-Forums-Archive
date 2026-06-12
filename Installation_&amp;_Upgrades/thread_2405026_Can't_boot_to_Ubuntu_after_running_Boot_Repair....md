---
title: "Can't boot to Ubuntu after running Boot Repair..."
date: 2018-10-31
forum: Installation &amp; Upgrades
---

### Post by hashs on 2018-10-31
[COLOR=#242729][FONT=Arial]Hi guys, it's my first post here and, as usual with newcomers, I am completely lost. I am not completely new to Ubuntu but I am dealing with an error I simply don't know how to solve.

I don't know where to start.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
I accidentaly deleted some commands in /bin, so my Ubuntu bionic wouldn't work properly. Firefox wouldn't open, the left bar with programs was not appearing, etc. When I was trying to apt-get update, this message was showing:[/FONT][/COLOR]

update-initramfs: Generating /boot/initrd.img-4.15.0-38-generic
WARNING: no ldd around - install libc-bin
update-initramfs: failed for /boot/initrd.img-4.15.0-38-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-4.15.0-38-generic (--configure):
 installed linux-image-4.15.0-38-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-4.15.0-38-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
[COLOR=#242729][FONT=Arial]
I've executed sudo apt-get install --reinstall debianutils and sudo apt-get install --reinstall grub-common.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
This made me not able to boot at all. A message showed "Kernel Panic":[/FONT][/COLOR]

kernel panic-not syncing: VFS: unable to mount root 
[COLOR=#242729][FONT=Arial]
I've restarted the computer then, and Grub was showing only Ubuntu (not designation for dev/sdX, only the name Ubuntu). When I've tried to enter it, only a blank screen was showing... Not able to boot at all.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
Then I've tried to enter from a Live USB. I executed Boot Repair. It exited with an error message and only made things worse. There was an message that said I should save this URL:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][https://paste.ubuntu.com/p/V2cXD2QQBG]("https://paste.ubuntu.com/p/V2cXD2QQBG/")[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
I rebooted and now grub shows Windows (was on dev/sda1 only) in other partition as well (/dev/sda2). I dont understand what is happening. Has it overwritten my Ubuntu partition? Is there a way I can still access my old Ubuntu partition?
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Maybe reinstalling the whole stuff would be easier, but I have stuff on the Ubuntu partition I have to access...

I don't know what I am doing at this point and would really appreciate help here. [/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
Thanks![/FONT][/COLOR]

---

### Post by oldfred on 2018-10-31
If you delete something or change permissions on something essential in / (root) which is just about everything other than log files, it probably is easier to reinstall.
You should have good backups anyway, so you do not have to worry about system issues, hard drive failure or operator error.
Also if you have /home in separate partition, it is easier. But still a few files in / that you may want to backup.

       Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872) 
    
       discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224](https://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224)
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery) 
    
       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

---

### Post by hashs on 2018-10-31
[COLOR=#242729][FONT=Arial]Thanks Oldfred! I guess  I will reinstall the whole thing. But I have one question:

Would it be possible to access info I had on the old Ubuntu before I reinstall it? Such as info stored on Firefox, preferences etc? Actually is the only thing I would like to save.
[/FONT][/COLOR]

---

### Post by oldfred on 2018-10-31
If file system is ok, you can normally mount a Linux partition and copy any data you want.
Firefox &  Thunderbird are in /home in . folders (hidden), so you have to unhide them. You should copy entire profile.

       Firefox
[https://support.mozilla.org/en-US/products/firefox](https://support.mozilla.org/en-US/products/firefox)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles](https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles)

---

### Post by hashs on 2018-11-01
Really appreciate your time answering this. Gonna try it out. 

Thank you! I'll be back here to say if its solved or not.

---

