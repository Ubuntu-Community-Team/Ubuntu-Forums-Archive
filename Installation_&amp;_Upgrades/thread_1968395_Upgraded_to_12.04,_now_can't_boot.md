---
title: "Upgraded to 12.04, now can't boot"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by DrMike on 2012-04-29
So I proceed with the upgrade for 12.04 over the internet and during the install process my computer locked while stating that it was 'restarting'. It did not respond to any command save ctrl+alt+F1 which gave me a command line to shut down my computer. Unfortunately, it no longer boots up properly. Upon start up I get a GNU GRUB version 1.99-12ubuntu5 screen with the following options:

Ubuntu, with Linux 3.0.0-17-generic
Ubuntu, with Linux 3.0.0-17-generic (recovery mode)
Previous Linux versions
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

If I choose the first option, I get a command line, but not much more. 

any suggestions?

thanks in advance!

---

### Post by darkod on 2012-04-29
If it didn't finish configuring all the packages, boot it into the command line and try:
sudo dpkg --configure -a

That should finish configuring all pending packages.

---

### Post by DrMike on 2012-04-29
thanks for the help. It's very much appreciated.

I get the follow error when I run that command:

dpkg: error: unable to access dpkg status area: Read-only file system

---

### Post by darkod on 2012-04-29
It seems it is mounting it as read only. What if you try the recovery mode entry? If you get a menu select something like Drop to root prompt. In the root prompt you don't need to put 'sudo' in front of commands. Try running the same command in recovery mode, maybe it's not read only.

---

### Post by DrMike on 2012-04-29
thanks again for the help.

I entered the recovery mode option, and go the recovery menu. I selected the root - Drop to root shell prompt option, and got the root@ command line. However when I run:

dpkg --configure -a

I still get the same error:

dpkg: error: unable to access dpkg status area: Read-only file system

---

### Post by darkod on 2012-04-29
OK. Boot with the 12.04 cd in live mode, and in terminal post the output of:
sudo fdisk -l (small L)

Lets see what is your root partition.

---

### Post by DrMike on 2012-04-29
I'm afraid I don't have a CD, so I'll have to wait until monday when I can burn one at work.

for what it's worth, when I run that command in the command line under root I get:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
units = sectors of 1 * 512 = 512 bytes
sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000aa3f0

Device      Boot   Start      End      Blocks    Id   System
/dev/sda1     *    2148    965484375  482741114  83   Linux
/dev/sda2        965484376 976773167   5644396    5   Extended
/dev/sda5        965484377 976773167   5644395+  83   Linux

---

### Post by darkod on 2012-04-29
OK, your root partition is /dev/sda1. But you will need to boot into live mode with a cd or usb stick. The idea is to enter inside your installation with chroot and then you can run commands as if you have booted your ubuntu.

Since the recovery mode is read only I can't see another option except the above.

PS. I just noticed that /dev/sda5 could potentially also be the root. But it's probably your /home partition. Would you know which is which?

---

### Post by DrMike on 2012-04-29
Sorry, I can't recall which is which.

I'll get a CD burnt and report back.

thanks!

---

### Post by DrMike on 2012-04-29
It's been suggested by someone else that I check my /etc/fstab file to verify everything is correct. 

Here's the output:

# <file system> <mount point> <type> <options> <dump> <pass>
proc  /proc  proc   novdev,noexec,nousid  0  0
# / was on /dev/sda1 during installation
UUID=33ac49be-0a52-411b-9654-4b7ccb572180 / ext4 errors=remount-ro 0  1  # /dev/sda1
# swap was on /dev/sda5 during installation
UUID=7ea419cd-c32e-476e-9928-07987e4db464 none swap sw 0 0 # /dev/sda5

---

### Post by darkod on 2012-04-29
Somehow sda5 does not have swap type right now. Since it all points out that it was swap, you can try changing the type. But I'm not sure it will let you if everything is read only and when you are not doing it from live mode. You should always have a cd or usb with ubuntu to use in live mode.

You can try something like:
swapoff
cfdisk /dev/sda

If that opens the disk partitions, select sda5, then in the menu below select Type, type 82 (that is the type for swap), hit Enter which will bring you again to the main screen. In the menu below select Write, after that Quit.

If it accepts those commands, the type of sda5 should be 82, not 83 as it is shown right now. That error might be what's holding it back.

If not, you can try all this from live mode.

---

### Post by DrMike on 2012-04-30
Hello helpful folk.

I've now got an Ubuntu CD for a re-install. I'm being asked to choose an installation type:

1) install ubuntu 12.04 alongside ubuntu 12.04
(I can apparently choose which one to startup with, but my files are not deleted)

2) erase ubuntu 12.04 and reinstall
(I loss all my documents)

3) something else.

what do I choose? I don't want to loose my documents obviously, but it seems silly to have 2 ubuntu 12.04 OSs to choose from at start-up.

thanks!

---

### Post by whiskers751 on 2012-05-01
I had the same problem!!
FIX:
```
mount -o remount,rw /dev/sd**a1** /
```
Replace the -a1 with your actual ROOT partition.

---

### Post by seventhsamurai on 2012-05-01
I installed 12.04 on an Acer Aspire Laptop and an intel iMac without any issues at all. However, I did have a similar issue after installing on my assembled Desktop PC. On all occasions, I in fact re-formatted my Ubuntu partition.

The fix is to reset the swap space. So when installing 12.04, choose the partition manually. And delete the swap space and reassign it.

Worked for me.

---

### Post by darkod on 2012-05-01
> **DrMike said:**
> Hello helpful folk.

I've now got an Ubuntu CD for a re-install. I'm being asked to choose an installation type:

1) install ubuntu 12.04 alongside ubuntu 12.04
(I can apparently choose which one to startup with, but my files are not deleted)

2) erase ubuntu 12.04 and reinstall
(I loss all my documents)

3) something else.

what do I choose? I don't want to loose my documents obviously, but it seems silly to have 2 ubuntu 12.04 OSs to choose from at start-up.

thanks!

To try and finish off the upgrade first, boot into live mode with the cd and try in terminal:
```
sudo mount /dev/sda1 /mnt
sudo chroot /mnt
dpkg --configure -a
exit
```

Also, later you will need to change the type of /dev/sda5 to 82 as I explained in my previous post.

If nothing of this works, from live mode you can open your root partition, /dev/sda1, copy all data you need to an external hdd or similar, and install over the failed 12.04.

---

### Post by DrMike on 2012-05-02
once again, many thanks darkod.

I apologize, as I clearly did not understand what you meant by 'live mode'. But I am now running 12-04 in live mode on my laptop - in fact, I'm posting this on my laptop.

I've followed the instructions you suggested. Unfortunately the pathway forward is still not clear.

now, that I'm in live mode, allow me to address your previous question.

the output of sudo fdisk -l is:


```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2148   965484375   482741114   83  Linux
/dev/sda2       965484376   976773167     5644396    5  Extended
/dev/sda5       965484377   976773167     5644395+  83  Linux
```I followed your instructions and did the following:

```
sudo mount /dev/sda1 /mnt
sudo chroot /mnt
dpkg --configure -a
```after the mount command, i was indeed able to see my old documents. So that's good!

however, the output of dpkg was:

```
root@ubuntu:/# dpkg --configure -a
dpkg: dependency problems prevent configuration of module-init-tools:
 module-init-tools depends on libc6 (>= 2.8); however:
  Package libc6 is not installed.
dpkg: error processing module-init-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-common:
 grub-common depends on libc6 (>= 2.8); however:
  Package libc6 is not installed.
dpkg: error processing grub-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libudev0:
 libudev0 depends on libc6 (>= 2.8); however:
  Package libc6 is not installed.
dpkg: error processing libudev0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-pc-bin:
 grub-pc-bin depends on libc6 (>= 2.14); however:
  Package libc6 is not installed.
 grub-pc-bin depends on grub-common (= 1.99-21ubuntu3); however:
  Package grub-common is not configured yet.
dpkg: error processing grub-pc-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mountall:
 mountall depends on libc6 (>= 2.9); however:
  Package libc6 is not installed.
 mountall depends on libudev0 (>= 151); however:
  Package libudev0 is not configured yet.
dpkg: error processing mountall (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libplymouth2:
 libplymouth2 depends on libc6 (>= 2.14); however:
  Package libc6 is not installed.
dpkg: error processing libplymouth2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpango1.0-0:
 libpango1.0-0 depends on libc6 (>= 2.14); however:
  Package libc6 is not installed.
 libpango1.0-0 depends on libglib2.0-0 (>= 2.31.8); however:
  Version of libglib2.0-0 on system is 2.30.0-0ubuntu4.
dpkg: error processing libpango1.0-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpango1.0-0:i386:
 libpango1.0-0:i386 depends on libcairo2 (>= 1.8.10-3).
 libpango1.0-0:i386 depends on libglib2.0-0 (>= 2.31.8); however:
  Version of libglib2.0-0:i386 on system is 2.30.0-0ubuntu4.
 libpango1.0-0:i386 depends on libthai0 (>= 0.1.12); however:
 libpango1.0-0:i386 depends on libxft2 (>> 2.1.1); however:
dpkg: error processing libpango1.0-0:i386 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of initramfs-tools-bin:
 initramfs-tools-bin depends on libc6 (>= 2.4); however:
  Package libc6 is not installed.
 initramfs-tools-bin depends on libudev0 (>= 147); however:
  Package libudev0 is not configured yet.
dpkg: error processing initramfs-tools-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth-label:
 plymouth-label depends on libc6 (>= 2.2.5); however:
  Package libc6 is not installed.
 plymouth-label depends on libpango1.0-0 (>= 1.14.0); however:
  Package libpango1.0-0 is not configured yet.
 plymouth-label depends on libplymouth2 (= 0.8.2-2ubuntu30); however:
  Package libplymouth2 is not configured yet.
dpkg: error processing plymouth-label (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth:
 plymouth depends on libc6 (>= 2.14); however:
  Package libc6 is not installed.
 plymouth depends on libplymouth2 (= 0.8.2-2ubuntu30); however:
  Package libplymouth2 is not configured yet.
 plymouth depends on mountall (>= 2.0); however:
  Package mountall is not configured yet.
dpkg: error processing plymouth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of upstart:
 upstart depends on libc6 (>= 2.9); however:
  Package libc6 is not installed.
 upstart depends on libudev0 (>= 151); however:
  Package libudev0 is not configured yet.
 upstart depends on mountall; however:
  Package mountall is not configured yet.
dpkg: error processing upstart (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of initscripts:
 initscripts depends on libc6 (>= 2.4); however:
  Package libc6 is not installed.
 initscripts depends on upstart; however:
  Package upstart is not configured yet.
 initscripts depends on mountall (>= 2.28); however:
  Package mountall is not configured yet.
dpkg: error processing initscripts (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of insserv:
 insserv depends on libc6 (>= 2.14); however:
  Package libc6 is not installed.
dpkg: error processing insserv (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-pc:
 grub-pc depends on grub-common; however:
  Package grub-common is not configured yet.
 grub-pc depends on grub-pc-bin (= 1.99-21ubuntu3); however:
  Package grub-pc-bin is not configured yet.
dpkg: error processing grub-pc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of busybox-initramfs:
 busybox-initramfs depends on libc6 (>= 2.11); however:
  Package libc6 is not installed.
dpkg: error processing busybox-initramfs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of friendly-recovery:
 friendly-recovery depends on upstart-job; however:
  Package upstart-job is not installed.
  Package upstart which provides upstart-job is not configured yet.
 friendly-recovery depends on upstart; however:
  Package upstart is not configured yet.
dpkg: error processing friendly-recovery (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing libc6:i386 (--configure):
 libc6:i386 cannot be configured because libc6:amd64 is not ready for configuration (current status 'half-installed')
dpkg: dependency problems prevent configuration of grub2-common:
 grub2-common depends on grub-common (= 1.99-21ubuntu3); however:
  Package grub-common is not configured yet.
dpkg: error processing grub2-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (>= 0.99ubuntu13); however:
  Package initramfs-tools-bin is not configured yet.
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.1~); however:
  Package initramfs-tools-bin is not configured yet.
 initramfs-tools depends on busybox-initramfs (>= 1:1.13.3-1ubuntu5); however:
  Package busybox-initramfs is not configured yet.
 initramfs-tools depends on module-init-tools; however:
  Package module-init-tools is not configured yet.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sysv-rc:
 sysv-rc depends on insserv (>> 1.12.0-10); however:
  Package insserv is not configured yet.
dpkg: error processing sysv-rc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libudev0:i386:
 libudev0:i386 depends on libc6 (>= 2.8); however:
  Package libc6:i386 is not configured yet.
dpkg: error processing libudev0:i386 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 module-init-tools
 grub-common
 libudev0
 grub-pc-bin
 mountall
 libplymouth2
 libpango1.0-0
 libpango1.0-0:i386
 initramfs-tools-bin
 plymouth-label
 plymouth
 upstart
 initscripts
 insserv
 grub-pc
 busybox-initramfs
 friendly-recovery
 libc6:i386
 grub2-common
 initramfs-tools
 sysv-rc
 libudev0:i386
```so it looks like I don't have all the necessary components to continue the install.

but at least I can access my files. So if nothing else, I'll copy them over to an external hard drive tomorrow, and reinstall from scratch.

thanks!

---

### Post by darkod on 2012-05-02
That procedure with chroot and dpkg was given here as a short version. I wonder if it doesn't work until you fully prepare the chroot. Instead of only one mount command before the chroot, try this four commands:
```
sudo mount /dev/sda1 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
```

After that continue with the chroot and dpkg. See if the errors go away.

---

### Post by DrMike on 2012-05-03
thanks once more for you help.

I tried adding those additional commands, but I still got the same errors. So I've decided to bite the bullet, backup my files to an external drive, and re-install ubuntu. 

so I learned a lesson: always upgrade ubuntu with a cd!

---

