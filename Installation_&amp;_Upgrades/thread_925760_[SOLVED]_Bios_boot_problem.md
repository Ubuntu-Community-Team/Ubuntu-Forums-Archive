---
title: "[SOLVED] Bios boot problem"
date: 2008-09-21
forum: Installation &amp; Upgrades
---

### Post by dan73 on 2008-09-21
Hi,

I recently installed Ubuntu 8.04 after numerous windows problems.I have installed windows on my 250gig (sda) and Ubuntu on my 160gig drive (sdb)
I also have an old drive with some backup files which i don't use apart from backups (sdc).

here is the result from sudo fdisk -lu


 ```
Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *          63   488375999   244187968+   7  HPFS/NTFS



Disk /dev/sdb: 160.0 GB, 160041885696 bytes

255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x09910990



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   *          63   300495824   150247881   83  Linux

/dev/sdb2       300495825   312576704     6040440    5  Extended

/dev/sdb5       300495888   312576704     6040408+  82  Linux swap / Solaris



Disk /dev/sdc: 81.9 GB, 81964302336 bytes

255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors

Units = sectors of 1 * 512 = 512 bytes

Disk identifier: 0x3bdb3bda



   Device Boot      Start         End      Blocks   Id  System

/dev/sdc1   *          63   160055594    80027766    7  HPFS/NTFS

ds@ds-desktop:~$ 
```



So both my main disks have no jumpers setting and show as master in the bios (sata). My motherboard is a gigabyte GA-M68SM-S2L. 


I had numerous install problems with Ubuntu last week until I figured out that I had to change the boot priority in bios so that sdb is set to boot first. I have just reinstalled windows and now neither OS will work unless it is set to boot first in bios. Windows throws a file error and Ubuntu error 17 if they are not set a priority drive for booting. I have used super grub disk, so i can access the grub menu fine.
SDC seems to work fine as a secondary drive, I set this as third boot.

Is there any way round this, as is a pain to have to go into bios each time I want to change OS. I have installed motherboard drivers for windows, but not in Ubuntu if this makes any difference.

---

### Post by caljohnsmith on 2008-09-21
So you are able to boot the Ubuntu drive OK if it is first to boot on start up? Because if you can do that, then all you need to do is add a entry for Windows in your Grub menu, and you should be able to boot Windows too. When you boot into Ubuntu, try the following:
```
gksudo gedit /boot/grub/menu.lst
```
At the bottom, add the following:
```
title	   Windows
root (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
makeactive
chainloader +1
```
That should work assuming that your Windows drive is second in the boot order when you boot the Ubuntu drive. Let me know how it goes.

---

### Post by dan73 on 2008-09-21
Hi Caljohnsmith

Thanks for your reply. Yes, Ubuntu does normally boot fine as long as it's first on the bios boot from hard disk list.


I tried your suggestion and the error message is still there for windows when its second on the bios list (it still works if I change it to first)

" NTDLR is missing 

Press ctrl, Alt and Del to restart"

Sorry I didn't clarify, Windows is on the boot menu, it's just that when I select it it goes into the error message.

---

### Post by caljohnsmith on 2008-09-21
OK, so Windows is in your Grub's menu on start up, but did you try the entry for Windows I gave? Is that when you received the "NTLDR missing" error? If that is the case, then also try the following instead in your menu.lst:
```
title	   Windows
root (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
makeactive
chainloader +1
```
Let me know what happens when you try that. Also, please do the following in Ubuntu:
```
sudo umount /dev/sda1
```
Don't worry about a "not mounted" error, it is only to make sure it isn't mounted somewhere. Then do:
```
sudo mount /dev/sda1 /mnt
ls -l /mnt
cat /mnt/boot.ini
```
Please post the results and we can go from there.

---

### Post by dan73 on 2008-09-22
Hi CalJohn Smith

the windows error was the same as before, when I used your code in the /boot/grub/menu.lst file. I tried the new code and unmounting the drive, but still no luck. 

I did have some previous problems mounting the ntfs hard drives in ubuntu, so i had mapped them to media/filesone and media/filestwo folders after following another post. This solved the problem is was getting which said "you do not have permission to mount this drive." in Ubuntu with sda and sdc (windows ntfs). I think I also had to force a mount as well if I remember. I can access them both OK now. 

```

ds@ds-desktop:~$ ls -l /mnt 
total 240 
drwxrwxrwx 1 root root      0 2008-05-29 23:53 1 NTFS 
drwxrwxrwx 1 root root      0 2008-05-12 16:41 Files to repair?? 
drwxrwxrwx 1 root root   8192 2008-08-23 15:37 Films Torrents 
drwxrwxrwx 1 root root   4096 2008-04-01 20:24 Fonts 
drwxrwxrwx 1 root root   4096 2008-04-01 20:28 HJT 
drwxrwxrwx 1 root root      0 2008-09-21 20:44 My Music 
drwxrwxrwx 1 root root 143360 2008-09-05 22:48 Photos 
drwxrwxrwx 1 root root      0 2006-06-16 20:44 Temp 
drwxrwxrwx 1 root root      0 2006-11-19 00:17 testlog 
drwxrwxrwx 1 root root      0 2006-06-24 00:35 VLOgs 
drwxrwxrwx 1 root root  86016 2008-09-21 22:51 WINDOWS 
ds@ds-desktop:~$ ds@ds-desktop:~$ sudo mount /dev/sda1 /mnt 
ds@ds-desktop:~$ ls -l /mnt 
total 240 
drwxrwxrwx 1 root root      0 2008-05-29 23:53 1 NTFS 
drwxrwxrwx 1 root root      0 2008-05-12 16:41 Files to repair?? 
drwxrwxrwx 1 root root   8192 2008-08-23 15:37 Films Torrents 
drwxrwxrwx 1 root root   4096 2008-04-01 20:24 Fonts 
drwxrwxrwx 1 root root   4096 2008-04-01 20:28 HJT 
drwxrwxrwx 1 root root      0 2008-09-21 20:44 My Music 
drwxrwxrwx 1 root root 143360 2008-09-05 22:48 Photos 
drwxrwxrwx 1 root root      0 2006-06-16 20:44 Temp 
drwxrwxrwx 1 root root      0 2006-11-19 00:17 testlog 
drwxrwxrwx 1 root root      0 2006-06-24 00:35 VLOgs 
drwxrwxrwx 1 root root  86016 2008-09-21 22:51 WINDOWS 
ds@ds-desktop:~$ cat /mnt/boot.ini 
cat: /mnt/boot.ini: No such file or directory 
```

There you are and thanks for your help so far.

---

### Post by caljohnsmith on 2008-09-22
[QUOTE=dan73]There you are and thanks for your help so far.
[/QUOTE]
You're welcome, hopefully we can straighten out your problem. :) 

You mentioned this in your original post:
[QUOTE=dan73]
I have just reinstalled windows and now neither OS will work unless it is set to boot first in bios.[/quote]
So I assumed that you can boot the sda Windows drive if you set it first in the BIOS boot order, is this not true? Because based on your Windows directory listing that you gave in your last post, I don't see how booting from your Windows drive could work; your directory listing doesn't show any of the necessary Windows boot files (boot.ini, NTDETECT.COM, and ntldr), and also it doesn't have a "Program Files" or "My Documents" folder, nor a pagefile.sys file, which all would indicate a Windows XP install. One of the only things that looks anything like a Windows XP install is the WINDOWS folder.

So bottom line is, there's certainly no way Grub can boot sda1 if it is not first bootable, and everything about sda1 says it is unbootable at this point. :) So we can't proceed until we figure out what the deal is with your "Windows install" first.

---

### Post by dan73 on 2008-09-22
Hi 

Sorry I've been at work all day, and just got home. My windows was booting yesterday without the grub menu when it was re-installed. 

Just now I tried getting into windows and and the grub menu was visible when I changed sda back to 1st priority (before it just booted without grub). As you figured out it windows no longer boots at all. :(

I have just looked and the results I have posted for you (sorry I didn't check this morning) appear to be from sdc (80gig) which did have a windows install on it a long time ago, but as i said before I just use for data storage now.

Sorry if this is any use-- When I reinstalled windows on Saturday, the person I bought my computer from will probably have moved around the 3 internal drives inside the computer. I don't know if this may have confused the laballeing of the drives within ubuntu. I used grub boot disk yesterday though to reinstall the grub menu.

---

### Post by caljohnsmith on 2008-09-22
> **dan73 said:**
> 
I have just looked and the results I have posted for you (sorry I didn't check this morning) appear to be from sdc (80gig) which did have a windows install on it a long time ago, but as i said before I just use for data storage now.
So the Windows directory from your post #5, was that sda1 or sdc1? Whichever one you have not posted, please post the contents of its directory using the same steps as before (but using sda1 or sdc1, whichever you have not posted yet).

---

### Post by dan73 on 2008-09-22
Hi caljohnsmith

Solved :)

Thanks

When I posted the last post it was for sda, as I just cut and pasted from your instructions. Even so the results came up for sdc which is strange???

so I looked at your first post for setting the /boot/grub/menu.lst  There already was a windows listing at the end of the list which was for sdc1 with (h2,0) codes, and when I deleted this and replaced it with your (hd1,0) codes, and hey presto windows.

So to understand hd1 means the second hard drive on the boot menu and hd2 the third??

I think my grub disk must have seen my old dead windows install and thought it was bootable.

I just wonder if I may have future problems due to my disk labelling in Ubuntu being confused?? Do you think this is a problem or should I just leave it.

thanks anyway, i'm now typing this in windows. Well I will carry on using Ubuntu as my main OS, as I like quite a few things about it even if things take a bit longer to setup than in windows.
I just need windows for Photoshop and printing really, my canon doesn't work under ubuntu. Maybe one day soon. I will try to learn gimp when I have time.

Many thanks again for your help.

Dan

---

### Post by caljohnsmith on 2008-09-22
> **dan73 said:**
> Hi caljohnsmith

Solved :)

Thanks

When I posted the last post it was for sda, as I just cut and pasted from your instructions. Even so the results came up for sdc which is strange???

so I looked at your first post for setting the /boot/grub/menu.lst  There already was a windows listing at the end of the list which was for sdc1 with (h2,0) codes, and when I deleted this and replaced it with your (hd1,0) codes, and hey presto windows.

So to understand hd1 means the second hard drive on the boot menu and hd2 the third??

Yes, the biggest confusion for most people when learning about Grub (including myself), is that on system start up when you get your Grub menu, *Grub sees the order of drives the same as the BIOS boot order*, not the same as the Ubuntu's order of devices in the /dev directory. So if you got Windows to boot with (hd1), that means that Windows must be on the 2nd drive in the BIOS boot order, just like you surmised.

Also, if you copied/pasted my previous commands to mount sda1, then that should truly be the directory listing of sda1. I think that maybe you mistakenly installed Windows to sdc1. How about we find out for sure:
```
sudo umount /dev/sdc1
sudo mount /dev/sda1 /mnt
ls -l /mnt
```
Please post the output of above. 
> **dan73 said:**
> 
I think my grub disk must have seen my old dead windows install and thought it was bootable.

I just wonder if I may have future problems due to my disk labelling in Ubuntu being confused?? Do you think this is a problem or should I just leave it.

I don't think Ubuntu is getting confused, but I think we may be at this point. :) Instead of mounting sda1 and sdc1 on /media/filesone and /media/filestwo, I think it would be clearer if you used something like /media/sda1 and /media/sdc1. You could even be more descriptive than that of course. It's easy to change where sda1 and sdc1 are mounted by changing the related lines in your /etc/fstab file. If you want help with that let me know.

---

### Post by dan73 on 2008-09-22
Hi

```
ds@ds-desktop:~$ sudo umount /dev/sdc1
[sudo] password for ds: 
umount: /: device is busy
umount: /: device is busy
ds@ds-desktop:~$ sudo mount /dev/sda1 /mnt
ds@ds-desktop:~$ ls -l /mnt
total 244
drwxrwxrwx 1 root root      0 2008-05-29 23:53 1 NTFS
drwxrwxrwx 1 root root      0 2008-05-12 16:41 Files to repair??
drwxrwxrwx 1 root root   8192 2008-08-23 15:37 Films Torrents
drwxrwxrwx 1 root root   4096 2008-04-01 20:24 Fonts
drwxrwxrwx 1 root root   4096 2008-04-01 20:28 HJT
drwxrwxrwx 1 root root      0 2008-09-21 20:44 My Music
drwxrwxrwx 1 root root 143360 2008-09-05 22:48 Photos
drwxrwxrwx 1 root root      0 2008-09-22 23:05 RECYCLER
drwxrwxrwx 1 root root   4096 2008-09-22 23:05 System Volume Information
drwxrwxrwx 1 root root      0 2006-06-16 20:44 Temp
drwxrwxrwx 1 root root      0 2006-11-19 00:17 testlog
drwxrwxrwx 1 root root      0 2006-06-24 00:35 VLOgs
drwxrwxrwx 1 root root  86016 2008-09-21 22:51 WINDOWS
ds@ds-desktop:~$ 
```

I only based my naming on the intial sudo fdisk lu results so i suppose these must be wrong??? 

I've just tried sudo fdisk lu again and terminal says

```
ds@ds-desktop:~$ sudo fdisk lu
[sudo] password for ds: 

Unable to open lu
```




My hard drive bios says 

Ch3 M  is my Linux 160gig drive
Ch2 M is my windows 250 gig
Ch0 S  is my windows old 80 gig

Sda will then be my 80 gig drive and Sdc my 250gig which has the working windows install? Is this correct??

Yes if you have time I would like help remounting the drives in my /etc/fstab file, I would like to straighten things out. 

By the way, both my windows drives are visible from ubuntu, and have shortcuts mounted when i open ubuntu, so there are no problems there.

I am off to bed now its 12.40 am here in Korea so I won't be able to reply until sometime tomorrow may be a long while before I can reply. Thanks again for your help

dan

---

### Post by caljohnsmith on 2008-09-22
You're welcome, glad to help out here when I can. :)

Please post the output of:
```
sudo mount
sudo fdisk -lu
cat /etc/fstab
```
Notice the dash "-" before the lu options with the fdisk command. :)

---

### Post by dan73 on 2008-09-22
hi

```
ds@ds-desktop:~$ sudo mount
[sudo] password for ds: 
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/filesone type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdc1 on /media/filestwo type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ds/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ds)
ds@ds-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x16b016af

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488375999   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x09910990

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   300495824   150247881   83  Linux
/dev/sdb2       300495825   312576704     6040440    5  Extended
/dev/sdb5       300495888   312576704     6040408+  82  Linux swap / Solaris

Disk /dev/sdc: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3bdb3bda

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   160055594    80027766    7  HPFS/NTFS
ds@ds-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sdb1 :
UUID=0b82c392-b7f4-4ec0-9e97-00deb2cba006 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sdb5 :
UUID=9ec6d9eb-8f56-4dec-822a-ea57594e29ab none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sda1 /media/filesone ntfs-3g defaults,locale=en_US.utf8 0 0
/dev/sdc1 /media/filestwo ntfs-3g defaults,locale=en_US.utf8 0 0
ds@ds-desktop:~$ 
```

---

### Post by caljohnsmith on 2008-09-22
OK, looks good, so just do:
```
ls -l /media/filesone
ls -l /media/filestwo
```
and please post the output.

---

### Post by dan73 on 2008-09-22
Hi

```
ds@ds-desktop:~$ ls -l /media/filesone
total 2095466
-rwxrwxrwx 1 root root          0 2008-09-20 20:17 AUTOEXEC.BAT
-rwxrwxrwx 1 root root        223 2008-09-20 20:57 boot.ini
-rwxrwxrwx 1 root root          0 2008-09-20 20:17 CONFIG.SYS
-rwxrwxrwx 1 root root        206 2008-09-20 20:58 csb.log
drwxrwxrwx 1 root root       4096 2008-09-20 20:21 Documents and Settings
-rwxrwxrwx 1 root root          0 2008-09-20 20:17 IO.SYS
-rwxrwxrwx 1 root root          0 2008-09-20 20:17 MSDOS.SYS
drwxrwxrwx 1 root root          0 2008-09-20 21:26 MSOCache
-rwxrwxrwx 1 root root      47564 2004-08-04 21:00 NTDETECT.COM
-rwxrwxrwx 1 root root     250048 2008-09-20 22:37 ntldr
drwxrwxrwx 1 root root          0 2008-09-20 21:10 NVIDIA
-rwxrwxrwx 1 root root 2145386496 2008-09-22 23:29 pagefile.sys
drwxrwxrwx 1 root root       8192 2008-09-22 23:07 Program Files
drwxrwxrwx 1 root root          0 2008-09-20 20:52 RECYCLER
-rwxrwxrwx 1 root root        429 2008-09-20 20:58 RHDSetup.log
drwxrwxrwx 1 root root       4096 2008-09-20 20:20 System Volume Information
drwxrwxrwx 1 root root      49152 2008-09-22 23:31 WINDOWS
ds@ds-desktop:~$ ls -l /media/filestwo
total 244
drwxrwxrwx 1 root root      0 2008-05-29 23:53 1 NTFS
drwxrwxrwx 1 root root      0 2008-05-12 16:41 Files to repair??
drwxrwxrwx 1 root root   8192 2008-08-23 15:37 Films Torrents
drwxrwxrwx 1 root root   4096 2008-04-01 20:24 Fonts
drwxrwxrwx 1 root root   4096 2008-04-01 20:28 HJT
drwxrwxrwx 1 root root      0 2008-09-21 20:44 My Music
drwxrwxrwx 1 root root 143360 2008-09-05 22:48 Photos
drwxrwxrwx 1 root root      0 2008-09-22 23:05 RECYCLER
drwxrwxrwx 1 root root   4096 2008-09-22 23:05 System Volume Information
drwxrwxrwx 1 root root      0 2006-06-16 20:44 Temp
drwxrwxrwx 1 root root      0 2006-11-19 00:17 testlog
drwxrwxrwx 1 root root      0 2006-06-24 00:35 VLOgs
drwxrwxrwx 1 root root  86016 2008-09-21 22:51 WINDOWS
ds@ds-desktop:~$ 

```

---

### Post by caljohnsmith on 2008-09-22
Well I don't know what happened earlier, but it looks like your Windows install is indeed on the sda drive which is where you wanted it; so that is good. Your Windows sda drive is now mounted on /media/filesone and the sdc drive with your other files is mounted on /media/filestwo. Is this how you want to keep it, or do you want to change the name of the mount points? It's not necessary of course, it's up to you. If you do want to change the mount point names to something other than "filesone" and "filestwo", let me know what you want to use instead, and we can step through the process of changing them.

---

### Post by dan73 on 2008-09-22
Hi 

No thanks, if you think everything is OK, I will leave it at that. I don't really need to change the names as long as everything is OK.


Dan:)

---

### Post by caljohnsmith on 2008-09-22
Sounds good to me. Cheers and have fun. :)

---

