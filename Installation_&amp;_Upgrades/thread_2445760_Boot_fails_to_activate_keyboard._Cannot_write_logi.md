---
title: "Boot fails to activate keyboard. Cannot write login password."
date: 2020-06-19
forum: Installation &amp; Upgrades
---

### Post by ffrr on 2020-06-19
Hello,

I cannot login, because due to an overly zealous autoremove the keyborad does not work by the time I am supposed to type my password. Up to that moment the boot proceeds automatically in the background. I can intercept it calling a recovery mode. None of the recovery menu's choices happen to be of any help. 'Repair broken packages' doesn't work, because I have no internet. 'Update grub bootloader' generates a grub configuration file of unknown content and name, finds six 'image' files in /boot and says 'done, finished'. 'Drop to root shell prompt' works with keyboard working, but no internet.

So here's my question: How can I gain control of the boot before even the recovery mode is activated. I believe I must restore internet access first thing in order to do package maintenance. There must be ways. In three hours of googling and scouring this forum I harvested 'grub terminal', 'manual boot', 'usb boot'. At this point I would greatly appreciate suggestions. 

(Ubuntu 18.04 LTS) 

Frederic

---

### Post by CatKiller on 2020-06-19
A useful troubleshooting tool (in general - I have no idea what's going on in your particular case) is to boot from a live USB and then chroot to your installation. You'll be able to run commands as if you'd booted normally, but with the supporting environment (graphics, network, web browser, keyboard in this case) of the live environment.

---

### Post by ffrr on 2020-06-19
Am I correct assuming that a live USB is a bootable USB stick? There must me tons of posts explaining how to make one. My research turned up a utility 'mkusb'. Would that serve?

What happened to my machine is that an autoremove must have erased stuff it shouldn't have. So when I started the machine the next day I couldn't log in because the keyboard was dead. When I made another try by way of the recovery menu, I didn't have an internet connection either. I gather that (at least) two devices don't get mounted.

---

### Post by CatKiller on 2020-06-19
Whatever you used to install Ubuntu will do fine. The main thing is that it's a Linux environment that isn't booting from your (currently) broken configuration so that you can fix that one.

---

### Post by ffrr on 2020-06-20
I do have a (homemade) installation DC that gives me three options: 1. install, 2. install side by side, 3. demo install. Option 1 implies losing all data. Option 2 installs on a separate partition. I could do that, but I doubt that I could access the broken partition from there, So while doing more research I have been working with option 3 (demo mode). It provides a basic working environment good enough to get at least some work done, like carrying on this correspondence. The demo mode does not change the state of the disk. I would try option 2, the installation side by side. If that din't provide access to the broken system, I could make a bootable USB stick from there. I'd find out how once I'd get there.

---

### Post by CatKiller on 2020-06-20
There's definitely no need to install side-by-side. If your existing install is so broken that you need a new one then you only need the new one.

If you've got a working environment from your live cd then you'll have access to the **mount** and **chroot** commands, which are what you need to chroot to your local installation. Then you can run the commands to undo or fix whatever it is that you've done to your install from that install, but using the keyboard and network connection of the live environment.

As an alternative, you can also use a live environment to back up your data and settings from your local installation in preparation for a fresh install. A fresh install takes maybe 20 minutes.

---

### Post by ffrr on 2020-06-20
CatKiller, Thank you for your patience. I believe we're getting there. I shall read up on chroot and be back tomorrow. Bedtime now.

---

### Post by ActionParsnip on 2020-06-20
You could boot to root recovery mode and reinstall the ubuntu-desktop package. This will install all its dependencies which should include the keyboard drivers in the GUI

---

### Post by ffrr on 2020-06-22
ActionParsnip, thanks for your advice, confirming a strategy which  have tried, unfortunately to no avail. 'Repair broken packages' fails with a bunch of "Failed to fetch https://..." messages which I take to mean that I have no network connection. 'Drop down to root prompt'" gives me a root terminal. The keyboard works. I can access the file system. It seems intact. I am root, I can type and so can do anything, except that precisely "apt-get" doesn't work without internet access. "Resume normal boot" leaves the recovery mode, but when the login prompt appears, I still have no keyboard.

I have a strong feeling that someone familiar with inner workings could fix the problem in no time at all from the root terminal, opening sockets, mounting devices, that sort of thing. I am currently improving my rather elementary system knowledge with an old book I had: "The Design of the UNIX Operating System" by Maurice J.Bach. I focus on devices and sockets. It's quite a curriculum, not to grasp in a lunch break.

I would at this point suggest that the recommendation to run "autoremove" be complemented with a warning that it may damage the system and with a recommendation how to proceed without running the risk. This current lockout of mine is now in its eighth day and beyond any doubt due to a malfunctioning autoremove. This said I emphasize that I am suggesting, not complaining. I firmly believe that open-source users owe the developers a great debt of gratitude and cannot in fairness criticize their work in any way.      

Frederic

---

### Post by CatKiller on 2020-06-22
So how did you get on with the live USB? You have both keyboard and Internet there, yes? 

From the live USB it's a two-step process; you insert your install's filesystem into some place in the filesystem tree with the **mount** command, then you change the interpretation of the root of the filesystem tree for subsequent commands with the **chroot** command.

```
sudo mkdir /mnt/*someplace* 
sudo mount /dev/*somedevice* /mnt/*someplace* 
sudo chroot /mnt/*someplace*
``` 

Then you can just run whichever commands you need normally.

---

### Post by ffrr on 2020-06-22
CatKiller, thanks again for your post. I shall definitely try your recipe. I hope I can make a USB stick from the installation CD in the demo mode, which I am using to carry on this correspondence. It works well, but doesn't provide my familiar working environment and doesn't retain any data from one session to the next (a minor inconvenience thanks to an external disk drive). I shall report on my progress.

---

### Post by CelticWarrior on 2020-06-22
Your installation media (a DVD, by the way - it doesn't fit in a CD) is enough. All you need is a live session, you DON'T need to make an USB with it.

---

### Post by CatKiller on 2020-06-22
Assuming your install disc is more recent than 2006, which is when the install disc and the live disc became the same thing, just use that. You don't need to use that to make another one. You just need a Linux environment (so that you have access to both mount and chroot) with working keyboard and working Internet. Which you have.

---

### Post by hugoparc on 2020-06-23
Tienen algun tuto similar en Español¿

---

### Post by ffrr on 2020-06-23
Thank you all. Great support!

So, here I am in a Linux 16.04 environment, created by the installation disk, option "demo", meant for playing around without touching anything outside the demo environment and utterly vanishing at shutdown. I am 'ubuntu', an assigned user name. If I do CatKiller's command sequence, here's what happens:

Note: First I have to find out the name of the inaccessible file system:

ubuntu@ubuntu fdisk -l

Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
. . .
Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 617011199 617009152 294.2G 83 Linux
/dev/sda2       617013246 625141759   8128514   3.9G  5 Extended
/dev/sda5       617013248 625141759   8128512   3.9G 82 Linux swap / Solaris
. . .

ubuntu@ubuntu:/$ ll /dev | grep sd
brw-rw----   1 root disk      8,   0 Jun 23 08:32 sda
brw-rw----   1 root disk      8,   1 Jun 23 08:32 sda1
brw-rw----   1 root disk      8,   2 Jun 23 08:32 sda2
brw-rw----   1 root disk      8,   5 Jun 23 08:32 sda5
brw-rw----   1 root disk      8,  16 Jun 23 08:33 sdb       # external USB hard disk
brw-rw----   1 root disk      8,  17 Jun 23 09:13 sdb1

Note: Now I do CatKiller's three commands:

ubuntu@ubuntu:/$ sudo mkdir /mnt/someplace      # command 1

ubuntu@ubuntu:/$ sudo mount /dev/sda /mnt/someplace       # command 2
mount: /dev/sda is already mounted or /mnt/someplace busy

ubuntu@ubuntu:/$ ll mnt/someplace      # checking
total 0
drwxr-xr-x 2 root root 40 Jun 23 16:02 ./
drwxr-xr-x 3 root root 60 Jun 23 16:02 ../

ubuntu@ubuntu:/$ sudo chroot /mnt/someplace      # command 3
chroot: failed to run command ‘/bin/bash’: No such file or directory

Note: No luck! Either the name of the file system to mount (/dev/sda) is wrong or this demo environment doesn't allow mounting and chrooting, Next I can either make a live USB stick or make  a side-by-side installation from the DVD.

---

### Post by CatKiller on 2020-06-23
> **ffrr said:**
> Note: First I have to find out the name of the inaccessible file system:

sda is the drive, rather than any of the partitions on it. From your fdisk output it looks like sda1 is the partition that you're interested in mounting.

---

### Post by ffrr on 2020-06-24
[FONT=courier new]CatKiller,

your commands worked beautifully! I managed to chroot the inaccessible file system. I don't have an internet connection, though. No internet, no package maintenance. I have a hunch that setting up a network connection from the root prompt is quite a simple task. Below the session:

-------------------------------------------------------------------------------
 
ubuntu@ubuntu:~$ sudo mkdir /mnt/someplace

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/someplace

ubuntu@ubuntu:~$ sudo chroot /mnt/someplace

root@ubuntu:/# pwd
/

root@ubuntu:/# whoami
root

root@ubuntu:/# ls -l /
total 1424
drwxr-xr-x   2 root root    4096 Jun 13 16:03 bin
drwxr-xr-x   3 root root    4096 Jun 13 16:11 boot
drwxrwxr-x   2 root root    4096 Sep  5  2017 cdrom
-rw-------   1 root root 1970176 Dec 11  2019 core
drwxr-xr-x   5 root root    4096 Aug  1  2017 dev
drwxr-xr-x 164 root root   12288 Jun 24 10:57 etc
drwxr-xr-x   3 root root    4096 Sep  5  2017 home
lrwxrwxrwx   1 root root      33 Apr 29 22:59 initrd.img -> boot/initrd.img-4.15.0-99-generic
lrwxrwxrwx   1 root root      33 Apr 29 22:59 initrd.img.old -> boot/initrd.img-4.15.0-96-generic
drwxr-xr-x  20 root root    4096 Jun 13 15:20 lib
drwxr-xr-x   2 root root    4096 Feb 21 15:26 lib64
drwx------   2 root root   16384 Sep  5  2017 lost+found
drwxr-xr-x   3 root root    4096 Sep  5  2017 media
drwxr-xr-x   3 root root    4096 Jun 24 13:28 mnt
drwxr-xr-x   2 root root    4096 Aug  1  2017 opt
dr-xr-xr-x 221 root root       0 Jun 24 14:13 proc
drwx------  14 root root    4096 Jun 24 10:03 root
drwxr-xr-x  13 root root    4096 Jun 24 13:17 run
drwxr-xr-x   2 root root   12288 Jun 13 16:03 sbin
drwxr-xr-x   5 root root    4096 Sep 24  2018 snap
drwxr-xr-x   2 root root    4096 Aug  1  2017 srv
drwxr-xr-x   2 root root    4096 Feb  5  2016 sys
drwxrwxrwt  13 root root    4096 Jun 24 14:12 tmp
drwxr-xr-x  12 root root    4096 Feb 21 18:25 usr
drwxr-xr-x  14 root root    4096 May 15 21:18 var
lrwxrwxrwx   1 root root      30 Apr 29 22:59 vmlinuz -> boot/vmlinuz-4.15.0-99-generic
lrwxrwxrwx   1 root root      30 Apr 29 22:59 vmlinuz.old -> boot/vmlinuz-4.15.0-96-generic

root@ubuntu:/# apt-get update
Err:1 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) bionic InRelease
  Temporary failure resolving 'ch.archive.ubuntu.com'
Err:2 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) bionic-updates InRelease
  Temporary failure resolving 'ch.archive.ubuntu.com'
Err:3 [http://ch.archive.ubuntu.com/ubuntu](http://ch.archive.ubuntu.com/ubuntu) bionic-backports InRelease
  Temporary failure resolving 'ch.archive.ubuntu.com'
Err:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
  Temporary failure resolving 'security.ubuntu.com'
Err:5 [https://packagecloud.io/AtomEditor/atom/any](https://packagecloud.io/AtomEditor/atom/any) any InRelease
  Temporary failure resolving 'packagecloud.io'
Err:6 [http://ppa.launchpad.net/jonathonf/vim/ubuntu](http://ppa.launchpad.net/jonathonf/vim/ubuntu) bionic InRelease
  Temporary failure resolving 'ppa.launchpad.net'
Err:7 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease
  Temporary failure resolving 'archive.canonical.com'
Reading package lists... Done
W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/bionic/InRelease](http://ch.archive.ubuntu.com/ubuntu/dists/bionic/InRelease)  Temporary failure resolving 'ch.archive.ubuntu.com'
W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease](http://ch.archive.ubuntu.com/ubuntu/dists/bionic-updates/InRelease)  Temporary failure resolving 'ch.archive.ubuntu.com'
W: Failed to fetch [http://ch.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease](http://ch.archive.ubuntu.com/ubuntu/dists/bionic-backports/InRelease)  Temporary failure resolving 'ch.archive.ubuntu.com'
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease](http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease)  Temporary failure resolving 'security.ubuntu.com'
W: Failed to fetch [https://packagecloud.io/AtomEditor/atom/any/dists/any/InRelease](https://packagecloud.io/AtomEditor/atom/any/dists/any/InRelease)  Temporary failure resolving 'packagecloud.io'
W: Failed to fetch [http://ppa.launchpad.net/jonathonf/vim/ubuntu/dists/bionic/InRelease](http://ppa.launchpad.net/jonathonf/vim/ubuntu/dists/bionic/InRelease)  Temporary failure resolving 'ppa.launchpad.net'
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/bionic/InRelease](http://archive.canonical.com/ubuntu/dists/bionic/InRelease)  Temporary failure resolving 'archive.canonical.com'
W: Some index files failed to download. They have been ignored, or old ones used instead.

-------------------------------------------------------------
[/FONT]

---

### Post by CatKiller on 2020-06-24
> **ffrr said:**
> I don't have an internet connection, though. No internet, no package maintenance.

That is definitely a pain.

> I have a hunch that setting up a network connection from the root prompt is quite a simple task.

It should just be a case of establishing a network connection from the live session: connecting to WiFi or whatever it is that you normally do. The chroot isn't like a virtual machine, it's just changing how paths and commands are interpreted from the live session.

---

### Post by ffrr on 2020-06-24
CatKiller, normally it's the boot that connects to the internet, as it also creates the graphical interface and the application icons (mysql, atom, python, firefox, thunderbird, ...) So I never had cause to connect manually and now can't fall back on routine facing this new challenge (connecting from a command prompt). 

Tomorrow I'll make a USB stick. I found a step-by-step description on "https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312". If meantime you, or anyone, would volunteer an explicit explanation of establishing an internet connection from a root prompt, I'd appreciate it very much, as I thank all for the suggestions they have bothered to offer.

Frederic

---

