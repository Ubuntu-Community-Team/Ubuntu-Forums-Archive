---
title: "Ubuntu &quot;filesystem doesn't have requested /sbin/init&quot;"
date: 2015-01-21
forum: Installation &amp; Upgrades
---

### Post by silverslide on 2015-01-21
Hello,


I am having troubles booting ubuntu 14.04 that came out of nowhere. After selecting the OS from the grub menu I get an error starting with this message:

filesystem doesn't have requested /sbin/init

I googled this and found a solution that involved checking the disk for errors. I did this already several time with fsck and e2fsck. I also did a grub restore but that gave me an error with this log: 

[http://paste.ubuntu.com/9810729/](http://paste.ubuntu.com/9810729/)

It seems that the file system can't be accessed but I am able to mount the drive and browse the files. Has anyone got any idea's? I made a back-up and I think of trying to repair all ubuntu related files but there is no such feature like windows provides to just restore the OS and leave the rest untouched. I have a fair amount of programs, IDE's and configurations set up that I would like to keep. Is it possible to repair ubuntu or is the disk corrupts?


Kind regards,

Roel

---

### Post by ubfan1 on 2015-01-21
You are apparently missing significant parts of your Ubuntu system, /sbin/init, /usr/sbin/grub-install, and who knows what else.  Back up your files immediately, but DO NOT overwrite your previous backup, the files you backup now may be corrupted, and all you have are your previous backups.  The disk checks will sometimes put files from corrupted directories into the "/lost+found" directory, but the names are gone, so that is not worth the effort for system files, just any of your own files that might be there.  From a live media, see if your disk has the S.M.A.R.T. capabilites, and use the smartctl -a /dev/sda  (or whatever your hard disk letter is) to check it (install the smartmontools package if necessary). It will usually be obvious when an item has failed from the report.  Don't bother trying to reinstall to a failing disk.  
  If you had originally set your partitions up with a "home" partition for your files, you could just reinstall the OS to the root partition, and then remount the home partition.  If you are doing a new install, consider doing that.

---

### Post by silverslide on 2015-01-22
Is it possible to restore these missing files? Maybe from another ubuntu installation? Or is it possible to restore parts of my backup to a new ubuntu installation so that I don't have to reconfigure printer drivers, IDE's, and other software? There is no problem with the HDD. I have no lost+found directory on the driver and also sbin is missing.

---

### Post by MAFoElffen on 2015-01-22
Is this a new install or an existing system that went south? If a new install, this needs to be a bug report. 

If existing and you have things you want to keep, [COLOR=#ff0000]get a **backup** of what you want to keep[/COLOR] (facilitated from a LiveCD) before you attempt or try anything on it.

As ubfan1 implied, this is "bad." [COLOR=#ff0000]After you get a **backup** of your /home directories...[/COLOR]
> 
**Reinstall Ubuntu While Keeping Files and Programs**
If there&#8217;s a problem with your installed Ubuntu system, you should still be able to boot up an Ubuntu live CD or USB drive. Boot to the live media and start installing Ubuntu. Ubuntu should find your existing installation and give you a &#8220;Reinstall Ubuntu&#8221; option. When you perform a reinstall, the installer will keep all your personal files and settings. It will even keep your installed software packages, if possible. The Reinstall option will wipe away all your system-wide settings and return them to their defaults, but that should fix problems that misconfigured system settings could cause.


Select this option and continue through the process to reinstall Ubuntu on your computer. The installation process will also reinstall the GRUB2 boot loader along with Ubuntu, so it will also fix any GRUB issues.

Another way I would repair that is using "ubuntu-core"... but I think that would be above your skill level. That is a tarball, that involves a lot of commandline manipulation to get installed. If you are confident about your commandline skills, you could extract what was needed from that archive into your mounted filesystem. (or from a LiveCD live image.)

A third way would be to do a fresh install, then use your [COLOR=#ff0000]backup[/COLOR] to restore your data files.

Remember that all three options I suggested, started with getting a [COLOR=#ff0000]backup[/COLOR] of what you wanted to keep... None of those 3 options are 100% foolproof and a a backup would give you a second chance of keeping what you had...

---

### Post by silverslide on 2015-01-22
It is an existing installation. That's why I don't want to reconfigure and re-install everything. I don't see a re-install ubuntu option. Only install alongside and erase. Do you have a more detailed explanation of the ubuntu-core solution?

---

### Post by MAFoElffen on 2015-01-22
> **silverslide said:**
> It is an existing installation. That's why I don't want to reconfigure and re-install everything. I don't see a re-install ubuntu option. Only install alongside and erase. Do you have a more detailed explanation of the ubuntu-core solution?
Detailed instructions on the previous:
[How to fix an Ubuntu system... (<-- Link)]("http://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot/")

Screen shot of that option on the 14.04LTS LiveCD disk:
[IMG]http://cdn5.howtogeek.com/wp-content/uploads/2014/09/650x320xreinstall-ubuntu-while-keeping-files-and-programs.png.pagespeed.ic.tNv2sjZKZg.png[/IMG]

Detailed instructions for creating a VM template, but by adpating that, it will work for what you need to do:
[Ubuntu Wiki / ubuntu-core (<-- Link)]("https://wiki.ubuntu.com/Core")

---

### Post by silverslide on 2015-01-23
I have the option to install alongside instead of reinstall. Also, when I chose 'something else' and I try to select the filesystem on which my broken ubuntu is installed to install a new ubuntu. I get an error 'no root file system defined'. This is probably due to the broken file system as well and might be the reason I don't see a reinstall option?

---

### Post by ubfan1 on 2015-01-23
You wouldn't have updated a 12.04 WUBI system by any chance, would you?  WUBI's not really supported anymore, see the staff recommendations at the beginning of this group.

---

### Post by MAFoElffen on 2015-01-24
Quick test on your installed media... From LiveCD, use the file manager to find and open this file in gedit:
```

/var/log/installer/media-info

```
Copy and paste the contents into quote or code tags into a post...

---

### Post by silverslide on 2015-01-25
In media-info I find: Ubuntu 14.04.1 LTS "Trusty Tahr" - Release amd64 (20140722.2)

I have not updated a 12.04 wubi system. This error occured when I wanted to boot without any kind of ubuntu upgrade or anything special in advance.

---

