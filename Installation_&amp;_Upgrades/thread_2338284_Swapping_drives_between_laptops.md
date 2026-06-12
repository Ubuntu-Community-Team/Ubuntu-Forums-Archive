---
title: "Swapping drives between laptops"
date: 2016-09-26
forum: Installation &amp; Upgrades
---

### Post by Roger_Williams on 2016-09-26
I decided to get a laptop with a faster processor and more memory. Am I able to swap the hard drive from my current laptop to the new laptop? I know in the Windows world it can be done but you have to run the sysprep tool to reset system settings and drivers. I don[t know if Linux is the same or if it's independent of the hardware? If I can't just do a straight swap what is the best way to do a backup of the current config so I don't have to redo everything from scratch? There is no data I'm concerned with it's all about the setup, settings and installed apps. I'm running ubuntu 16 x64 and the latest Kali x64. I'm going from a Dell to an HP Pavillion.

---

### Post by TheFu on 2016-09-26
Remove any proprietary drivers first - like video drivers.  Use the F/LOSS drivers.

Laptops are harder for drivers ... sometimes the SATA controller isn't supported, wifi, GPUs ... so be prepared. If you need to go back to the other system, have a solid, backup.

I've never moved between laptops, but have moved between P4 and Core i7 desktops.  Also moved from C2D to Core i5 desktops.
Only thing I remember cleaning up was the udev rules for eth0, but systemd has totally screwed that up already, so no cleanup will make that better.

Really, the better answer would be to use your normal backup and restore methods to migrate the installs over.  If they don't work perfectly, you'd know it and could practice until it does work. This is an opportunity.

---

### Post by him610 on 2016-09-26
FWIW - I have swapped HDDs between laptops without any problems. They are both about eight years old one of them, Alienware Area51, is one that always gave me difficulties while trying to install a new distribution. I think it was because of the dual graphics chips. 

I finally hit upon the idea of installing a new distro on my other laptop, Acer 8930, then moving the HDD with newly installed distro to the Alienware. Worked like a charm with both 14.04 and 16.04. Both laptops were equipped with intel CPUs and Nvidia graphics chips.

Follow the advice provided by TheFu and you should not have any problems.

---

### Post by oldfred on 2016-09-26
Is old laptop BIOS and new one UEFI?

HP is not UEFI dual boot friendly. If violates UEFI spec that says not to use description as part of boot.
There are multiple work arounds depending on your installs.
Some just revert to older BIOS/MBR which should work if system is set to CSM/Legacy. But you lose the advantages of UEFI & gpt.

---

### Post by Roger_Williams on 2016-09-27
> **TheFu said:**
> Remove any proprietary drivers first - like video drivers.  Use the F/LOSS drivers.

Laptops are harder for drivers ... sometimes the SATA controller isn't supported, wifi, GPUs ... so be prepared. If you need to go back to the other system, have a solid, backup.

I've never moved between laptops, but have moved between P4 and Core i7 desktops.  Also moved from C2D to Core i5 desktops.
Only thing I remember cleaning up was the udev rules for eth0, but systemd has totally screwed that up already, so no cleanup will make that better.

Really, the better answer would be to use your normal backup and restore methods to migrate the installs over.  If they don't work perfectly, you'd know it and could practice until it does work. This is an opportunity.

> **him610 said:**
> FWIW - I have swapped HDDs between laptops without any problems. They are both about eight years old one of them, Alienware Area51, is one that always gave me difficulties while trying to install a new distribution. I think it was because of the dual graphics chips. 

I finally hit upon the idea of installing a new distro on my other laptop, Acer 8930, then moving the HDD with newly installed distro to the Alienware. Worked like a charm with both 14.04 and 16.04. Both laptops were equipped with intel CPUs and Nvidia graphics chips.

Follow the advice provided by TheFu and you should not have any problems.

> **oldfred said:**
> Is old laptop BIOS and new one UEFI?

HP is not UEFI dual boot friendly. If violates UEFI spec that says not to use description as part of boot.
There are multiple work arounds depending on your installs.
Some just revert to older BIOS/MBR which should work if system is set to CSM/Legacy. But you lose the advantages of UEFI & gpt.

Thanks guys for the awesome information. I'm new to Linux so what are the best backup options? In the newer laptop I may go away from dual boot with more memory I can have a usable virtuial Kali in Ubuntu. TheFu is right it is a great oppurtunity to learn so I will be trying to swap between the systems. If I can get the setup I already have to work that would be great since it's all configured.

---

### Post by oldfred on 2016-09-27
This is what I use for backup, but I have a home system and I do not really consider the rsync my real backup, but the copies of grandkids photos copied to DVD every 6 months, so multiple copies as real backup.

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

TheFu has better backup suggestions if server or more critical system.
      
 Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)
Sample rdiff file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)
[http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use)

---

### Post by Roger_Williams on 2016-09-27
> **oldfred said:**
> This is what I use for backup, but I have a home system and I do not really consider the rsync my real backup, but the copies of grandkids photos copied to DVD every 6 months, so multiple copies as real backup.

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

TheFu has better backup suggestions if server or more critical system.
      
 Discussion of issues on rsync bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)
Sample rdiff file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)
[http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use)

Awesome info, it's def not a critical system it's just a personal laptop for learning Linux and pentesting.

---

