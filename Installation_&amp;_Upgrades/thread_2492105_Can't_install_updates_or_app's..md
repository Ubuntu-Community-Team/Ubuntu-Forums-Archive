---
title: "Can't install updates or app's."
date: 2023-10-30
forum: Installation &amp; Upgrades
---

### Post by jackjump on 2023-10-30
The problems:
_______________________________________________________

When attempting to do updates, the following is the dialog:

  	 	 	 	   **Package failed to install:**  
Error while installing package: installed **linux-image-5.13.0-37-generic** package post-removal script subprocess returned error exit status 1



  _______________________________________________________

  	 	 	 	   When attempting to install an application:
[B]
Confirm package removal[/B]
This action will also remove the following packages:
  [B]linux-image-5.13.0-37-generic(5.13.0.37.42~20.04.1)
  linux-image-5.13.0-39-generic(5.13.0.39.44~20.04.1)[/B]

**Proceed** is clicked.

Package failed to install
Too few items to process

(And the install doesn’t happen.)

_______________________________________________________

What I think I did to cause this.

- I did an in place upgrade from 20.X to 22.04.3
- During the upgrade I was prompted about Grub as to, whether or not, I wanted to keep the existing config file.  Since this OS is on a multi-boot platform (like an idiot) I elected to keep the existing config file.

Now it appears that I can't get rid of the 20.x kernels, (5.13.0-37-generic and 5.13.0-39-generic) even when using **sudo apt-get purge**.  My guess is that the purge script is checking the existing (old) grub config file and is finding references to the older 20.X kernels.  Then, since the old kernels are referenced in the grub config file, the script refuses to remove the kernels.  That's my  guess but it's nothing more than speculation.

Are there any ideas short of reinstalling?

Thanks for the help.

---

### Post by MAFoElffen on 2023-10-30
First... Lets see what is there in /boot. Please post the output within CODE Tags.
```

ls -lah /boot/*

```
Then the results of this
```

apt list installed linux-image* linux-generic* --installed

```
Then lets gather just a bit on what it thinks it is currently
```

uname -a
lsb_release -a

```

---

### Post by ian-weisser on 2023-10-31
Also please show us the complete apt output.

Often when folks post summaries, they edit out the important information a few lines above that is frequently key to understanding the problem.

---

### Post by Impavidus on 2023-10-31
As I have the impression that you ran the updater through the GUI, that command is```
sudo apt update
sudo apt upgrade
```The output of the first isn't really important (usually), but it must be run shortly before the second. The output of the second command is what we need.
> **jackjump said:**
> 
Now it appears that I can't get rid of the 20.x kernels, (5.13.0-37-generic and 5.13.0-39-generic) even when using **sudo apt-get purge**.  My guess is that the purge script is checking the existing (old) grub config file and is finding references to the older 20.X kernels.  Then, since the old kernels are referenced in the grub config file, the script refuses to remove the kernels.  That's my  guess but it's nothing more than speculation.

The removal script doesn't check the grub config file. It just removes the kernel, then runs update-grub, which creates a new grub config file with whatever kernels are left. It could be that your grub update scripts are broken. Did you have anything special in there? Grub-customizer is known for causing this kind of trouble sometimes. Or maybe installation of some kernel went wrong due to lack of disk space, usually when you've got a small /boot partition.

---

### Post by jackjump on 2023-10-31
Output:


```
(base) jack@HR-Kubuntu:~$ sudo ls -lah /boot/*
[sudo] password for jack: 
-rw-r--r-- 1 root root 256K Oct  2 15:33 /boot/config-5.15.0-87-generic
lrwxrwxrwx 1 root root   28 Oct 27 11:02 /boot/initrd.img -> initrd.img-5.15.0-87-generic
-rw-r--r-- 1 root root 106M Oct 28 09:02 /boot/initrd.img-5.15.0-87-generic
lrwxrwxrwx 1 root root   28 Oct 28 09:10 /boot/initrd.img.old -> initrd.img-5.15.0-87-generic
-rw-r--r-- 1 root root 179K Feb  6  2022 /boot/memtest86+.bin
-rw-r--r-- 1 root root 181K Feb  6  2022 /boot/memtest86+.elf
-rw-r--r-- 1 root root 181K Feb  6  2022 /boot/memtest86+_multiboot.bin
-rw------- 1 root root 6.0M Oct  2 15:33 /boot/System.map-5.15.0-87-generic
lrwxrwxrwx 1 root root   25 Oct 27 11:02 /boot/vmlinuz -> vmlinuz-5.15.0-87-generic
-rw------- 1 root root  12M Oct  2 15:42 /boot/vmlinuz-5.15.0-87-generic
lrwxrwxrwx 1 root root   25 Oct 28 09:10 /boot/vmlinuz.old -> vmlinuz-5.15.0-87-generic

/boot/grub:
total 2.4M
drwxr-xr-x 5 root root 4.0K Oct 30 20:48 .
drwxr-xr-x 5 root root 4.0K Oct 28 09:10 ..
drwxr-xr-x 2 root root 4.0K Feb 18  2022 fonts
-rw-r--r-- 1 root root  712 Aug 19  2021 gfxblacklist.txt
-r--r--r-- 1 root root  12K Oct 28 09:03 grub.cfg
-rw-r--r-- 1 root root  12K Oct 30 20:35 grub.cfg.bak
-rw------- 1 root root 3.1K Oct 30 19:07 grub.cfg.new
-rw-rw-r-- 1 root root 1.0K Oct 31 10:50 grubenv
drwxr-xr-x 2 root root  12K Feb 18  2022 i386-pc
drwxr-xr-x 2 root root 4.0K Feb 18  2022 themes
-rw-r--r-- 1 root root 2.3M Oct 28 08:56 unicode.pf2

/boot/lost+found:
total 20K
drwx------ 2 root root  16K Feb 18  2022 .
drwxr-xr-x 5 root root 4.0K Oct 28 09:10 ..

/boot/timeshift:
total 12K
drwxr-xr-x 3 root root 4.0K Oct 28 01:00 .
drwxr-xr-x 5 root root 4.0K Oct 28 09:10 ..
drwxr-xr-x 2 root root 4.0K Oct 28 01:00 snapshots
(base) jack@HR-Kubuntu:~$ 
```

____________________________________________________________________________________

```
(base) jack@HR-Kubuntu:~$ sudo apt list installed linux-image* linux-generic* --installed
Listing... Done
linux-generic-hwe-20.04/now 5.15.0.87.97~20.04.45 amd64 [installed,upgradable to: 5.15.0.88.85]
linux-generic/now 5.15.0.87.84 amd64 [installed,upgradable to: 5.15.0.88.85]
linux-image-5.13.0-37-generic/now 5.13.0-37.42~20.04.1 amd64 [installed,local]
linux-image-5.13.0-39-generic/now 5.13.0-39.44~20.04.1 amd64 [installed,local]
linux-image-5.15.0-87-generic/jammy-updates,jammy-security,now 5.15.0-87.97 amd64 [installed]
linux-image-generic-hwe-20.04/now 5.15.0.87.97~20.04.45 amd64 [installed,upgradable to: 5.15.0.88.85]
linux-image-generic/now 5.15.0.87.84 amd64 [installed,upgradable to: 5.15.0.88.85]
(base) jack@HR-Kubuntu:~$ 
```

____________________________________________________________________________________

```
(base) jack@HR-Kubuntu:~$ uname -a
Linux HR-Kubuntu 5.15.0-87-generic #97-Ubuntu SMP Mon Oct 2 21:09:21 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
(base) jack@HR-Kubuntu:~$ 
```

____________________________________________________________________________________

```
(base) jack@HR-Kubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.3 LTS
Release:        22.04
Codename:       jammy
(base) jack@HR-Kubuntu:~$ 
```

---

### Post by jackjump on 2023-10-31
This is the a sample output from an attempt to install an app:

```
(base) jack@HR-Kubuntu:~$ sudo apt-get install kolourpaint
[sudo] password for jack: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  linux-image-5.13.0-37-generic linux-image-5.13.0-39-generic
The following NEW packages will be installed:
  kolourpaint
0 upgraded, 1 newly installed, 2 to remove and 6 not upgraded.
2 not fully installed or removed.
Need to get 5,517 kB of archives.
After this operation, 10.4 MB disk space will be freed.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/universe amd64 kolourpaint amd64 4:21.12.3-0ubuntu1 [5,517 kB]
Fetched 5,517 kB in 5s (1,095 kB/s)      
(Reading database ... 215206 files and directories currently installed.)
Removing linux-image-5.13.0-37-generic (5.13.0-37.42~20.04.1) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.13.0-37-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
using custom appearance settings
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries:  libcrypto.so.1.1: cannot open shared object file: No such file or  directory
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.13.0-37-generic (--remove):
 installed linux-image-5.13.0-37-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.13.0-37-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
(base) jack@HR-Kubuntu:~$
```

---

### Post by jackjump on 2023-10-31
The outputs of **sudo apt update **and **sudo apt upgrade**:

As it is with the previously supplied output, there seems to be a common theme.  (Which, for a NOOB, is baffling.)
_______________________________________________________

```

(base) jack@HR-Kubuntu:~$ sudo apt update
Hit:1 http://us.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:3 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease
Hit:4 http://security.ubuntu.com/ubuntu jammy-security InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
6 packages can be upgraded. Run 'apt list --upgradable' to see them.
(base) jack@HR-Kubuntu:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-generic-hwe-20.04 linux-image-generic-hwe-20.04
Use 'sudo apt autoremove' to remove them.
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  vlc-plugin-qt libvlc5 vlc-data libvlccore9 vlc imagemagick vlc-bin vlc-l10n
  libopenexr25 libpostproc55 libmagickcore-6.q16-6-extra vlc-plugin-samba
  libavcodec58 libmagickwand-6.q16-6 vlc-plugin-notify libavutil56
  imagemagick-6.q16 libswscale5 libeditorconfig0 libmagickcore-6.q16-6
  vlc-plugin-access-extra vlc-plugin-skins2 vlc-plugin-video-splitter
  libswresample3 imagemagick-6-common vlc-plugin-video-output libavformat58
  libvlc-bin vlc-plugin-base vlc-plugin-visualization libavfilter7
Learn more about Ubuntu Pro at https://ubuntu.com/pro
#
# Canonical released microcode updates for both Intel (CVE-2022-40982) and AMD
# (CVE-2023-20593). ‘Unattended upgrades’ provide security updates by default.
# Ensure it remains enabled to always get all updates as they become available.
#
The following packages will be REMOVED:
  linux-image-5.13.0-37-generic linux-image-5.13.0-39-generic
The following NEW packages will be installed:
  linux-generic-hwe-22.04 linux-headers-5.15.0-88 linux-headers-5.15.0-88-generic
  linux-headers-6.2.0-36-generic linux-headers-generic-hwe-22.04 linux-hwe-6.2-headers-6.2.0-36
  linux-image-5.15.0-88-generic linux-image-6.2.0-36-generic linux-image-generic-hwe-22.04
  linux-modules-5.15.0-88-generic linux-modules-6.2.0-36-generic
  linux-modules-extra-5.15.0-88-generic linux-modules-extra-6.2.0-36-generic
The following packages will be upgraded:
  linux-generic linux-generic-hwe-20.04 linux-headers-generic linux-headers-generic-hwe-20.04
  linux-image-generic linux-image-generic-hwe-20.04
6 upgraded, 13 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
6 standard LTS security updates
Need to get 0 B/242 MB of archives.
After this operation, 1,260 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 215206 files and directories currently installed.)
Removing linux-image-5.13.0-37-generic (5.13.0-37.42~20.04.1) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.13.0-37-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
using custom appearance settings
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.1: cannot open shared object file: No such file or directory
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-5.13.0-37-generic (--remove):
 installed linux-image-5.13.0-37-generic package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.13.0-37-generic
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
(base) jack@HR-Kubuntu:~$ 
```

_______________________________________________________

> The removal script doesn't check the grub config file. It just removes  the kernel, then runs update-grub, which creates a new grub config file  with whatever kernels are left. It could be that your grub update  scripts are broken. Did you have anything special in there?  Grub-customizer is known for causing this kind of trouble sometimes. Or  maybe installation of some kernel went wrong due to lack of disk space,  usually when you've got a small /boot partition.

The "grub config file" theory was, admittedly, speculation.  (A WAG might be a better description.)  But it was the only deviation I made (saving the existing/old Grub config file) when upgrading from 20.X to 22.X.  Since Grub selects the kernel to be used, well, again, the association between kernels that refuse to purge and Grub was a guess.

---

### Post by jackjump on 2023-10-31
Sorry that I didn't reply to each of you with your replies quoted.  I'm still figuring out how the forum works.

Thanks for your patience.

---

### Post by MAFoElffen on 2023-10-31
That's okay... Let me try to explain what I see from all that output, and tell the story it tell's...

*** The only kernel that is currently there in the /boot folder to actually boot from is kernel 5.15.0-87-generic. ***

That is odd, because package-wise it says that these kernels are installed:
```

linux-image-5.13.0-37-generic
linux-image-5.13.0-39-generic
linux-image-5.15.0-87-generic

```
So the kernels for -39 and -37 didn't completely install correctly (no initramfs images present in /boot). It looks like the problems started with -37 back in 20.04... Either that, or it started to remove them , then when that failed, didn't roll anything back. It shows -87 as the current running kernel...

Your updates are trying to install kernel versions 5.15.0-88-generic and 6.2.0-36-generic... Those are the current kernels for 22.04 in the generic and generic-hwe series.

This starts a change of events... When Ubuntu installs a new kernel, it leaves 2 previous kernels, and tries to remove the older kernels than those.

It sees kernel 5.15.0-87 as an installed package, is booted from that as the latest kernel.

It's trying to remove the oldest kernels, so that after the install of the 2 new kernels that there will be the newest, and 2 older kernels (6.2.0-36, 5.15.0-88, 5.15.0-87). That would be the right things to do.

But it can't, because it cannot remove those because there were some problems. It cannot resolve those problems on it's own.

Did you follow that logic?

[HR][/HR]
Let's try to check if they are even available anymore through his apt system. Becaseu they were 20.04 kernels, and he is now 22.04...
```

apt list linux-*-5.13.0-37-generic

```
I see those in my 22.04 results... 
```

sudo update 
sudo apt install --reinstall openssl
sudo apt install --reinstall linux-modules-extra-5.13.0-37-generic linux-modules-extra-5.13.0-37-generic linux-headers-5.13.0-37-generic linux-image-5.13.0-37-generic
sudo apt install --reinstall linux-modules-extra-5.13.0-39-generic  linux-modules-extra-5.13.0-39-generic linux-headers-5.13.0-39-generic  linux-image-5.13.0-39-generic

```
The run your updates to see if they get removed successfully.

---

### Post by Impavidus on 2023-11-01
```
Generating grub configuration file ...
using custom appearance settings
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.1: cannot open shared object file: No such file or directory
```
I can't find /etc/grub.d/bin/grubcfg_proxy in the official repos, neither in 20.04 nor in 22.04. I can find libcrypto.so.1.1, which is in libssl1.1, a package in the repos for 20.04, but not for 22.04. I suspect that grubcfg_proxy was installed from some third party source and wasn't removed during the upgrade. It depends on libcrypto.so.1.1, which was removed during the upgrade. So your update-grub is broken and must be fixed before any kernel can be fully installed or removed. Leaving third party software during an upgrade, especially is such a vital position as grub, may lead to trouble. May it have anything to do with those "custom appearance settings"?

Question is: how to cleanly remove grubcfg_proxy? Maybe this will give a clue:```
dpkg --list grub*
dpkg --search /etc/grub.d/bin/grubcfg_proxy
```

---

### Post by jackjump on 2023-11-01
> **MAFoElffen said:**
> That's okay... Let me try to explain what I see from all that output, and tell the story it tell's...

*** The only kernel that is currently there in the /boot folder to actually boot from is kernel 5.15.0-87-generic. ***

That is odd, because package-wise it says that these kernels are installed:
```

linux-image-5.13.0-37-generic
linux-image-5.13.0-39-generic
linux-image-5.15.0-87-generic

```
So the kernels for -39 and -37 didn't completely install correctly (no initramfs images present in /boot). It looks like the problems started with -37 back in 20.04... Either that, or it started to remove them , then when that failed, didn't roll anything back. It shows -87 as the current running kernel...

Your updates are trying to install kernel versions 5.15.0-88-generic and 6.2.0-36-generic... Those are the current kernels for 22.04 in the generic and generic-hwe series.

This starts a change of events... When Ubuntu installs a new kernel, it leaves 2 previous kernels, and tries to remove the older kernels than those.

It sees kernel 5.15.0-87 as an installed package, is booted from that as the latest kernel.

It's trying to remove the oldest kernels, so that after the install of the 2 new kernels that there will be the newest, and 2 older kernels (6.2.0-36, 5.15.0-88, 5.15.0-87). That would be the right things to do.

But it can't, because it cannot remove those because there were some problems. It cannot resolve those problems on it's own.

Did you follow that logic?

[HR][/HR]
Let's try to check if they are even available anymore through his apt system. Becaseu they were 20.04 kernels, and he is now 22.04...
```

apt list linux-*-5.13.0-37-generic

```
I see those in my 22.04 results... 
```

sudo update 
sudo apt install --reinstall openssl
sudo apt install --reinstall linux-modules-extra-5.13.0-37-generic linux-modules-extra-5.13.0-37-generic linux-headers-5.13.0-37-generic linux-image-5.13.0-37-generic
sudo apt install --reinstall linux-modules-extra-5.13.0-39-generic  linux-modules-extra-5.13.0-39-generic linux-headers-5.13.0-39-generic  linux-image-5.13.0-39-generic

```
The run your updates to see if they get removed successfully.
_____________________________________________________________________________________________________________________________


I'm not sure if I follow your logic.  I did find that there's a number of differences between how a Grub menu is generated now versus back in the day.  (Which was my only lead in this matter - the choice I made - when upgrading.)  It seems that there's a number of ref'ed files and at least one script, in auto configuring Grub.  On the other hand, I probably went down the garden path on a mistaken hunch.

I didn't know what to make of the SSL issue but it seemed to be unrelated and I didn't want to dig my hole deeper.


Command outputs:

```

[FONT=monospace][COLOR=#000000](base) [/COLOR][COLOR=#54ff54]**jack@HR-Kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo apt update [/COLOR]
[sudo] password for floyd:  
Get:1 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB] 
Hit:2 http://us.archive.ubuntu.com/ubuntu jammy InRelease 
Get:3 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease [119 kB] 
Hit:4 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease 
Fetched 229 kB in 1s (172 kB/s) 
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
6 packages can be upgraded. Run 'apt list --upgradable' to see them. 
(base) [COLOR=#54ff54]**jack@HR-Kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR]
[/FONT]
```


[FONT=monospace]```
[COLOR=#000000](base) [/COLOR][COLOR=#54ff54]**jack@HR-Kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo apt install --reinstall openssl [/COLOR]
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
The following packages will be REMOVED: 
  linux-image-5.13.0-37-generic linux-image-5.13.0-39-generic 
0 upgraded, 0 newly installed, 1 reinstalled, 2 to remove and 6 not upgraded. 
2 not fully installed or removed. 
Need to get 0 B/1,182 kB of archives. 
After this operation, 20.4 MB disk space will be freed. 
Do you want to continue? [Y/n] Y 
(Reading database ... 215206 files and directories currently installed.) 
Removing linux-image-5.13.0-37-generic (5.13.0-37.42~20.04.1) ... 
/etc/kernel/postrm.d/initramfs-tools: 
update-initramfs: Deleting /boot/initrd.img-5.13.0-37-generic 
/etc/kernel/postrm.d/zz-update-grub: 
Sourcing file `/etc/default/grub' 
Sourcing file `/etc/default/grub.d/init-select.cfg' 
Generating grub configuration file ... 
using custom appearance settings 
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.1
: cannot open shared object file: No such file or directory 
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127 
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package linux-image-5.13.0-37-generic (--remove): [/COLOR]
 installed linux-image-5.13.0-37-generic package post-removal script subprocess retur
ned error exit status 1 
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] too many errors, stopping [/COLOR]
Errors were encountered while processing: 
 linux-image-5.13.0-37-generic 
Processing was halted because there were too many errors. 
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Sub-process /usr/bin/dpkg returned an error code (1) [/COLOR]
(base) [COLOR=#54ff54]**jack@HR-Kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$
```  [/COLOR]


[/FONT]```
[FONT=monospace][COLOR=#000000](base) [/COLOR][COLOR=#54ff54]**jack@HR-Kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo apt install --reinstall linux-modules-extra-5.13.0-37[/COLOR]
-generic linux-modules-extra-5.13.0-37-generic linux-headers-5.13.0-37-generic linux-
image-5.13.0-37-generic 
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
Package linux-headers-5.13.0-37-generic is not available, but is referred to by anoth
er package. 
This may mean that the package is missing, has been obsoleted, or 
is only available from another source 

Package linux-modules-extra-5.13.0-37-generic is not available, but is referred to by
 another package. 
This may mean that the package is missing, has been obsoleted, or 
is only available from another source 

[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Package 'linux-modules-extra-5.13.0-37-generic' has no installation candidate [/COLOR]
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Package 'linux-modules-extra-5.13.0-37-generic' has no installation candidate [/COLOR]
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Package 'linux-headers-5.13.0-37-generic' has no installation candidate [/COLOR]
(base) [COLOR=#54ff54]**jack@HR-Kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR][/FONT]
```


```

[FONT=monospace][COLOR=#000000](base) [/COLOR][COLOR=#54ff54]**jack@HR-Kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo apt install --reinstall linux-modules-extra-5.13.0-39[/COLOR]
-generic  linux-modules-extra-5.13.0-39-generic linux-headers-5.13.0-39-generic  linu
x-image-5.13.0-39-generic 
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
Package linux-headers-5.13.0-39-generic is not available, but is referred to by anoth
er package. 
This may mean that the package is missing, has been obsoleted, or 
is only available from another source 

Package linux-modules-extra-5.13.0-39-generic is not available, but is referred to by
 another package. 
This may mean that the package is missing, has been obsoleted, or 
is only available from another source 

[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Package 'linux-modules-extra-5.13.0-39-generic' has no installation candidate [/COLOR]
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Package 'linux-modules-extra-5.13.0-39-generic' has no installation candidate [/COLOR]
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Package 'linux-headers-5.13.0-39-generic' has no installation candidate [/COLOR]
(base) [COLOR=#54ff54]**jack@HR-Kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$[/COLOR]
[/FONT]
```

After the above, I tried the package update, in the GUI, with the same result:

```
Package failed to install:
Error while installing package: installed linux-image-5.13.0-37-generic package post-removal script subprocess returned error exit status 1
```

I'm baffled. (That's why I'm here. O:) )
apt-get remove and apt-get purge (with sudo, essentially root access) doesn't work.  It's as if something is blocking the action.

Again, thanks for your time and help.


[FONT=monospace] 
[/FONT]

---

### Post by jackjump on 2023-11-01
> **Impavidus said:**
> ```
Generating grub configuration file ...
using custom appearance settings
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.1: cannot open shared object file: No such file or directory
```
I can't find /etc/grub.d/bin/grubcfg_proxy in the official repos, neither in 20.04 nor in 22.04. I can find libcrypto.so.1.1, which is in libssl1.1, a package in the repos for 20.04, but not for 22.04. I suspect that grubcfg_proxy was installed from some third party source and wasn't removed during the upgrade. It depends on libcrypto.so.1.1, which was removed during the upgrade. So your update-grub is broken and must be fixed before any kernel can be fully installed or removed. Leaving third party software during an upgrade, especially is such a vital position as grub, may lead to trouble. May it have anything to do with those "custom appearance settings"?

Question is: how to cleanly remove grubcfg_proxy? Maybe this will give a clue:```
dpkg --list grub*
dpkg --search /etc/grub.d/bin/grubcfg_proxy
```

________________________________________________________________________________________________________________

Some of that might make some sense.  I believe I enabled a third party repo for a specific app, some time ago, but that wouldn't have anything to do with grub.  As I recall it was to load up a cutting edge version of a game, Endless-Sky.  (This was a year or two ago.)  I beleive I disabled the custom repo.  
In any case,,

The Command Outputs:

[FONT=monospace]```
[COLOR=#000000](base) [/COLOR][COLOR=#54ff54]**jack@HR-Kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ dpkg --list grub* [/COLOR]
Desired=Unknown/Install/Remove/Purge/Hold 
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend 
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad) 
||/ Name                  Version         Architecture Description 
+++-=====================-===============-============-===================================================== 
un  grub                  <none>          <none>       (no description available) 
un  grub-cloud-amd64      <none>          <none>       (no description available) 
ii  grub-common           2.06-2ubuntu7.2 amd64        GRand Unified Bootloader (common files) 
un  grub-coreboot         <none>          <none>       (no description available) 
un  grub-doc              <none>          <none>       (no description available) 
un  grub-efi              <none>          <none>       (no description available) 
un  grub-efi-amd64        <none>          <none>       (no description available) 
un  grub-efi-arm          <none>          <none>       (no description available) 
un  grub-efi-arm64        <none>          <none>       (no description available) 
un  grub-efi-ia32         <none>          <none>       (no description available) 
un  grub-efi-ia64         <none>          <none>       (no description available) 
un  grub-emu              <none>          <none>       (no description available) 
ii  grub-gfxpayload-lists 0.7             amd64        GRUB gfxpayload blacklist 
un  grub-ieee1275         <none>          <none>       (no description available) 
un  grub-legacy           <none>          <none>       (no description available) 
un  grub-legacy-doc       <none>          <none>       (no description available) 
un  grub-linuxbios        <none>          <none>       (no description available) 
ii  grub-pc               2.06-2ubuntu7.2 amd64        GRand Unified Bootloader, version 2 (PC/BIOS version) 
ii  grub-pc-bin           2.06-2ubuntu7.2 amd64        GRand Unified Bootloader, version 2 (PC/BIOS modules) 
un  grub-uboot            <none>          <none>       (no description available) 
un  grub-xen              <none>          <none>       (no description available) 
un  grub-yeeloong         <none>          <none>       (no description available) 
un  grub2                 <none>          <none>       (no description available) 
ii  grub2-common          2.06-2ubuntu7.2 amd64        GRand Unified Bootloader (common files for version 2) 
(base) [COLOR=#54ff54]**jack@HR-Kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$[/COLOR]
```[COLOR=#000000] 


[/COLOR][/FONT]```
[FONT=monospace][COLOR=#000000](base) [/COLOR][COLOR=#54ff54]**jack@HR-Kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ dpkg --search /etc/grub.d/bin/grubcfg_proxy [/COLOR]
[COLOR=#000000]**dpkg-query:**[/COLOR][COLOR=#000000] no path found matching pattern /etc/grub.d/bin/grubcfg_proxy [/COLOR]
(base) [COLOR=#54ff54]**jack@HR-Kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000]


I navigated to the above location and, interestingly, I found the file as follows:[/COLOR][/FONT][FONT=monospace]

```
[COLOR=#000000]
(base) [/COLOR][COLOR=#54ff54]**floyd@HR-Kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/etc/grub.d/bin**[/COLOR][COLOR=#000000]$ ls [/COLOR]
[COLOR=#54ff54]**grubcfg_proxy**[/COLOR]
(base) [COLOR=#54ff54]**floyd@HR-Kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/etc/grub.d/bin**[/COLOR][COLOR=#000000]$[/COLOR]
```
[COLOR=#000000]

I viewed the contents of the grubcfg_proxy file in nano.
It's obviously not a text file but it contains text that indicates that it might affect the Grub menu.  It contains fields for other inputs and outputs.


[/COLOR]
[/FONT][FONT=monospace]

[/FONT]
[FONT=monospace]
[/FONT]

---

### Post by MAFoElffen on 2023-11-02
This error... I've seen this before...
```

/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.1: cannot open shared object file: No such file or directory

```
That error doesn't affect everyone, but seems to only hit when certain conditions are seen together. That is somewhere in the code, that is met / repaired by this, that I posted my solution above...
```

sudo apt install --reinstall openssl

```
Which, that package adds that module there, or reinstalls it if not, so then it is found. Not really sure why they are looking for that. Like I said, when some machines hit a certain perfect storm condition... That openssl package is not a default installed, but no harm if you do install it, and it gets that past that error that appears on some machines.

---

### Post by qyot27 on 2023-11-02
A quick search uncovered this on AskUbuntu:

[https://askubuntu.com/questions/1116133/ubuntu-18-04-libcrypto-so-1-0-0-cannot-open-shared-object-file-no-such-file-o/1185815#1185815](https://askubuntu.com/questions/1116133/ubuntu-18-04-libcrypto-so-1-0-0-cannot-open-shared-object-file-no-such-file-o/1185815#1185815)

Short version: find where libcrypto.so.1.1 is on your system (possibly inside a snap directory), copy it to one of the library paths where grubcfg_proxy can find it.  Then run
```
sudo apt-get --fix-broken install
```
and then
```
sudo apt-get --purge autoremove
```

---

### Post by MAFoElffen on 2023-11-02
From that, then this to find and copy it...
```

sudo cp $(ls  /snap/core*/*/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1 } | head -n1) /usr/lib/x86_64-linux-gnu/

```

---

### Post by jackjump on 2023-11-02
> **MAFoElffen said:**
> This error... I've seen this before...
```

/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.1: cannot open shared object file: No such file or directory

```
That error doesn't affect everyone, but seems to only hit when certain conditions are seen together. That is somewhere in the code, that is met / repaired by this, that I posted my solution above...
```

sudo apt install --reinstall openssl

```
Which, that package adds that module there, or reinstalls it if not, so then it is found. Not really sure why they are looking for that. Like I said, when some machines hit a certain perfect storm condition... **That openssl package is not a default installed, but no harm if you do install it, and it gets that past that error that appears on some machines**.
_________________________________________________________________

That's the main problem as I perceive it.  The issue, I can't install anything without deleting the old kernels (that ***refuse*** to be deleted), preclude the possibility of reinstalling something (like openssl) that might straighten this out.  It's a circular problem.

```
[FONT=monospace][COLOR=#000000](base) [/COLOR][COLOR=#54ff54]**jack@HR-Kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo apt install --reinstall openssl [/COLOR]
[sudo] password for jack:  
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
The following packages will be REMOVED: 
  linux-image-5.13.0-37-generic linux-image-5.13.0-39-generic 
0 upgraded, 0 newly installed, 1 reinstalled, 2 to remove and 9 not upgraded. 
2 not fully installed or removed. 
Need to get 0 B/1,182 kB of archives. 
After this operation, 20.4 MB disk space will be freed. 
Do you want to continue? [Y/n] Y 
(Reading database ... 215206 files and directories currently installed.) 
Removing linux-image-5.13.0-37-generic (5.13.0-37.42~20.04.1) ... 
/etc/kernel/postrm.d/initramfs-tools: 
update-initramfs: Deleting /boot/initrd.img-5.13.0-37-generic 
/etc/kernel/postrm.d/zz-update-grub: 
Sourcing file `/etc/default/grub' 
Sourcing file `/etc/default/grub.d/init-select.cfg' 
Generating grub configuration file ... 
using custom appearance settings 
/etc/grub.d/bin/grubcfg_proxy: error while loading shared libraries: libcrypto.so.1.1: cannot open shared objec
t file: No such file or directory 
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127 
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] error processing package linux-image-5.13.0-37-generic (--remove): [/COLOR]
 installed linux-image-5.13.0-37-generic package post-removal script subprocess returned error exit status 1 
[COLOR=#000000]**dpkg:**[/COLOR][COLOR=#000000] too many errors, stopping [/COLOR]
Errors were encountered while processing: 
 linux-image-5.13.0-37-generic 
Processing was halted because there were too many errors. 
[COLOR=#ff5454]**E: **[/COLOR][COLOR=#000000]Sub-process /usr/bin/dpkg returned an error code (1) [/COLOR]
(base) [COLOR=#54ff54]**jack@HR-Kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ [/COLOR][/FONT]
```

---

### Post by tea for one on 2023-11-02
> **jackjump said:**
>  I did an in place upgrade from 20.X to 22.04.3
During the upgrade I was prompted about Grub as to, whether or not, I wanted to keep the existing config file.  Since this OS is on a multi-boot platform (like an idiot) I elected to keep the existing config file.
Did you have grub-customizer installed in Ubuntu 20.X?
Later posts show the existence of [COLOR="#0000FF"]/etc/grub.d/bin/grubcfg_proxy[/COLOR] and grub proxy files are generated by grub-customizer.
Try this in a terminal:-
```
apt policy grub-customizer

```

---

### Post by jackjump on 2023-11-02
> **MAFoElffen said:**
> From that, then this to find and copy it...
```

sudo cp $(ls  /snap/core*/*/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1 } | head -n1) /usr/lib/x86_64-linux-gnu/

```
_____________________________________________________________________-

The command failed:

```
[FONT=monospace][COLOR=#000000](base) [/COLOR][COLOR=#54ff54]**jack@HR-Kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/usr/lib/x86_64-linux-gnu**[/COLOR][COLOR=#000000]$ sudo cp $(ls  /snap/core*/*/usr/lib/x86_64-linux-gnu/libcryp[/COLOR]
to.so.1.1 } | head -n1) /usr/lib/x86_64-linux-gnu/ 
ls: cannot access '}': No such file or directory[/FONT]
```

However, the package exists in the destination location:

```
[FONT=monospace][COLOR=#000000](base) [/COLOR][COLOR=#54ff54]**jack@HR-Kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/usr/lib/x86_64-linux-gnu**[/COLOR][COLOR=#000000]$ ls libcrypto* [/COLOR]
**libcrypto.so.1.1**  libcrypto.so.3[/FONT]  
```

---

### Post by deadflowr on 2023-11-02
look in /snap/core22/current/lib/x86_64-linux-gnu

Never mind.
I missed the bottom of the above post.

---

### Post by jackjump on 2023-11-02
> **qyot27 said:**
> A quick search uncovered this on AskUbuntu:

[https://askubuntu.com/questions/1116133/ubuntu-18-04-libcrypto-so-1-0-0-cannot-open-shared-object-file-no-such-file-o/1185815#1185815](https://askubuntu.com/questions/1116133/ubuntu-18-04-libcrypto-so-1-0-0-cannot-open-shared-object-file-no-such-file-o/1185815#1185815)

Short version: find where libcrypto.so.1.1 is on your system (possibly inside a snap directory), copy it to one of the library paths where grubcfg_proxy can find it.  Then run
```
sudo apt-get --fix-broken install
```
and then
```
sudo apt-get --purge autoremove
```

_______________________________________________________________________________

Since the file (libcrypto.so.1.1) was found in the location specified by @**MAFoElffen  **/usr/lib/x86_64-linux-gnu/ 
I ran your command lines.

Command outputs:

```
[FONT=monospace][COLOR=#000000](base) [/COLOR][COLOR=#54ff54]**jack@HR-Kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/usr/lib/x86_64-linux-gnu**[/COLOR][COLOR=#000000]$ **sudo apt-get --fix-broken install **[/COLOR]
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
The following packages will be REMOVED: 
  linux-image-5.13.0-37-generic linux-image-5.13.0-39-generic 
0 upgraded, 0 newly installed, 2 to remove and 9 not upgraded. 
2 not fully installed or removed. 
After this operation, 20.4 MB disk space will be freed. 
Do you want to continue? [Y/n] Y 
(Reading database ... 215206 files and directories currently installed.) 
Removing linux-image-5.13.0-37-generic (5.13.0-37.42~20.04.1) ... 
/etc/kernel/postrm.d/initramfs-tools: 
update-initramfs: Deleting /boot/initrd.img-5.13.0-37-generic 
/etc/kernel/postrm.d/zz-update-grub: 
Sourcing file `/etc/default/grub' 
Sourcing file `/etc/default/grub.d/init-select.cfg' 
Generating grub configuration file ... 
using custom appearance settings 
Found linux image: /boot/vmlinuz-5.15.0-87-generic 
Found initrd image: /boot/initrd.img-5.15.0-87-generic 
Found linux image: /boot/vmlinuz-5.15.0-87-generic 
Found initrd image: /boot/initrd.img-5.15.0-87-generic 
Found memtest86+ image: /memtest86+.elf 
Found memtest86+ image: /memtest86+.bin 
Found Windows 10 on /dev/sda1 
Found memtest86+ image: /memtest86+.elf 
Found memtest86+ image: /memtest86+.bin 
done 
Removing linux-image-5.13.0-39-generic (5.13.0-39.44~20.04.1) ... 
/etc/kernel/postrm.d/initramfs-tools: 
update-initramfs: Deleting /boot/initrd.img-5.13.0-39-generic 
/etc/kernel/postrm.d/zz-update-grub: 
Sourcing file `/etc/default/grub' 
Sourcing file `/etc/default/grub.d/init-select.cfg' 
Generating grub configuration file ... 
using custom appearance settings 
Found linux image: /boot/vmlinuz-5.15.0-87-generic 
Found initrd image: /boot/initrd.img-5.15.0-87-generic 
Found linux image: /boot/vmlinuz-5.15.0-87-generic 
Found initrd image: /boot/initrd.img-5.15.0-87-generic 
Found memtest86+ image: /memtest86+.elf 
Found memtest86+ image: /memtest86+.bin 
Found Windows 10 on /dev/sda1 
Found memtest86+ image: /memtest86+.elf 
Found memtest86+ image: /memtest86+.bin 
done 
(base) [COLOR=#54ff54]**jack@HR-Kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/usr/lib/x86_64-linux-gnu**[/COLOR][COLOR=#000000]$[/COLOR]
[/FONT]
```


```
[FONT=monospace][COLOR=#000000](base) [/COLOR][COLOR=#54ff54]**jack@HR-Kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**/usr/lib/x86_64-linux-gnu**[/COLOR][COLOR=#000000]$ **sudo apt-get --purge autoremove** [/COLOR]
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
0 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
[/FONT]
```____________________________________________________________________

[FONT=monospace][COLOR=#000000]**sudo apt-get --fix-broken install  **

appears to have cleared the log jam.  My normal updates have cleared and I can now install apps.

Thanks! 

 



[/COLOR][/FONT]

---

### Post by jackjump on 2023-11-02
I'd like to say thanks to all for your time and expertise.  Events like this can be baffling for a NOOB.

Regards,
Jack

---

### Post by deadflowr on 2023-11-02
If the problem has been fixed, [Please marked this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

