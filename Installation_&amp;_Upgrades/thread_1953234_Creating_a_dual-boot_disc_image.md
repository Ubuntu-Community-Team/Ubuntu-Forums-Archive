---
title: "Creating a dual-boot disc image"
date: 2012-04-05
forum: Installation &amp; Upgrades
---

### Post by icydash on 2012-04-05
Hey guys.  This may be the wrong place to post this, but here's my question:

I have partitioned my laptop (Dell Studio XPS 1640) so that one partition contains the latest Ubuntu release, and the other has Windows Vista.  As installation and configuration of both OSes was a major hassle, I'd like to backup my HD in such a way that, should it crash, I can easily restore it to it's current dual-boot setup.

I think the correct way to do that is with disc imaging (but if someone else has any better ideas, let me know).  Does anyone know of free (or if need be, paid) software with which I can backup both partitions / create a full HD image onto my Passport backup drive ([http://external-hard-drive-review.toptenreviews.com/western-digital-hard-drives-review.html](http://external-hard-drive-review.toptenreviews.com/western-digital-hard-drives-review.html))?  Of course, the software should have some kind of way for me to reinstall both OSes in their entirety on a new HD if (when) my current HD crashes.

Thanks!

---

### Post by oldfred on 2012-04-05
Welcome to the forums.

Many suggest Windows software for Windows and Linux software for Linux. I also believe in small system partitions and separate data partitions. And then only backup configuration settings, so you can do a clean install.

For Windows you should make the vendor recovery DVDs, a system repairCD or USB and a full backup of your system.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

For Ubuntu you can make a full image backup with clonezilla and others.

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
Free Imaging software - CloneZilla & PartImage - Tutorial 
[http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)

But you will not make a full image often enough, so other tools can easily back up important data.

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

### Post by icydash on 2012-04-06
Thanks for the response!

So I have like 2 years worth of stuff, tons of programs installed and configured, system updates, etc.  So I'm not looking for a clean install, but a backup of my current system as it stands today, with everything.  So I think that's called a "full backup" by what you were saying?  Which of those links applies for this?

And I need to do a full backup for both partitions, but I only have a single Passport USB backup drive.  So do I do the windows full backup first and then the ubuntu one?  Or do I need to buy another backup drive and do them separately on separate backup drives?

Ideally, I'd like to just run one program and have my computer returned to the way it is now, exactly, including both partitions.

Thanks!

---

### Post by oldfred on 2012-04-06
As I mentioned I only back up my data and configurations, some data goes back to DOS days and I am not sure why I am still backing that up? It has been on several DVDs a year for 20 years. :)

But some have posted that Macrim & clonezilla both work well. I think either can back up full system but am not sure.

---

### Post by Mark Phelps on 2012-04-06
Macrium Reflect (MR), which can be downloaded for free, can either backup entire physical drives (when multiple Windows filesystem partitions are needed), or just individual partitions.

Since it doesn't work on Ext4 partitions, you should just install it in Win7 and use it to back up Win7.  Use the option to create the Linux Boot CD -- if you want to be able to restore it later should Win7 stop working.

If you BUY MR, it also comes with an option of installing a Recovery boot app on your hard drive -- which then allows you to run the restore without having to boot from CD.

---

### Post by icydash on 2012-04-06
> **Mark Phelps said:**
> Macrium Reflect (MR), which can be downloaded for free, can either backup entire physical drives (when multiple Windows filesystem partitions are needed), or just individual partitions.

Since it doesn't work on Ext4 partitions, you should just install it in Win7 and use it to back up Win7.  Use the option to create the Linux Boot CD -- if you want to be able to restore it later should Win7 stop working.

If you BUY MR, it also comes with an option of installing a Recovery boot app on your hard drive -- which then allows you to run the restore without having to boot from CD.

Thanks for your comment!

Since overwriting my current Vista setup with Win7 and erasing 2 years worth of work would defeat the purpose of the backup system, I'm not really sure that's an option (unless I'm missing something).  I do own Win7, but got it after I already had Vista installed on this laptop, and I have tons of programs installed / configured which is what I'm trying to save.  According to the Macrium website, though, it should work with Vista  ([http://www.macrium.com/reflectfree.aspx](http://www.macrium.com/reflectfree.aspx)).

I'm not sure what you mean with Ext4 partitions; is it the Ubuntu partition that's the problem then? What is a linux boot CD exactly, anyway?

You said Macrium back up entire physical drives -- does that include the linux partition then?

Thanks for the help!

---

### Post by oldfred on 2012-04-07
Standard Ubuntu desktop install ISOs are boot CD or USB if installed correctly (not copied). Other versions like the server or alternate installer are just install disks. Even if installing with an install only version, you should download the liveCD version to be able to make repairs if need be. 

Ubuntu uses ext4 formated partitions for a standard install. Many other types can be used but not Windows NTFS unless using Wubi which is just a file in the NTFS partition.

To see your partitions from a terminal in your install or from a liveCD.

```
sudo fdisk -lu
```

---

### Post by icydash on 2012-04-07
> **oldfred said:**
> Standard Ubuntu desktop install ISOs are boot CD or USB if installed correctly (not copied). Other versions like the server or alternate installer are just install disks. Even if installing with an install only version, you should download the liveCD version to be able to make repairs if need be. 

Ubuntu uses ext4 formated partitions for a standard install. Many other types can be used but not Windows NTFS unless using Wubi which is just a file in the NTFS partition.

To see your partitions from a terminal in your install or from a liveCD.

```
sudo fdisk -lu
```

I did that command and this was the response:
```

zsk@ubuntu:~$ sudo fdisk -lu
[sudo] password for zsk: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x70000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      321299      160618+  de  Dell Utility
/dev/sda2          321536    31778815    15728640    7  HPFS/NTFS/exFAT
/dev/sda3   *    31778816   625139711   296680448    7  HPFS/NTFS/exFAT
zsk@ubuntu:~$ 
```

So it looks like the ubuntu partition is exFAT?  Is that different from ext4?  If so, does that mean I can back it up?

---

### Post by oldfred on 2012-04-07
If that is the case you have to have installed wubi as that is the only version that works with NTFS and is just a file inside the NTFS partition.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
The Windows-based Ubuntu Installer (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user try Ubuntu without risking any data loss due to disk formatting or partitioning.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

You then should be able to just use Windows tools. But may want to separately back up root.disk at that is your Ubuntu install.

---

### Post by icydash on 2012-04-07
> **oldfred said:**
> If that is the case you have to have installed wubi as that is the only version that works with NTFS and is just a file inside the NTFS partition.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
The Windows-based Ubuntu Installer (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows. It lets a Microsoft Windows user try Ubuntu without risking any data loss due to disk formatting or partitioning.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

You then should be able to just use Windows tools. But may want to separately back up root.disk at that is your Ubuntu install.
Yep that all looks familiar; I definitely have Wubi.

Ok so I should be able to use something like Macrium Reflect to back up both by backing up my NTFS file partition, correct?  Because ubuntu is just a bunch of files on my windows partition?

And I do see on that link you sent that I should copy root.disk; how is that different then just copying all my files by making an image of my NTFS? Presumably, imaging my HD will also backup the ubuntu files, including root.disk?

What's the main difference between wubi and having ubuntu on its own partition?

---

### Post by oldfred on 2012-04-08
Wubi is fine for a test that is longer than the liveCD. You then can easily uninstall it as you have not created partitions. But it is just a file in the NTFS partition and relies on the Windows boot loader. So any system hiccup in Windows will prevent booting or it is not a true dual boot. With a separate partition if one system does not work, the other may unless it is total hard drive failure.

If you decide you like and want to use Ubuntu a fair amount it may be time for a partitioned install.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by icydash on 2012-04-08
> **oldfred said:**
> Wubi is fine for a test that is longer than the liveCD. You then can easily uninstall it as you have not created partitions. But it is just a file in the NTFS partition and relies on the Windows boot loader. So any system hiccup in Windows will prevent booting or it is not a true dual boot. With a separate partition if one system does not work, the other may unless it is total hard drive failure.

If you decide you like and want to use Ubuntu a fair amount it may be time for a partitioned install.

HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Great! Thanks a lot for all the help.  

I only really use ubuntu for doing ruby on rails development for fun in my free time, so I don't think (for the time being) a whole separate partition is really necessary.  

I'm mostly just trying to back up my system in case of a full hard drive failure; I'm not so worried about Windows itself having major issues where it won't boot.  But everything you guys have told me is definitely good to know just in case.

Thanks again!

---

### Post by oldfred on 2012-04-08
I am a belt & suspender type, so I have several drives with different Ubuntus or an XP on each drive. I also have several USB flash drives for installing and found with a larger flash drive (8GB or more) I could do a full install. It is not speedy but functional if you have a fair amount of RAM. You do want to turn off some settings to reduce writes.

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

---

### Post by roelforg on 2012-04-08
If you just wan't backups of your docs, this might be an addition to full backups:
Get someone to host you a private git repo, clone it into your home dir and keep your docs there.
Add some startup/shutdown scripts to run an add, commit with a commitmsg containing date and finally a push.
Great addition to full backups as it gives you the benefit of being able to "restore" to a previous boot.

---

### Post by icydash on 2012-04-08
Cool thanks everyone!

---

