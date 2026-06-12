---
title: "udevadm trigger is not permitted while udev is unconfigured"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by bries on 2010-09-02
Hi,
I use Parallels 5 for Mac (10.6.4). I started my Ubuntu 10.4 virtual machine and it didn't load the Ubuntu Gnome desktop. In stead I did get a command line prompt. I could login with normal username and password, rebooted again, but same result.
I tried to update the system with:
```
sudo apt-get update
sudo apt-get upgrade
```
The update went smooth, but after rebooting the system I get the message:
udevadm trigger is not permitted while udev is unconfigured

I tried to load a Live CD, but I can't boot it.
Where do I go from here?
Any advise much appreciated, :confused:

---

### Post by bries on 2010-09-02
Found a fix. Fixed problem with advice from this thread: [http://ubuntuforums.org/showthread.php?t=433710](http://ubuntuforums.org/showthread.php?t=433710)

Downloaded a fresh .iso file from Ubuntu.com. Connected the .iso image to the virtual machine and changed the prefs in order to boot from CD. 

1. Boot LiveCD
2. create /media/newroot/ and mount / on HD to it (in my case /dev/sda1)
```
sudo mkdir /media/newroot/
sudo mount /dev/sda1 /media/newroot/
```
3. chroot to /media/newroot/
```
sudo chroot /media/newroot/
```
4. update and dist-upgrade
```
sudo apt-get update
sudo apt-get dist-upgrade
```

On my machine the fix didn't work without the sudo command.

:)

---

### Post by doktorOblivion on 2010-09-08
As per the other post, running the command below does fix the issue.

[FONT="Courier New"]sudo update-initramfs -u -k <your kernel>[/FONT]

Perform an ls on /boot to see what kernel you need to supply for <your kernel>.

Though I must admit to a certain level of aggravation on two counts.
1.) Someone let's an update get through that didn't do this correctly and hosed a lot people up.
2.) The message that comes out gives you no idea what the problem is, its more or less useless.  But this is an overall problem with Linux in general.  :rolleyes:

---

### Post by AKnightintheDesert on 2010-09-14
I am trying to do this on a system that uses a software raid.  How would one do this??

---

### Post by yoramdavid on 2010-12-19
I am having the same problem. At about half way through installing, after downloading all the files needed, it tells me not enough space. But there is space, I have 128Mb free on the /boot partition and 1.5 Gb on the /Ubuntu partition.

The above solution fails at step 2. I get the following error:
mount: / is not a block device

I cannot do the initramfs update because it says it is a read-only directory.

With the chroot /media/newroot I get the error "cannot run command '/bind/bash': no such file or directory"

I tried from both a USB drive and from a CD.

Any help is welcome, thanks.

Update:
I realized a "File System" drive (folder (inode/directory) was created during this process which gets out of space.
Location: computer:///, Volume: unknown.
Is there something I am doing wrong?

---

