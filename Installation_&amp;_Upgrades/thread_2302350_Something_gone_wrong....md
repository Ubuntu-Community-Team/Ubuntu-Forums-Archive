---
title: "Something gone wrong..."
date: 2015-11-09
forum: Installation &amp; Upgrades
---

### Post by Dmitry_Samokhin_Ic on 2015-11-09
Hey guys, just had to update my nodejs server on VPS and decided to update all the packages at once as most of them are several months old (Its a small private VPS for testing so i dont worry about it). And i run apt-get update and then apt-get dist-upgrade (like i said i dont worry about it :D). Now my package manager bump into a strange problem:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-server : Depends: linux-headers-server (= 3.2.0.92.106) but 3.2.0.93.107 is installed
E: Unmet dependencies. Try using -f.

```

The thing is if i try to apt-get -f install as it "suggest" (yeah i know its not actually a suggestion), it fails, and if i try apt-get upgrade/dist-upgrade again it just returns same error as above. If im not wrong that is a kernel package for server, and it actually tries to downgrade it... I dont know what package is causing these (and i actually dont want to know unless i need in order to fix server - i already planned clean system reinstall even before these)

sudo apt-get -f install
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-image-3.2.0-89-generic linux-headers-3.2.0-86-generic
  linux-headers-3.2.0-29 linux-headers-3.2.0-85 linux-headers-3.2.0-86
  linux-headers-3.2.0-87 linux-headers-3.2.0-88 linux-headers-3.2.0-89
  linux-headers-3.2.0-29-generic linux-headers-3.2.0-89-generic
  linux-image-3.2.0-87-generic linux-headers-3.2.0-87-generic
  linux-image-3.2.0-85-generic linux-image-3.2.0-88-generic
  linux-headers-3.2.0-85-generic linux-headers-3.2.0-88-generic
  linux-image-3.2.0-86-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-server linux-server
The following packages will be upgraded:
  linux-image-server linux-server
2 upgraded, 0 newly installed, 0 to remove and 50 not upgraded.
4 not fully installed or removed.
Need to get 0 B/4,036 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]?
Setting up linux-image-3.2.0-92-generic (3.2.0-92.130) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.2.0-93-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-92-generic /boot/vmlinuz-3.2.0-92-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-92-generic /boot/vmlinuz-3.2.0-92-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-92-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-92-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-92-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-92-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-93-generic (3.2.0-93.133) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-3.2.0-92-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-93-generic /boot/vmlinuz-3.2.0-93-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-93-generic /boot/vmlinuz-3.2.0-93-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-93-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-93-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-93-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-93-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-3.2.0-92-generic; however:
  Package linux-image-3.2.0-92-generic is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.2.0.92.106); however:
  Package linux-image-server is not configured yet.
 linux-server depends on linux-headers-server (= 3.2.0.92.106); however:
  Version of linux-headers-server on system is 3.2.0.93.107.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        Errors were encountered while processing:
 linux-image-3.2.0-92-generic
 linux-image-3.2.0-93-generic
 linux-image-server
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

By the way i use 64bit Ubuntu Server 12.04
If you need any other logs just specify path to a file and what to look for (logs are going way back to when os is installed)
Some softwares i have installed are lamp,node,sftpd,fail2ban,bind9 - not used for anything atm,youtube-dl,c/c++ compilers and everything that goes with it + more libraries only for them. There are two small game servers but they are not installed with package manager (downloaded directly and sitting in users home dir)

---

### Post by Dmitry_Samokhin_Ic on 2015-11-09
Okay after searching forums and google i MAYBE found problem. My boot partition is full.
```
Filesystem              Size  Used Avail Use% Mounted on/dev/mapper/vps01-root   29G  6.7G   21G  25% /
udev                    489M   12K  489M   1% /dev
tmpfs                   100M  280K  100M   1% /run
none                    5.0M     0  5.0M   0% /run/lock
none                    498M  4.0K  498M   1% /run/shm
/dev/sda1               228M  225M     0 100% /boot
```

But now my problem is how to empty it (I know i need to remove old packages with [COLOR=#111111][FONT=Consolas]sudo apt-get purge linux-image-*version*-generic[/FONT][/COLOR] ) But problem is when i do that i run into the same error like in first post:

command: sudo apt-get purge linux-image-3.2.0-29-generic   (oldest one)
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-server : Depends: linux-headers-server (= 3.2.0.92.106) but 3.2.0.93.107 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by grahammechanical on 2015-11-09
Ah, but did it remove linux-image-3.2.0.29-generic?

---

