---
title: "[SOLVED] How to migrate the primary hard disk?"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by craigni on 2008-10-30
Hi Ubuntu gurus.  I'm a longtime Fedora user, and am now migrating my main machine to Ubuntu.  I typically install a new test system on a test hard disk, and then when I've decided to migrate, move the system on the test hard disk to my "real" hard disk.  I know how to do this for Fedora (I'll put a very limited system including grub on the real hard disk, then with a rescue disk rsync the test disk to the real disk, then turn on SELINUX,) but don't know how to do this for Ubuntu.

Is there an equally simple (or simpler) way to migrate an Ubuntu system (I'm using 8.04) from one hard disk to another?

Many TIA,
Craig

:popcorn:

---

### Post by lemming465 on 2008-11-01
You should be able to migrate an Ubuntu system with rsync fairly well, yes.  If you are handy with grub-install you could probably skip the minimal install first.  If you need a minimal install, try a server CD.  Though there shouldn't be any particular issue with overwriting a regular desktop install.

The other tricky point to watch out for on the migration, besides redoing /boot/grub/menu.lst, is /etc/fstab.  Ubuntu by default identifies the root filesystem by UUID.  You'll have to edit the migrated /etc/fstab to specify the new root filesystem.  If you migrated the grub menu.list you might have the same issue in there too.  It's OK to replace the UUID with /dev/sda1 or whatever, or you can find the new UUID with *sudo blkid*

---

### Post by craigni on 2008-11-01
Thanks--I tried all last night to rsync to the new disk and install grub, but all I kept getting was kicked into an ash shell.  These are the basic steps I tried:

1. fdisk new disk and partition and format with ext3.  rsync then install grub (should I have made two partitions?  If so, how to size?)

2. minimal system install, then rsync.  I see your point about /etc/fstab--I could try to just restore the freshly made one after rsyncing, as I see your point about the labels.

I'd really like to hammer this down.  Right now I'm bringing up the new disk by hand, rsyncing only /home, and it's taking a lot of time.  I'm leery to have an ubuntu system that's a pain to restore, even though I'm seeing some real advantages over fedora at this point.

Again, thanks,
Craig

---

### Post by caljohnsmith on 2008-11-01
One really easy method you could use from your Live CD (so that nothing is mounted), is to open up System > Admin > Partition Editor (gparted), and use gparted to copy your entire Ubuntu partition from one HDD to the other. I'm fairly certain that will preserve the UUID of the partition, so you wouldn't have to edit fstab and your menu.lst. You would have to take a few steps to install Grub to the MBR of the new drive and have it point to your new Ubuntu partition, but that's quick and easy. And when you go to boot into the newly copied Ubuntu, be sure to disconnect your other drive since the UUIDs will be the same, and it could confuse Ubuntu.

I've also successfully used your method of copying the entire file system from one partition to another, so I know that works; but as lemming465 pointed out, you'll have to modify your fstab, menu.lst, and also /etc/initramfs-tools/conf.d/resume if your swap partition UUID changes too (and then you'll need to update the initrd images). And also you would need to install Grub to the MBR of the new disk and point it to your new Ubuntu partition for its boot files. 

Anyway, let us know what you decide to do, and I'll be happy to provide more specifics if you want them; I just don't want to waste typing it all out until we know which method you decide to use. :)

---

### Post by craigni on 2008-11-01
Wow, thanks for that incredible reply.  One of the things I'm really happy about migrating to ubuntu is the user community and ubuntuforums--as a fedore user I've trolled the ubuntu forum many times looking for solutions, and now it's really nice to be actually using it "for real" :)

What I really want to do is two things.  One is to clone the test drive onto the primary drive, and your instructions are excellent.  Question: when I partition the drive, do I just put in one partition?

The second, which is becoming more compelling as I fully migrate to ubuntu, is to have an easily restorable backup.  I use the rsnapshot script to back up using rsync to a backup drive, and I'd like to easily restore if I change my primary hard disk or if it crashes.  I've been around the block enough to have done both many times :)

Again, many thanks,
Craig

---

### Post by caljohnsmith on 2008-11-01
I should mention that if you want to do a true "clone" of your entire test drive to your primary drive so that even the MBR is copied and all partitions will be exactly the same, you could simply do:
```
sudo dd if=/dev/[COLOR="Blue"]<test drive>[/COLOR] of=/dev/[COLOR="Blue"]<primary drive>[/COLOR] bs=10M conv=notrunc
```
That does a low-level byte-for-byte copy of the entire test drive to the primary drive. Obviously the primary drive would have to be at least as big as the test drive. One advantage of that is you wouldn't even need to install Grub to the MBR of the new drive, since it will be taken care of as part of the clone process. 
> **craigni]What I really want to do is two things. One is to clone the test drive onto the primary drive, and your instructions are excellent. Question: when I partition the drive, do I just put in one partition?[/QUOTE]
I'm not sure what you mean, because if you copy the Ubuntu partition from your test drive to your primary drive, you wouldn't need to create a partition for it first on the primary drive said:**
> The second, which is becoming more compelling as I fully migrate to ubuntu, is to have an easily restorable backup. I use the rsnapshot script to back up using rsync to a backup drive, and I'd like to easily restore if I change my primary hard disk or if it crashes. I've been around the block enough to have done both many times.
OK, I guess I'm not following, but what is your question about your restorable backup image? Just a thought about saving an image of the HDD to a backup drive: if you don't need to access anything in the drive image, you could bzip or gzip the image to save space, similar to:
```
sudo mount /dev/[COLOR="Blue"]<destination drive partition>[/COLOR] /mnt
sudo dd if=/dev/[COLOR="Blue"]<source drive>[/COLOR] bs=10M conv=notrunc | gzip -c > /mnt/sda.bin.gz
```
Just an idea. Anyway, let me know what you decide to do. :)

---

### Post by craigni on 2008-11-01
Thanks super again for the great reply.

```
sudo dd if=/dev/[COLOR="Blue"]<test drive>[/COLOR] of=/dev/[COLOR="Blue"]<primary drive>[/COLOR] bs=10M conv=notrunc
```

I had considered that, but the two drives are often of differing sizes.  I think I'll try the gparted strategy so that I actually know what I'm talking about when I ask questions about it :)

> OK, I guess I'm not following, but what is your question about your restorable backup image? Just a thought about saving an image of the HDD to a backup drive: if you don't need to access anything in the drive image...

Not sure if you're familiar with rsnapshot [http://rsnapshot.org/]("http://rsnapshot.org/")--it's a wrapper for rsync.  It's a really nice backup strategy as I'm often looking for files in older backups.  rsnapshot uses hard links to files that don't change, so it's really space efficient.  It's also mondo easy to set up.  So I have all of the files backed up, and I'd really like a step by step on how to restore the primary drive--I have a notes to self on fedora which looks like

0. Unplug everything except the new hard drive

1. Insert the Fedora DVD, and install a barebone OS on the new hard drive

2. Push the DVD tray back into its bay

3. During the reboot cycle, do not allow the system to reboot.  Turn off the computer, and plug in the backup drive

4. Turn on the computer (with the install disk in the DVD tray) into rescue mode, with network interface

5. chroot /mnt/sysimage
6. update Kernel by "yum update kernel"

7. mkdir /backup

8. mount -t ext3 /dev/sdb1 /backup
9. rsync -av /backup/snapshots/hourly.0/localhost/ /
10. reboot with SELinux disabled with the following instructions:
        [http://www.linuxquestions.org/questions/fedora-35/login-error-cans-start-session-due-to-internal-error-472622/](http://www.linuxquestions.org/questions/fedora-35/login-error-cans-start-session-due-to-internal-error-472622/)
        Turn off SELinux at boot time
    10.1 When the grub splash screen is displayed press any key
    10.2 Select the Linux boot choice and press the 'e' key
    10.3 Select the kernel line and press the 'e' key again
    10.4 At the end of the line add a space followed by selinux=0
    10.5 When done press the 'Enter' key followed by the 'b' key
        If you need to adjust your selinux security policy or disable selinux permanently [http://fedora.redhat.com/docs/selinux-faq-fc5/](http://fedora.redhat.com/docs/selinux-faq-fc5/)
11. After booting into the system with SELinux disabled, check /etc/selinux/config and check if the options shows the same as below:
    SELinux=enforcing
    selinuxtype=targeted....
12. Reboot
Note: it will take a while because "SELinux targeted policy relabel is required. It will take some time depending on the system"...

Now it should be good to go!

---

Again, many thanks,
Craig

---

### Post by craigni on 2008-11-06
So I'm running Ubuntu 8.10 and it looks like there's no turning back (for now) to Fedora.  So I'm really interested in making sure that I'm able to restore from my rsync backup.

Going through the procedure below, I'm getting this when I boot the restored system:

Boot from (hd0,0) ext3 {UUID here}
Starting up ...
Loading, please wait...
Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/{different UUID here} does not exist.  Dropping to a shell!

Any ideas?  It looks like I did not replace a UUID somewhere for the restored system.  Any ideas where, or how to fix this?

Here is the procedure I'm using to restore from an rsync archive:

0. Unplug everything except the new hard drive
1. Insert the Ubuntu DVD, and install a barebone OS on the new hard drive
2. Turn off the computer
3. Plug in the backup drive
4. Insert the Ubuntu DVD, and boot from the DVD (not the hard drive)
5. Applications->Accessories->Terminal
```

$ sudo mkdir /mnt/newOS
$ sudo mkdir /mnt/backup
$ sudo mount -t ext3 /dev/sda1 /mnt/newOS
$ sudo mount -t ext3 /dev/sdb1 /mnt/backup
$ sudo rsync -av /mnt/newOS/etc/initramfs-tools /mnt/backup
$ sudo cp /mnt/newOS/etc/fstab /mnt/backup
$ sudo cp /mnt/newOS/boot/grub/menu.lst /mnt/backup
$ sudo rsync -av /mnt/backup/snapshots/hourly.0/localhost/ /mnt/newOS
$ sudo rsync -av /mnt/backup/initramfs-tools/ /mnt/newOS/etc/initramfs-tools

```
Bring up another terminal
```

1$ sudo vi sudo view /mnt/backup/fstab
2$ sudo vi /mnt/newOS/etc/fstab

```
Change the UUIDs for / and swap in /mnt/newOS/etc/fstab to match /mnt/backup/fstab
```

1$ sudo view /mnt/backup/menu.lst
2$ sudo vi /mnt/newOS/boot/grub/menu.lst

```
Change the UUIDs in /mnt/newOS/boot/grub/menu.lst to match /mnt/backup/menu.lst
6. Reboot, eject DVD when prompted

Many TIA,
Craig

---

### Post by meindian523 on 2008-11-06
> **craigni said:**
> 
[/CODE]
Change the UUIDs for / and swap in /mnt/newOS/etc/fstab to match /mnt/backup/fstab
```

1$ sudo view /mnt/backup/menu.lst
2$ sudo vi /mnt/newOS/boot/grub/menu.lst

```
Change the UUIDs in /mnt/newOS/boot/grub/menu.lst to match /mnt/backup/menu.lst
6. Reboot, eject DVD when prompted

Many TIA,
Craig
I think your problem lies in "Change the UUIDs for / and swap in /mnt/newOS/etc/fstab to match /mnt/backup/fstab".AFAIK,you should be changing the UUIDs for / and swap to the ones you get by typing ```
sudo blkid
``` in Ubuntu and identifying your / and swap partitions by /dev/whatever.Now,this is by assuming that by /mnt/backup/menu.lst,you are referring to the menu.lst stored on your test drive.

And many thanks to all posters,I've followed this thread since the past week,though I knew nothing about this topic.I've learnt a lot by just reading these posts,as in the use of dd and rsync for an experiment as this. :) :guitar:

---

### Post by caljohnsmith on 2008-11-06
> **craigni said:**
> 
```

$ sudo mkdir /mnt/newOS
$ sudo mkdir /mnt/backup
$ sudo mount -t ext3 /dev/sda1 /mnt/newOS
$ sudo mount -t ext3 /dev/sdb1 /mnt/backup
$ sudo rsync -av /mnt/newOS/etc/initramfs-tools /mnt/backup
$ sudo cp /mnt/newOS/etc/fstab /mnt/backup
$ sudo cp /mnt/newOS/boot/grub/menu.lst /mnt/backup
$ sudo rsync -av /mnt/backup/snapshots/hourly.0/localhost/ /mnt/newOS
$ sudo rsync -av /mnt/backup/initramfs-tools/ /mnt/newOS/etc/initramfs-tools

```
I'm not following why you did some of the steps above; if "/mnt/backup" is the backed up file system that you want to restore, why do you use rsync to copy initramfs-tools from the new OS partition to the backed up archive? Shouldn't it be ther other way around? Same with fstab and menu.lst if I'm reading it correctly, but correct me if I'm wrong. Also, as you've written it above, it looks to me like fstab and menu.lst would be copied to the root directory of your backed up archive. Isn't that second to the last line enough to copy your backed up archive over to the New OS partition? And why are you copying over initramfs-tools separately? Also, I agree with meindian523, why aren't you using "sudo blkid" to set your UUIDs? I think you lost me, so please explain your steps. :)

---

### Post by craigni on 2008-11-06
Thanks super for the replies.

The entire archive is on /mnt/backup/snapshots/hourly.0/localhost/ .  The reason I'm copying/rsyncing /mnt/newOS/etc/initramfs-tools /mnt/newOS/etc/fstab and /mnt/newOS/boot/grub/menu.lst to /mnt/backup is to back them up so that I'll have copies that won't be overwritten by the rsync from /mnt/backup/snapshots/hourly.0/localhost/ to the new drive's root.

If I boot back up with the live CD, I get

```

ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="{UUID 1}" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="{UUID 2}" TYPE="swap" 
/dev/sdb1: LABEL="/backup" UUID="7b6b7a5d-dd68-406c-86ed-ff2ad86f7b73" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
ubuntu@ubuntu:~$ sudo mkdir /mnt/newOS
ubuntu@ubuntu:~$ sudo mkdir /mnt/backup
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /mnt/newOS
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sdb1 /mnt/backup
ubuntu@ubuntu:~$ sudo cat /mnt/newOS/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID={UUID1} /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID={UUID2} none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
...

```

Which match.

Any other ideas?

---

### Post by caljohnsmith on 2008-11-06
Did you also check if your sda1 menu.lst uses the correct UUID of sda1?

---

### Post by craigni on 2008-11-06
There are 3 entries at the end of sudo cat /mnt/newOS/boot/grub/menu.lst and they all match UUID1 from sudo blkid

But here's the weird thing--when I went to check

sudo cat /mnt/newOS/etc/initramfs-tools/conf.d/resume

it gave me UUID2--the one that matches swap--not UUID1.  I replaced resume's UUID with UUID1, rebooted with the new hard drive, got the same error, booted with the live CD, ran 

sudo cat /mnt/newOS/etc/initramfs-tools/conf.d/resume and got UUID2 again--the system had changed the UUID in that file.

Is that expected behavior, or an indication something's wrong?

---

### Post by caljohnsmith on 2008-11-06
> **craigni said:**
> There are 3 entries at the end of sudo cat /mnt/newOS/boot/grub/menu.lst and they all match UUID1 from sudo blkid

But here's the weird thing--when I went to check

sudo cat /mnt/newOS/etc/initramfs-tools/conf.d/resume

it gave me UUID2--the one that matches swap--not UUID1.  I replaced resume's UUID with UUID1, rebooted with the new hard drive, got the same error, booted with the live CD, ran 

sudo cat /mnt/newOS/etc/initramfs-tools/conf.d/resume and got UUID2 again--the system had changed the UUID in that file.

Is that expected behavior, or an indication something's wrong?
Yes, I believe that's expected behavior, because if I remember correctly, you have to run:
```
sudo update-initramfs -u -k all
```
When you are booted into sda1 in order to update all your initrd images and make your UUID change stick. But having the swap UUID wrong in the resume file should not prevent you from booting into sda1 though; that will only affect your ability to suspend your computer once you boot into sda1. Also, when you mount your new OS sda1 partition from your DVD, is the /proc directory empty? It should be. If not, I would manually delete it. That could affect your ability to boot into sda1.

---

### Post by craigni on 2008-11-06
Dumb question: how can I boot into sda1 if it keeps bombing out into an ash shell when I try to boot from that drive?

---

### Post by craigni on 2008-11-06
ubuntu@ubuntu:~$ sudo ls -al /mnt/newOS/proc
total 8
drwxr-xr-x  2 root root 4096 2008-10-20 12:27 .
drwxr-xr-x 21 root root 4096 2008-11-03 22:05 ..

---

### Post by KuroYoma on 2008-11-06
I will say that you guys are all out of my league... But that said I tend to crash my Ubuntu 2 to 4 times a month because I tend to tinker with things.  In my fustration I have start to use PING.  It is a backup system that works incredibly well and works no matter what OS you are running.  Thought I would suggest it since you were asking about backing up your HD.

[http://ping.windowsdream.com/](http://ping.windowsdream.com/)

---

### Post by craigni on 2008-11-06
Thanks for the PING link--but the really great thing about a rsnapshot/rsync backup strategy is that you can access single individual files that you may have deleted without much trouble.

We should be able to restore a linux filesystem from a full rsync backup without this kind of trouble, no?

I'm rooting around the ash shell, and I can't find update-initramfs to run it from sda1.  Any ideas?

TIA,
Craig

---

### Post by caljohnsmith on 2008-11-06
> **craigni said:**
> Dumb question: how can I boot into sda1 if it keeps bombing out into an ash shell when I try to boot from that drive?
That's not a dumb question at all, in fact that's why I made sure I mentioned that having your resume file using the wrong UUID should not prevent you from booting into Ubuntu; I didn't want you to feel like you had to do anything about it at this point. :) But it won't hurt to update your initrd images, so I guess you might as well; the way to do it without booting into sda1 is to mount the important system directories to sda1, and then "chroot" into sda1. That way it's basically like booting into sda1:
```
sudo mkdir /mnt/newOS
sudo mount /dev/sda1 /mnt/newOS
sudo mount --bind /sys /mnt/newOS/sys
sudo mount --bind /dev /mnt/newOS/dev
sudo mount --bind /proc /mnt/newOS/proc
sudo chroot /mnt/newOS /bin/bash
update-initramfs -u -k all
exit
```
But unfortunately I doubt that is going to help your booting problem.

---

### Post by craigni on 2008-11-06
Tried this: booted up with live CD, mounted new OS

$ sudo chroot /mnt/newOS
# sudo update-initramfs -u -k all

Rebooted, got exactly the same error with the weird /dev/disk/by-uuid/{UUID} does not exist.

Listed /dev/disk/by-uuid, and there are 3 UUIDs there, all corresponding to the correct UUIDs in my updated /etc/fstab.

Any clues at all what's pointing to that wrong UUID in the boot sequence?  And how to fix it?

Many TIA,
Craig

---

### Post by craigni on 2008-11-06
I wrote that last msg before seeing your post, Caljohnsmith (many thanks)--so I'll try it with your better version of "booting into sda"... :)

---

### Post by craigni on 2008-11-06
Hmmm...  Still getting the same error, bombing out into an ash shell when I boot...

Boot from (hd0,0) ext3 {UUID here}
Starting up ...
Loading, please wait...
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/{UUID that does not exist in that directory} does not exist. Dropping to a shell!

Any ideas?  Could this be a x64 bug?

---

### Post by caljohnsmith on 2008-11-06
> **craigni said:**
> 
Rebooted, got exactly the same error with the weird /dev/disk/by-uuid/{UUID} does not exist.

[COLOR="Blue"]Listed /dev/disk/by-uuid, and there are 3 UUIDs there, all corresponding to the correct UUIDs in my updated /etc/fstab.[/COLOR]

When you listed /dev/disk/by-uuid, was that from the /dev directory on your DVD, or was that in /mnt/newOS/dev/disk/by-uuid, i.e. sda1? If you have any UUIDs in your sda1 /dev/disk/by-uuid directory, I would delete them, because I believe those UUIDs are supposed to be created each time on start up, similar to how your entire /proc directory is created on start up. At least that's the way my Intrepid works, because I don't have any UUIDs in my /dev/disk/by-uuid directory unless I actually boot into Intrepid.

---

### Post by craigni on 2008-11-06
sudo mkdir /mnt/newOS
sudo mount -t ext3 /dev/sda1 /mnt/newOS
sudo ls /mnt/newOS/dev/disk
ls: cannot access /mnt/newOS/dev/disk: No such file or directory

But if I boot into sda, after it bombs out if I ls /dev/disk, by-uuid exists, and contains 3 entries which match /etc/fstab

---

### Post by caljohnsmith on 2008-11-06
I probably should have asked this sooner, but just to clarify, were you able to boot fine into the Ubuntu that you made the backup archive of?

---

### Post by craigni on 2008-11-06
:lolflag: Yes--it's a rsync full backup of a very working--shall I say beautiful--Intrepid Ibex install.  I can't go back to Fedora having become used to Intrepid Ibex, and hence my quandary--I have a method to restore Fedora from a rsync archive, but not Ubuntu.

---

### Post by craigni on 2008-11-06
Just came across

[http://ge.ubuntuforums.com/showthread.php?t=955378](http://ge.ubuntuforums.com/showthread.php?t=955378)

> rsync cannot be used to backup and restore an entire system. However, trying to backup your entire system is tedious and is not quite useful. Just reinstalling Ubuntu takes less than an hour.

Eek!  Is this true?  Why??  If so, this is clearly incorrect: > Just reinstalling Ubuntu takes less than an hour.

I have a truckload of installed programs that I would have to reinstall, and although I have the commands listed as notes to self, it takes about a day.

Why would you be able to restore an entire system with Fedora, but not Ubuntu? :confused:

---

### Post by caljohnsmith on 2008-11-06
> **craigni said:**
> Just came across

[http://ge.ubuntuforums.com/showthread.php?t=955378](http://ge.ubuntuforums.com/showthread.php?t=955378)
> rsync cannot be used to backup and restore an entire system. However, trying to backup your entire system is tedious and is not quite useful. Just reinstalling Ubuntu takes less than an hour.
Eek!  Is this true?  Why??  

The only thing I can say for sure is that using "cp -ax" to make a working backup of an entire Ubuntu partition works for me, because I've used it and know it works; from a cursory glance through the rsync man page, it looks like the "rsync -av" option is basically the same thing, so I think it should work fine. I don't believe that quote is true.

---

### Post by craigni on 2008-11-06
Well, I finally restored from the archive by being very selective about what to restore.  Here's my HOW-TO procedure for those who are interested to restore Intrepid Ibex 8.10 (should work on Hardy Heron 8.04 and other Ubuntu variants but has not been tested) from a rsnapshot / rsync full archive.  Thanks super for all of your help!

(Installing the video drivers at first may be unnecessary, but I'm in a very don't mess with success mode right now.)

```

0. Unplug everything except the new hard drive
1. Insert the Ubuntu DVD, and install a barebone OS on the new hard drive
2. Reboot, removing the DVD when prompted
3. Install system updates and video driver (icons appear in upper right hand corner of Gnome desktop)
4. Shut down, turn off computer
5. Plug in the backup drive and boot
6. Open a terminal and type
sudo mkdir /backup
sudo mount -t ext3 /dev/sdb1 /backup
sudo rsync -av /backup/snapshots/hourly.0/localhost/etc/ /etc
sudo blkid
sudo vi /etc/fstab
7. Copy the UUIDs from the output of blkid for / and swap to /etc/fstab
8. Type in a terminal
sudo vi /etc/initramfs-tools/conf.d/resume
9. Copy the UUIDs from the output of blkid for / to /etc/initramfs-tools/conf.d/resume
10. Type in a terminal
sudo apt-get install gawk
sudo update-initramfs -u -k all
sudo rsync -av /backup/snapshots/hourly.0/localhost/bin/ /bin
sudo rsync -av /backup/snapshots/hourly.0/localhost/home/ /home
sudo rsync -av /backup/snapshots/hourly.0/localhost/lib/ /lib
sudo rsync -av /backup/snapshots/hourly.0/localhost/lib64/ /lib64
sudo rsync -av /backup/snapshots/hourly.0/localhost/opt/ /opt
sudo rsync -av /backup/snapshots/hourly.0/localhost/sbin/ /sbin
sudo rsync -av /backup/snapshots/hourly.0/localhost/usr/ /usr
sudo rsync -av /backup/snapshots/hourly.0/localhost/var/ /var
11. Make the mount points in /etc/fstab
sudo mkdir /mnt/...
12. Reboot

```

---

### Post by meindian523 on 2008-11-07
So,in short,you have a working Intrepid installation on your main drive now?If so,please mark the thread solved.

---

### Post by craigni on 2008-11-07
I had wanted to test it and to see if there was a more efficient way before marking as solved, but I haven't found a more efficient way, and it appears to work in tests.  Consider this a working recipe, and I'm marking this as solved.

---

