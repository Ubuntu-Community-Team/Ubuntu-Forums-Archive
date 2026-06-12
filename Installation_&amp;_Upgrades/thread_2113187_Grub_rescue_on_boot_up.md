---
title: "Grub rescue on boot up?"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by boy18nj on 2013-02-06
what happened-

i cloned my ubuntu partition to new ext4 partition using dd command. deleted the old partition. rebooted laptop, then i have error grub rescue.

obviously i searched on net on grub rescue, tried everything out there, still it didn't fixed the issue. it seems it's really bad. tried boot repair tool. still it didn't helped.

i've spent almost 2 days to fix this. but can't.

Although boot repair says repaired successfully, it's not. see the pastbin output-

[http://paste.ubuntu.com/1618128/](http://paste.ubuntu.com/1618128/)

---

### Post by ahallubuntu on 2013-02-06
~

---

### Post by boy18nj on 2013-02-06
thanks for replying.

yes the copied partition shows up data.

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="TOSHIBA SYSTEM VOLUME" UUID="3E345FA1345F5ACB" TYPE="ntfs" 
/dev/sda2: UUID="7e759d52-ef42-4aa2-8b36-74c5584f482f" TYPE="ext4" 
/dev/sda4: LABEL="30-1" UUID="a87fa281-7168-4c29-95b1-de30489fbaeb" TYPE="ext4" 
/dev/sdb1: LABEL="PENDRIVE" UUID="1813-3B06" TYPE="vfat" 
/dev/sdc1: LABEL="BOOT" UUID="F2FF-0501" TYPE="vfat" 


ubuntu@ubuntu:~$ more /etc/fstab
overlayfs / overlayfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
ubuntu@ubuntu:~$ 

where should i update UUID in /etc/fstab?

---

### Post by oldfred on 2013-02-06
You probably will have to use the chroot method to reinstall grub. As you have no grub in MBR, you have a grub in the sda2 partition boot sector that is looking for core.img in sda5 which you do even have a sda5. And you are missing grub.cfg.

I would suggest once chrooted you do the full uninstall and reinstall of grub2. Boot-Repair has advanced options that help you chroot and do a full reinstall of grub.

OR:
       chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by ahallubuntu on 2013-02-06
~

---

### Post by boy18nj on 2013-02-06
no it's not WUBI install.

---

### Post by boy18nj on 2013-02-06
> **oldfred said:**
> You probably will have to use the chroot method to reinstall grub. As you have no grub in MBR, you have a grub in the sda2 partition boot sector that is looking for core.img in sda5 which you do even have a sda5. And you are missing grub.cfg.

I would suggest once chrooted you do the full uninstall and reinstall of grub2. Boot-Repair has advanced options that help you chroot and do a full reinstall of grub.

OR:
       chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)


which one should i go with?

**[COLOR=DarkRed]A. Only If You Have a Separate /boot partition. [/COLOR]**If you have a separate /boot partition run these commands. Most users do  not have a separate /boot partition and should go to the normal  partition section. 
[B][COLOR=DarkRed]
[/COLOR][/B]**[COLOR=DarkRed]C. If You Have a Normal Installation.[/COLOR]** No separate /boot partition, not a Windows/Wubi installation.

---

### Post by boy18nj on 2013-02-06
i went ahead with C option (**[COLOR=DarkRed]C. If You Have a Normal Installation.[/COLOR]** No separate /boot partition, not a Windows/Wubi installation.    &nbsp;).

Now getting this error (in my previous attempts too, got this error but was never able o resolve it)-

ubuntu@ubuntu:~$ sudo chroot /mnt/temp
chroot: failed to run command `/bin/bash': No such file or directory

when  i ran this command, it is successful

ubuntu@ubuntu:~$ /bin/bash
ubuntu@ubuntu:~$


Also tried- 
sudo cp -r /bin /lib /mnt/temp this also, didn't fixed the issue.

Any idea, so why above error?

---

### Post by boy18nj on 2013-02-06
I'm stuck here-

root@ubuntu:~# chroot /mnt/temp
chroot: failed to run command `/bin/bash': No such file or directory
root@ubuntu:~# ldd /bin/bash
    linux-vdso.so.1 =>  (0x00007fffe01cb000)
    libtinfo.so.5 => /lib/x86_64-linux-gnu/libtinfo.so.5 (0x00007fe63f5a3000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fe63f39f000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fe63efe1000)
    /lib64/ld-linux-x86-64.so.2 (0x00007fe63f7dc000)
root@ubuntu:~# 

Any help is appreciated?

---

### Post by oldfred on 2013-02-06
Did you run the first commands to create a mount point and mount it?

> sudo mkdir /mnt/temp
 sudo mount /dev/sd**XY** /mnt/temp  # Example: sudo mount /dev/sd*a5* /mnt/temp
Then run the chroot all one line:

> 
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done 
sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf  # May be required to connect to the Internet. sudo chroot /mnt/temp


---

### Post by boy18nj on 2013-02-06
> **oldfred said:**
> Did you run the first commands to create a mount point and mount it?

Then run the chroot all one line:

yes, i did ran those all commands.

---

### Post by boy18nj on 2013-02-06
I'm getting sick of this. done everything.

---

### Post by ahallubuntu on 2013-02-06
~

---

### Post by boy18nj on 2013-02-06
there is a link that explains how to fix this- [http://brucencnp.blogspot.com/2010/10/chroot-failed-to-run-command-binbash-no.html](http://brucencnp.blogspot.com/2010/10/chroot-failed-to-run-command-binbash-no.html)

but i don't get the required libraries.

---

### Post by ahallubuntu on 2013-02-06
~

---

### Post by boy18nj on 2013-02-06
> **ahallubuntu said:**
> Oh, now I understand: you need to mount the partition - say in /mnt/temp - then find the fstab there:

```
more /mnt/temp/etc/fstab
```and not the one from the live CD.

this seems to be correct, as you have expected.

root@ubuntu:/lib64# more /mnt/temp/etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=7e759d52-ef42-4aa2-8b36-74c5584f482f /               ext4    errors=remount
-ro 0       1
root@ubuntu:/lib64#

---

### Post by boy18nj on 2013-02-06
> **ahallubuntu said:**
> Can you give the output of:

```
ls /mnt/temp
```?

root@ubuntu:~# ls /mnt/temp
bin                         home            media    srv  vmlinuz
boot                        initrd.img      proc     sys  vmlinuz.old
C:\nppdf32Log\debuglog.txt  initrd.img.old  run      tmp
dev                         lib             sbin     usr
etc                         lost+found      selinux  var
root@ubuntu:~#

---

### Post by boy18nj on 2013-02-06
i never imagined, i would be stuck. 

should i now go ahead with fresh ubuntu installation?

---

### Post by ahallubuntu on 2013-02-06
OK, the directory looks OK.

It looks like the chroot worked?  You have a root prompt.  Or did you login as root to get there?

If you did the chroot successfully, then do the grub-install and update-grub commands within the chroot environment.

But you'll have to look at the UUID thing I mentioned before and /mnt/temp/etc/fstab .  Look for the line that has just "/" in it.  The UUID must match the UUID of the new partition.  Otherwise, it's not going to boot even after you've fixed Grub.

---

### Post by boy18nj on 2013-02-11
> **boy18nj said:**
> i never imagined, i would be stuck. 

should i now go ahead with fresh ubuntu installation?

I installed fresh ubuntu in 20 minutes after taking backup's.

Am happy.

Earlier wasted 2 days in GRUB ubuntu issue.

---

### Post by boy18nj on 2013-02-11
Now I'm going to create such a setup where i keep my all files in separate partition.

And Ubuntu installed in separate partition. Will create an image of it. Whenever something happens just restore the image.

This approach is little different from traditional slow changing data backup's.

---

### Post by oldfred on 2013-02-12
I know an image gets obsolete quickly. So I just plan on a new install. So then I backup the things that may change. Mostly /home which I keep in my / (root) and my data which is in separate data partitions.

       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

   Opposing viewpoint on separate data partitions - post 14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

    
       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

