---
title: "xubuntu 7.10 unclean boot after dual installation with kunbuntu 7.10"
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by jim.hitch on 2007-11-14
Hi

I've been running a kunbuntu / xubuntu dual boot for about 9 months and decided I needed a bigger HDD for my laptop, this gave me the opportunity (and no more excuses) to start over with a clean installation.

When I did the installation the 1st time I did it Kubuntu 1st then Xubuntu and noticed that grub then focussed on the menu.lst etc. in the Xubuntu partition, which I wasn't so happy with, hence this time I installed the Xubuntu 1st.

Installed Xubuntu after creating a partion - no problems, worked a treat, then did the Kubuntu, and that worked a treat too, only now the boot to Xubuntu doesn't go all the way through, the fsck fails (I think) and I can only get the Xubuntu to work with the help of a couple of ctrl+Ds.

The only difference I can see is that with the new HDD I have put in an extra partition, FAT32, in order to install, possibly, a version of windows at a later date.

Anyhow, here's the /media/Xubuntu/var/log/fsck/checkfs from the failed boot:

[B]Log of fsck -C -R -A -a 
Tue Nov 13 07:32:53 2007

fsck 1.40.2 (12-Jul-2007)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda2: 0 files, 1/1922905 clusters
fsck.ext3: Unable to resolve 'UUID=ff6d250a-6eef-4656-85e8-1da846df1abf'
fsck died with exit status 8

Tue Nov 13 07:32:54 2007
----------------[/B]

Is it that it can't check the extra partition because it's FAT32?

Would appreciate some help.

Thanks

Jim

Acer Travelmate C111tci (1Ghz Centrino; 2Gb RAM; 100Gb Hdd)

---

### Post by jim.hitch on 2007-11-16
Ok, I have realised something else. In grub the boot choice for Xubuntu looks like this:

[B]title		Xubuntu 7.10, kernel 2.6.22-14-generic
root		        (hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=0dcfb68e-76b0-44ab-8221-a66c90aa669e ro quiet splash
initrd		        /boot/initrd.img-2.6.22-14-generic
quiet[/B]

whereas the UUID in the checkfs log is this

**UUID=ff6d250a-6eef-4656-85e8-1da846df1abf**

I'm assuming this is significant, but what can I do about it?

Thanks

---

### Post by Doggles on 2007-11-16
Hi Jim - I've got the same problem - I found this thread which might help?

[http://ubuntuforums.org/showthread.php?t=599546&highlight=resolve+UUID](http://ubuntuforums.org/showthread.php?t=599546&highlight=resolve+UUID)

I've emailed it home to try to make sense of it later so I don't know if it works for me yet...

---

### Post by jim.hitch on 2007-11-16
Thanks for the link Doggles.

From what I can guess the UUID of sda1 got mixed up somehow along the way, and it was the check of that that was causing the Xubuntu boot to stall.

So, I ran this command in the terminal

**ls -l  /dev/disk/by-uuid/**

Which gave me this

[B]lrwxrwxrwx 1 root root 10 2007-11-16 11:52 0dcfb68e-76b0-44ab-8221-a66c90aa669e -> ../../sda3
lrwxrwxrwx 1 root root 10 2007-11-16 11:52 4732-F9DF -> ../../sda2
lrwxrwxrwx 1 root root 10 2007-11-16 11:52 [COLOR="Red"]4dc9de23-6b17-4cd1-9122-4c22d6ae49a9[/COLOR] -> ../../sda1
lrwxrwxrwx 1 root root 10 2007-11-16 11:52 d0f07dfd-8741-4793-ac15-f26446237bc1 -> ../../sda4[/B]

and compared that with /media/Xubuntu/etc/fstab (ie. the fstab in the Xubuntu build), which was

[B]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=0dcfb68e-76b0-44ab-8221-a66c90aa669e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=[COLOR="red"]ff6d250a-6eef-4656-85e8-1da846df1abf[/COLOR] /media/sda1     ext3    defaults        0       2
# /dev/sda2
UUID=4732-F9DF  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda4
UUID=d0f07dfd-8741-4793-ac15-f26446237bc1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0[/B]

It was easy to see from this that it was the UUID for /dev/sda1 which was incorrect. I copied and pasted (ie. correcting /media/Xubuntu/etc/fstab) and bingo, boots no problem.

Thanks again and good luck!

Jim

---

### Post by infoseeker on 2007-11-16
You could simply change
```
# /dev/sda1
UUID=ff6d250a-6eef-4656-85e8-1da846df1abf /media/sda1 ext3 defaults 0 2
```
to```
/dev/sda1  /media/sda1 ext3 defaults 0 2
```
Not sure what the differences are :)

---

