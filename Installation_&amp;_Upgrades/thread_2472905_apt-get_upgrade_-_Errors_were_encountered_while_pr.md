---
title: "apt-get upgrade - Errors were encountered while processing linux-image-4.15.0-171-gen"
date: 2022-03-16
forum: Installation &amp; Upgrades
---

### Post by marchello_lippi2 on 2022-03-16
Hi all, getting below error when running apt-get upgrade: 
```

$ sudo apt-get upgrade
sudo: unable to resolve host m5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  netplan.io ubuntu-advantage-tools
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up linux-image-4.15.0-171-generic (4.15.0-171.180) ...
Processing triggers for linux-image-4.15.0-171-generic (4.15.0-171.180) ...
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-4.15.0-171-generic
Warning: couldn't identify filesystem type for fsck hook, ignoring.
/etc/kernel/postinst.d/x-grub-legacy-ec2:
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-4.15.0-33-generic
Found kernel: /boot/vmlinuz-4.4.0-134-generic
dpkg-query: error: package 'grub-legacy-ec2' is not installed
run-parts: /etc/kernel/postinst.d/x-grub-legacy-ec2 exited with return code 10
dpkg: error processing package linux-image-4.15.0-171-generic (--configure):
 installed linux-image-4.15.0-171-generic package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-4.15.0-171-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Please advise.

---

### Post by grahammechanical on 2022-03-16
I think that this message is important.

> dpkg-query: error: package 'grub-legacy-ec2' is not installed

I had to do an internet search to learn what ec2 is. Amazon AWS Elastic Compute Cloud. Apparently it uses what is now called Grub legacy which in turn uses Grub menu.lst as its configuration file. Ubuntu now uses Grub 2 which uses grub.cfg as its configuration file.

[https://www.sumologic.com/insight/what-is-aws-ec2/](https://www.sumologic.com/insight/what-is-aws-ec2/)

Amazon AWS ec2 is way out of my range of experience.

Regards

---

### Post by marchello_lippi2 on 2022-03-17
> **grahammechanical said:**
> I think that this message is important.



I had to do an internet search to learn what ec2 is. Amazon AWS Elastic Compute Cloud. Apparently it uses what is now called Grub legacy which in turn uses Grub menu.lst as its configuration file. Ubuntu now uses Grub 2 which uses grub.cfg as its configuration file.

[https://www.sumologic.com/insight/what-is-aws-ec2/](https://www.sumologic.com/insight/what-is-aws-ec2/)

Amazon AWS ec2 is way out of my range of experience.

Regards
But... how come it requires aws-ec2 related package if my instance is not related to aws?... How do I configure my system so that this package is not needed at all?

Btw, I tried to install mentioned grub ec2 package, here are details: 
```

$ sudo apt-get install grub-legacy-ec2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-legacy-doc
The following NEW packages will be installed:
  grub-legacy-ec2
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 19,4 kB of archives.
After this operation, 82,9 kB of additional disk space will be used.
Get:1 http://ua.archive.ubuntu.com/ubuntu bionic/main amd64 grub-legacy-ec2 all 1:1 [19,4 kB]
Fetched 19,4 kB in 0s (42,5 kB/s)    
Preconfiguring packages ...
(Reading database ... 111010 files and directories currently installed.)
Preparing to unpack .../grub-legacy-ec2_1%3a1_all.deb ...
Adding 'diversion of /usr/sbin/grub-set-default to /usr/sbin/grub-set-default.real by grub-legacy-ec2'
dpkg-divert: error: rename involves overwriting '/usr/sbin/grub-set-default.real' with
  different file '/usr/sbin/grub-set-default', not allowed
dpkg: error processing archive /var/cache/apt/archives/grub-legacy-ec2_1%3a1_all.deb (--unpack):
 new grub-legacy-ec2 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/grub-legacy-ec2_1%3a1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

