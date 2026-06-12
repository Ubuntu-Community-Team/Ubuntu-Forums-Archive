---
title: "Upgrade Ubuntu Portable inplace 11.04 to 11.10"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by cm0n3y34 on 2011-10-18
I use a flash drive with ubuntu 11.04 x86 installed on it, with a persistant filesystem. The drive is 4gb, and has ~800mb free space, after apt-get autoremove and clean. 

My question is is it safe to try to upgrade, keeping the settings intact (especially ubuntu classic), without erasing and starting with the iso?

---

### Post by decoherence on 2011-10-18
Well, I'm not sure how well tested your usage scenario is. I would suggest following the standard practice of backing everything up, doing the install and restoring when^W if things go wrong.

---

### Post by arpanaut on 2011-10-18
ubuntu classic is not an option in 11.10.
If that is important to you don't upgrade.
and yes you may have space issues if you do try to upgrade
as I believe that all the upgrade files are downloaded before the upgrade begins
and the old purged afterwards.

good luck

---

### Post by cm0n3y34 on 2011-10-18
*facepalm* That makes sense, 

Since its not well tested, should I post results? I'm sure i'm not the only person who uses Ubuntu at school/work to escape the horrible slowness and instability of a winXP image that has been passed through 3 generations of computers with no updates! They have freaking i5 processors in them, but they run slower than my parent's computer! (except when I get there :)heh heh)

---

### Post by cm0n3y34 on 2011-10-18
> **arpanaut said:**
> ubuntu classic is not an option in 11.10.
If that is important to you don't upgrade.
and yes you may have space issues if you do try to upgrade
as I believe that all the upgrade files are downloaded before the upgrade begins
and the old purged afterwards.

good luck

If Unity has some customizations and maybe something to do CPU scaling with, then I wouldn't mind it at all. If nothing else, I just want the upgrades to the video drivers and the kernel. IDK if the video drivers got updated to the new ones, but i notice that all the kernel updates are held back...

---

### Post by cm0n3y34 on 2011-10-18
Also, when I upgraded my parent's laptop to 11.10, my account still had ubuntu classic, while theirs was the upgraded unity. So I assume it holds onto classic, possibly only if at least one user has it as default.

---

### Post by decoherence on 2011-10-18
> **cm0n3y34 said:**
> *facepalm* That makes sense, 

Since its not well tested, should I post results? I'm sure i'm not the only person who uses Ubuntu at school/work to escape the horrible slowness and instability of a winXP image that has been passed through 3 generations of computers with no updates! They have freaking i5 processors in them, but they run slower than my parent's computer! (except when I get there :)heh heh)

Results are always welcome!

And I hear ya about the ancient XP images. School and corporate Windows machines can be a nightmare. Good luck!

---

### Post by cm0n3y34 on 2011-10-18
OK, didn't have enough time to try a full upgrade, but in theory, couldn't one copy the casperfs to an external HDD, resize it to a larger FS, upgrade to 11.10, clean up, shrink the FS, and copy it back? I will try this when I have time, if for no other reason, because I am curious to see if this will work as I think it will.

 I DID try to force the held back packages (after a full backup of course)
It seems to still work, but I encountered some errors during the process, specifically while upgrading the kernel and kernel headers, leading me to think there was a REASON they were held back *gasp*! this may also be an issue with upgrading to 11.10. 

I'm not sure if its worth the time and trouble to try to upgrade to 11.10 now, and if I do, it may be easier to selectively tar some of the settings in the user folder and copy it over, like when all hell broke loose on my main system during the upgrade to 11.04. 

Below is the relevant issues that came up. Everything in ()s assume business as usual.

ubuntu@ubuntu:~$ sudo apt-get install   libsyncdaemon-1.0-1  linux-generic linux-headers-generic linux-image-generic  python-ubuntuone-client ubuntuone-client ubuntuone-client-gnome  ubuntuone-client-dbg fdutils linux-doc-2.6.38 linux-source-2.6.38  linux-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-doc-2.6.38 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'linux-doc-2.6.38' has no installation candidate
ubuntu@ubuntu:~$  sudo apt-get install   libsyncdaemon-1.0-1 linux-generic  linux-headers-generic linux-image-generic python-ubuntuone-client  ubuntuone-client ubuntuone-client-gnome ubuntuone-client-dbg fdutils   linux-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gir1.2-dbusmenu-glib-0.4 gir1.2-dee-0.5 gir1.2-unity-3.0 libdw1 linux-headers-2.6.38-11 linux-headers-2.6.38-11-generic linux-image-2.6.38-11-generic linux-tools-2.6.38-11 linux-tools-common
Suggested packages:
  linux-doc-2.6.38 linux-source-2.6.38
The following NEW packages will be installed:
  fdutils gir1.2-dbusmenu-glib-0.4 gir1.2-dee-0.5 gir1.2-unity-3.0 libdw1 linux-headers-2.6.38-11 linux-headers-2.6.38-11-generic linux-image-2.6.38-11-generic linux-tools linux-tools-2.6.38-11
  linux-tools-common ubuntuone-client-dbg
The following packages will be upgraded:
   libsyncdaemon-1.0-1 linux-generic linux-headers-generic  linux-image-generic python-ubuntuone-client ubuntuone-client  ubuntuone-client-gnome
7 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 49.0 MB of archives.
After this operation, 214 MB of additional disk space will be used.
Do you want to continue [Y/n]? y

(get operations)

(preparing/unpacking)
...

Preparing to replace linux-generic 2.6.38.8.22 (using .../linux-generic_2.6.38.11.26_i386.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 2.6.38.8.22 (using .../linux-image-generic_2.6.38.11.26_i386.deb) ...
Unpacking replacement linux-image-generic ...
Selecting previously deselected package linux-headers-2.6.38-11.
Unpacking linux-headers-2.6.38-11 (from .../linux-headers-2.6.38-11_2.6.38-11.50_all.deb) ...
Selecting previously deselected package linux-headers-2.6.38-11-generic.
Unpacking linux-headers-2.6.38-11-generic (from .../linux-headers-2.6.38-11-generic_2.6.38-11.50_i386.deb) ...
Preparing to replace linux-headers-generic 2.6.38.8.22 (using .../linux-headers-generic_2.6.38.11.26_i386.deb) ...
Unpacking replacement linux-headers-generic ...
...
(more preparing/unpacking)
(processing)
...
Setting up linux-image-2.6.38-11-generic (2.6.38-11.50) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic
cryptsetup: WARNING: failed to detect canonical device of aufs
cryptsetup: WARNING: could not determine root device from /etc/fstab
The link /vmlinuz is a dangling linkto /boot/vmlinuz-2.6.38-8-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
/usr/sbin/grub-probe: error: cannot stat `aufs'.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-11-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-11-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
...
(more processing)
...
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-11-generic; however:
  Package linux-image-2.6.38-11-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.11.26); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Setting up linux-headers-2.6.38-11 (2.6.38-11.50) ...
Setting up linux-headers-2.6.38-11-generic (2.6.38-11.50) ...
Examining /etc/kernel/header_postinst.d.
Setting up linux-headers-generic (2.6.38.11.26) ...
Setting up linux-tools-common (2.6.38-11.50) ...
Setting up linux-tools-2.6.38-11 (2.6.38-11.50) ...
Setting up linux-tools (2.6.38.11.26) ...
...
(more processing)
Errors were encountered while processing:
 linux-image-2.6.38-11-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

...

ubuntu@ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 96.0 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 164191 files and directories currently installed.)
Removing linux-headers-2.6.38-8-generic ...
Removing linux-headers-2.6.38-8 ...
Setting up linux-image-2.6.38-11-generic (2.6.38-11.50) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic
cryptsetup: WARNING: failed to detect canonical device of aufs
cryptsetup: WARNING: could not determine root device from /etc/fstab
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
/usr/sbin/grub-probe: error: cannot stat `aufs'.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-11-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-11-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-11-generic; however:
  Package linux-image-2.6.38-11-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.11.26); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
    Errors were encountered while processing:
 linux-image-2.6.38-11-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu:~$

---

