---
title: "File atrributes lost after copying to new mSATA SSD"
date: 2015-11-30
forum: Installation &amp; Upgrades
---

### Post by modjtabaf on 2015-11-30
Hi all,

Recently I purchased a mSATA SSD for my ThinkPad X220 laptop. I wanted to have both Windows 10 and Ubuntu installed on my laptop, so I created a 60GB NTFS partition for Windows 10, a 110GB NTFS partition for my data and a 60GB ext4 partition for my Ubuntu installation. After installing both OSs and the grub, I decided to copy my personal files from my old HDD to my data partition. First I tried 'sudo cp -rp' command to copy one directory, but after doing that I noticed all permissions were set to rwxrwxrwx and all files were owned by root. Then I tried 'sudo rsync -a' which resulted the same. I also tried running the commands without 'sudo', copying the files using Ubuntu file manager program and copying in Windows 10, but I always got new files with permissions set to rwxrwxrwx and owned by root user.

For your reference, in order to mount my data partition in Ubuntu, I added this line to '/etc/fstab/':

```

UUID=xxxxxxxxxxxx /media/D ntfs-3g rw,user,exec,discard,noatime,errors=remount-ro 0 1

```

I don't know what I am doing wrong. Any ideas?

---

### Post by Vladlenin5000 on 2015-11-30
Hi and welcome.

Copying files to a NTFS partition will override any previous (Linux/Unix) permissions no matter what you do.

---

### Post by modjtabaf on 2015-11-30
Thanks for your response. My old HDD is formatted as NTFS too. I used 'cp -rp' command to copy some files to another location on that drive and all permissions were preserved. So, I am assuming this shouldn't be an issue with NTFS itself.

---

### Post by oldfred on 2015-11-30
NTFS does not support ownership nor permissions. It all is set with defaults with the mount either manually or with fstab.

I have seen & used this for NTFS on HDD. But you should keep the noatime for SSD.
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

   For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

### Post by modjtabaf on 2015-12-01
I just figured out what the problem is and how to solve it. First of all, as the second answer to the following post states, NTFS does support ownership and permissions:

[http://askubuntu.com/questions/11840/how-do-i-use-chmod-on-an-ntfs-or-fat32-partition](http://askubuntu.com/questions/11840/how-do-i-use-chmod-on-an-ntfs-or-fat32-partition)

In order to enable them, one can either use 'fmask=0022,dmask=0000' flags while mounting the partition or make use of user mapping. User mapping is the preferred method if the drive will be used by both Linux and Windows, which is exactly what I need. You may find the details in this excellent article:

[http://www.tuxera.com/community/ntfs-3g-advanced/user-mapping/](http://www.tuxera.com/community/ntfs-3g-advanced/user-mapping/)

After doing that, both 'cp -rp' and 'rsync -a' worked as I expected.

---

