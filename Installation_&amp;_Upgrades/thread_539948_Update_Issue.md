---
title: "Update Issue"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by royalgfx on 2007-08-31
Just installed 7.04 and then I updated the system.

It asked for a reboot. Did so.

Upon rebooting, it froze at the loading screen, then reverted to this:

> udevd-event[1938]: run_program: '/sbin/modprobe' abnormal exit

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in Shell (ash)
Enter 'help' for a list of built in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

Thanks! Sorry to be n00b.

Also, I press alt-cntrl-f1 up to f7, as i read it in another post and it read:
> 
Starting up ...
Loading, please wait...
usplash: Setting mode 1024 x 768 failed
usplash: Using mode 800x600
              Check root= bootarg cat /proc/cmdline
              or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/5bf53e3b-368d-4681-b234-19b3a61a60cb does not exist. Dr
opping to a shell!


Ubuntu was running just perfectly until the installation of the updates, and it was just after the restart that it wouldn't work.

I can't tell you much bout the hardware of the PC as it was given to me. I know that it's old, and has 256mb of ram and a 10gb harddrive, but it was running PERFECTLY before the updates.

---

### Post by Pumalite on 2007-08-31
Try Ctrl+Alt+F1 to get a command line, if so, then try first 'startx'. If not, then sudo dpkg-reconfigure xserver-xorg. Accept most fefaults, choose 'vesa ' as thr driver. Then: startx
If none of this works, here is some reading for you:

[http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)

---

### Post by diatribe on 2007-08-31
there is a problem with your /etc/fstab, it is not recognizing one of your drives

---

### Post by Pumalite on 2007-08-31
Or your menu.lst was changed by the update; in that case if no command line: boot with live CD, mount your partition ( filesystem) at the terminal: sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sdx /media/ubuntu ( x known by you)
cat boot/grub/menu.lst
cat /etc/fstab
sudo fdisk -l ( small L)
blkid
Post them. Lets compare UUID's

---

### Post by royalgfx on 2007-09-01
> **Pumalite said:**
> Or your menu.lst was changed by the update; in that case if no command line: boot with live CD, mount your partition ( filesystem) at the terminal: sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sdx /media/ubuntu ( x known by you)
cat boot/grub/menu.lst
cat /etc/fstab
sudo fdisk -l ( small L)
blkid
Post them. Lets compare UUID's


hey, thanks for your help.

i couldn't get a command line, so im rebooting from disk.

i'm ******* new as **** to ubuntu and linux so apologies for all this.

im loading it from the cd, but what do you mean by X known by me? What is x?

---

### Post by Pumalite on 2007-09-01
If you have one drive, then: sda1, sda2, sda3, etc; where 'x' can be 1 or or2 or 3. Sudo fdisk -l will show partitions, formats and bootflags, among other things. You should know where you installed your system: sda1, sda2, sda3?

---

### Post by royalgfx on 2007-09-01
> **Pumalite said:**
> Or your menu.lst was changed by the update; in that case if no command line: boot with live CD, mount your partition ( filesystem) at the terminal: sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sdx /media/ubuntu ( x known by you)
cat boot/grub/menu.lst
cat /etc/fstab
sudo fdisk -l ( small L)
blkid
Post them. Lets compare UUID's


Hmm, yeah, i am running my cd from the live cd.

internets working and all...

i open terminal and type

sudo mkdir /media/ubuntu

and it says...

mkdir: cannot create directory '/media/ubuntu already exists...

So then i type:

sudo mount -t ext3 /dev/sda1/media/ubuntu

and comes up with 

Usage: mount - v             :print version
            mount -h              : print this help

etc...

Help? Thanks!

---

### Post by Pumalite on 2007-09-01
copy and paste this: sudo mount -t ext3 /dev/sda1 /media/ubuntu
(there is a space between sda1 and /media)

---

### Post by royalgfx on 2007-09-01
> **Pumalite said:**
> copy and paste this: sudo mount -t ext3 /dev/sda1 /media/ubuntu
(there is a space between sda1 and /media)

Done.

it replies with:

mount: /dev/sda1 already mounted or /media/ubuntu busy
mount: according to mtab, /dev/sda1 is already mounted on /media/ubuntu

check your pm inbox pumalite.

---

### Post by Pumalite on 2007-09-01
If your filesystem is mounted; then post: fstab, menu,lst, fdisk -l (small L).Also blkid

---

### Post by royalgfx on 2007-09-01
> **Pumalite said:**
> If your filesystem is mounted; then post: fstab, menu,lst, fdisk -l (small L).Also blkid

I typed all that in as a whole...and it says

bash: command not found.

i typed them in seperately, and command not found...also

i type in blkid
and it does nothing.

---

### Post by Pumalite on 2007-09-01
My fault. These are the commands:
sudo fdisk -l (small L)
cat /boot/grub/menu.lst
cat /etc/fstab
blkid
Copy and paste in your post.

---

### Post by royalgfx on 2007-09-01
> **Pumalite said:**
> My fault. These are the commands:
sudo fdisk -l (small L)
cat /boot/grub/menu.lst
cat /etc/fstab
blkid
Copy and paste in your post.

ok...i got this:
> 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 10.1 GB, 10110320640 bytes
255 heads, 63 sectors/track, 1229 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1171     9406026   83  Linux
/dev/sda2            1172        1229      465885    5  Extended
/dev/sda5            1172        1229      465853+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
ubuntu@ubuntu:~$ blkid
ubuntu@ubuntu:~$ 

---

### Post by Pumalite on 2007-09-01
You don't seem to have your filesystem mounted. You are getting stuff from the Live CD.

---

### Post by royalgfx on 2007-09-01
Well, I am currently running Ubuntu from the Live CD cause I can't load the GUI running from the hard disk cause it posts my original error.

And I cant enter this script from there either.

---

### Post by Pumalite on 2007-09-01
In Live CD you can actually mount your filesystem with a double click in Nautilus (Places>Home Folder)

---

### Post by royalgfx on 2007-09-01
> **Pumalite said:**
> In Live CD you can actually mount your filesystem with a double click in Nautilus (Places>Home Folder)

Ok.

I'm on the live cd. I open Nautilus. On the left it has places. 

Desktop.
File System.
Floppy Drive.
Disk. 

I right click on them all.

File system has no option to mount. Only Remove, Rename.
Floppy disk has the option to mount, but I tried it, and it wouldn't work.
Disk, has the option to unmount. So I did that...and it became 9.0GB VOLUME.

I mounted it again, and it became disk again.

How do I fix this so that I can boot Ubuntu without a Live CD and so that it doesn't freeze on start up!

---

### Post by Pumalite on 2007-09-01
From what you tell me, you managed to mount your filesystem. Change menu.lst back ( with instructions on my posts), or backup all your data and do a fresh install. If you decide to pursue finding the problem, I need all the data that I ask you for some posts back.

---

### Post by royalgfx on 2007-09-01
> **Pumalite said:**
> From what you tell me, you managed to mount your filesystem. Change menu.lst back ( with instructions on my posts), or backup all your data and do a fresh install. If you decide to pursue finding the problem, I need all the data that I ask you for some posts back.

I told you. the cat boot grub menu.lst command you gave me doesn't do anything!

the terminal tells me there is no such file or directory!!!

if i do a fresh install, then it will work, but after the install....i will install the updates...and i will probably get the same issue again!

---

### Post by royalgfx on 2007-09-01
> **Pumalite said:**
> From what you tell me, you managed to mount your filesystem. Change menu.lst back ( with instructions on my posts), or backup all your data and do a fresh install. If you decide to pursue finding the problem, I need all the data that I ask you for some posts back.

Ok. Here is the ENTIRE story.

I have an old PC. 

I don't know much about it. 

It has 10gb of space, and is 256mb of ram.

I had XP on it. 

I didn't want XP.

I installed Ubuntu 7.04 with a Live CD.

I installed it perfectly, and could run Ubuntu 7.04 without a Live CD.

I used Ubuntu and connected to the Internet and it worked fine.

I decided to install the necessary Updates.

I installed them and once they were installed, Ubuntu asked me to Restart my system.

I restarted the computer, and when it hit the GUI Ubuntu loading screen with the loading bar, it froze and after 3 minutes it did this:

> udevd-event[1938]: run_program: '/sbin/modprobe' abnormal exit

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in Shell (ash)
Enter 'help' for a list of built in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

I then pressed CTRL+ALT+F1 and it got this:
> Starting up ...
Loading, please wait...
usplash: Setting mode 1024 x 768 failed
usplash: Using mode 800x600
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/5bf53e3b-368d-4681-b234-19b3a61a60cb does not exist. Dr
opping to a shell!

So...I put in the LIVE CD, and ran Ubuntu off the Live CD.

While Ubuntu was running off the Live CD, I did all those commands you told me, and my disk is now mounted apparantly. As when I right click on it...it has the option to "unmount".

So...I turned off my computer, and took out the Live CD, and booted up my computer again...

and the Ubuntu loading screen froze again, and gave me the same message as before:

> udevd-event[1938]: run_program: '/sbin/modprobe' abnormal exit

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in Shell (ash)
Enter 'help' for a list of built in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

---

### Post by royalgfx on 2007-09-01
bump.

---

### Post by Pumalite on 2007-09-01
With your specs, you should install Alternate CD.

---

