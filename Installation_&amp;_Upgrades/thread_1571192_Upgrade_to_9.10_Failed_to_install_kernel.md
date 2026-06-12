---
title: "Upgrade to 9.10: Failed to install kernel"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by sawatdee on 2010-09-09
I have a Dell Vostro v13 laptop that was shipped with 9.04. I upgraded to 9.10 and it told me it could not upgrade the kernel. The error message said something about a problem with the kernel file. I can still run the system and have not rebooted since the upgrade, but I need to be able to reboot eventually.

[B]The System Monitor says:
Release 9.10 (karmic)
Kernel Linux 2.6.28-19-generic[/B]

Everything I have read says that 9.10 includes kernel 2.6.31. So I am afraid to reboot now. Any ideas?

---

### Post by tyblogger5 on 2010-09-09
I suggest you back-up your data before continuing to do anything else.  Later on we can try to reboot.

---

### Post by sawatdee on 2010-09-09
I've backed up my data. It's the rebooting part I'm nervous about.

If I go into the Update Manager, it says "New Ubuntu release '10.04.1 LTS' is available", which means the Update Manager thinks I have a full 9.10 installed (even though I believe I am still running the 9.04 kernel). So my options are:
1. Upgrade to 10.04 immediately and hope it works.
2. Reboot and hope the system runs well enough to repair it.
3. Hope I backed up everything and reinstall 9.04, 9.10, or 10.04.

---

### Post by tyblogger5 on 2010-09-09
Try to run:

```
sudo apt-get install linux-image-2.6.31-14-generic
```

Copy the output and post it to the forms.

-Tariq

---

### Post by sawatdee on 2010-09-09
Here is what I get. I answered yes to create a new file for grub.


```
$ sudo apt-get install linux-image-2.6.31-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqimageblitz4 postfix liblog4j1.2-java-gcj localechooser-data liblzo2-2 libphonon4 bsd-mailx mailx qt4-qtconfig
Use 'apt-get autoremove' to remove them.
Suggested packages:
  fdutils linux-doc-2.6.31 linux-source-2.6.31
The following NEW packages will be installed:
  linux-image-2.6.31-14-generic
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 28.8MB of archives.
After this operation, 90.2MB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main linux-image-2.6.31-14-generic 2.6.31-14.48 [28.8MB]
Fetched 28.8MB in 28s (1,025kB/s)                                                                                                                                      
Selecting previously deselected package linux-image-2.6.31-14-generic.
(Reading database ... 277019 files and directories currently installed.)
Unpacking linux-image-2.6.31-14-generic (from .../linux-image-2.6.31-14-generic_2.6.31-14.48_i386.deb) ...
Done.
Setting up linux-image-2.6.31-22-generic (2.6.31-22.63) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-22-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/vmlinuz-2.6.31-22-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.28-19-generic
Found kernel: /boot/vmlinuz-2.6.28-18-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-22-generic                                                                                                  
 *  bcmwl (5.10.91.9+bdcom)...                                                                                                                                          bcmwl (5.10.91.9+bdcom): Installing module.
..........
......
                                                                                                                                                                 [ OK ]
 *  rts-ustor (1.04)...                                                                                                                                                 rts-ustor (1.04): Installing module.
.........
......
                                                                                                                                                                 [ OK ]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up linux-image-generic (2.6.31.22.35) ...
Setting up linux-generic (2.6.31.22.35) ...
Setting up linux-image-2.6.31-14-generic (2.6.31-14.48) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-14-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.31-22-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.28-19-generic
Found kernel: /boot/vmlinuz-2.6.28-18-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-14-generic                                                                                                  
 *  bcmwl (5.10.91.9+bdcom)...                                                                                                                                          bcmwl (5.10.91.9+bdcom): Installing module.
  Kernel headers for 2.6.31-14-generic are not installed.  Cannot install this module.
  Try installing linux-headers-2.6.31-14-generic or equivalent.
                                                                                                                                                                 [fail]
 *  rts-ustor (1.04)...                                                                                                                                                 rts-ustor (1.04): Installing module.
  Kernel headers for 2.6.31-14-generic are not installed.  Cannot install this module.
  Try installing linux-headers-2.6.31-14-generic or equivalent.
                                                                                                                                                                 [fail]
run-parts: executing /etc/kernel/postinst.d/nvidia-common
```

---

### Post by sawatdee on 2010-09-09
Looks like it needs some linux headers. I did a full upgrade of all my 9.04 packages before trying to upgrade to 9.10. What else would I need to do to prepare for an upgrade to 9.10?

---

### Post by tyblogger5 on 2010-09-09
I think you're right about the linux headers, go ahead and run:

```
sudo apt-get install linux-headers-2.6.31-14-generic
```

first before running the other command that I asked you to run earlier.

---

### Post by sawatdee on 2010-09-09
I installed linux-headers. It said it was already installed.
Then I installed linux-image again. It said that was already installed too.
If I run dpkg, I can see that several versions of linux-headers and linux-image are installed, including the version that is apparently needed by my new upgrade to 9.10.

The upgrade never rebooted, so the currently running kernel is still the one from 9.04. That could be why uname and other applications report what they do. If I reboot, I think it should boot the most recent kernel, provided it is installed completely and correctly. Otherwise, I am hoping I can boot one of the previous kernels. I am at work now, so I will have to try it later tonight. Should be interesting.....

---

### Post by tyblogger5 on 2010-09-09
Yeah, I guess just try to reboot later and post back from the LiveCD if it doesn't work.  Either way, let me know when you get it all worked out.

-Tariq

---

### Post by ezsit on 2010-09-09
> Everything I have read says that 9.10 includes kernel 2.6.31. So I am afraid to reboot now. Any ideas?

If you have run the update and NOT rebooted, **of course** you are still running the old kernel. The update/upgrade process cannot replace the running kernel with the newer kernel until you reboot.

---

### Post by sawatdee on 2010-09-09
> **ezsit said:**
> If you have run the update and NOT rebooted, **of course** you are still running the old kernel. The update/upgrade process cannot replace the running kernel with the newer kernel until you reboot.

True. But wouldn't the upgrade have rebooted automatically if there had not been an error upgrading the kernel? And the apt-get output above shows an error too. So something went awry somewhere in the process. I will find out later when I can reboot the system.

---

### Post by tyblogger5 on 2010-09-11
> **sawatdee said:**
> True. But wouldn't the upgrade have rebooted automatically if there had not been an error upgrading the kernel? And the apt-get output above shows an error too. So something went awry somewhere in the process. I will find out later when I can reboot the system.

Yeah, I think just try rebooting and see if the new kernel loads.  The installer will never reboot automatically, it will always let you know that it's done and give you the choice to reboot or continue the Live session.

---

