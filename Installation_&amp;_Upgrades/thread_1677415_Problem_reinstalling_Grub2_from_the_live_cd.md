---
title: "Problem reinstalling Grub2 from the live cd"
date: 2011-01-28
forum: Installation &amp; Upgrades
---

### Post by Skios on 2011-01-28
On my old laptop, I installed Ubuntu 10.04 alongside Windows XP using WUBI. This all went off without a hitch. Afterwards, I upgraded to Ubuntu 10.10. That's when I began having problems with Grub. I tried reinstalling Grub through the steps described in [this guide](http://ubuntuforums.org/showthread.php?t=1581099). Everything works fine up until the actual reinstallation of the Grub packages as described in step 4. Here's what my terminal looks like:```
ubuntu@ubuntu:~$ sudo mkdir /mnt/windows /mnt/temp
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/windows
ubuntu@ubuntu:~$ sudo mount -o loop /mnt/windows/ubuntu/disks/root.disk /mnt/temp
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf
ubuntu@ubuntu:~$ sudo chroot /mnt/temp
root@ubuntu:/# apt-get update
(meaningless crap filtered)
Reading package lists... Done
root@ubuntu:/# apt-get purge grub grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
The following packages will be REMOVED:
  grub-common* grub-pc*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 5,804kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 125245 files and directories currently installed.)
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...
root@ubuntu:/# apt-get install grub-common grub-pc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2,204kB of archives.
After this operation, 5,804kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 124967 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.98+20100804-5ubuntu3_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.98+20100804-5ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for ureadahead ...
Setting up grub-common (1.98+20100804-5ubuntu3) ...
Setting up grub-pc (1.98+20100804-5ubuntu3) ...

Creating config file /etc/default/grub with new version
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.
Generating grub.cfg ...
/usr/sbin/grub-probe: error: cannot stat `/mnt/windows/ubuntu/disks/root.disk'.
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# 
```Unfortunately that's pretty much all the info I have. Google doesn't seem to be any help at all. Any idea what I could do to fix my problem?

---

### Post by kansasnoob on 2011-01-28
If this is a Wubi install those are the wrong instructions, look here:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Please do take time to read it all but to recover booting you could just copy-n-paste these two commands using the Live CD:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```

---

### Post by Skios on 2011-01-28
> **kansasnoob said:**
> If this is a Wubi install those are the wrong instructions, look here:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

Please do take time to read it all but to recover booting you could just copy-n-paste these two commands using the Live CD:

```
sudo apt-get install lilo
```

```
sudo lilo -M /dev/sda mbr
```Thanks a lot. This at least allowed me to revert my laptop to the original state (Windows is booting but Ubuntu 10.10 isn't), and I'm sure I'll find the answers I need in the thread you linked to.

---

