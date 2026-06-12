---
title: "OK to mv /initrd.img.old to /initrd.img so I can boot?"
date: 2015-07-18
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2015-07-18
The /boot/**initrd.img-3-13.0-[COLOR=#0000ff]57[/COLOR]-generic** archive on my Precise system got hosed during a "routine" upgrade of kernel files, and doesn't exist.  

That means I can't boot into Precise.  (Because **/initrd.img** links to it, and "it" isn't there.)

I do have an** /initrd.img.old** linked to /boot**/initrd.img-3.13.0-[COLOR=#0000ff]55[/COLOR]-generic**.  

***Should*** I be able to link **/initrd.img** to /boot**/initrd.img-3.13.0-[COLOR=#0000ff]55[/COLOR]-generic **and thereby boot with no problems?  (Once I get booted in, I can upgrade the kernel appropriately.)

I ask because the other files in /boot -- *System.map*, *abi*, *config* and *vmlinuz* -- all contain both kernel numbers **[COLOR=#0000ff]-55[/COLOR] *and*** **[COLOR=#0000ff]-57[/COLOR]** (as well as some older versions). 

If there's a **[COLOR=#0000ff]-57[/COLOR]** for all these files in /boot, will it still be possible / okay to link** /initrd.img** to /boot**/initrd.img-3.13.0[COLOR=#0000ff]-55[/COLOR]-generic** and boot up without causing conflicts or problems?  

Thanks.


[ Edit: my subject header mistakenly contains "ubuntu-mate"  -- I don't know how to change that after I've posted. My question is about an Ubuntu Precise installation. ]

---

### Post by Bashing-om on 2015-07-18
watchpocket; Uuoohhh ..

Do not think that is such a good idea.
Perhaps better to boot up and older kernel and rebuild the -57 image .
```

sudo update-initramfs -u -k 3-13.0-57 -generic

```

This is providing that there is operating headroom in /boot.
Always a good idea to remove no-longer-needed(wanted) old kernels.
Check for space:
```

df -h
df -i

```

[INDENT][INDENT]let the system
[INDENT][INDENT][INDENT]do it's job
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by watchpocket on 2015-07-18
> **Bashing-om said:**
>  . . . Perhaps better to boot up and older kernel and rebuild the -57 image .

Thanks for the response, Bashing-om. I'm not sure how I'd boot up into an older kernel -- I didn't include older kernels in my GRUB2 menu when I configured it. (A mistake, I now realize.)

I did try to boot into recovery mode but had no success with that.

I can boot to my **sda1** disk (my Ubunut-MATE system).  My **sdb1** disk is the Precise system, and that's what I can't boot into, that's where I'm missing the init.img-57.

> ```

sudo update-initramfs -u -k 3-13.0-57 -generic

```

I take it I would not want to issue this command from sda1.  And I can't boot into sdb1.  Would this work (and be functioning on sdb1) if I mounted sdb1 and then cd'd into /media/rj/Ubuntu-12.04.5, and then issued the command from there?   And should I be using the "-c" flag (creates a new initramfs)  instead of the "-u" flag (updates an existing initramfs), since I have no init.img for -57 at all?

> This is providing that there is operating headroom in /boot.
Always a good idea to remove no-longer-needed(wanted) old kernels.
Check for space:
```

df -h
df -i

``` . . . 

I do want to get rid of all but the current and maybe previous two kernels. Space shouldn't be a problem:

```
--> df -h 
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       907G   13G  849G   2% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            3.9G  8.0K  3.9G   1% /dev
tmpfs           799M  1.2M  798M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  3.9M  3.9G   1% /run/shm
none            100M   52K  100M   1% /run/user
[COLOR=#0000ff]/dev/sdb1       907G   17G  845G   2% /media/rj/Ubuntu-12.04.5[/COLOR]

--> df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda1      60399616 610218 59789398    2% /
none            1021633      2  1021631    1% /sys/fs/cgroup
udev            1018935    531  1018404    1% /dev
tmpfs           1021633    542  1021091    1% /run
none            1021633      3  1021630    1% /run/lock
none            1021633      7  1021626    1% /run/shm
none            1021633     25  1021608    1% /run/user
[COLOR=#0000ff]/dev/sdb1      60399616 541425 59858191    1% /media/rj/Ubuntu-12.04.5[/COLOR]

```

Here is something I posted about the same issue a few days ago, but it didn't get much attention:
[URL="http://ubuntuforums.org/showthread.php?t=2286417"]http://ubuntuforums.org/showthread.php?t=2286417
[/URL]

---

### Post by Bashing-om on 2015-07-18
watchpocket; Well.

A couple of things we can do. Like perhaps pull a CHange Root routine into the sda install, from either the install on sdb or from a liveDVD and do what we need to do.

But first.
Let's take a gander at what we are working with and toward.

Boot up another install such as sda, and mount the sdb ubuntu precise partition and we take that look;
from 'sda':
terminal commands:
```

sudo mkdir /mnt/looksee
sudo mount /dev/sdb1 /mnt/looksee
ls -al /mnt/looksee/boot

```

Once done "looking" we must UNmount what we manually mounted, otherwise; file system corruption will happen at some level.
```

sudo umount /mnt/looksee

```

see then what options we can scare up.

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by watchpocket on 2015-07-18
> **Bashing-om said:**
> *Boot up another install such as sda, and mount the sdb ubuntu precise partition and we take that look*
***sda*** is on its own one-terabye drive (running Ubunt-MATE).  ***sdb*** is also on its own one-terabyte drive (running Ubuntu-12.04.5).  I have a third one-terabyte drive (***sdc***) for storage, with no OS on it.  All three drives consist of one large partition and a small swap partition.

I can easily boot from a live USB stick if necessary.  *Thanks!*

```
***--> sudo mkdir /mnt/looksee *** 
[sudo] password for rj: 

--> ***sudo mount /dev/sdb1 /mnt/looksee***
--> ***ls -al /mnt/looksee ***
total 132
 4 drwxr-xr-x  26 root root  4096 Jul 18 01:22 ./
 4 drwxr-xr-x   3 root root  4096 Jul 18 23:00 ../
 4 drwxr-xr-x   2 root root  4096 Jul 18  2014 .rpmdb/
 4 drwxr-xr-x   2 root root  4096 May 31 15:57 bin/
 4 drwxr-xr-x   4 root root  4096 Jul  9 02:06 boot/
 4 drwxr-xr-x   2 root root  4096 Jan 11  2014 cdrom/
 4 drwxr-xr-x   4 root root  4096 Aug 20  2013 dev/
12 drwxr-xr-x 152 root root 12288 Jul  9 02:13 etc/
 4 drwxr-xr-x   3 root root  4096 Jan 11  2014 home/
[COLOR=#0000ff] 0 lrwxrwxrwx   1 root root    33 Jul  9 02:13 initrd.img -> boot/initrd.img-3.13.0-57-generic   [/COLOR][COLOR=#ff0000] <-- this is gray to the right of the "->", & I have all files set to appear purple, others are purple. [/COLOR]
 0 lrwxrwxrwx   1 root root    33 Jun 19 03:54 initrd.img.old -> boot/initrd.img-3.13.0-55-generic
 4 drwxr-xr-x  27 root root  4096 May 22 13:29 lib/
 4 drwxr-xr-x   2 root root  4096 Apr 10 02:44 lib32/
 4 drwxr-xr-x   2 root root  4096 Apr 10 02:44 lib64/
16 drwx------   2 root root 16384 Jan 11  2014 lost+found/
 4 drwxr-xr-x   2 root root  4096 May 31 15:54 media/
 4 drwxr-xr-x   2 root root  4096 Apr 19  2012 mnt/
 4 drwxr-xr-x   4 root root  4096 Jul  6  2014 opt/
 4 drwxr-xr-x   2 root root  4096 Apr 19  2012 proc/
 4 drwx------  13 root root  4096 May  9 01:13 root/
 4 drwxr-xr-x   9 root root  4096 Aug 20  2013 run/
12 drwxr-xr-x   2 root root 12288 Jun 19 03:54 sbin/
 4 drwxr-xr-x   2 root root  4096 Mar  5  2012 selinux/
 4 drwxr-xr-x   2 root root  4096 Aug 20  2013 srv/
 4 drwxr-xr-x   2 root root  4096 Apr 14  2012 sys/
 4 drwxrwxrwt   8 root root  4096 Jul  9 02:13 tmp/
 4 drwxr-xr-x  11 root root  4096 Dec 14  2014 usr/
 4 drwxr-xr-x  13 root root  4096 Jul  9 02:13 var/
 0 lrwxrwxrwx   1 root root    30 Jul  9 02:13 vmlinuz -> boot/vmlinuz-3.13.0-57-generic
 0 lrwxrwxrwx   1 root root    30 Jun 19 03:54 vmlinuz.old -> boot/vmlinuz-3.13.0-55-generic

--> ***ls -al /mnt/looksee/boot***  
total 300900
    4 drwxr-xr-x  4 root root     4096 Jul  9 02:06 ./
    4 drwxr-xr-x 26 root root     4096 Jul 18 01:22 ../
 3444 -rw-------  1 root root  3525141 Dec 16  2014 System.map-3.13.0-44-generic
 3444 -rw-------  1 root root  3525572 Jan 15  2015 System.map-3.13.0-45-generic
 3444 -rw-------  1 root root  3525792 Mar 10 16:50 System.map-3.13.0-46-generic
 3444 -rw-------  1 root root  3525711 Mar 12 15:56 System.map-3.13.0-48-generic
 3444 -rw-------  1 root root  3525956 Mar 25 12:58 System.map-3.13.0-49-generic
 3444 -rw-------  1 root root  3526265 Apr 15 18:10 System.map-3.13.0-51-generic
 3444 -rw-------  1 root root  3526298 May  5 14:33 System.map-3.13.0-52-generic
 3444 -rw-------  1 root root  3526638 May 20 13:59 System.map-3.13.0-53-generic
 3448 -rw-------  1 root root  3527402 May 27 07:15 System.map-3.13.0-54-generic
 3448 -rw-------  1 root root  3527402 Jun 18 06:19 System.map-3.13.0-55-generic
 3448 -rw-------  1 root root  3528045 Jun 22 06:08 System.map-3.13.0-57-generic
 1140 -rw-r--r--  1 root root  1164720 Dec 16  2014 abi-3.13.0-44-generic
 1140 -rw-r--r--  1 root root  1164967 Jan 15  2015 abi-3.13.0-45-generic
 1140 -rw-r--r--  1 root root  1164852 Mar 10 16:50 abi-3.13.0-46-generic
 1140 -rw-r--r--  1 root root  1164723 Mar 12 15:56 abi-3.13.0-48-generic
 1140 -rw-r--r--  1 root root  1164723 Mar 25 12:58 abi-3.13.0-49-generic
 1140 -rw-r--r--  1 root root  1164671 Apr 15 18:10 abi-3.13.0-51-generic
 1140 -rw-r--r--  1 root root  1164671 May  5 14:33 abi-3.13.0-52-generic
 1140 -rw-r--r--  1 root root  1164671 May 20 13:59 abi-3.13.0-53-generic
 1140 -rw-r--r--  1 root root  1164806 May 27 07:15 abi-3.13.0-54-generic
 1140 -rw-r--r--  1 root root  1164806 Jun 18 06:19 abi-3.13.0-55-generic
 1140 -rw-r--r--  1 root root  1164984 Jun 22 06:08 abi-3.13.0-57-generic
  164 -rw-r--r--  1 root root   165757 Dec 16  2014 config-3.13.0-44-generic
  164 -rw-r--r--  1 root root   165757 Jan 15  2015 config-3.13.0-45-generic
  164 -rw-r--r--  1 root root   165757 Mar 10 16:50 config-3.13.0-46-generic
  164 -rw-r--r--  1 root root   165782 Mar 12 15:56 config-3.13.0-48-generic
  164 -rw-r--r--  1 root root   165782 Mar 25 12:58 config-3.13.0-49-generic
  164 -rw-r--r--  1 root root   165771 Apr 15 18:10 config-3.13.0-51-generic
  164 -rw-r--r--  1 root root   165771 May  5 14:33 config-3.13.0-52-generic
  164 -rw-r--r--  1 root root   165771 May 20 13:59 config-3.13.0-53-generic
  164 -rw-r--r--  1 root root   165771 May 27 07:15 config-3.13.0-54-generic
  164 -rw-r--r--  1 root root   165771 Jun 18 06:19 config-3.13.0-55-generic
  164 -rw-r--r--  1 root root   165771 Jun 22 06:08 config-3.13.0-57-generic
    4 drwxr-xr-x  3 root root     4096 Jun 20 13:20 extlinux/
   12 drwxr-xr-x  3 root root    12288 Jun 20 13:20 grub/
18484 -rw-r--r--  1 root root 18920653 Jan 16  2015 initrd.img-3.13.0-44-generic
18484 -rw-r--r--  1 root root 18927341 Feb 16 18:34 initrd.img-3.13.0-45-generic
18484 -rw-r--r--  1 root root 18926775 Mar 13 03:51 initrd.img-3.13.0-46-generic
18484 -rw-r--r--  1 root root 18926245 Mar 23 18:38 initrd.img-3.13.0-48-generic
18484 -rw-r--r--  1 root root 18923909 Apr 10 02:46 initrd.img-3.13.0-49-generic
18484 -rw-r--r--  1 root root 18924568 May  2 20:17 initrd.img-3.13.0-51-generic
18484 -rw-r--r--  1 root root 18925240 May  8 02:17 initrd.img-3.13.0-52-generic
18488 -rw-r--r--  1 root root 18929418 May 22 13:31 initrd.img-3.13.0-53-generic
18488 -rw-r--r--  1 root root 18929000 Jun 12 15:58 initrd.img-3.13.0-54-generic
[COLOR=#0000ff]18488 -rw-r--r--  1 root root 18929785 Jun 20 13:20 initrd.img-3.13.0-55-generic[/COLOR]
  176 -rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
  176 -rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
 5764 -rw-------  1 root root  5896992 Dec 16  2014 vmlinuz-3.13.0-44-generic
 5764 -rw-------  1 root root  5898624 Jan 15  2015 vmlinuz-3.13.0-45-generic
 5764 -rw-------  1 root root  5899520 Mar 10 16:50 vmlinuz-3.13.0-46-generic
 5764 -rw-------  1 root root  5900896 Mar 12 15:56 vmlinuz-3.13.0-48-generic
 5768 -rw-------  1 root root  5902944 Mar 25 12:58 vmlinuz-3.13.0-49-generic
 5768 -rw-------  1 root root  5904096 Apr 15 18:10 vmlinuz-3.13.0-51-generic
 5768 -rw-------  1 root root  5904192 May  5 14:33 vmlinuz-3.13.0-52-generic
 5768 -rw-------  1 root root  5903360 May 20 13:59 vmlinuz-3.13.0-53-generic
 5768 -rw-------  1 root root  5903392 May 27 07:15 vmlinuz-3.13.0-54-generic
 5768 -rw-------  1 root root  5903328 Jun 18 06:19 vmlinuz-3.13.0-55-generic
 5768 -rw-------  1 root root  5903904 Jun 22 06:08 vmlinuz-3.13.0-57-generic

--> [I][B]sudo umount /mnt/looksee
[/B][/I]-->

```

---

### Post by Bashing-om on 2015-07-19
watchpocket; Hey :

I see no fault with the image mapping ; -57 is the current boot, with -55 (.old) as the backup. I would not expect a problem.

As a reference; My output for the hard drive I am presently booting:
```

sysop@1404mini:~$ ls -al /
total 108
drwxr-xr-x  25 root root  4096 Jul 16 16:35 .
drwxr-xr-x  25 root root  4096 Jul 16 16:35 ..
drwxr-xr-x   2 root root  4096 Jun 16 17:30 bin
drwxr-xr-x   4 root root  4096 Jul  6 13:58 boot
drwxr-xr-x  14 root root  4360 Jul 19 11:34 dev
drwxr-xr-x  98 root root 12288 Jul 19 11:34 etc
-rw-r--r--   1 root root     0 Jul 18  2013 forcefsdk
drwxr-xr-x   5 root root  4096 Jun  9  2014 grub
drwxr-xr-x   4 root root  4096 May 19  2013 home
lrwxrwxrwx   1 root root    33 Jul  6 13:58 initrd.img -> boot/initrd.img-3.13.0-57-generic
lrwxrwxrwx   1 root root    33 Jun 16 17:30 initrd.img.old -> boot/initrd.img-3.13.0-55-generic
drwxr-xr-x  22 root root  4096 Jul  6  2014 lib
drwxr-xr-x   2 root root  4096 Feb 27 10:31 lib64
drwx------   2 root root 16384 May 19  2013 lost+found
drwxr-xr-x   3 root root  4096 May 19  2013 media
drwxr-xr-x  11 root root  4096 Feb 19 12:51 mnt
drwxr-xr-x   3 root root  4096 May 19  2013 opt
dr-xr-xr-x 150 root root     0 Jul 19 11:34 proc
drwx------   7 root root  4096 May 20  2013 root
drwxr-xr-x  17 root root   540 Jul 19 11:39 run
drwxr-xr-x   2 root root 12288 Jun 25 06:40 sbin
drwxr-xr-x   2 root root  4096 May 19  2013 srv
dr-xr-xr-x  13 root root     0 Jul 19 11:34 sys
drwxr-xr-x   2 root root  4096 Mar 31  2014 test
drwxrwxrwt   6 root root   180 Jul 19 11:41 tmp
drwxr-xr-x  10 root root  4096 May 19  2013 usr
drwxr-xr-x  13 root root  4096 Mar 13  2014 var
lrwxrwxrwx   1 root root    30 Jul  6 13:58 vmlinuz -> boot/vmlinuz-3.13.0-57-generic
lrwxrwxrwx   1 root root    30 Jun 16 17:30 vmlinuz.old -> boot/vmlinuz-3.13.0-55-generic
drwxr-xr-x   2 r

```
Are your 3 hard drives in a raid configuration ?
> 
sda is on its own one-terabye drive (running Ubunt-MATE). sdb is also on its own one-terabyte drive (running Ubuntu-12.04.5). I have a third one-terabyte drive (sdc) for storage, with no OS on it. All three drives consist of one large partition and a small swap partition.


Most raid configurations require the boot code to be outside of the raid array.

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by oldfred on 2015-07-19
Are you using the short grub config files like in Cavsfan's instructions?
 [https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)

You do not want to mix versions. 

You can convert this type:

```
 menuentry "Ubutu on sdb1" {
    set root=(hd1,1)
        linux /vmlinuz root=/dev/sdb1 ro quiet splash
        initrd /initrd.img
}


```

to this:
```
 menuentry "Ubuntu on sdb1 - old" {
    set root=(hd1,1)
        linux /vmlinuz.old root=/dev/sdb1 ro quiet splash
        initrd /initrd.img.old
}


```

That should work as long as new link does get copied to .old when even newer one is added and you still have those versions of kernel & initrd in /boot.
Otherwise you have to go to specific boot/initrd.img-3.13.0-57-generic type entry.

You can manually edit grub boot stanza with the changes to boot and then update from inside your install. But if kernels are not correct or other issues then you will have to chroot from either you Mate install or live installer.

Above entry assumes booting from sda, if using grub on sdb, the drive will be hd0 as boot drive is always hd0 but device for root will still be sdb1.

---

### Post by watchpocket on 2015-07-19
> **Bashing-om said:**
> I see no fault with the image mapping ; -57 is the current boot, with -55 (.old) as the backup. I would not expect a problem.

Well, if you look in my sdb drive's /boot dir, you'll see that every file there has a -57 except  initrd.img, the latest one of which is [B]initrd.img-3.13.0-[COLOR=#0000ff]55[/COLOR]-generic
[/B](and right now, /media/rj/Ubuntu-12.04.5**/initrd.img** links to a [COLOR=#0000ff]non-existent[/COLOR]  /media/rj/Ubuntu-12.04.5**/boot/initrd.img-3.13.0-57-generic**):

```
--> **ls -la /media/rj/Ubuntu-12.04.5/boot** 
total 300900
    4 drwxr-xr-x  4 root root     4096 Jul  9 02:06 ./
    4 drwxr-xr-x 26 root root     4096 Jul 18 01:22 ../
 3444 -rw-------  1 root root  3525141 Dec 16  2014 System.map-3.13.0-44-generic
 3444 -rw-------  1 root root  3525572 Jan 15  2015 System.map-3.13.0-45-generic
 3444 -rw-------  1 root root  3525792 Mar 10 16:50 System.map-3.13.0-46-generic
 3444 -rw-------  1 root root  3525711 Mar 12 15:56 System.map-3.13.0-48-generic
 3444 -rw-------  1 root root  3525956 Mar 25 12:58 System.map-3.13.0-49-generic
 3444 -rw-------  1 root root  3526265 Apr 15 18:10 System.map-3.13.0-51-generic
 3444 -rw-------  1 root root  3526298 May  5 14:33 System.map-3.13.0-52-generic
 3444 -rw-------  1 root root  3526638 May 20 13:59 System.map-3.13.0-53-generic
 3448 -rw-------  1 root root  3527402 May 27 07:15 System.map-3.13.0-54-generic
 3448 -rw-------  1 root root  3527402 Jun 18 06:19 System.map-3.13.0-55-generic
 3448 -rw-------  1 root root  3528045 Jun 22 06:08 System.map-3.13.0-57-generic
 1140 -rw-r--r--  1 root root  1164720 Dec 16  2014 abi-3.13.0-44-generic
 1140 -rw-r--r--  1 root root  1164967 Jan 15  2015 abi-3.13.0-45-generic
 1140 -rw-r--r--  1 root root  1164852 Mar 10 16:50 abi-3.13.0-46-generic
 1140 -rw-r--r--  1 root root  1164723 Mar 12 15:56 abi-3.13.0-48-generic
 1140 -rw-r--r--  1 root root  1164723 Mar 25 12:58 abi-3.13.0-49-generic
 1140 -rw-r--r--  1 root root  1164671 Apr 15 18:10 abi-3.13.0-51-generic
 1140 -rw-r--r--  1 root root  1164671 May  5 14:33 abi-3.13.0-52-generic
 1140 -rw-r--r--  1 root root  1164671 May 20 13:59 abi-3.13.0-53-generic
 1140 -rw-r--r--  1 root root  1164806 May 27 07:15 abi-3.13.0-54-generic
 1140 -rw-r--r--  1 root root  1164806 Jun 18 06:19 abi-3.13.0-55-generic
 1140 -rw-r--r--  1 root root  1164984 Jun 22 06:08 abi-3.13.0-57-generic
  164 -rw-r--r--  1 root root   165757 Dec 16  2014 config-3.13.0-44-generic
  164 -rw-r--r--  1 root root   165757 Jan 15  2015 config-3.13.0-45-generic
  164 -rw-r--r--  1 root root   165757 Mar 10 16:50 config-3.13.0-46-generic
  164 -rw-r--r--  1 root root   165782 Mar 12 15:56 config-3.13.0-48-generic
  164 -rw-r--r--  1 root root   165782 Mar 25 12:58 config-3.13.0-49-generic
  164 -rw-r--r--  1 root root   165771 Apr 15 18:10 config-3.13.0-51-generic
  164 -rw-r--r--  1 root root   165771 May  5 14:33 config-3.13.0-52-generic
  164 -rw-r--r--  1 root root   165771 May 20 13:59 config-3.13.0-53-generic
  164 -rw-r--r--  1 root root   165771 May 27 07:15 config-3.13.0-54-generic
  164 -rw-r--r--  1 root root   165771 Jun 18 06:19 config-3.13.0-55-generic
  164 -rw-r--r--  1 root root   165771 Jun 22 06:08 config-3.13.0-57-generic
    4 drwxr-xr-x  3 root root     4096 Jun 20 13:20 extlinux/
   12 drwxr-xr-x  3 root root    12288 Jun 20 13:20 grub/
18484 -rw-r--r--  1 root root 18920653 Jan 16  2015 initrd.img-3.13.0-44-generic
18484 -rw-r--r--  1 root root 18927341 Feb 16 18:34 initrd.img-3.13.0-45-generic
18484 -rw-r--r--  1 root root 18926775 Mar 13 03:51 initrd.img-3.13.0-46-generic
18484 -rw-r--r--  1 root root 18926245 Mar 23 18:38 initrd.img-3.13.0-48-generic
18484 -rw-r--r--  1 root root 18923909 Apr 10 02:46 initrd.img-3.13.0-49-generic
18484 -rw-r--r--  1 root root 18924568 May  2 20:17 initrd.img-3.13.0-51-generic
18484 -rw-r--r--  1 root root 18925240 May  8 02:17 initrd.img-3.13.0-52-generic
18488 -rw-r--r--  1 root root 18929418 May 22 13:31 initrd.img-3.13.0-53-generic
18488 -rw-r--r--  1 root root 18929000 Jun 12 15:58 initrd.img-3.13.0-54-generic
[COLOR=#0000ff]18488 -rw-r--r--  1 root root 18929785 Jun 20 13:20 initrd.img-3.13.0-55-generic[/COLOR]
  176 -rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
  176 -rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
 5764 -rw-------  1 root root  5896992 Dec 16  2014 vmlinuz-3.13.0-44-generic
 5764 -rw-------  1 root root  5898624 Jan 15  2015 vmlinuz-3.13.0-45-generic
 5764 -rw-------  1 root root  5899520 Mar 10 16:50 vmlinuz-3.13.0-46-generic
 5764 -rw-------  1 root root  5900896 Mar 12 15:56 vmlinuz-3.13.0-48-generic
 5768 -rw-------  1 root root  5902944 Mar 25 12:58 vmlinuz-3.13.0-49-generic
 5768 -rw-------  1 root root  5904096 Apr 15 18:10 vmlinuz-3.13.0-51-generic
 5768 -rw-------  1 root root  5904192 May  5 14:33 vmlinuz-3.13.0-52-generic
 5768 -rw-------  1 root root  5903360 May 20 13:59 vmlinuz-3.13.0-53-generic
 5768 -rw-------  1 root root  5903392 May 27 07:15 vmlinuz-3.13.0-54-generic
 5768 -rw-------  1 root root  5903328 Jun 18 06:19 vmlinuz-3.13.0-55-generic
 5768 -rw-------  1 root root  5903904 Jun 22 06:08 vmlinuz-3.13.0-57-generic
-->
```

(Once I can boot into my sdb drive, I know how to (and will) get rid of all the old kernels.)
> Are your 3 hard drives in a raid configuration ?
No they aren't, but I'd like to look into the potential advantages of that.

---

### Post by watchpocket on 2015-07-19
> **oldfred said:**
> Are you using the short grub config files like in Cavsfan's instructions?
 [URL="https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen"]https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen
[/URL]

Yeah I'm pretty sure I do.  I went through a whole long thing with him 6 months or so ago to get my grub set up.

> You can convert this type:

```
 menuentry "Ubutu on sdb1" {
    set root=(hd1,1)
        linux /vmlinuz root=/dev/sdb1 ro quiet splash
        initrd /initrd.img
}


```

to this:
```
 menuentry "Ubuntu on sdb1 - old" {
    set root=(hd1,1)
        linux /vmlinuz.old root=/dev/sdb1 ro quiet splash
        initrd /initrd.img.old
}


```

Which file exactly in (I'm assuming) the /boot/grub dir are we looking at here?

For right now, I'll have to re-read a couple of times and think about the rest of what you wrote here to fully grok it:

> That should work as long as new link does get copied to .old when even newer one is added and you still have those versions of kernel & initrd in /boot.
Otherwise you have to go to specific boot/initrd.img-3.13.0-57-generic type entry.

You can manually edit grub boot stanza with the changes to boot and then update from inside your install. But if kernels are not correct or other issues then you will have to chroot from either you Mate install or live installer.

Above entry assumes booting from sda, if using grub on sdb, the drive will be hd0 as boot drive is always hd0 but device for root will still be sdb1.

---

### Post by Bashing-om on 2015-07-19
watchpocket; HoKay;

Try this:
```

sudo update-initramfs -u -k 3.13.0-57-generic

```
to rebuild the initrd.img. 

Then, to remove the old kernels one - in 12.04 - has to use either synaptic or the command line tools of apt/dpkg .

[INDENT][INDENT]me, I follow the KISS principal
[INDENT][INDENT][INDENT]1 thing at a time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2015-07-19
Are you booting from a grub in sda or sdb?

And if you get to grub menu, press e.
 if you press the "e" key when at the grub menu while the option you want to boot is seleced, you will be able to modify the boot .

---

### Post by watchpocket on 2015-07-19
> **Bashing-om said:**
> watchpocket; HoKay;

Try this:
```

sudo update-initramfs -u -k 3.13.0-57-generic

```
to rebuild the initrd.img. 

My only question about doing this is that I'm at a shell prompt in my sda drive (Ubuntu-MATE), and if I (a) mount the sdb drive and then (b) 
chdir into /media/rj/Ubuntu-12.04.5 (my sdb drive), last night, for example, after getting rid of all the old kernels in sda using
```
sudo apt-get purge linux-image-3.13.0-xx
```

I cd'd into /media/rj/Ubuntu-12.04.5 and from there did a
```
sudo apt-get purge linux-image-3.13.0-44
```

Now, sda has no -44 but sdb does.  But I only got a message that there was no -44.  So, I'm not doing it right.  That's why I don't want to just do the update command above from my sda shell prompt.  So I need to make sure when I issue that command, I know it's executing in sdb.  Thanks for bearing with.

---

### Post by watchpocket on 2015-07-19
> **oldfred said:**
> Are you booting from a grub in sda or sdb?

I boot up, see the BIOS screen ("system76"), then I see my grub menu. If I don't touch it, I'm automatically booted into sda. Then I see the plymouth "Ubuntu MATE" screen with the 5 sequentially-lit dots under it, then I see the greeter.

Right now if, when in the grub menu, I arrow-key down to "Ubuntu-12.04.5" to try to boot into sdb, I get a warning: "initrd.img not found".


>  And if you get to grub menu, press e.
 if you press the "e" key when at the grub menu while the option you want to boot is seleced, you will be able to modify the boot .

Okay . . . exactly what to do to modify, I'm not yet sure of.  Maybe that's where I need to go back to what you wrote in your previous post. 

*[Edit: Actually, yeah, let me see if I can try that - just add the ".old"  twice in the right places.]*

 My own fuzzy-ball thought-process assumes that I somehow need to generate a new initrd.img, making sure I'm doing it in sdb.  I don't know just where to do that from, and maybe it's from the edit menu of grub.

---

### Post by watchpocket on 2015-07-19
I'm guessing that if, editing grub, I add ".old" where you indicated (for purposes of at least being able to boot into -55 on sdb) (and sudo update-grub, of course after editing and saving), then after I install, from synaptic, linux-image -57 or perhaps preferably -58, I would then want to go back and edit grub again to* remove* the 2 instances of ".old" where I've inserted them.  

Would that be correct?

---

### Post by Bashing-om on 2015-07-19
watchpocket; Hey !

You are oh ! so correct. When the 'initramfs' command is run, one has to be in that installed operating system,
a) booted into the install on an alternate kernel
b) booted from another system, and in a complete full CHange Root to implement that command.

When you are back to this stage we will continue.

[INDENT][INDENT]one thing at a time is all my little mind
[INDENT][INDENT][INDENT]is going to cope with
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oldfred on 2015-07-19
If you manually edit grub when booting then that is a one time change. Easier for testing. And no sudo update-grub required. 
If you edit 40_custom or any of the scripts then that is a permanent change. And then sudo update-grub is required, but you have to be inside your install either by booting, or chrooting into your install.

An update to new kernel should then write new links. And grub should boot those.
The non-working one may then be the .old until you get a second new one.

---

### Post by watchpocket on 2015-07-19
Okay, so right now I'll go into grub, arrow down to my precise drive, hit return, then enter 'e' to edit.  I'll manually put in the 2 links to intra.img.**old** and vmlinuz.**old**, exit the grub editor and see if I can boot in to sdb once I do that.  

Problem: right now I'm not sure, once booted, which file is the appropriate file to edit.  My sdb /etc/grub.d/40_custom consists only of:

```
  1 #!/bin/sh
  2 exec tail -n +3 $0
  3 # This file provides an easy way to add custom menu entries.  Simply type the
  4 # menu entries you want to add after this comment.  Be careful not to change
  5 # the 'exec tail' line above.
```

Would I put here the stanza entry the example in your earlier post? :

```

 menuentry "Ubuntu on sdb1 - old" {
    set root=(hd1,1)
        linux /vmlinuz.old root=/dev/sdb1 ro quiet splash
        initrd /initrd.img.old
}
```

---

### Post by watchpocket on 2015-07-19
OK,** [COLOR=#0000ff]partial victory[/COLOR]**. 

 I made the changes in the grub menu and was able to boot into sdb.  That's great.  While I was in there, I edited my **/etc/grub.d/40_custom **file thusly, copying the changes I'd made in the grub menu:

```
 1 #!/bin/sh
  2 exec tail -n +3 $0
  3 # This file provides an easy way to add custom menu entries.  Simply type the
  4 # menu entries you want to add after this comment.  Be careful not to change
  5 # the 'exec tail' line above.
  6 menuentry "Ubuntu-12.04.5 - old" {
  7     set root=(hd1,1)
  8         linux /vmlinuz.old root=/dev/sdb1 ro quiet splash
  9         initrd /initrd.img.old
 10 } 
```

I then did a *sudo update-grub *and re-booted.

What happened then was that (after selecting 12.04 from grub), I was put into the low-rez large-print busybox login prompt.  I logged in and was still in low-rez busybox mode at my shell prompt, only the shell was the old zsh-5.0.5, not my current 5.0,7.

So, the changes I made to /etc/grub.d/40_custom were not what I actually need to do.

 I need to double back & figure out exactly how to make the login permanent.[I]  Thanks for all the great help.
[/I]

---

### Post by oldfred on 2015-07-19
With two drives and two installs, I prefer to have each install have its grub in the MBR of its drive.
You can quickly change that.
Boot into install in sda:
       sudo grub-install /dev/sda

Then boot into install in sdb:

 sudo grub-install /dev/sdb
sudo update-grub

Then in BIOS you can choose which drive to boot from and each install should let you boot other install.
But you may need other updates to make install to sdb permanent, grub remembers where it originally installed and want to reinstall there are major updates.
      
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 


 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

Also if you install grub to sdb, and directly boot sdb, your 40_custom needs the hd1 all changed to hd0. Boot drive in grub is always hd0. 
If you added the 40_custom to sda and that was your install on sda, then hd1 would remain correct. You have two 40_customs and entries may not be exactly the same in each.

---

### Post by watchpocket on 2015-07-20
> *With two drives and two installs, I prefer to have each install have its grub in the MBR of its drive.*

For me that would be a project for later.  I'm not so inclined to do any of that right now unless it's necessary. 

 I'd like to try to keep things simple and -- if possible -- get back to being able to boot into sdb the way I could before. 

The first time I edited in grub per your info, I was indeed able to temporarily log into sdb normally.  After that I couldn't log in temporarily or permanently (with the same editing of grub -- adding '.old' to change the links). 

Now I get put into a busybox login prompt. At least I can login that way (into the low-rez big-print busybox) and perhaps take appropriate action from there, since from there I'm inside the sdb installation.

Right now, in my sdb root dir, I have the unfortunate circumstance that[COLOR=#0000ff] both **initrd.img ***and ***initrd.img.old **are linked to** boot/initrd.img-3.13.0-57-generic.  **[/COLOR]I'm not sure what caused that, and I'm not sure what to do about it.  I'm a bit lost:```
*--> ***ls -la /media/rj/Ubuntu-12.04.5**  
total 132
 4 drwxr-xr-x   26 root root  4096 Jul 19 18:14 ./
 4 drwxr-x---+   3 root root  4096 Jul 20 00:38 ../
 4 drwxr-xr-x    2 root root  4096 Jul 18  2014 .rpmdb/
 4 drwxr-xr-x    2 root root  4096 May 31 15:57 bin/
 4 drwxr-xr-x    4 root root  4096 Jul 20 00:33 boot/
 4 drwxr-xr-x    2 root root  4096 Jan 11  2014 cdrom/
 4 drwxr-xr-x    4 root root  4096 Aug 20  2013 dev/
12 drwxr-xr-x  152 root root 12288 Jul 20 00:26 etc/
 4 drwxr-xr-x    3 root root  4096 Jan 11  2014 home/
 0 lrwxrwxrwx    1 root root    33 Jul 19 18:14[COLOR=#ff0000] initrd.img -> boot/initrd.img-3.13.0-57-generic[/COLOR]
 0 lrwxrwxrwx    1 root root    33 Jul  9 02:13 [COLOR=#ff0000]initrd.img.old -> boot/initrd.img-3.13.0-57-generic[/COLOR]
 4 drwxr-xr-x   27 root root  4096 May 22 13:29 lib/
 4 drwxr-xr-x    2 root root  4096 Apr 10 02:44 lib32/
 4 drwxr-xr-x    2 root root  4096 Apr 10 02:44 lib64/
16 drwx------    2 root root 16384 Jan 11  2014 lost+found/
 4 drwxr-xr-x    2 root root  4096 May 31 15:54 media/
 4 drwxr-xr-x    2 root root  4096 Apr 19  2012 mnt/
 4 drwxr-xr-x    4 root root  4096 Jul  6  2014 opt/
 4 drwxr-xr-x    2 root root  4096 Apr 19  2012 proc/
 4 drwx------   13 root root  4096 May  9 01:13 root/
 4 drwxr-xr-x    9 root root  4096 Aug 20  2013 run/
12 drwxr-xr-x    2 root root 12288 Jun 19 03:54 sbin/
 4 drwxr-xr-x    2 root root  4096 Mar  5  2012 selinux/
 4 drwxr-xr-x    2 root root  4096 Aug 20  2013 srv/
 4 drwxr-xr-x    2 root root  4096 Apr 14  2012 sys/
 4 drwxrwxrwt    6 root root  4096 Jul 20 00:33 tmp/
 4 drwxr-xr-x   11 root root  4096 Dec 14  2014 usr/
 4 drwxr-xr-x   13 root root  4096 Jul 19 18:21 var/
 0 lrwxrwxrwx    1 root root    30 Jul  9 02:13 vmlinuz -> boot/vmlinuz-3.13.0-57-generic
 0 lrwxrwxrwx    1 root root    30 Jun 19 03:54 vmlinuz.old -> boot/vmlinuz-3.13.0-55-generic
```

My /boot dir look OK as far as I can tell (exept for the fact that I have a ton of old kernel files in it).
Wait -- I now see I have in /boot an **initrd.img-3.13.0.[COLOR=#0000ff]58[/COLOR]-generic** item, but** no other [COLOR=#0000ff]-58[/COLOR] **files.
:
```
--> **ls -la /media/rj/Ubuntu-12.04.5/boot**  
total 323540
    4 drwxr-xr-x  4 root root     4096 Jul 20 00:33 ./
    4 drwxr-xr-x 26 root root     4096 Jul 19 18:14 ../
 3444 -rw-------  1 root root  3525141 Dec 16  2014 System.map-3.13.0-44-generic
 3444 -rw-------  1 root root  3525572 Jan 15  2015 System.map-3.13.0-45-generic
 3444 -rw-------  1 root root  3525792 Mar 10 16:50 System.map-3.13.0-46-generic
 3444 -rw-------  1 root root  3525711 Mar 12 15:56 System.map-3.13.0-48-generic
 3444 -rw-------  1 root root  3525956 Mar 25 12:58 System.map-3.13.0-49-generic
 3444 -rw-------  1 root root  3526265 Apr 15 18:10 System.map-3.13.0-51-generic
 3444 -rw-------  1 root root  3526298 May  5 14:33 System.map-3.13.0-52-generic
 3444 -rw-------  1 root root  3526638 May 20 13:59 System.map-3.13.0-53-generic
 3448 -rw-------  1 root root  3527402 May 27 07:15 System.map-3.13.0-54-generic
 3448 -rw-------  1 root root  3527402 Jun 18 06:19 System.map-3.13.0-55-generic
 3448 -rw-------  1 root root  3528045 Jun 22 06:08 System.map-3.13.0-57-generic
 1140 -rw-r--r--  1 root root  1164720 Dec 16  2014 abi-3.13.0-44-generic
 1140 -rw-r--r--  1 root root  1164967 Jan 15  2015 abi-3.13.0-45-generic
 1140 -rw-r--r--  1 root root  1164852 Mar 10 16:50 abi-3.13.0-46-generic
 1140 -rw-r--r--  1 root root  1164723 Mar 12 15:56 abi-3.13.0-48-generic
 1140 -rw-r--r--  1 root root  1164723 Mar 25 12:58 abi-3.13.0-49-generic
 1140 -rw-r--r--  1 root root  1164671 Apr 15 18:10 abi-3.13.0-51-generic
 1140 -rw-r--r--  1 root root  1164671 May  5 14:33 abi-3.13.0-52-generic
 1140 -rw-r--r--  1 root root  1164671 May 20 13:59 abi-3.13.0-53-generic
 1140 -rw-r--r--  1 root root  1164806 May 27 07:15 abi-3.13.0-54-generic
 1140 -rw-r--r--  1 root root  1164806 Jun 18 06:19 abi-3.13.0-55-generic
 1140 -rw-r--r--  1 root root  1164984 Jun 22 06:08 abi-3.13.0-57-generic
  164 -rw-r--r--  1 root root   165757 Dec 16  2014 config-3.13.0-44-generic
  164 -rw-r--r--  1 root root   165757 Jan 15  2015 config-3.13.0-45-generic
  164 -rw-r--r--  1 root root   165757 Mar 10 16:50 config-3.13.0-46-generic
  164 -rw-r--r--  1 root root   165782 Mar 12 15:56 config-3.13.0-48-generic
  164 -rw-r--r--  1 root root   165782 Mar 25 12:58 config-3.13.0-49-generic
  164 -rw-r--r--  1 root root   165771 Apr 15 18:10 config-3.13.0-51-generic
  164 -rw-r--r--  1 root root   165771 May  5 14:33 config-3.13.0-52-generic
  164 -rw-r--r--  1 root root   165771 May 20 13:59 config-3.13.0-53-generic
  164 -rw-r--r--  1 root root   165771 May 27 07:15 config-3.13.0-54-generic
  164 -rw-r--r--  1 root root   165771 Jun 18 06:19 config-3.13.0-55-generic
  164 -rw-r--r--  1 root root   165771 Jun 22 06:08 config-3.13.0-57-generic
    4 drwxr-xr-x  3 root root     4096 Jul 19 18:14 extlinux/
   12 drwxr-xr-x  3 root root    12288 Jul 19 18:20 grub/
18484 -rw-r--r--  1 root root 18920653 Jan 16  2015 initrd.img-3.13.0-44-generic
18484 -rw-r--r--  1 root root 18927341 Feb 16 18:34 initrd.img-3.13.0-45-generic
18484 -rw-r--r--  1 root root 18926775 Mar 13 03:51 initrd.img-3.13.0-46-generic
18484 -rw-r--r--  1 root root 18926245 Mar 23 18:38 initrd.img-3.13.0-48-generic
18484 -rw-r--r--  1 root root 18923909 Apr 10 02:46 initrd.img-3.13.0-49-generic
18484 -rw-r--r--  1 root root 18924568 May  2 20:17 initrd.img-3.13.0-51-generic
18484 -rw-r--r--  1 root root 18925240 May  8 02:17 initrd.img-3.13.0-52-generic
18488 -rw-r--r--  1 root root 18929418 May 22 13:31 initrd.img-3.13.0-53-generic
18488 -rw-r--r--  1 root root 18929000 Jun 12 15:58 initrd.img-3.13.0-54-generic
18488 -rw-r--r--  1 root root 18929785 Jun 20 13:20 initrd.img-3.13.0-55-generic
18488 -rw-r--r--  1 root root 18930955 Jul 19 18:14 initrd.img-3.13.0-57-generic
 2076 -rw-r--r--  1 root root  2121848 Jul 20 00:32 initrd.img-3.13.0.57-generic
 2076 -rw-r--r--  1 root root  2121840 Jul 20 00:33 [COLOR=#ff0000]initrd.img-3.13.0.58-generic[/COLOR]
  176 -rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
  176 -rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
 5764 -rw-------  1 root root  5896992 Dec 16  2014 vmlinuz-3.13.0-44-generic
 5764 -rw-------  1 root root  5898624 Jan 15  2015 vmlinuz-3.13.0-45-generic
 5764 -rw-------  1 root root  5899520 Mar 10 16:50 vmlinuz-3.13.0-46-generic
 5764 -rw-------  1 root root  5900896 Mar 12 15:56 vmlinuz-3.13.0-48-generic
 5768 -rw-------  1 root root  5902944 Mar 25 12:58 vmlinuz-3.13.0-49-generic
 5768 -rw-------  1 root root  5904096 Apr 15 18:10 vmlinuz-3.13.0-51-generic
 5768 -rw-------  1 root root  5904192 May  5 14:33 vmlinuz-3.13.0-52-generic
 5768 -rw-------  1 root root  5903360 May 20 13:59 vmlinuz-3.13.0-53-generic
 5768 -rw-------  1 root root  5903392 May 27 07:15 vmlinuz-3.13.0-54-generic
 5768 -rw-------  1 root root  5903328 Jun 18 06:19 vmlinuz-3.13.0-55-generic
 5768 -rw-------  1 root root  5903904 Jun 22 06:08 vmlinuz-3.13.0-57-generic
```

 I have a feeling I need to take care of the root dir linking problem before I try anything else.  I'm on uncertain ground at this point. 

> *You have two 40_customs and entries may not be exactly the same in each.*

In sda, I have a 40_custom file (and an identical backup 40_custom file); in sdb I have one 40_custom file that is essentially empty.  

Thanks in advance to anyone who can point me out of this somewhat messy situation.

---

### Post by oldfred on 2015-07-20
Your .old are now different. init is 57 & vmlin is 55. That will not work. So .old will not work.
And if 57 is bootable you can just remove the .old.
But now to boot .55 you will have to use the full path and name. Change link to full path & name.
        linux [COLOR=#ff0000]/boot/vmlinuz-3.13.0-55-generic[/COLOR] root=/dev/sdb1 ro quiet splash
        initrd [COLOR=#ff0000]/boot/initrd.img-3.13.0-55-generic[/COLOR]


Every update you do that updates kernel moves the current links to .old and creates new currents. But both vmlinux and initrd must be same version.

You really should houseclean old kernels. I normally keep 2. The old just as you have found may be required. I typically let it grow to 3 or 4 then pare back to 2.

I prefer to use synaptic so I can see what I am purging, but you can use command line.
 Determine your current kernel:
uname -a
-s is similate so you can review first:
sudo apt-get -s autoremove
sudo apt-get install synaptic
In synaptic search for linux-image to choose to delete old ones
Using synaptic
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by watchpocket on 2015-07-20
>* Your .old are now different. init is 57 & vmlin is 55. That will not work. So .old will not work.*

Right. Understood.

> [I]And if 57 is bootable you can just remove the .old.
[/I]
I don't consider 57 bootable because right now all it does is put me into busybox.

> [I]But now to boot .55 you will have to use the full path and name. Change link to full path & name.
        > linux [COLOR=#ff0000]/boot/vmlinuz-3.13.0-55-generic[/COLOR] root=/dev/sdb1 ro quiet splash
        > initrd [COLOR=#ff0000]/boot/initrd.img-3.13.0-55-generic[/COLOR][/I]

**This worked.**  (i.e., I managed to do it correctly.) I logged into -55 on a temporary basis only, and didn't try to edit anything to make it permanent (I don't want to boot to -55 on a permanent basis.)

So, having logged into sdb, I deleted the old kernel-files individually at the command-line, using ```
sudo apt-get purge linux-image-1.13.0-xx
``` 

I also deleted the kernel-headers at the command-line.

> *Every update you do that updates kernel moves the current links to .old and creates new currents. *

Understood.

*> But both vmlinux and initrd must be same version.*

Now *that*, I need to figure out how to make that happen.


> *You really should houseclean old kernels. [...]*

I've now deleted all but -54, -55 and -57.


> [I]-s is similate so you can review first:
> sudo apt-get -s autoremove[/I]

Didn't know about the "-s" flag, thanks.

*> sudo apt-get install synaptic*

I do already have synaptic installed on both my sda (trusty-mate) and sdb (precise) drives.

[B]
So at this point,[/B] [COLOR=#0000ff]**my goal now is to**[/COLOR]:

(**[COLOR=#ff0000]a[/COLOR]**) Log into kernel **-55** on my sdb drive again (on a temporary basis) by editing grub per full-path as you've indicated above (this I know how to do); and once I'm logged in, to:

(**[COLOR=#ff0000]b[/COLOR]**) Get rid of that** initrd.img-1.13.0-58** that's in my boot dir, because it's the only **-58** item there (this I'm *not* sure how to do -- should I simply issue
'*sudo rm /boot/initrd.img-1.13.0-58*' ??;  (**-58** is there because I tried to install it, but I obviously didn't do that correctly.)

(**[COLOR=#ff0000]c[/COLOR]**) Re-install the **-58** kernel *[COLOR=#0000cd]properly[/COLOR]* from synaptic, if that's possible.  (What, by the way, should I search on for that in synaptic?  "**linux-image-1.13.0-58**" ??  And would installing this one thing  ("linux-image-1.13.0-58") put into /boot everything I need for **-58**?  Or do I need to *separately* get any other files, for example, -58 header-files or some such ?

(**[COLOR=#ff0000]d[/COLOR]**) Make it so that in my root directory, ** /initrd.img** links to **/boot/initrd.img-1.13.0[COLOR=#ff0000]-58[/COLOR]-generic**, and that **/initrd.img.old** links to **/boot/initrd.img-1.13.0[COLOR=#ff0000]-57[/COLOR]-generic **(not sure how to do that);

(**[COLOR=#ff0000]e[/COLOR]**) Make it so that in my root directory, ** /vmlinuz** links to **/boot/vmlinuz-3.13.0[COLOR=#ff0000]-58[/COLOR]-generic**, and that **/vmlinuz.old** links to **/boot/vmlinuz-1.13.0[COLOR=#ff0000]-57[/COLOR]-generic **(not sure how to do that);

Doing (d) and (e) so that I can ultimately boot normally into* kernel 58*. 

([COLOR=#ff0000]**f**[/COLOR]) Figure out exactly which file(s) to edit  (** /etc/grub.d/40_custom** ?? ) so as to make booting normally into kernel 58 *a permanent thing*, and, finally,

(**[COLOR=#ff0000]g[/COLOR]**) Make sure I edit that file accurately.

I'm afraid I'm still fuzzy on how to correctly execute all that.  Thanks for the info so far.

---

### Post by oldfred on 2015-07-20
In synaptic is a full reinstall option. So even if it says your -58 is installed you should be able to reinstall it. That may clean up some of the links.
Or a purge & then reinstall.
I always search on linux-image to see all current kernels & status.

Make sure you have a working one installed before exiting synaptic. You can actually delete the kernel you are using, but then when you reboot it is gone. And if no other kernel you have bigger issues. Chroot or reinstall.

The final 40_custom should just be able to boot the links without the .old. And you an add a second stanza just for .old also if you want to boot newest and one older. 
Not sure how you managed to get links out of sync. I did not think that was possible.

---

### Post by watchpocket on 2015-07-22
>[I] In synaptic is a full reinstall option. So even if it says your -58 is installed you should be able to reinstall it. That may clean up some of the links.

[/I]I purged the -58 that I previously had tried to install.  (It never actually had gotten fully installed.)

Ready for a fresh start, and searching on "linux-image" in synaptic from my sdb Precise drive*, *there was no -58 available. (Also, the -57 that was available in synaptic was for Trusty, not Precise, which I thought was odd, but that's what I already had installed. There was no -57 for Precise, only Trusty).

So I did a complete reinstall of -57 from within synaptic. 

 But after I did that, I saw the same thing in **/** and **/boot** that had been there before:

(I was hoping **initrd.img.old** would now point to -55 (the way **vmlinuz.old** does) instead of to a 2nd, mutant -57.)

```
-->** ls -la /**
total 132
 4 drwxr-xr-x   26 root root  4096 Jul 19 18:14 ./
 4 drwxr-x---+   3 root root  4096 Jul 22 14:07 ../
 4 drwxr-xr-x    2 root root  4096 Jul 18  2014 .rpmdb/
 4 drwxr-xr-x    2 root root  4096 May 31 15:57 bin/
 4 drwxr-xr-x    4 root root  4096 Jul 22 02:12 boot/
 4 drwxr-xr-x    2 root root  4096 Jan 11  2014 cdrom/
 4 drwxr-xr-x    4 root root  4096 Aug 20  2013 dev/
12 drwxr-xr-x  152 root root 12288 Jul 22 13:27 etc/
 4 drwxr-xr-x    3 root root  4096 Jan 11  2014 home/
 0 lrwxrwxrwx    1 root root    33 Jul 19 18:14 initrd.img -> boot/initrd.img-3.13.0-57-generic
 0 lrwxrwxrwx    1 root root    33 Jul  9 02:13[COLOR=#ff0000] initrd.img.old -> boot/initrd.img-3.13.0-57-generic[/COLOR]
 4 drwxr-xr-x   27 root root  4096 May 22 13:29 lib/
 4 drwxr-xr-x    2 root root  4096 Apr 10 02:44 lib32/
 4 drwxr-xr-x    2 root root  4096 Apr 10 02:44 lib64/
16 drwx------    2 root root 16384 Jan 11  2014 lost+found/
 4 drwxr-xr-x    2 root root  4096 May 31 15:54 media/
 4 drwxr-xr-x    2 root root  4096 Apr 19  2012 mnt/
 4 drwxr-xr-x    4 root root  4096 Jul  6  2014 opt/
 4 drwxr-xr-x    2 root root  4096 Apr 19  2012 proc/
 4 drwx------   13 root root  4096 May  9 01:13 root/
 4 drwxr-xr-x    9 root root  4096 Aug 20  2013 run/
12 drwxr-xr-x    2 root root 12288 Jun 19 03:54 sbin/
 4 drwxr-xr-x    2 root root  4096 Mar  5  2012 selinux/
 4 drwxr-xr-x    2 root root  4096 Aug 20  2013 srv/
 4 drwxr-xr-x    2 root root  4096 Apr 14  2012 sys/
 4 drwxrwxrwt    6 root root  4096 Jul 22 13:28 tmp/
 4 drwxr-xr-x   11 root root  4096 Dec 14  2014 usr/
 4 drwxr-xr-x   13 root root  4096 Jul 22 13:27 var/
 0 lrwxrwxrwx    1 root root    30 Jul  9 02:13 vmlinuz -> boot/vmlinuz-3.13.0-57-generic
 0 lrwxrwxrwx    1 root root    30 Jun 19 03:54 vmlinuz.old -> boot/vmlinuz-3.13.0-55-generic

--> **ls -la /boot**
total 89476
    4 drwxr-xr-x  4 root root     4096 Jul 22 02:12 ./
    4 drwxr-xr-x 26 root root     4096 Jul 19 18:14 ../
 3448 -rw-------  1 root root  3527402 May 27 07:15 System.map-3.13.0-54-generic
 3448 -rw-------  1 root root  3527402 Jun 18 06:19 System.map-3.13.0-55-generic
 3448 -rw-------  1 root root  3528045 Jun 22 06:08 System.map-3.13.0-57-generic
 1140 -rw-r--r--  1 root root  1164806 May 27 07:15 abi-3.13.0-54-generic
 1140 -rw-r--r--  1 root root  1164806 Jun 18 06:19 abi-3.13.0-55-generic
 1140 -rw-r--r--  1 root root  1164984 Jun 22 06:08 abi-3.13.0-57-generic
  164 -rw-r--r--  1 root root   165771 May 27 07:15 config-3.13.0-54-generic
  164 -rw-r--r--  1 root root   165771 Jun 18 06:19 config-3.13.0-55-generic
  164 -rw-r--r--  1 root root   165771 Jun 22 06:08 config-3.13.0-57-generic
    4 drwxr-xr-x  3 root root     4096 Jul 20 14:20 extlinux/
   12 drwxr-xr-x  3 root root    12288 Jul 20 14:20 grub/
18488 -rw-r--r--  1 root root 18929000 Jun 12 15:58 initrd.img-3.13.0-54-generic
18488 -rw-r--r--  1 root root 18929785 Jun 20 13:20 initrd.img-3.13.0-55-generic
[COLOR=#ff0000]18488 -rw-r--r--  1 root root[/COLOR] [COLOR=#ff0000]18930955 Jul 19 18:14 initrd.img-3.13.0-57-generic[/COLOR]
 [COLOR=#ff0000]2076 -rw-r--r--  1 root root  2121848 Jul 20 00:32 initrd.img-3.13.0.57-generic[/COLOR]
  176 -rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
  176 -rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
 5768 -rw-------  1 root root  5903392 May 27 07:15 vmlinuz-3.13.0-54-generic
 5768 -rw-------  1 root root  5903328 Jun 18 06:19 vmlinuz-3.13.0-55-generic
 5768 -rw-------  1 root root  5903904 Jun 22 06:08 vmlinuz-3.13.0-57-generic
```
I think I need to delete that 2nd, smaller -57, but I have no idea how to specify that one when trying to delete it, when both files have the exact same identical name.

This is very mysterious, and very frustrating.   I still cannot boot into kernel -57.  It just puts me at the busybox prompt.

What might you (anyone?) do in this situation?

---

### Post by Bashing-om on 2015-07-22
watchpocket; Hey;

I do continue to watch this thread.

How about we look at the base files, and ONLY CONSIDER a manual intervention :
```

ls -la /lib/modules/
ls -al /usr/src/
dpkg -l | grep linux
ls -al /
ls -al /boot/

```
I would much prefer to stay within the package management system, BUT, there are alternatives.

[INDENT][INDENT]maybe it is time to get drastic 
[/INDENT][/INDENT]

---

### Post by oldfred on 2015-07-22
If updates were for trusty, are you sure you have not booted into trusty?
Otherwise software sources may have a major issue, of not all the same or you ran a version update in precise?

You can always check what you are in:
 Version or DISTRIB:
cat /etc/*release
cat /etc/lsb-release

---

### Post by watchpocket on 2015-07-22
Thanks, bashing-om.  I will post the output of those commands tonight about 1:30 a.m. (east coast time) when I get home.  

I do have the output from ***ls -al /*** and ***ls -al /boot*** above (at least of what they look like right now).

---

### Post by watchpocket on 2015-07-22
> *If updates were for trusty, are you sure you have not booted into trusty?*

No, I definitely booted into precise.  My synaptic in precise has a whole different look than it does in my trusty. (But even that's not the only way I know I was in precise).


> *Otherwise software sources may have a major issue, *

Yeah, I better take a look at the list of my software sources ( [FONT=lucida console]/etc/apt/sources.list[/FONT] ) in precise later tonight and make sure there's nothing there that says 'trusty'.

> *of not all the same or you ran a version update in precise?*

I did hit the *software updater* while booted into precise -55 earlier today, but there were no kernel updates that took place.  


My guess (my hope) is that if I were to delete the **-57** in /boot -- the one with the smaller file size (and I hope there's a way to do that without deleting the other, larger -57) -- that** initrd.img.old** in **/** will then link to **/boot/initrd.img[COLOR=#0000ff]-55[/COLOR]-generic**.

I won't try that, though, until I have a clearer idea that I should, or that I can do it correctly and get the desired result.  

I'll examine what's up with software sources first. Thanks & stay tuned.

---

### Post by watchpocket on 2015-07-23
**My problem has been solved**, but for one minor detail.  Here's how:

I logged into my sdb precise drive by editing the grub menu.  I logged into kernel -55.  I first checked software sources to see if a Trusty ppa or Trusty anything had made its way there, & it had not.  Every line in the list under the "Other Software" tab had "Precise" in it.

Then I opened "Software Up to Date" from the system drop-down menu in the top gnome panel.  I pressed "Check" to update the cache, and there suddenly was a bunch of kernel and kernel-header updates (for Precise) to kernel -58.  

I installed all of them (I noticed during this that the install process automatically removed a Trusty kernel). I re-booted, selected Precise from grub, and, voila, booted directly into kernel -58 normally.  I write this now from my Precise install:

```
--> [COLOR=#0000ff]**uname -a**[/COLOR]
Linux rjbox 3.13.0-58-generic #97~precise1-Ubuntu SMP Wed Jul 8 14:07:17 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

Which means that everything is suddenly back to normal.

**Except for the small detail that I still have** ***TWO*** of the [COLOR=#ff0000]***initrd.img-3.13.0.57-generic ***[/COLOR]in my /boot directory.  Though at the moment this does not appear to be interfering with anything, or to otherwise be of any consequence:

```
--> **[COLOR=#0000ff]ls -la /boo[/COLOR]**t 
total 89484
    4 drwxr-xr-x  4 root root     4096 Jul 23 02:33 ./
    4 drwxr-xr-x 26 root root     4096 Jul 23 02:23 ../
 3448 -rw-------  1 root root  3527402 Jun 18 06:19 System.map-3.13.0-55-generic
 3448 -rw-------  1 root root  3528045 Jun 22 06:08 System.map-3.13.0-57-generic
 3448 -rw-------  1 root root  3528274 Jul  8 10:24 System.map-3.13.0-58-generic
 1140 -rw-r--r--  1 root root  1164806 Jun 18 06:19 abi-3.13.0-55-generic
 1140 -rw-r--r--  1 root root  1164984 Jun 22 06:08 abi-3.13.0-57-generic
 1140 -rw-r--r--  1 root root  1165129 Jul  8 10:24 abi-3.13.0-58-generic
  164 -rw-r--r--  1 root root   165771 Jun 18 06:19 config-3.13.0-55-generic
  164 -rw-r--r--  1 root root   165771 Jun 22 06:08 config-3.13.0-57-generic
  164 -rw-r--r--  1 root root   165771 Jul  8 10:24 config-3.13.0-58-generic
    4 drwxr-xr-x  3 root root     4096 Jul 23 02:33 extlinux/
   12 drwxr-xr-x  3 root root    12288 Jul 23 02:33 grub/
18488 -rw-r--r--  1 root root 18929785 Jun 20 13:20 initrd.img-3.13.0-55-generic
[COLOR=#ff0000]**18488 -rw-r--r--  1 root root 18930955 Jul 19 18:14 initrd.img-3.13.0-57-generic**[/COLOR]
18492 -rw-r--r--  1 root root 18931742 Jul 23 02:24 initrd.img-3.13.0-58-generic
 [COLOR=#ff0000]**2076 -rw-r--r--  1 root root  2121848 Jul 20 00:32 initrd.img-3.13.0.57-generic**[/COLOR]
  176 -rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
  176 -rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
 5768 -rw-------  1 root root  5903328 Jun 18 06:19 vmlinuz-3.13.0-55-generic
 5768 -rw-------  1 root root  5903904 Jun 22 06:08 vmlinuz-3.13.0-57-generic
 5772 -rw-------  1 root root  5907232 Jul  8 10:24 vmlinuz-3.13.0-58-generic
```

But I would think that the second, smaller, -57 shouldn't be there.

Accordingly I'll go ahead and post **the output to your suggested commands**, *bashing-om*:

You have the /boot dir above; here's **/**:
```
-->** [COLOR=#0000ff]ls -la /[/COLOR]**
total 116
 4 drwxr-xr-x  26 root root  4096 Jul 23 02:23 ./
 4 drwxr-xr-x  26 root root  4096 Jul 23 02:23 ../
 4 drwxr-xr-x   2 root root  4096 Jul 18  2014 .rpmdb/
 4 drwxr-xr-x   2 root root  4096 May 31 15:57 bin/
 4 drwxr-xr-x   4 root root  4096 Jul 23 02:33 boot/
 4 drwxr-xr-x   2 root root  4096 Jan 11  2014 cdrom/
 0 drwxr-xr-x  15 root root  4420 Jul 23 02:33 dev/
12 drwxr-xr-x 152 root root 12288 Jul 23 02:33 etc/
 4 drwxr-xr-x   3 root root  4096 Jan 11  2014 home/
 0 lrwxrwxrwx   1 root root    33 Jul 23 02:23 initrd.img -> boot/initrd.img-3.13.0-58-generic
 0 lrwxrwxrwx   1 root root    33 Jul 19 18:14 initrd.img.old -> boot/initrd.img-3.13.0-57-generic
 4 drwxr-xr-x  27 root root  4096 May 22 13:29 lib/
 4 drwxr-xr-x   2 root root  4096 Apr 10 02:44 lib32/
 4 drwxr-xr-x   2 root root  4096 Apr 10 02:44 lib64/
16 drwx------   2 root root 16384 Jan 11  2014 lost+found/
 4 drwxr-xr-x   2 root root  4096 May 31 15:54 media/
 4 drwxr-xr-x   2 root root  4096 Apr 19  2012 mnt/
 4 drwxr-xr-x   4 root root  4096 Jul  6  2014 opt/
 0 dr-xr-xr-x 207 root root     0 Jul 23 02:25 proc/
 4 drwx------  13 root root  4096 May  9 01:13 root/
 0 drwxr-xr-x  21 root root   820 Jul 23 02:26 run/
12 drwxr-xr-x   2 root root 12288 Jun 19 03:54 sbin/
 4 drwxr-xr-x   2 root root  4096 Mar  5  2012 selinux/
 4 drwxr-xr-x   2 root root  4096 Aug 20  2013 srv/
 0 dr-xr-xr-x  13 root root     0 Jul 23 02:25 sys/
 4 drwxrwxrwt   9 root root  4096 Jul 23 03:17 tmp/
 4 drwxr-xr-x  11 root root  4096 Dec 14  2014 usr/
 4 drwxr-xr-x  13 root root  4096 Jul 23 02:25 var/
 0 lrwxrwxrwx   1 root root    30 Jul 23 02:23 vmlinuz -> boot/vmlinuz-3.13.0-58-generic
 0 lrwxrwxrwx   1 root root    30 Jul  9 02:13 vmlinuz.old -> boot/vmlinuz-3.13.0-57-generic
```

And the others:

```
-->**[COLOR=#0000ff] ls -la /lib/modules/[/COLOR]**
total 20
4 drwxr-xr-x  5 root root 4096 Jul 23 02:33 ./
4 drwxr-xr-x 27 root root 4096 May 22 13:29 ../
4 drwxr-xr-x  5 root root 4096 Jun 20 13:20 3.13.0-55-generic/
4 drwxr-xr-x  5 root root 4096 Jul 19 18:14 3.13.0-57-generic/
4 drwxr-xr-x  5 root root 4096 Jul 23 02:24 3.13.0-58-generic/
```

```
--> **[COLOR=#0000ff]ls -la /lib/modules/3.13.0-57-generic[/COLOR]**                                                                                                          pts/2  Thursday  2015-07-23  03:32:49 
total 4576
  4 drwxr-xr-x  5 root root   4096 Jul 19 18:14 ./
  4 drwxr-xr-x  5 root root   4096 Jul 23 02:33 ../
  0 lrwxrwxrwx  1 root root     40 Jun 22 06:19 build -> /usr/src/linux-headers-3.13.0-57-generic/
  4 drwxr-xr-x  2 root root   4096 Jun 22 06:09 initrd/
  4 drwxr-xr-x 11 root root   4096 Jul  9 02:06 kernel/
920 -rw-r--r--  1 root root 939410 Jul 19 18:14 modules.alias
904 -rw-r--r--  1 root root 921789 Jul 19 18:14 modules.alias.bin
  8 -rw-r--r--  1 root root   7013 Jun 22 06:08 modules.builtin
 12 -rw-r--r--  1 root root   9241 Jul 19 18:14 modules.builtin.bin
  4 -rw-r--r--  1 root root     69 Jul 19 18:14 modules.ccwmap
372 -rw-r--r--  1 root root 377835 Jul 19 18:14 modules.dep
544 -rw-r--r--  1 root root 555099 Jul 19 18:14 modules.dep.bin
  4 -rw-r--r--  1 root root    240 Jul 19 18:14 modules.devname
  4 -rw-r--r--  1 root root   1259 Jul 19 18:14 modules.ieee1394map
  4 -rw-r--r--  1 root root    295 Jul 19 18:14 modules.inputmap
  8 -rw-r--r--  1 root root   4547 Jul 19 18:14 modules.isapnpmap
  8 -rw-r--r--  1 root root   7381 Jul 19 18:14 modules.ofmap
152 -rw-r--r--  1 root root 153963 Jun 22 06:08 modules.order
572 -rw-r--r--  1 root root 583227 Jul 19 18:14 modules.pcimap
  4 -rw-r--r--  1 root root   1681 Jul 19 18:14 modules.seriomap
  4 -rw-r--r--  1 root root    160 Jul 19 18:14 modules.softdep
412 -rw-r--r--  1 root root 417844 Jul 19 18:14 modules.symbols
512 -rw-r--r--  1 root root 521244 Jul 19 18:14 modules.symbols.bin
108 -rw-r--r--  1 root root 109696 Jul 19 18:14 modules.usbmap
  4 drwxr-xr-x  3 root root   4096 Jul 19 18:13 updates/
```

```
--> **[COLOR=#0000ff]ls -la /lib/modules/3.13.0-58-generic[/COLOR]** 
total 4576
  4 drwxr-xr-x  5 root root   4096 Jul 23 02:24 ./
  4 drwxr-xr-x  5 root root   4096 Jul 23 02:33 ../
  0 lrwxrwxrwx  1 root root     40 Jul  8 10:39 build -> /usr/src/linux-headers-3.13.0-58-generic/
  4 drwxr-xr-x  2 root root   4096 Jul  8 10:24 initrd/
  4 drwxr-xr-x 11 root root   4096 Jul 23 02:23 kernel/
920 -rw-r--r--  1 root root 940033 Jul 23 02:24 modules.alias
904 -rw-r--r--  1 root root 922199 Jul 23 02:24 modules.alias.bin
  8 -rw-r--r--  1 root root   7013 Jul  8 10:24 modules.builtin
 12 -rw-r--r--  1 root root   9241 Jul 23 02:24 modules.builtin.bin
  4 -rw-r--r--  1 root root     69 Jul 23 02:24 modules.ccwmap
372 -rw-r--r--  1 root root 377901 Jul 23 02:24 modules.dep
544 -rw-r--r--  1 root root 555187 Jul 23 02:24 modules.dep.bin
  4 -rw-r--r--  1 root root    240 Jul 23 02:24 modules.devname
  4 -rw-r--r--  1 root root   1259 Jul 23 02:24 modules.ieee1394map
  4 -rw-r--r--  1 root root    295 Jul 23 02:24 modules.inputmap
  8 -rw-r--r--  1 root root   4547 Jul 23 02:24 modules.isapnpmap
  8 -rw-r--r--  1 root root   7381 Jul 23 02:24 modules.ofmap
152 -rw-r--r--  1 root root 153963 Jul  8 10:24 modules.order
572 -rw-r--r--  1 root root 583682 Jul 23 02:24 modules.pcimap
  4 -rw-r--r--  1 root root   1681 Jul 23 02:24 modules.seriomap
  4 -rw-r--r--  1 root root    160 Jul 23 02:24 modules.softdep
412 -rw-r--r--  1 root root 418175 Jul 23 02:24 modules.symbols
512 -rw-r--r--  1 root root 521427 Jul 23 02:24 modules.symbols.bin
108 -rw-r--r--  1 root root 109696 Jul 23 02:24 modules.usbmap
  4 drwxr-xr-x  3 root root   4096 Jul 23 02:23 updates/

```

```
--> **[COLOR=#0000ff]ls -al /usr/src/[/COLOR]**                                                                                                                               pts/2  Thursday  2015-07-23  03:41:53 
total 44
4 drwxr-xr-x 11 root root 4096 Jul 23 02:23 ./
4 drwxr-xr-x 11 root root 4096 Dec 14  2014 ../
4 drwxr-xr-x 24 root root 4096 Jun 20 13:20 linux-headers-3.13.0-55/
4 drwxr-xr-x  7 root root 4096 Jun 20 13:20 linux-headers-3.13.0-55-generic/
4 drwxr-xr-x 24 root root 4096 Jul  9 02:06 linux-headers-3.13.0-57/
4 drwxr-xr-x  7 root root 4096 Jul  9 02:06 linux-headers-3.13.0-57-generic/
4 drwxr-xr-x 24 root root 4096 Jul 23 02:23 linux-headers-3.13.0-58/
4 drwxr-xr-x  7 root root 4096 Jul 23 02:23 linux-headers-3.13.0-58-generic/
4 drwxr-xr-x  3 root root 4096 Feb 16 18:32 nvidia-304-304.125/
4 drwxr-xr-x  3 root root 4096 Feb 16 18:32 nvidia-304-updates-304.125/
4 drwxr-xr-x  3 root root 4096 Feb 16 18:32 nvidia-331-updates-331.113/
```

```
--> [COLOR=#0000ff]**dpkg -l | grep linux**[/COLOR]
ii  extlinux                                 2:4.05+dfsg-2                                       collection of boot loaders (ext2/3/4 and btrfs bootloader)
ii  libselinux1                              2.1.0-4.1ubuntu1                                    SELinux runtime shared libraries
ii  libselinux1:i386                         2.1.0-4.1ubuntu1                                    SELinux runtime shared libraries
ii  libv4l-0                                 0.8.6-1ubuntu2                                      Collection of video4linux support libraries
ii  libv4l-0:i386                            0.8.6-1ubuntu2                                      Collection of video4linux support libraries
ii  libv4lconvert0                           0.8.6-1ubuntu2                                      Video4linux frame format conversion library
ii  libv4lconvert0:i386                      0.8.6-1ubuntu2                                      Video4linux frame format conversion library
ii  linux-firmware                           1.79.18                                             Firmware for Linux kernel drivers
ii  linux-generic-lts-trusty                 3.13.0.58.50                                        Generic Linux kernel image and headers
ii  linux-headers-3.13.0-55                  3.13.0-55.94~precise1                               Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic          3.13.0-55.94~precise1                               Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-57                  3.13.0-57.95~precise1                               Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic          3.13.0-57.95~precise1                               Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-58                  3.13.0-58.97~precise1                               Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-58-generic          3.13.0-58.97~precise1                               Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
**[COLOR=#800080]ii  linux-headers-generic-lts-trusty         3.13.0.58.50                                        Generic Linux kernel headers[/COLOR]**
ii  linux-image-3.13.0-55-generic            3.13.0-55.94~precise1                               Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-57-generic            3.13.0-57.95~precise1                               Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-58-generic            3.13.0-58.97~precise1                               Linux kernel image for version 3.13.0 on 64 bit x86 SMP
[COLOR=#800080]**ii** ** linux-image-generic-lts-trusty           3.13.0.58.50                                        Generic Linux kernel image**[/COLOR]
ii  linux-libc-dev                           3.2.0-88.126                                        Linux Kernel Headers for development
ii  linux-sound-base                         1.0.25+dfsg-0ubuntu1.1                              base package for ALSA and OSS sound systems
ii  pptp-linux                               1.7.2-6                                             Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                 2:4.05+dfsg-2                                       collection of boot loaders
ii  syslinux-common                          2:4.05+dfsg-2                                       collection of boot loaders (common files)
ii  syslinux-legacy                          2:3.63+dfsg-2ubuntu5                                Bootloader for Linux/i386 using MS-DOS floppies
ii  syslinux-themes-debian                   10-1                                                collection of boot loaders (theme metapackage)
ii  syslinux-themes-debian-squeeze           10-1                                                collection of boot loaders (debian-squeeze theme)
ii  util-linux                               2.20.1-1ubuntu3.1                                   Miscellaneous system utilities
```

Anything 'Trusty' in that last list should be removed on the next boot, as I've already done a 

```
--> [COLOR=#0000ff]**sudo apt-get autoclean**[/COLOR]
[sudo] password for rj: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del linux-headers-3.13.0-55-generic 3.13.0-55.92~precise1 [1,121 kB]
**[COLOR=#800080]Del linux-generic-lts-trusty 3.13.0.54.47 [1,744 B][/COLOR]**
Del linux-libc-dev 3.2.0-85.122 [858 kB]
Del libssl-dev 1.0.1-4ubuntu5.28 [1,576 kB]
Del openssl 1.0.1-4ubuntu5.28 [524 kB]
[COLOR=#800080]**Del linux-headers-generic-lts-trusty 3.13.0.54.47 [2,410 B]**[/COLOR]
Del linux-libc-dev 3.2.0-87.125 [854 kB]
Del linux-libc-dev 3.2.0-86.123 [860 kB]
Del linux-generic-lts-trusty 3.13.0.57.49 [1,746 B]
Del linux-headers-generic-lts-trusty 3.13.0.55.48 [2,402 B]
Del libssl-doc 1.0.1-4ubuntu5.28 [1,034 kB]
Del flashplugin-installer 11.2.202.468ubuntu0.12.04.1 [6,976 B]
Del linux-libc-dev 3.2.0-84.121 [860 kB]
Del libssl1.0.0 1.0.1-4ubuntu5.28 [1,051 kB]
Del linux-libc-dev 3.2.0-86.124 [856 kB]
Del linux-generic-lts-trusty 3.13.0.55.48 [1,744 B]
Del linux-generic-lts-trusty 3.13.0.53.46 [1,746 B]
Del linux-headers-generic-lts-trusty 3.13.0.57.49 [2,416 B]
Del flashplugin-installer 11.2.202.481ubuntu0.12.04.1 [7,024 B]
Del libssl1.0.0 1.0.1-4ubuntu5.28 [1,009 kB]
Del linux-image-generic-lts-trusty 3.13.0.55.48 [2,408 B]
Del flashplugin-installer 11.2.202.466ubuntu0.12.04.1 [7,022 B]
Del linux-image-generic-lts-trusty 3.13.0.53.46 [2,426 B]
Del linux-image-generic-lts-trusty 3.13.0.54.47 [2,422 B]
Del linux-headers-generic-lts-trusty 3.13.0.53.46 [2,426 B]
Del linux-headers-3.13.0-55 3.13.0-55.92~precise1 [12.9 MB]
Del smplayer 14.9.0.6994-1~precise1 [2,628 kB]
Del linux-image-generic-lts-trusty 3.13.0.57.49 [2,418 B]
Del smplayer 14.9.0.6966-1~precise1 [2,620 kB]
Del linux-image-3.13.0-55-generic 3.13.0-55.92~precise1 [52.5 MB]
```

[ Edit: Hm, **the two trusty items are still there** when I run* "dpkg -l | grep linux"* again after having re-booted. ]

But I do need to delete the[COLOR=#ff0000][B]  
2076 -rw-r--r--  1 root root  2121848 Jul 20 00:32 initrd.img-3.13.0.57-generic  [/B][/COLOR]that is in my /boot dir.

How can I do that without removing the **[COLOR=#a52a2a]*other*[/COLOR]**  **initrd.img-3.13.0.57-generic** file in /boot of the same name?

---

### Post by oldfred on 2015-07-23
Linux does not allow two files with same name, so that is an issue on how you got it and then how you can delete it.
Can you use 
gksudo nautilus

---

### Post by Bashing-om on 2015-07-23
watchpocket; Hello ;

Great ! 

+1; My thoughts also :
> 
<oldfred>
Linux does not allow two files with same name, so that is an issue on how you got it and then how you can delete it.
Can you use 
gksudo nautilus


[INDENT][INDENT]shinning like a new penny
[/INDENT][/INDENT]

---

### Post by watchpocket on 2015-07-23
Yes -- using gksudo nautilus, I "moved to trash" ("delete" wasn't in the
right-click menu) the

[I]2076 -rw-r--r--  1 root root  2121848 Jul 20 00:32 initrd.img-3.13.0.57-generic
[/I]
archive file from /boot.  I did get the following message at my terminal prompt:

```
** (nautilus:3055): WARNING **: Could not inhibit power management:
GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Name
"org.gnome.SessionManager" does not exist
ares. Error No such file or directory
gksudo nautilus  7.14s user 0.47s system 1% cpu 7:05.81 total
```

but the offending -57 archive file appears to have been successfully deleted, with no observable problems resulting from its deletion.

About the trusty files I highlighted above, I think I may be able to remove them using *"sudo apt-get clean"*, but one question about 'clean' -- [I]man apt-get says:

clean clears out the local repository of retrieved package files. It removes everything but the lock file from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When APT is used as a dselect(1) method, clean is run automatically. Those who do not use dselect will likely want to run apt-get clean from time to time to free up disk space.

[/I]So, if a package is cleared from the local repository, can one still re-install that package, say, from synaptic?*  (Maybe it would get it from a non-locoal repository?) *I'm not losing anything I can't get back  when I run 'clean' am I?

Finally, I've been wondering why, at '*uname -a*' I always see THREE of "x86_64" ??

```
-->[COLOR=#0000ff] uname -a [/COLOR]
Linux rjbox 3.13.0-58-generic #97~precise1-Ubuntu SMP Wed Jul 8 14:07:17 UTC 2015 [COLOR=#ff0000]x86_64 x86_64 x86_64 [/COLOR]GNU/Linux
```

---

### Post by Bashing-om on 2015-07-23
watchpocket; Good deal ;
As to :
> 
So, if a package is cleared from the local repository, can one still re-install that package, say, from synaptic? (Maybe it would get it from a non-locoal repository?) I'm not losing anything I can't get back when I run 'clean' am I?

You have the right of it, IF required the package manager will fetch that package from the software repository.

And in respect to the 3 "x86_64"'s :

Just reporting what is in the respective fields:
mine:
```

sysop@1404mini:~$ uname -a
Linux 1404mini 3.13.0-58-generic #97-Ubuntu SMP Wed Jul 8 02:56:15 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
sysop@1404mini

```
see:
```

man uname

```
for the full disclosure of those fields.

[INDENT][INDENT]we seek to learn
[/INDENT][/INDENT]

---

### Post by watchpocket on 2015-07-23
[URL="https://unix.stackexchange.com/questions/188524/why-is-architecture-listed-thrice-in-uname-a"]https://unix.stackexchange.com/questions/188524/why-is-architecture-listed-thrice-in-uname-a

[/URL]

---

