---
title: "Installing in Hard Drive with XP on It (ntfs)"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by Pumalite on 2007-05-26
Here is my fdisk -l:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14595   117234306    7  HPFS/NTFS

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         262     2104483+  82  Linux swap / Solaris
/dev/sdb2             263        2179    15398302+  83  Linux
/dev/sdb3            2180        4998    22643617+  83  Linux

Disk /dev/sdc: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        4870    39118243+  83  Linux
ubuntu@ubuntu:~$ 

I want to install to 1st Hard Drive (ntfs) with XP on it (120GB of which 60GB are free), but Ubuntu installer doesn't see it that way; it gives me 8MB free??? Can someone help with this problem. I tried with Gparted, but wouldn't allow me to make a new partition with the free space. Winblows doesn't allow me change the partition of the disk which is one huge primary partition of 120GB. I want to install Ubuntu, but I'm stuck with this problem. I'm sure is due to my ignorance of managing partitions. Any help would be much appreciated.

---

### Post by taurus on 2007-05-26
Open a terminal and run these commands.

Applications -> Accessories -> Terminal
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/sda1 /media/windows -o nls=utf8,umask=0222
df -h
```
Post the output of the last command here.  Will see how much space left on /dev/sda1.

---

### Post by Pumalite on 2007-05-26
> **taurus said:**
> Open a terminal and run these commands.

Applications -> Accessories -> Terminal
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/sda1 /media/windows -o nls=utf8,umask=0222
df -h
```
Post the output of the last command here.  Will see how much space left on /dev/sda1.

Here is my output:

ubuntu@ubuntu:~$ sudo mkdir /media/windows
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda1 /media/windows -o nls=utf8,umask=0222
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1014M   33M  981M   4% /lib/modules/2.6.20-15-generic/volatile
tmpfs                1014M   33M  981M   4% /lib/modules/2.6.20-15-generic/volatile
varrun               1014M  108K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M  112K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
tmpfs                1014M   12K 1014M   1% /tmp
/dev/sdb2              15G   11G  3.8G  73% /media/disk-1
/dev/sdb3              22G   10G   11G  50% /media/disk-2
/dev/sda1             112G   54G   59G  48% /media/windows
ubuntu@ubuntu:~$ 

I thank you very much and I'm awaiting anxiously your answer. I have to tell you I have Suse 10.2 installed in a 40GB Drive in the same computer. What I see is that only 48% of sda1 is being used. How to make the partition with the rest???

---

### Post by taurus on 2007-05-26
Boot into XP (/dev/sda1) and defrag the harddrive a few times.  Then, boot GParted LiveCD and use it to resize your /dev/sda1.  Now, reboot with Ubuntu LiveCD and install it on the new empty space on /dev/sda.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Pumalite on 2007-05-26
Sorry Taurus, but I already tried Gparted ( check my original post ). It threw me an Error when I tried to resize: 'unable to perform operation on sda1'. What to do now???What could be the reason for this error? What is the possible workaround? Why Windoblows does not allow me to make a partition with the free space?

---

### Post by taurus on 2007-05-26
You tried gparted from Ubuntu LiveCD which is an old version.  This is _GParted LiveCD_ I am talking about.

Again, you need to boot into XP and defrag the harddrive first.

---

### Post by Pumalite on 2007-05-26
No; I tried the latest version of Gparted that I downloaded recently, and before posting already defraged with Perfect Disk and also erased all temp files and erased all folders that I didn't consider necessary and the rest I stored in external hard drive. I'm down to the bare bones.So, I still have the same questions. I'm really grateful that you are spending the time and sharing your knowledge with me, but I'm not completely unprepared. I'm completely puzzled by the problems that I confront. I thank you very much, in anticipation, for all the help you can give me.

---

### Post by taurus on 2007-05-26
Can you boot your machine with GParted LiveCD, run gparted, and take a screenshot of your desktop, showing your harddrives?

---

### Post by Pumalite on 2007-05-26
> **taurus said:**
> Can you boot your machine with GParted LiveCD, run gparted, and take a screenshot of your desktop, showing your harddrives?

I'll give it a shot. I'll get back to you ASAP. Thanks a lot.

---

### Post by Pumalite on 2007-05-26
> **taurus said:**
> Can you boot your machine with GParted LiveCD, run gparted, and take a screenshot of your desktop, showing your harddrives?

Sorry taurus; I took the screenshot and it got located in /root/gparted.png, but I couldn't find it anywhere. But any other information you want; I'll provide it. I get the feeling that the only way to do this is reformating sda1. ( That, Gparted is more than willing to perform). That would imply making an image of my XP, save it in external drive, reformatting and making 2 partitions; later reinstalling XP in one of them, but I consider that cumbersome, dangerous and something that shouldn't be

---

### Post by taurus on 2007-05-26
If the screenshot, gparted.png, is in /root, see if it's there from a terminal.

```
ls -la /root
```

---

### Post by Pumalite on 2007-05-26
> **taurus said:**
> If the screenshot, gparted.png, is in /root, see if it's there from a terminal.

```
ls -la /root
```

This is my output:

macho@linux-wwtz:~> ls -la /root
ls: cannot open directory /root: Permission denied
macho@linux-wwtz:~> su
Password: 
linux-wwtz:/home/macho # cd
linux-wwtz:~ # chmod 777 /root
linux-wwtz:~ # ls -la /root
total 332
drwxrwxrwx 33 root root  4096 2007-05-26 23:15 .
drwxr-xr-x 26 root root  4096 2007-05-26 18:27 ..
drwxr-xr-x  9 root root  4096 2007-04-08 23:00 .azureus
-rw-------  1 root root   193 2007-05-26 22:40 .bash_history
drwx------  4 root root  4096 2007-04-08 22:26 .beagle
drwxr-xr-x  2 root root  4096 2006-11-25 18:49 bin
drwx------  2 root root  4096 2007-04-08 21:43 .config
drwxr-xr-x  2 root root  4096 2007-04-08 21:43 Desktop
-rw-------  1 root root    24 2007-04-08 21:43 .dmrc
-rw-------  1 root root    16 2007-04-08 21:43 .esd_auth
drwxr-xr-x  3 root root  4096 2007-04-08 23:26 .evolution
-rw-r--r--  1 root root  1332 2005-11-23 13:06 .exrc
-rw-------  1 root root   298 2007-04-21 17:14 .fs-CNkdSb
-rw-------  1 root root   298 2007-04-26 12:39 .fs-cvNc6c
-rw-------  1 root root   298 2007-05-26 14:17 .fs-eHEtLb
-rw-------  1 root root   298 2007-04-21 17:16 .fs-f7HkKa
-rw-------  1 root root   299 2007-05-26 14:34 .fs-haJY6d
-rw-------  1 root root   298 2007-04-22 07:19 .fs-hu0Yoa
-rw-------  1 root root   298 2007-04-14 18:51 .fs-QtJsSd
-rw-------  1 root root   298 2007-05-26 14:33 .fs-VH1hBb
-rw-------  1 root root   298 2007-04-13 22:47 .fs-w5ulVb
drwxr-xr-x  2 root root  4096 2007-04-01 08:21 .fvwm
drwx------  5 root root  4096 2007-05-25 20:26 .gconf
drwx------  2 root root  4096 2007-05-25 21:37 .gconfd
drwxr-xr-x  5 root root  4096 2007-05-09 22:40 .gkrellm2
drwxr-xr-x  3 root root  4096 2007-04-08 21:43 .gnome
drwx------  8 root root  4096 2007-05-25 21:37 .gnome2
drwx------  2 root root  4096 2007-04-08 21:43 .gnome2_private
drwx------  3 root root  4096 2007-05-01 11:20 .gnupg
drwxr-xr-x  2 root root  4096 2007-04-08 21:43 .gstreamer-0.10
-rw-r--r--  1 root root   134 2007-04-08 21:43 .gtkrc-1.2-gnome2
-rw-------  1 root root     0 2007-05-25 21:37 .ICEauthority
drwxr-xr-x  3 root root  4096 2007-05-01 18:35 images
drwxr-xr-x  2 root root  4096 2007-04-01 08:21 .kbd
drwxr-xr-x  2 root root  4096 2007-04-22 14:37 .kchmviewer
drwx------  3 root root  4096 2007-04-13 18:00 .kde
-rw-------  1 root root    35 2007-05-13 17:17 .lesshst
-rwxrwxrwx  1 root root     0 2007-04-27 15:13 macho
drwx------  3 root root  4096 2007-04-11 12:47 .macromedia
drwx------  3 root root  4096 2007-04-08 21:43 .metacity
drwx------  3 root root  4096 2007-04-08 22:26 .mozilla
drwxr-xr-x  3 root root  4096 2007-05-25 21:37 .nautilus
drwx------ 10 root root  4096 2007-04-30 23:15 .opera
drwxr-xr-x  2 root root  4096 2007-04-01 14:23 .qt
-rw-r--r--  1 root root  6017 2007-05-25 20:26 .recently-used.xbel
drwxr-xr-x  2 root root  4096 2007-04-08 21:43 .skel
-rw-------  1 root root    10 2007-04-26 18:08 .smart_history
-rw-------  1 root root 59189 2007-04-27 15:41 .suse_register.log
drwx------  4 root root  4096 2007-04-12 22:13 .thumbnails
drwxr-xr-x  3 root root  4096 2007-04-08 21:43 .tomboy
-rw-r--r--  1 root root   781 2007-05-25 20:26 .tomboy.log
-rw-------  1 root root  5318 2007-05-13 13:07 .viminfo
drwxr-xr-x  2 root root  4096 2007-05-25 21:37 .wapi
-rw-r--r--  1 root root     5 2007-04-06 10:57 .windows-label
drwxr-xr-x  4 root root  4096 2007-05-04 19:48 .wine
-rw-r--r--  1 root root     0 2007-04-23 09:34 woot.txt
-rw-------  1 root root    55 2007-05-06 19:31 .xauthDK63fY
-rw-------  1 root root    55 2007-04-22 15:30 .xauthf76IV0
-rw-------  1 root root    55 2007-04-23 13:37 .xauthHpimFL
-rw-------  1 root root    55 2007-04-28 08:25 .xauthIBHdcT
-rw-------  1 root root    55 2007-05-03 16:48 .xauthnpZtSZ
-rw-------  1 root root   121 2007-05-26 14:32 .Xauthority
-rw-------  1 root root    55 2007-05-26 23:15 .xauthrt7RDA
-rw-------  1 root root    55 2007-05-10 14:42 .xauthWqUDjL
drwxr-xr-x  2 root root  4096 2007-04-08 21:47 .xine
-rw-r--r--  1 root root  7445 2007-05-25 21:37 .xsession-errors
linux-wwtz:~ # ls -la /windows/C/root
ls: cannot access /windows/C/root: No such file or directory
linux-wwtz:~ # chmod 000 /root
linux-wwtz:~ # 

I'm going to bed. I'm exausted. I'll see you tomorrow.

---

### Post by Pumalite on 2007-05-27
> **taurus said:**
> If the screenshot, gparted.png, is in /root, see if it's there from a terminal.

```
ls -la /root
```

Cleaning up Windblows and getting it ready for TrueImage+External Drive+Reformat entire Disk> 2 partitions> Installation of Ubuntu. I'll let you know guys.

---

### Post by Pumalite on 2007-05-27
> **Pumalite said:**
> Cleaning up Windblows and getting it ready for TrueImage+External Drive+Reformat entire Disk> 2 partitions> Installation of Ubuntu. I'll let you know guys.

Well Taurus, thanks a lot for your help. At the end I TrueImage Windblows and packed it in an external drive. Deleted the partition and reformated it to ext3 and then installed Ubuntu 7.04 in 1290GB. I'm now up and running and already full of stuff. Thanks again.

---

### Post by Pumalite on 2007-05-27
Hey taurus, you seem to be the boss around here or at least one of them. Do you know when they are going to fix the well known bug in 7.04 of not recognizing the CD-ROM?

---

