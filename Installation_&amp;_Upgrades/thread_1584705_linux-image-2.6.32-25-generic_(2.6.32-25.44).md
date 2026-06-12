---
title: "linux-image-2.6.32-25-generic (2.6.32-25.44)"
date: 2010-09-29
forum: Installation &amp; Upgrades
---

### Post by nickguletskii on 2010-09-29
I have searched a lot for solutions of this problem, but there seems to be no solution that works for me.

It was time to update my installation... AS I have NEVER updated it. So I ran the update manager and launched updates. Many packages completed, but linux-image-2.6.32-25-generic (2.6.32-25.44) gave me a lot of errors. I don't ave the terminal output from the update manager, but I have info from apt-get install -f. I am using root account.

```
root@ubuntu:~# apt-get upgrade vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.32-25-generic (2.6.32-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/memtest86+.bin
User postinst hook script [/sbin/update-grub] exited with value 10
dpkg: error processing linux-image-2.6.32-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-25-generic; however:
  Package linux-image-2.6.32-25-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.25.27); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up samba-common (2:3.4.7~dfsg-1ubuntu3.2) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                        dpkg: error processing samba-common (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of samba-common-bin:
 samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however:
  Package samba-common is not configured yet.
dpkg: error processing samba-common-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of smbclient:
 smbclient depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.2); however:
  Package samba-common is not configured yet.
dpkg: error processing smbclient (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of winbind:
 winbind depends on samba-common (= 2:3.4.7~dfsg-1ubuntu3.2); however:
  Package samba-common is not configured yet.
dpkg: error processing winbind (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                                                        No apport report written because MaxReports has already been reached
                                            No apport report written because MaxReports has already been reached
                                Errors were encountered while processing:
 linux-image-2.6.32-25-generic
 linux-image-generic
 linux-generic
 samba-common
 samba-common-bin
 smbclient
 winbind
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


I am sure the update manager was doing the same as apt-get at the moment. 

Any ideas on how to solve that? Lucky me: I did a backup of my wubi virtual disk before the update. I can reverse the update at any moment. Did it two times, every time the same problem.

Thanks in advance.

---

### Post by nickguletskii on 2010-09-30
Bump... :/

---

### Post by Glaucous on 2010-10-01
Same problem, and that's all I have to add to this topic right now. :/
[http://paste.ubuntu.com/503956/](http://paste.ubuntu.com/503956/)

Edit: Now I have something more to add, fixed it by uninstalling nvidia-common (I have ATI).
Tip from this thread:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9911488](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9911488)

Probably won't help your problem though.

---

### Post by nickguletskii on 2010-10-02
Thank you for the info, but in my case it is something to do with the way grub is installed, I think...

---

