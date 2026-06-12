---
title: "Why is there a problem with &quot;sudo apt --purge autoremove&quot;"
date: 2022-07-13
forum: Installation &amp; Upgrades
---

### Post by elpidiovaldez5 on 2022-07-13
I did a successful upgrade of my system.  A new kernel was installed and booted correctly.  Since I have had a lot of problems with insufficient space in /boot, I decided to remove unnecessary kernels following the procedure [here]("https://www.cyberciti.biz/faq/ubuntu-18-04-remove-all-unused-old-kernels/").

However there were problems and I would like to understand what is happening, and fix this so that autoremove can be used in future.

Hera are the installed kernels:

```
paul@clio:~$ dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+'
rc  linux-image-5.4.0-107-generic                 5.4.0-107.121                        amd64        Signed kernel image generic
ii  linux-image-5.4.0-110-generic                 5.4.0-110.124                        amd64        Signed kernel image generic
ii  linux-image-5.4.0-121-generic                 5.4.0-121.137                        amd64        Signed kernel image generic
ii  linux-image-5.4.0-122-generic                 5.4.0-122.138                        amd64        Signed kernel image generic

```

I am currently using 5.4.0-122:

```
paul@clio:~$ uname -r
5.4.0-122-generic

```

Autoremove failed to fully remove 5.4.0-110:

```
paul@clio:~$ sudo apt --purge autoremove
[sudo] password for paul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED                                                                                                                                  
  linux-headers-5.4.0-110* linux-headers-5.4.0-110-generic* linux-image-5.4.0-110-generic* linux-modules-5.4.0-110-generic* linux-modules-extra-5.4.0-110-generic*      
0 to upgrade, 0 to newly install, 5 to remove and 0 not to upgrade.                                                                                                     
After this operation, 380 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 461827 files and directories currently installed.)
Removing linux-headers-5.4.0-110-generic (5.4.0-110.124) ...
Removing linux-headers-5.4.0-110 (5.4.0-110.124) ...
Removing linux-modules-extra-5.4.0-110-generic (5.4.0-110.124) ...
Removing linux-image-5.4.0-110-generic (5.4.0-110.124) ...
/etc/kernel/prerm.d/dkms:
dkms: removing: bcmwl 6.30.223.271+bdcom (5.4.0-110-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.271+bdcom
Kernel:  5.4.0-110-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/5.4.0-110-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod...

DKMS: uninstall completed.
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.4.0-110-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-122-generic
Found initrd image: /boot/initrd.img-5.4.0-122-generic
Found linux image: /boot/vmlinuz-5.4.0-121-generic
Found initrd image: /boot/initrd.img-5.4.0-121-generic
Adding boot menu entry for UEFI Firmware Settings
done
Removing linux-modules-5.4.0-110-generic (5.4.0-110.124) ...
(Reading database ... 425400 files and directories currently installed.)
Purging configuration files for linux-modules-extra-5.4.0-110-generic (5.4.0-110.124) ...
Purging configuration files for linux-modules-5.4.0-110-generic (5.4.0-110.124) ...
dpkg: warning: while removing linux-modules-5.4.0-110-generic, directory '/lib/modules/5.4.0-110-generic' not empty so not removed
Purging configuration files for linux-image-5.4.0-110-generic (5.4.0-110.124) ...
```

Oddly the directory which it says will not be removed does not exist (I don't know if the system did remove it, or if it was not there before autoremove).

I do not understand what is going on with bcmwl.

---

### Post by TheFu on 2022-07-13
The manpage for apt doesn't show 
```
sudo apt --purge autoremove
```
as a valid option.
I've always used 2 commands, based on what the apt-get manpage says.

```
sudo apt --purge remove
sudo apt autoremove
```

If we want to script these, then don't use 'apt', use 'apt-get'.
Those pesky manpages are full of useful information.

---

### Post by Impavidus on 2022-07-14
> ```
dpkg: warning: while removing linux-modules-5.4.0-110-generic, directory '/lib/modules/5.4.0-110-generic' not empty so not removed
```I get those warnings too, but the directory is properly removed. Maybe the next line> ```
Purging configuration files for linux-image-5.4.0-110-generic (5.4.0-110.124) ...
```does that.

> The manpage for apt doesn't show ```
sudo apt --purge autoremove
``` 
as a valid option.The man page for apt doesn't appear complete. The command works and has the expected result.

---

### Post by TheFu on 2022-07-14
> **Impavidus said:**
> I get those warnings too, but the directory is properly removed. Maybe the next linedoes that.

The man page for apt doesn't appear complete. The command works and has the expected result.

apt used to pass unknown options to apt-get. I don't know how it works now, but apt-get specifically says that --purge is for use with the remove option. It doesn't say anything about the autoremove option working with --purge.  I'd rather not use undocumented "features", which someone could call a bug at any point where the approved solution is so easy, but everyone has their own take on that stuff.

---

