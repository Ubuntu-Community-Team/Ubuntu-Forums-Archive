---
title: "HELP! Upgrade interrupted &amp; can't boot up"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by davek22 on 2011-05-01
First, let me explain that I am NOT a computer techy and sometime think I got in way over my head with switching to Umbuntu. Please...any advice or intructions needs to be BASIC :)

I am running Umbuntu 10.10 on my laptop (co-worker walked me through intitail install) and decided to upgrade to the "natty" upgrade. While the laptop was running the upgrade, I went to bed as it apeared it was going to take an hour or so. My wife closed the laptop lid and apparently interrupted the install.

Next morning, I went to boot up and it wouldn't. It goes to where it lists "generic" versions (each with recovery mode version)...nothing will load. When i chose one, it goes to a point of running all kinds of script or something...then saying in the last few lines "The disk drive for / is not ready yet or present". Next line: "Continue to wait; pr Press S to skip mounting or M for manual recovery". Nothing I try with those options does anything to boot.

I REALLY don't wan't to lose all my emails, files, etc. so I'm hesitant with trying to reload with a cd.

Any advice?

Thanks in advance.

---

### Post by davek22 on 2011-05-01
bump

---

### Post by odessa2 on 2011-05-01
Wow the answers keep coming in.  I have the same issue.

---

### Post by wilee-nilee on 2011-05-01
Op can you get to a command line from booting one of the recovery's if so run this command to start with it may unlock the rest of the upgrade, make sure you are plugged in to the net.
```
sudo apt-get -f install
```

@odessa2, yeah lets get you some help too, if you want, try this if it doesn't work then start a thread of your own, and give a description of when and where the fails happened altogether, ie the upgrade and now the reboot..

---

### Post by davek22 on 2011-05-02
> **wilee-nilee said:**
> Op can you get to a command line from booting one of the recovery's if so run this command to start with it may unlock the rest of the upgrade, make sure you are plugged in to the net.
```
sudo apt-get -f install
```@odessa2, yeah lets get you some help too, if you want, try this if it doesn't work then start a thread of your own, and give a description of when and where the fails happened altogether, ie the upgrade and now the reboot..

When I chose "s" for "skip mounting" during boot of generic version install, I end up getting the following:
Mountall: mounting Plymouth failed
Mountall: disconnected from Plymouth

(I tried entering the sudo command there and nothing)

Then I re-tried loading again but chose "M" for "manual install". I ended up with: "root@new-host:~#". 
I again tried entering the sudo command there and I got the following:
W: not using locking for read only locking file /var/lib/dpkg/lock
E: dpkg was interuppted, you must run 'sudu dpkg --configure -a' to correct the problem.

Any ideas?

---

### Post by davek22 on 2011-05-02
After some searching...I tried "dpkg --configure -a" & "dpkg --configure -a --force-all"but I get the following error code...

"unable to access dpkg status area: read only system" 

I'm trying:(

---

### Post by garvinrick4 on 2011-05-02
Lets see if getting into the file system in a Live Cd will work. Must have your linux install sda#
so run:
sudo fdisk -l (lower case L) and get your number.
I will use sda5 for this example use your own number: Use a Live CD (install CD using Try Ubuntu) with internet connection in upper right corner.
> E: dpkg was interuppted, you must run 'sudu dpkg --configure -a' to correct the problem. 
 System was stopped in the middle of upgrading so needs to continue the process. Copy and paste these commands in a terminal in Live CD)
                          ```
sudo mount /dev/sda5 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
 
``````
dpkg --configure -a
``````
apt-get update && apt-get upgrade
``````
exit
```                          ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
 
``````
sudo shutdown -r now
```Hopefully that got the process started again, then updated and upgraded anything else left
and exited chroot and unmounted the /root of operating System and rebooted;

---

### Post by wilee-nilee on 2011-05-02
> **garvinrick4 said:**
> Lets see if getting into the file system in a Live Cd will work. Must have your linux install sda#
so run:
sudo fdisk -l (lower case L) and get your number.
I will use sda5 for this example use your own number: Use a Live CD (install CD using Try Ubuntu) with internet connection in upper right corner.
 System was stopped in the middle of upgrading so needs to continue the process. Copy and paste these commands in a terminal in Live CD)
                          ```
sudo mount /dev/sda5 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
 
``````
dpkg --configure -a
``````
apt-get update && apt-get upgrade
``````
exit
```                          ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
 
``````
sudo shutdown -r now
```Hopefully that got the process started again, then updated and upgraded anything else left
and exited chroot and unmounted the /root of operating System and rebooted;

+1 
@davek22
This is a excellent method see if it works, just wanted to let you know since we have been working together.;)

---

### Post by garvinrick4 on 2011-05-02
Going out for a while wilee-nilee keep an eye on this thread in case chroot did not help or he
needs to update-grub. Should have ran one while in chroot just in case, can never hurt while in there, no what I mean.

---

### Post by davek22 on 2011-05-02
> **garvinrick4 said:**
> Going out for a while wilee-nilee keep an eye on this thread in case chroot did not help or he
needs to update-grub. Should have ran one while in chroot just in case, can never hurt while in there, no what I mean.

OK, I followed the instructions in your first reply. 

First problem was the sudo fdisk seemed to return 3 sda #s. Here is cut/paste:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e0b4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60618   486907904   83  Linux
/dev/sda2           60618       60802     1476609    5  Extended
/dev/sda5           60618       60802     1476608   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

2nd problem:
I chose to run the code using sda1 since it had the largest "blocks" (was that wrong?)...here is what I got:

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt && sudo mount -o bind  /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts  && sudo mount -o bind /proc /mnt/proc && sudo mount -o  bind /sys /mnt/sys && sudo cp /etc/resolv.conf  /mnt/etc/resolv.conf && sudo chroot /mnt
chroot: failed to run command `/bin/bash': Exec format error
ubuntu@ubuntu:~$ 

STILL NEED HELP :(

---

### Post by wilee-nilee on 2011-05-02
> **davek22 said:**
> OK, I followed the instructions in your first reply. 

First problem was the sudo fdisk seemed to return 3 sda #s. Here is cut/paste:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e0b4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60618   486907904   83  Linux
/dev/sda2           60618       60802     1476609    5  Extended
/dev/sda5           60618       60802     1476608   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

2nd problem:
I chose to run the code using sda1 since it had the largest "blocks" (was that wrong?)...here is what I got:

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt && sudo mount -o bind  /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts  && sudo mount -o bind /proc /mnt/proc && sudo mount -o  bind /sys /mnt/sys && sudo cp /etc/resolv.conf  /mnt/etc/resolv.conf && sudo chroot /mnt
chroot: failed to run command `/bin/bash': Exec format error
ubuntu@ubuntu:~$ 

STILL NEED HELP :(

sda1 appears to be correct and the command is as well, as far as  can tell. You can always confirm partitions and make sure correct with just opening gparted, which may need to be installed in a Ubuntu installation.

To be honest I don't know anything beyond this maybe garvinrick4 will have more ideas. 

Have you had a chance to back up what is there if you want it in case this can't be fixed?

---

### Post by garvinrick4 on 2011-05-02
```
sudo e2fsck /dev/sda1
```#Will run a check on file system.
See if it is clean: If says clean now: Try the code again:
#sda1 is right, code looks good. 
#We are mounting sda1 to /mnt and binding /dev /dev/pts
/sys and /proc to /mnt getting internet connection to /mnt and chroot /mnt so you can be
in root of operating system sda1 mounted in /mnt ,if you wanted to know what line of code does.

Lets try /media if cannot get into chroot:
if you go in live cd in terminal:
```
sudo mkdir /media/root
``````
sudo mount /dev/sda1 /media/root
```Does it mount on your desktop as name root and you can open a file system when clicked on?

---

### Post by davek22 on 2011-05-02
...just remember...I'm not a comp techy and really don't have a clue as to what I'm doing :(

I ran the first command line, got the following and stopped:

ubuntu@ubuntu:~$ sudo e2fsck /dev/sda1
e2fsck 1.41.14 (22-Dec-2010)
/dev/sda1 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)?

I TYPED NO AND TRIED THE OTHER COMMAND LINES, HERE IS WHAT I GOT:

ubuntu@ubuntu:~$ sudo e2fsck /dev/sda1
e2fsck 1.41.14 (22-Dec-2010)
/dev/sda1 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)? no

check aborted.
ubuntu@ubuntu:~$ sudo mkdir /media/root
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/root
ubuntu@ubuntu:~$

---

### Post by davek22 on 2011-05-02
GUYS...I GOT IT! I ENDED FINDING THIS POST WHICH WORKED PERFECTLY! (Thanbks to Gryall)

[http://ubuntuforums.org/showthread.php?t=1742933&highlight=upgrade+lost+power&page=2](http://ubuntuforums.org/showthread.php?t=1742933&highlight=upgrade+lost+power&page=2)

Ref:
[I]I have now  sort of fixed it maybe

I started up, selected m to get to a comand line[/I] [I]
ran
sudo mount -o remount,rw /

then was able to run[/I] [I]
dpkg --configure -a
selecting the defaults whenever given a choice.

After that it hung, I restarted and I was able to log in normally, went to update manager and was prompted to do a partial upgrade[/I] 
                                                                                                                                    *                                              Last edited by gryall; 2 Days Ago at 08:40 PM..                                                                   Reason: new info                                      *

---

### Post by garvinrick4 on 2011-05-02
> I ran the first command line, got the following and stopped:

ubuntu@ubuntu:~$ sudo e2fsck /dev/sda1
e2fsck 1.41.14 (22-Dec-2010)
/dev/sda1 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.

Do you really want to continue (y/n)?

I TYPED NO AND TRIED THE OTHER COMMAND LINES, HERE IS WHAT I GOT:

ubuntu@ubuntu:~$ sudo e2fsck /dev/sda1
e2fsck 1.41.14 (22-Dec-2010)
/dev/sda1 is mounted.  

WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage. You cannot run a fsck on a mounted partition:

---

### Post by jusis on 2011-05-04
thank you SO MUCH davek22!!!  I too had to interrupt the installation, and exactly same lines appeared afterwards on the command line while trying to recover. when I tried gryall's solution, which thanks to your above link I came to know about, all was in motion at once again, and likewise after restart all was back there!!!  thank you so much again!!  and, once again yet another reason to be happy about having ubuntu!

---

### Post by davek22 on 2011-05-06
> **jusis said:**
> thank you SO MUCH davek22!!!  I too had to interrupt the installation, and exactly same lines appeared afterwards on the command line while trying to recover. when I tried gryall's solution, which thanks to your above link I came to know about, all was in motion at once again, and likewise after restart all was back there!!!  thank you so much again!!  and, once again yet another reason to be happy about having ubuntu!

Real thanks should go to "Grayall"! I am finding this forum great for tech support but sometimes the answers are buried deep into threads and often with topic titles that are not too descriptive. Maybe "Grayall"s solution should be a sticky?

---

### Post by pcampa on 2012-05-05
The solution from *Grayall* didn't work for me: I could remount the whole file system of course but then couldn't fix my packages: my upgrade went just too far before getting interrupted and my networking was simply too spoiled to work.

Thanks *wilee-nilee*, I could restore my system and my unbacked-up data with your solution: Live CD + chroot. Thanks so much.

---

