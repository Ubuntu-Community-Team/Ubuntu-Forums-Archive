---
title: "Ubuntu 10.04 - Cannot install, update or upgrade"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by sahiljha84 on 2011-04-21
[B]Hello Everyone,
I am getting the following following error while installing or upgrading any software or package in Ubuntu 10.04. I followed many threads but could not figure out the right solution. I tried Synaptic too, but no success. Please guide me. Thanks in Advance.[/B]

                     p { margin-bottom: 0.08in; }  **sylar@ubuntu:~$ sudo apt-get install -f **
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
 4 not fully installed or removed. 
 After this operation, 0B of additional disk space will be used. 
 Setting up linux-image-2.6.32-31-generic (2.6.32-31.61) ... 
 Running depmod. 
 update-initramfs: Generating /boot/initrd.img-2.6.32-31-generic 
 mkinitramfs: missing loop root /dev/loop0 /sys entry 
 mkinitramfs: workaround is MODULES=most 
 mkinitramfs: Error please report the bug 
 update-initramfs: failed for /boot/initrd.img-2.6.32-31-generic 
 Failed to create initrd image. 
 dpkg: error processing linux-image-2.6.32-31-generic (--configure): 
  subprocess installed post-installation script returned error exit status 2 
 Setting up linux-image-2.6.32-31-generic-pae (2.6.32-31.61) ... 
 Running depmod. 
 update-initramfs: Generating /boot/initrd.img-2.6.32-31-generic-pae 
 mkinitramfs: missing loop root /dev/loop0 /sys entry 
 mkinitramfs: workaround is MODULES=most 
 mkinitramfs: Error please report the bug 
 update-initramfs: failed for /boot/initrd.img-2.6.32-31-generic-pae 
 Failed to create initrd image. 
 dpkg: error processing linux-image-2.6.32-31-generic-pae (--configure): 
  subprocess installed post-installation script returned error exit status 2 
 dpkg: dependency problems prevent configuration of linux-image-generic: 
  linux-image-generic depends on linux-image-2.6.32-31-generic; however: 
   Package linux-image-2.6.32-31-generic is not configured yet. 
 dpkg: error processing linux-image-generic (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of linux-generic: 
  linux-generic depends on linux-image-generic (= 2.6.32.31.37); however: 
   Package linux-image-generic is not configured yet. 
 dpkg: error processing linux-generic (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because the error message indicates its a followup error from a previous failure. 
                                     No apport report written because MaxReports is reached already 
                             Errors were encountered while processing: 
  linux-image-2.6.32-31-generic 
  linux-image-2.6.32-31-generic-pae 
  linux-image-generic 
  linux-generic 
 E: Sub-process /usr/bin/dpkg returned an error code (1) 
 

 

 

 **sylar@ubuntu:~$ sudo dpkg --configure -a **
 Setting up linux-image-2.6.32-31-generic (2.6.32-31.61) ... 
 Running depmod. 
 update-initramfs: Generating /boot/initrd.img-2.6.32-31-generic 
 mkinitramfs: missing loop root /dev/loop0 /sys entry 
 mkinitramfs: workaround is MODULES=most 
 mkinitramfs: Error please report the bug 
 update-initramfs: failed for /boot/initrd.img-2.6.32-31-generic 
 Failed to create initrd image. 
 dpkg: error processing linux-image-2.6.32-31-generic (--configure): 
  subprocess installed post-installation script returned error exit status 2 
 Setting up linux-image-2.6.32-31-generic-pae (2.6.32-31.61) ... 
 Running depmod. 
 update-initramfs: Generating /boot/initrd.img-2.6.32-31-generic-pae 
 mkinitramfs: missing loop root /dev/loop0 /sys entry 
 mkinitramfs: workaround is MODULES=most 
 mkinitramfs: Error please report the bug 
 update-initramfs: failed for /boot/initrd.img-2.6.32-31-generic-pae 
 Failed to create initrd image. 
 dpkg: error processing linux-image-2.6.32-31-generic-pae (--configure): 
  subprocess installed post-installation script returned error exit status 2 
 dpkg: dependency problems prevent configuration of linux-image-generic: 
  linux-image-generic depends on linux-image-2.6.32-31-generic; however: 
   Package linux-image-2.6.32-31-generic is not configured yet. 
 dpkg: error processing linux-image-generic (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of linux-generic: 
  linux-generic depends on linux-image-generic (= 2.6.32.31.37); however: 
   Package linux-image-generic is not configured yet. 
 dpkg: error processing linux-generic (--configure): 
  dependency problems - leaving unconfigured 
 Errors were encountered while processing: 
  linux-image-2.6.32-31-generic 
  linux-image-2.6.32-31-generic-pae 
  linux-image-generic 
  linux-generic 



**---> I tried configuring "dpkg" but got following error**


s**ylar@ubuntu:~$ sudo dpkg --configure -a**
[sudo] password for sylar: 
Setting up linux-image-2.6.32-31-generic (2.6.32-31.61) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-31-generic
mkinitramfs: missing loop root /dev/loop0 /sys entry
mkinitramfs: workaround is MODULES=most
mkinitramfs: Error please report the bug
update-initramfs: failed for /boot/initrd.img-2.6.32-31-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.32-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.32-31-generic-pae (2.6.32-31.61) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-31-generic-pae
mkinitramfs: missing loop root /dev/loop0 /sys entry
mkinitramfs: workaround is MODULES=most
mkinitramfs: Error please report the bug
update-initramfs: failed for /boot/initrd.img-2.6.32-31-generic-pae
Failed to create initrd image.
dpkg: error processing linux-image-2.6.32-31-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-31-generic; however:
  Package linux-image-2.6.32-31-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.31.37); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.32-31-generic
 linux-image-2.6.32-31-generic-pae
 linux-image-generic
 linux-generic

---

### Post by tmugan on 2011-04-22
I got the same after patching an old Ubuntu 10.04 server yesterday also.

---

### Post by sahiljha84 on 2011-04-22
So did you solve it ?

---

### Post by tmugan on 2011-04-22
No not yet.

I've filed a bug report as it seems like something wrong with the new kernel package.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/769116](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/769116)

Not exactly the same as yours now that I read it more carefully but similar.

---

### Post by candlerb on 2011-05-08
I thought I had the same problem here. Mine is an Ubuntu Server box which was originally installed as 9.10, then upgraded online to 10.04 LTS.

However, careful examination of the output showed an error in mine: "gzip: stdout: no space left on device". My 256MB /boot partition was full, with all those old kernels left around after upgrades. It would be nice if it kept only, say, the last 5.

```

$ sudo dpkg-configure
sudo: dpkg-configure: command not found
brian@www1:~/git/couchdb$ man dpkg-reconfigure
brian@www1:~/git/couchdb$ man debconf
brian@www1:~/git/couchdb$ man dpkg-reconfigure
brian@www1:~/git/couchdb$ man apt-get 
brian@www1:~/git/couchdb$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.32-31-generic-pae (2.6.32-31.61) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-31-generic-pae

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.32-31-generic-pae
Failed to create initrd image.
dpkg: error processing linux-image-2.6.32-31-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-2.6.32-31-generic-pae; however:
  Package linux-image-2.6.32-31-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured

```

In your case, I see "mkinitramfs: missing loop root /dev/loop0 /sys entry" which seems suspicious to me.

---

### Post by codedmin on 2011-05-11
Check if you have space left on harddisk or partition where have /boot installed

---

### Post by Jacolyte on 2011-05-14
I'm getting something pretty much the same in every way except I seem to have free space on /boot. Where my failure differs is:

```

/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

```

I've been able to launch a LiveCD (11.04) and mount all of my VFSes (/proc /sys /dev/pts etc.) and chroot into my root partition and mount my boot partition. I've been able to browse around freely on my disk, and can verify all of my data is still there.

Here's my output:

```

root@ubuntu:/# sudo apt-get install -f
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.32-31-generic (2.6.32-31.61) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-31-generic
Running postinst hook script /usr/sbin/update-grub.
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
User postinst hook script [/usr/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.32-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-image-2.6.32-31-generic-pae (2.6.32-31.61) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-31-generic-pae
Running postinst hook script /usr/sbin/update-grub.
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
User postinst hook script [/usr/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.32-31-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-31-generic; however:
  Package linux-image-2.6.32-31-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.31.37); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        Errors were encountered while processing:
 linux-image-2.6.32-31-generic
 linux-image-2.6.32-31-generic-pae
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I checked the [URL of the filed bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/769116") and it has been confirmed but no official fix listed :(

---

