---
title: "unable to install any new software (Ubuntu 10.04)"
date: 2011-07-15
forum: Installation &amp; Upgrades
---

### Post by linux83 on 2011-07-15
Hello freinds,

i'm unable to install any new software and get these errors:

root@workss:~# apt-get install docky 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libmono-getoptions2.0-cil python-docky
The following NEW packages will be installed:
  docky libmono-getoptions2.0-cil python-docky
0 upgraded, 3 newly installed, 0 to remove and 1 not upgraded.
7 not fully installed or removed.
Need to get 755kB of archives.
After this operation, 3,256kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://bh.archive.ubuntu.com/ubuntu/](http://bh.archive.ubuntu.com/ubuntu/) lucid/main libmono-getoptions2.0-cil 2.4.4~svn151842-1ubuntu4 [46.0kB]
Get:2 [http://bh.archive.ubuntu.com/ubuntu/](http://bh.archive.ubuntu.com/ubuntu/) lucid-updates/universe python-docky 2.0.6-0ubuntu1 [9,278B]
Get:3 [http://bh.archive.ubuntu.com/ubuntu/](http://bh.archive.ubuntu.com/ubuntu/) lucid-updates/universe docky 2.0.6-0ubuntu1 [700kB]
Fetched 755kB in 6s (112kB/s)                                                  
Selecting previously deselected package libmono-getoptions2.0-cil.
(Reading database ... 219603 files and directories currently installed.)
Unpacking libmono-getoptions2.0-cil (from .../libmono-getoptions2.0-cil_2.4.4~svn151842-1ubuntu4_all.deb) ...
Selecting previously deselected package python-docky.
Unpacking python-docky (from .../python-docky_2.0.6-0ubuntu1_all.deb) ...
Selecting previously deselected package docky.
Unpacking docky (from .../docky_2.0.6-0ubuntu1_all.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up linux-image-2.6.32-33-generic (2.6.32-33.70) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-33-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 9: quiet: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-33-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up linux-image-2.6.32-33-generic-pae (2.6.32-33.70) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-33-generic-pae
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 9: quiet: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-33-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-2.6.32-33-generic-pae; however:
  Package linux-image-2.6.32-33-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 2.6.32.33.39); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-iNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                 No apport report written because MaxReports is reached already
                                               No apport report written because MaxReports is reached already
                             No apport report written because MaxReports is reached already
           No apport report written because MaxReports is reached already
                                                                         mage-2.6.32-33-generic; however:
  Package linux-image-2.6.32-33-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.32.33.39); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-generic-pae; however:
  Package linux-generic-pae is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
Setting up libmono-getoptions2.0-cil (2.4.4~svn151842-1ubuntu4) ...
Setting up python-docky (2.0.6-0ubuntu1) ...

Setting up docky (2.0.6-0ubuntu1) ...
Processing triggers for python-support ...
Errors were encountered while processing:
 linux-image-2.6.32-33-generic
 linux-image-2.6.32-33-generic-pae
 linux-image-generic-pae
 linux-generic-pae
 linux-image-generic
 linux-image
 linux-server
W: Duplicate sources.list entry [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_lucid_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_lucid_non-free_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@workss:~# 


what i change before getting these error only my Ram was 4G and i downgrade it to 
2 G only. i try this solution without any sucess: [http://ubuntuforums.org/showthread.php?t=1578513](http://ubuntuforums.org/showthread.php?t=1578513)

any help.

---

### Post by zvacet on 2011-07-20
You may want to resolve issue with duplicate lines in source list.Look in /etc/apt/sources.list.d and remove duplicated medibuntu lines.After that

```
sudo dpkg --configure -a
```

---

