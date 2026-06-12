---
title: "&quot;/boot partition 95% full&quot; message - help?"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by richardq on 2006-06-19
Linux newbie question:

I'm running Dapper. I've got a 100MB /boot partition. The system is popping up a message now telling me that the boot partition is 95% full. There are 9 gzip archives about 6-7MB each which are named 'initrd.img-2.6.15-25-686' etc.. I can't seem to delete any of them. It tells me I don't have permission to the parent folder. I've opened up the Disks Manager and hit the browse button for that partition - given my admin password but it won't let me delete any of those files.

I'm booting the 2.6.15-25-686 kernel. Can I safely delete any of those files? How can I do it? Or should I re-size the /boot partition? When I originally set up my dual boot system (xp/Breezy) I was told that 100MB would be plenty. Any help much appreciated.

---

### Post by rai4shu2 on 2006-06-19
You should go into Synaptic/Adept and remove old "linux-image" packages you don't need.

---

### Post by SpacePony on 2006-06-20
There may be something odd going on with your /boot partition. I too have a 100mb partition, and about 5 linux-images but my partition is only 23% full. rai4shu2's idea should work but there may be something there worth investigating. 

If you want to look into in further, paste here the output of the following commands:
df
ls -la /boot

If there's any directories in /boot, paste the ls -la output of those aswell.

---

### Post by richardq on 2006-06-20
I used Synaptic to remove the 386 linux image package but that only got rid of about 3 MB. So something is still not right.


[QUOTE=SpacePony]There may be something odd going on with your /boot partition. I too have a 100mb partition, and about 5 linux-images but my partition is only 23% full. rai4shu2's idea should work but there may be something there worth investigating. 

If you want to look into in further, paste here the output of the following commands:
df
ls -la /boot

If there's any directories in /boot, paste the ls -la output of those aswell.[/QUOTE]

Here is the output:

```
richard@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda6             27442716   4178020  21870660  17% /
varrun                  512888        88    512800   1% /var/run
varlock                 512888         4    512884   1% /var/lock
udev                    512888       144    512744   1% /dev
devshm                  512888         0    512888   0% /dev/shm
lrm                     512888     18316    494572   4% /lib/modules/2.6.15-25-686/volatile
/dev/sda2                90329     81883      3627  96% /boot
/dev/hdb5             41990128   2904756  36952344   8% /home
/dev/sda1            125379260  97923364  27455896  79% /media/windowsC
/dev/hdb1            113627712  98430492  15197220  87% /media/windowsG
richard@ubuntu:~$ ls -la /boot
total 77593
drwxr-xr-x  4 root root    2048 2006-06-17 00:19 .
drwxr-xr-x 23 root root    4096 2006-06-17 00:24 ..
-rw-r--r--  1 root root  239811 2006-03-11 12:42 abi-2.6.12-10-386
-rw-r--r--  1 root root  239770 2005-10-10 09:16 abi-2.6.12-9-386
-rw-r--r--  1 root root  262654 2006-04-04 18:00 abi-2.6.15-20-386
-rw-r--r--  1 root root  263321 2006-04-21 14:00 abi-2.6.15-21-386
-rw-r--r--  1 root root  266619 2006-05-23 12:56 abi-2.6.15-23-386
-rw-r--r--  1 root root  265781 2006-05-23 12:57 abi-2.6.15-23-686
-rw-r--r--  1 root root  266619 2006-06-14 08:15 abi-2.6.15-25-386
-rw-r--r--  1 root root  265781 2006-06-14 08:16 abi-2.6.15-25-686
-rw-r--r--  1 root root   64125 2006-03-11 11:12 config-2.6.12-10-386
-rw-r--r--  1 root root   64045 2005-08-30 17:39 config-2.6.12-8-386
-rw-r--r--  1 root root   64135 2005-10-10 08:12 config-2.6.12-9-386
-rw-r--r--  1 root root   69443 2006-04-04 13:42 config-2.6.15-20-386
-rw-r--r--  1 root root   69704 2006-04-21 12:41 config-2.6.15-21-386
-rw-r--r--  1 root root   69878 2006-05-23 09:47 config-2.6.15-23-386
-rw-r--r--  1 root root   69719 2006-05-23 10:00 config-2.6.15-23-686
-rw-r--r--  1 root root   69876 2006-06-14 07:24 config-2.6.15-25-386
-rw-r--r--  1 root root   69717 2006-06-14 07:33 config-2.6.15-25-686
drwxr-xr-x  2 root root    1024 2006-06-18 21:10 grub
-rw-r--r--  1 root root 6056024 2006-04-21 00:22 initrd.img-2.6.12-10-386
-rw-r--r--  1 root root 4781684 2005-09-15 21:09 initrd.img-2.6.12-8-386
-rw-r--r--  1 root root 5296052 2005-10-11 20:49 initrd.img-2.6.12-9-386
-rw-r--r--  1 root root 6541747 2006-04-26 23:51 initrd.img-2.6.15-20-386
-rw-r--r--  1 root root 6755703 2006-05-27 09:59 initrd.img-2.6.15-21-386
-rw-r--r--  1 root root 6766636 2006-05-27 10:20 initrd.img-2.6.15-23-386
-rw-r--r--  1 root root 6962431 2006-06-05 22:58 initrd.img-2.6.15-23-686
-rw-r--r--  1 root root 6784572 2006-06-17 00:17 initrd.img-2.6.15-25-386
-rw-r--r--  1 root root 6978696 2006-06-17 00:24 initrd.img-2.6.15-25-686
drwxr-xr-x  2 root root   12288 2005-09-15 21:06 lost+found
-rw-r--r--  1 root root   94760 2005-10-25 06:32 memtest86+.bin
-rw-r--r--  1 root root  897419 2006-03-11 12:42 System.map-2.6.12-10-386
-rw-r--r--  1 root root  897036 2005-08-30 19:10 System.map-2.6.12-8-386
-rw-r--r--  1 root root  897159 2005-10-10 09:16 System.map-2.6.12-9-386
-rw-r--r--  1 root root  724002 2006-04-04 18:01 System.map-2.6.15-20-386
-rw-r--r--  1 root root  724851 2006-04-21 14:00 System.map-2.6.15-21-386
-rw-r--r--  1 root root  725460 2006-05-23 12:56 System.map-2.6.15-23-386
-rw-r--r--  1 root root  732702 2006-05-23 12:57 System.map-2.6.15-23-686
-rw-r--r--  1 root root  725531 2006-06-14 08:15 System.map-2.6.15-25-386
-rw-r--r--  1 root root  732773 2006-06-14 08:16 System.map-2.6.15-25-686
-rw-r--r--  1 root root 1207036 2006-03-11 12:42 vmlinuz-2.6.12-10-386
-rw-r--r--  1 root root 1206596 2005-08-30 19:10 vmlinuz-2.6.12-8-386
-rw-r--r--  1 root root 1206555 2005-10-10 09:16 vmlinuz-2.6.12-9-386
-rw-r--r--  1 root root 1413740 2006-04-04 18:00 vmlinuz-2.6.15-20-386
-rw-r--r--  1 root root 1415441 2006-04-21 14:00 vmlinuz-2.6.15-21-386
-rw-r--r--  1 root root 1414477 2006-05-23 12:56 vmlinuz-2.6.15-23-386
-rw-r--r--  1 root root 1508444 2006-05-23 12:57 vmlinuz-2.6.15-23-686
-rw-r--r--  1 root root 1414674 2006-06-14 08:15 vmlinuz-2.6.15-25-386
-rw-r--r--  1 root root 1508808 2006-06-14 08:16 vmlinuz-2.6.15-25-686
richard@ubuntu:~$
richard@ubuntu:~$
richard@ubuntu:~$ ls -la /boot/grub
total 183
drwxr-xr-x 2 root root   1024 2006-06-18 21:10 .
drwxr-xr-x 4 root root   2048 2006-06-17 00:19 ..
-rw-r--r-- 1 root root     30 2005-09-15 21:17 device.map
-rw-r--r-- 1 root root   8116 2005-09-15 21:17 e2fs_stage1_5
-rw-r--r-- 1 root root   7908 2005-09-15 21:17 fat_stage1_5
-rw-r--r-- 1 root root   8608 2005-09-15 21:17 jfs_stage1_5
-rw-r--r-- 1 root root   6368 2006-06-18 21:10 menu.lst
-rw-r--r-- 1 root root   6368 2006-06-17 00:25 menu.lst~
-rw-r--r-- 1 root root   5390 2006-05-28 10:16 menu.lst.05-28-06-backup
-rw-r--r-- 1 root root   7316 2005-09-15 21:17 minix_stage1_5
-rw-r--r-- 1 root root   9588 2005-09-15 21:17 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2005-09-15 21:17 stage1
-rw-r--r-- 1 root root 105576 2005-09-15 21:17 stage2
-rw-r--r-- 1 root root   9468 2005-09-15 21:17 xfs_stage1_5
richard@ubuntu:~$ ls -la /boot/lost+found
total 14
drwxr-xr-x 2 root root 12288 2005-09-15 21:06 .
drwxr-xr-x 4 root root  2048 2006-06-17 00:19 ..
richard@ubuntu:~$

```

---

### Post by ranf on 2006-06-20
You can also remove all the Breezy kernels (linux-image-2.6.12...).

---

### Post by BoB! on 2006-06-20
ok, I'm having the same type of issue.  A friend of mine set up my partitions and I've only got 23.50MB for my boot partition.  Now it come up as 100% used, and synaptic  wont upgrade my kernel to the newest version.  So here's the output from those cmds.  what if anything can I delete so synaptic will be able to get the latest kernel?
thnx.


```
bob@bob-laptop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda4             27324316   2978444  22957856  12% /
varrun                  257712        88    257624   1% /var/run
varlock                 257712         4    257708   1% /var/lock
udev                    257712       132    257580   1% /dev
devshm                  257712         0    257712   0% /dev/shm
/dev/hda1                22549     22548         0 100% /boot
/dev/sda1            195263040  54621120 140641920  28% /media/usbdisk
bob@bob-laptop:~$ ls -la /boot
total 21365
drwxr-xr-x  4 root root    1024 2006-06-20 19:57 .
drwxr-xr-x 21 root root    4096 2006-05-22 14:31 ..
-rw-r--r--  1 root root  263321 2006-05-04 18:18 abi-2.6.15-21-386
-rw-r--r--  1 root root  266614 2006-05-07 16:04 abi-2.6.15-22-386
-rw-r--r--  1 root root  266619 2006-05-18 16:57 abi-2.6.15-23-386
-rw-r--r--  1 root root   69704 2006-05-04 18:18 config-2.6.15-21-386
-rw-r--r--  1 root root   69863 2006-05-07 11:42 config-2.6.15-22-386
-rw-r--r--  1 root root   69878 2006-05-18 12:36 config-2.6.15-23-386
drwxr-xr-x  2 root root    1024 2006-05-04 21:29 grub
-rw-r--r--  1 root root 6959759 2006-05-11 10:13 initrd.img-2.6.15-21-386
-rw-r--r--  1 root root 7000413 2006-05-22 14:28 initrd.img-2.6.15-22-386
-rw-r--r--  1 root root  270336 2006-06-04 20:17 initrd.img-2.6.15-23-386
drwxr-xr-x  2 root root   12288 2006-05-04 18:03 lost+found
-rw-r--r--  1 root root   94760 2006-05-04 18:18 memtest86+.bin
-rw-r--r--  1 root root  724851 2006-05-04 18:18 System.map-2.6.15-21-386
-rw-r--r--  1 root root  725303 2006-05-07 16:04 System.map-2.6.15-22-386
-rw-r--r--  1 root root  725460 2006-05-18 16:58 System.map-2.6.15-23-386
-rw-r--r--  1 root root 1415441 2006-05-04 18:18 vmlinuz-2.6.15-21-386
-rw-r--r--  1 root root 1413681 2006-05-07 16:04 vmlinuz-2.6.15-22-386
-rw-r--r--  1 root root 1414477 2006-05-18 16:57 vmlinuz-2.6.15-23-386
bob@bob-laptop:~$ ls -la /boot/grub
total 159
drwxr-xr-x 2 root root   1024 2006-05-04 21:29 .
drwxr-xr-x 4 root root   1024 2006-06-20 19:57 ..
-rw-r--r-- 1 root root    197 2006-05-04 18:26 default
-rw-r--r-- 1 root root     15 2006-05-04 18:18 device.map
-rw-r--r-- 1 root root   7508 2006-05-04 18:26 e2fs_stage1_5
-rw-r--r-- 1 root root   7332 2006-05-04 18:26 fat_stage1_5
-rw-r--r-- 1 root root   8128 2006-05-04 18:26 jfs_stage1_5
-rw-r--r-- 1 root root    161 2006-05-04 21:29 menu.lst
-rw-r--r-- 1 root root   6804 2006-05-04 18:26 minix_stage1_5
-rw-r--r-- 1 root root   9076 2006-05-04 18:26 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2006-05-04 18:26 stage1
-rw-r--r-- 1 root root 105428 2006-05-04 18:26 stage2
-rw-r--r-- 1 root root   8764 2006-05-04 18:26 xfs_stage1_5
bob@bob-laptop:~$ ls -la /boot/lost+found/
total 13
drwxr-xr-x 2 root root 12288 2006-05-04 18:03 .
drwxr-xr-x 4 root root  1024 2006-06-20 19:57 ..
bob@bob-laptop:~$

```

---

### Post by ranf on 2006-06-21
Use synaptic to remove `linux-image-2.6.15-21' and -22.

---

### Post by dcstar on 2006-06-21
[QUOTE=ranf]Use synaptic to remove `linux-image-2.6.15-21' and -22.[/QUOTE]
And when you have freed up some disk space, install a 686 kernel (if you have an Intel CPU) or a K7 kernel (AMD CPU), then uninstall the last 386 kernel after you are happy with the new one.

---

### Post by garba on 2006-06-21
all I can say is I can't understand why people insist on setting up a separate boot partition, 9 cases out of 10 it's totally pointless, reminds me of the /usr/src/linux symlink thing

---

### Post by richardq on 2006-06-21
[QUOTE=garba]all I can say is I can't understand why people insist on setting up a separate boot partition, 9 cases out of 10 it's totally pointless,[/QUOTE]

People like me don't insist on it. We come to a forum like this one and post a question on how to best set up the partitions for a linux install. We're told to make partitions x,y and z and we do it... because we're newbs. Believe me, if I *didn't* have to do something I wouldn't. ;)

---

### Post by BoB! on 2006-06-22
ok, I was able to free up space by getting rid of my 2.6.15-22, -23 images.  But it didn't want me to get rid of the -21, b/c it said I had booted from it.  I installed the -25 image files using synaptic (I tried both the 386 and 686 versions, not at the same time) but when I boot up, I only have the option of using the -21. do I need to do something to get my computer to recognize that I have the -25 stuff?

---

### Post by Mguel on 2006-07-14
> **richardq said:**
> [quote=garba;1166919]all I can say is I can't understand why people insist on setting up a separate boot partition, 9 cases out of 10 it's totally pointless, reminds me of the /usr/src/linux symlink thingPeople like me don't insist on it. We come to a forum like this one and post a question on how to best set up the partitions for a linux install. We're told to make partitions x,y and z and we do it... because we're newbs. Believe me, if I *didn't* have to do something I wouldn't. ;)[/quote]

I'm in the same situation... a newbie and made a special partition for boot following advise on the web, and now I am having the same problems as the others here.

Now, once we've done it, Is there a way to move boot partition to the main root one? (without needing to reinstall)

And what do you think of using a partition for your /home? (something that is also commonly recommended)

Thanks in advance,
Mguel

---

### Post by garba on 2006-07-14
> **Mguel said:**
> I'm in the same situation... a newbie and made a special partition for boot following advise on the web, and now I am having the same problems as the others here.

Now, once we've done it, Is there a way to move boot partition to the main root one? (without needing to reinstall)

And what do you think of using a partition for your /home? (something that is also commonly recommended)

Thanks in advance,
Mguel

storing the contents of /home on a separate partition is good practice, but just i stated above, using a separate partition for /boot is, in my opinion, pointless, unless you just need the extra safety a read-only mount would provide... anyway, moving the contents of boot to the root partition is possible and not hard at all, create a new boot dir in root, say bootnew, copy the contents over to it from /boot, then amend the /boot/grub/menu.lst to make it point to the new location of the kernel/initrd files, and then, last but not least, the most importante part of it: you'll have to reinstall grub's "boot chain":

sudo grub-install <yourdev> --root-directory=/bootnew

with <yourdev> being something like /dev/sda /dev/hda etc.
then reboot, once your system is up and running remove /boot, rename /bootnew to /boot, re-amend menu.lst and do the sudo grub-install thing again using /boot as the new boot dir, i think that's all there's to it unless i'm mistaken, feel free to message me if you need help, and please don't kill me if smoething goes wrong ;) i'd reccomend you keep a rescue disk handy, regards, andre

---

### Post by Mguel on 2006-07-14
> **garba said:**
> storing the contents of /home on a separate partition is good practice, but just i stated above, using a separate partition for /boot is, in my opinion, pointless, unless you just need the extra safety a read-only mount would provide... anyway, moving the contents of boot to the root partition is possible and not hard at all, create a new boot dir in root, say bootnew, copy the contents over to it from /boot, then amend the /boot/grub/menu.lst to make it point to the new location of the kernel/initrd files, and then, last but not least, the most importante part of it: you'll have to reinstall grub's "boot chain":

sudo grub-install <yourdev> --root-directory=/bootnew

with <yourdev> being something like /dev/sda /dev/hda etc.
then reboot, once your system is up and running remove /boot, rename /bootnew to /boot, re-amend menu.lst and do the sudo grub-install thing again using /boot as the new boot dir, i think that's all there's to it unless i'm mistaken, feel free to message me if you need help, and please don't kill me if smoething goes wrong ;) i'd reccomend you keep a rescue disk handy, regards, andre

Thanks! I'll try it

---

### Post by ezsit on 2006-07-14
I too am in the habit of using a seperate partition for /boot. However, with the size of my hard drives, I allocate the first 500MB to /boot and I never run out of space. I usually pu the /boot partition first on the drive, then Windows, then linx swap, then my linux partitions and this has worked very well for me. I know it's alot to suggest a reinstall to repartition your drives, but unless you are really hurting for disk space, just give /boot plenty of space up front.

---

### Post by zitch on 2006-07-14
> **garba said:**
> all I can say is I can't understand why people insist on setting up a separate boot partition, 9 cases out of 10 it's totally pointless, reminds me of the /usr/src/linux symlink thing

Actually, there's a real reason in the past for setting up a separate boot partition; older BIOS couldn't boot from files that were past the first 1024 cylinders (about 8.4 Gigs into the drive, if I remember).  So, for that reason, a small /boot partition is created at the beginning of the drive to guarantee that the system will boot.  I remember having to work around this limitation with an old 486 DX2 running Slackware on a 40-gig drive many years back (1999?).  

Now-a-days?  With modern hardware on a system to be used as a desktop for a newbie I agree that it's largely pointless to have a separate /boot partition (Unless you're doing something special, like LVM or software RAID).  I *do* recommend having a separate /home partition, only if you need to re-install the O.S. (or even install another linux distro!), you can keep the data you've accumulated in your home directories.

I'll now finish up with what my /boot directory looks like after cleaning out older kernels (I have a habit of keeping an older kernel around for a few days before I remove it while I run on the newer one.): ```
$ ls -lia /boot
total 9493
    2 drwxr-xr-x  4 root root    1024 2006-07-14 15:13 .
    2 drwxr-xr-x 22 root root    4096 2006-07-14 15:13 ..
   17 -rw-r--r--  1 root root  265781 2006-07-07 16:23 abi-2.6.15-26-686
   14 -rw-r--r--  1 root root   69706 2006-07-07 14:45 config-2.6.15-26-686
12050 drwxr-xr-x  2 root root    1024 2006-07-14 15:13 grub
12062 -rw-r--r--  1 root root 6973231 2006-07-11 17:33 initrd.img-2.6.15-26-686
   11 drwxr-xr-x  2 root root   12288 2006-05-29 04:12 lost+found
   16 -rw-r--r--  1 root root   94760 2005-10-25 05:32 memtest86+.bin
   18 -rw-r--r--  1 root root  735461 2006-07-07 16:23 System.map-2.6.15-26-686
   15 -rw-r--r--  1 root root 1517225 2006-07-07 16:23 vmlinuz-2.6.15-26-686

```

---

### Post by garba on 2006-07-16
> **zitch said:**
>   

Now-a-days?  With modern hardware on a system to be used as a desktop for a newbie I agree that it's largely pointless to have a separate /boot partition (Unless you're doing something special, like LVM or software RAID). 


indeed, those howto's keep telling people to setup a separate /boot partition, even if it's toally useless with modern hardware, and should there be need for it, they usually omit the most important bit: that partition is to be placed at the BEGINNING of the HD to actually be useful.

---

### Post by Mguel on 2006-08-16
> **garba said:**
> then amend the /boot/grub/menu.lst to make it point to the new location of the kernel/initrd files...

Finally got time to work on this. I have some questions, and as I'm afraid of spoilling my boot process I prefer to ask first ;)

I'm not sure about how to make menu.lst point to the bootnew folder. I have:
```
title        Ubuntu, kernel 2.6.15-26-386
root        (hd1,6)
kernel        /vmlinuz-2.6.15-26-386 root=/dev/hdb6 ro quiet splash
initrd        /initrd.img-2.6.15-26-386
savedefault
boot
``` Should I leave it:
```
title        Ubuntu, kernel 2.6.15-26-386
root        (hd1,6)
kernel        /vmlinuz-2.6.15-26-386 root=/dev/hdb6 ro quiet splash
initrd        /initrd.img-2.6.15-26-386
savedefault[COLOR=Red]
**bootnew**[/COLOR]
``` or is it someplace else I should change the path?

And the other question:



> **garba said:**
> sudo grub-install <yourdev> --root-directory=/bootnew
In my case (considering I have root mounted on /dev/hdb6) this would be:
```
sudo grub-install [COLOR=Red]**/dev/hdb6**[/COLOR] --root-directory=/bootnew
``` right?

Sorry for the silly questions, but I prefer to ask and don't do trial and error with this, since I'm not too confident yet with linux.


Thanks,
Mguel


PS: I also have a another question related to the topic regarding the /home partition. I first installed Ubuntu 5.10 and I had a separate /home partition. When upgrading to Dapper (Kubuntu) I made a clean install and wanted to keep and use my /home partition, but on the install process I couldn't make Kubuntu to use the /home partition without reformating it, hence loosing all my config files. And that was why I installed Dapper with /home on the same partition as root. A few days ago I moved /home to it's own partition, but I'm not sure how to mount /home on it, without the need of formating it, on the future when I install a new Kubuntu version or another distro to try out.

PSS: And the last question: if you have more than one linux distro installed, wouldn't it be better to have /boot on it's own partition? (I'm thinking that maybe when installing grub on the "second distro", it could mess my "first distro" root dir for instance). Or when having more than one linux from the second install on you don't install grub and just manually add the new distros to menu.lst?

Thanks

---

### Post by garba on 2006-08-17
find out which device your root partition resides on through:

cat /proc/mount
i
I seem to understand it's hdb6, hence your menu.lst should look like:

title Ubuntu
kernel        /bootnew/vmlinuz-2.6.15-26-386 root=/dev/hdb7 ro quiet splash
initrd        /initrd.img-2.6.15-26-386

note the leading "/boot", since the boot files now reside in a subdir within the filesystem on hdb6

now you have to tell grub to adjust the boot chain as to make the MBR point to the boot dir, from a terminal issue:

grub-install --root-directory=/bootnew /dev/hdb

and NOT hdb6

PS question: move the the file in /home out of the way, mount your partition on /home and then move the files back in

PPS question: yes, that's a good point, problem is that if the kernel provided by distro a happens to have the same name as the one provided by distro b then some problem might arise

hope this answered your questions! regards, andre

---

### Post by Mguel on 2006-08-20
> **garba said:**
> title Ubuntu
kernel        /bootnew/vmlinuz-2.6.15-26-386 root=/dev/hdb7 ro quiet splash
initrd        /initrd.img-2.6.15-26-386

note the leading "/boot", since the boot files now reside in a subdir within the filesystem on hdb6

now you have to tell grub to adjust the boot chain as to make the MBR point to the boot dir, from a terminal issue:

grub-install --root-directory=/bootnew /dev/hdb

and NOT hdb6

Thanks!

Now that I have some time I tried to do it, but get some errors with grup-install command.

First I changed the menu.lst as you suggested:
kernel        /bootnew/vmlinuz-2.6.15-26-386 root=/dev/hdb[COLOR=Red]**6**[/COLOR] ro quiet (hdb6 is my root I believe you made a typo error writing hdb7)

Runned: 
```
$ sudo grub-install --root-directory=/bootnew /dev/hdb
Probing devices to guess BIOS drives. This may take a long time.
The file /bootnew/boot/grub/stage1 not read correctly.
``` 
Since I copied /boot to /bootnew and not /bootnew/boot, I thought that that might be the error not reading the stage1 file. So moved content of bootnew to /bootnew/boot, then rerun the command: (I should also change menu.lst to  kernel        /bootnew/boot/vmlinuz-2.6.15-26-386 root=/dev/hdb[COLOR=Red]**6**[/COLOR] ro quiet, right?)

```
$ sudo grub-install --root-directory=/bootnew /dev/hdb
The file /bootnew/boot/grub/stage1 not read correctly.
``` 
So now I'm not sure if grub boot chain was modified, and don't know if its safe to reboot neither.

---

### Post by garba on 2006-08-20
my mistake miguel sorry, I should be banned from this planet because of that --root-directory=/bootnew thing :mrgreen: okie let's go over it one more time:

- boot from the live cd, this way things will be easier
- mount your root partition somewhere, for example in /mnt
- now create the /boot dir in /mnt and copy all the files from your previous boot partition (which you'll have to mount somewhere of course)
- from a terminal type grub-install --root-directory=/mnt /dev/hdb
- amend your menu.lst file

and you're all set, if you still have troube i can ssh into your machine and do it myself, regards, andre

---

### Post by Mguel on 2006-08-20
Done!

Thanks a lot for your help.

I followed now your intructions with no problem, the only different things that I made were:

grub-install --root-directory=/mnt/hdb6 /dev/hdb
I didn't touch the menu.lst
And I modified fstab so hdb7 wasn't mounted on /boot on the new reboot.

Cheers,
Mguel

---

### Post by garba on 2006-08-20
cheers! i'm glad you finally managed to make it, grub can be a pain sometimes ;) regards, andre

---

