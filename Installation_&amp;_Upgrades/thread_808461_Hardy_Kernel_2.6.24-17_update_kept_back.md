---
title: "Hardy Kernel 2.6.24-17 update kept back"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by bford16 on 2008-05-26
There were updates available today, so I installed them.  Among the updates were the 2.6.24-17 kernel updates.  I selected to install these as well, but during the install, a Debconf prompt appeared.  The only option was to "keep local installed version."  I selected the Forward button, and the installation completed, but with a comment that the kernel updates were "kept back."  I can't figure out why.  The kernel updates installed just fine on my other two computers.  One is using Ubuntu x86_64 Hardy 8.04, and the other is using Xubuntu i386 Hardy 8.04.

I know that when a package is kept back, it usuall means a dependency is not satisfied, but I can't figure out what is needed.  Can anyone help?

```
barry@ubuntu64:~$ uname -a
Linux ubuntu64 2.6.24-16-generic #1 SMP Thu Apr 10 12:47:45 UTC 2008 x86_64 GNU/Linux

```
```
barry@ubuntu64:~$ sudo apt-get install linux-generic
[sudo] password for barry: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-generic is already the newest version.

```

---

### Post by Timal on 2008-05-27
Hello,
I've posted here as search mapped this thread and hope is similar enough to not block Barry's post - excuse me if this post should not be here (please tell me ok? ;)

Am wannabe fullTime Linux user needing MetaTrader so did Wine upgrade from 0.9.59 to 1.0~rc2...
After did 'sudo apt-get update' as last part of the upgrade the Upgrade Manager runs (either coincidence or?) saying have 20pkgs, one of which was 24-17 and as per Barry's text but I was given dropdown selection: some various ways to *view* the changes in menu.lst (as I had edited to allow default OS other than ubuntu). Totally confused by the wording of the dropdown entries I selected "...package manager..." - well believe these words in it. Basically I was given choices to [I think] keep existing, merge, update... ALL confusing and not make sense really. End result was Wine upgraded along with other pkgs. Wanted restart... boot menu showed **24-16**.
Have just copied cmds Barry used - kept fingers crossed when did apt-get as no way *that linux'd up...*
```
tim@tim-desktop:~$ uname -a
Linux tim-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

```
and:
```
tim@tim-desktop:~$ sudo apt-get install linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-16-generic linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
Not understand the *apt-get autoremove* action since not see how 24-17 ever get loaded if menu.lst has 24-16.
Basically not know what to put in menu.lst or indeed do I need do anything...

Thanks All

btw
although new to linux, it does not help usability to have DebConf offer [to me anyway] meaningless choices... hey! I just wanna install upgrade and next thing know, am involved in *kernal versions...*
I have never ever enjoyed Win and desperately want to change that grub default to **Hardy Heron** and then *finally* ditch Win totally... but - such stuff like this does put one off somewhat - lol

---

### Post by ibutho on 2008-05-27
Try the following
```
sudo aptitude update
sudo aptitude full-upgrade

```
Does that help with upgrading to the latest kernel?

---

### Post by Timal on 2008-05-27
Hi ibutho - not sure your post directed at me but I'll try anything...
partial update:
```
tim@tim-desktop:~$ sudo aptitude update
[sudo] password for tim: 
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_GB            
Hit http://gb.archive.ubuntu.com hardy Release.gpg                              
Get:1 http://gb.ar
**.....**
Fetched 62.0kB in 0s (145kB/s)
Reading package lists... Done

```

```
tim@tim-desktop:~$ sudo aptitude full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are unused and will be REMOVED:
  linux-headers-2.6.24-16 linux-headers-2.6.24-16-generic 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 68.3MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 119160 files and directories currently installed.)
Removing linux-headers-2.6.24-16-generic ...
Removing linux-headers-2.6.24-16 ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done
Building tag database... Done             
tim@tim-desktop:~$ uname -a
Linux tim-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

```

---

### Post by ibutho on 2008-05-27
The command should have installed the new kernel and removed any obsolete packages. What is the output of running 
```
dpkg -S linux-image
```

---

### Post by Arthur Archnix on 2008-05-27
Bford, try this, but don't say yes, just post the output back here if you aren't sure:
```
sudo apt-get update
sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade
```

---

### Post by wariskampar on 2008-05-27
Just write because I want to monitor this thread to find solution for my same problem here.

---

### Post by Arthur Archnix on 2008-05-27
> **wariskampar said:**
> Just write because I want to monitor this thread to find solution for my same problem here.

No need to comment just to monitor the thread waris. Just click on thread tools up near the top and choose "subscribe to this thread."

---

### Post by Timal on 2008-05-27
> **ibutho said:**
> The command should have installed the new kernel and removed any obsolete packages. What is the output of running 
```
dpkg -S linux-image
```

```
tim@tim-desktop:~$ dpkg -S linux-image
linux-image-2.6.24-17-generic: /usr/share/doc/linux-image-2.6.24-17-generic/copyright
linux-image-generic: /usr/share/doc/linux-image-generic/copyright
linux-image-2.6.24-17-generic: /usr/share/doc/linux-image-2.6.24-17-generic/changelog.Debian.gz
linux-image-2.6.24-16-generic: /usr/share/doc/linux-image-2.6.24-16-generic/changelog.Debian.gz
linux-image-2.6.24-16-generic: /usr/share/doc/linux-image-2.6.24-16-generic/copyright
linux-image-generic: /usr/share/doc/linux-image-generic
linux-image-2.6.22-14-generic: /usr/share/doc/linux-image-2.6.22-14-generic/copyright
linux-image-2.6.22-14-generic: /usr/share/doc/linux-image-2.6.22-14-generic/changelog.Debian.gz
linux-image-2.6.24-16-generic: /usr/share/doc/linux-image-2.6.24-16-generic
linux-image-2.6.22-14-generic: /usr/share/doc/linux-image-2.6.22-14-generic
linux-image-2.6.24-17-generic: /usr/share/doc/linux-image-2.6.24-17-generic
linux-image-generic: /usr/share/doc/linux-image-generic/changelog.gz

```

seeing what dpkg was and saw --status cmd, of any use?
```
tim@tim-desktop:~$ dpkg --status linux-image-2.6.24-17-generic
Package: linux-image-2.6.**24-17**-generic
Status: install ok installed
Priority: optional
Section: base
Installed-Size: 60356
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux
Version: 2.6.24-17.31
Provides: fuse-module, ivtv-modules, kvm-api-4, linux-image, linux-image-2.6, redhat-cluster-modules
Depends: coreutils | fileutils (>= 4.0), initramfs-tools (>= 0.36ubuntu6), module-init-tools (>= 3.3-pre11-4ubuntu3)
Pre-Depends: dpkg (>= 1.10.24)
Recommends: lilo (>= 19.1) | grub
Suggests: fdutils, linux-doc-2.6.24 | linux-source-2.6.24
Conflicts: hotplug (<< 0.0.20040105-1)
Description: Linux kernel image for version 2.6.24 on x86/x86_64
 This package contains the Linux kernel image for version 2.6.24 on
 x86/x86_64.
 .
 Also includes the corresponding System.map file, the modules built by the
 packager, and scripts that try to ensure that the system is not left in an
 unbootable state after an update.
 .
 Supports Generic processors.
 .
 Geared toward desktop systems.
 .
 You likely do not want to install this package directly. Instead, install
 the linux-generic meta-package, which will ensure that upgrades work
 correctly, and that supporting packages are also installed.
tim@tim-desktop:~$
```

and:
```
tim@tim-desktop:~$ dpkg --status linux-image-2.6.24-16-generic
Package: linux-image-2.6.**24-16**-generic
Status: install ok installed
Priority: optional
Section: base
Installed-Size: 60332
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux
Version: 2.6.24-16.30
Provides: fuse-module, ivtv-modules, kvm-api-4, linux-image, linux-image-2.6, redhat-cluster-modules
Depends: coreutils | fileutils (>= 4.0), initramfs-tools (>= 0.36ubuntu6), module-init-tools (>= 3.3-pre11-4ubuntu3)
Pre-Depends: dpkg (>= 1.10.24)
Recommends: lilo (>= 19.1) | grub
Suggests: fdutils, linux-doc-2.6.24 | linux-source-2.6.24
Conflicts: hotplug (<< 0.0.20040105-1)
Description: Linux kernel image for version 2.6.24 on x86/x86_64
 This package contains the Linux kernel image for version 2.6.24 on
 x86/x86_64.

```

_also tried cmd in Arthur Archnix post:_
```
(the *apt-get update* o/p)...Reading package lists... Done
tim@tim-desktop:~$ sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Starting
Starting 2
Done
Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tim@tim-desktop:~$ uname -a
Linux tim-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
tim@tim-desktop:~$ 

```

---

### Post by vincentvee on 2008-05-27
I got the upgrade, but my inspiron 1501 will not boot to it, well kind of, it boots, kives me a white screen and a cursor, nothing else, anyone know how i might remove it and re-install it again? or even if that will fix my problem....i dunno, but i got a heap of work to get through and don't wanna lose the previous kernel as that is what i am booted into at the moment

---

### Post by Evanmakundi on 2008-05-27
> **wariskampar said:**
> Just write because I want to monitor this thread to find solution for my same problem here.
I also installed this update and end up with my network connectivity being killed completely. I am using HP6710S Laptop. I am now searching the forum using another machine trying to get some help to restore my network connectivity.

---

### Post by ibutho on 2008-05-27
> **Timal said:**
> ```
tim@tim-desktop:~$ dpkg -S linux-image
linux-image-2.6.24-17-generic: /usr/share/doc/linux-image-2.6.24-17-generic/copyright
linux-image-generic: /usr/share/doc/linux-image-generic/copyright
linux-image-2.6.24-17-generic: /usr/share/doc/linux-image-2.6.24-17-generic/changelog.Debian.gz
linux-image-2.6.24-16-generic: /usr/share/doc/linux-image-2.6.24-16-generic/changelog.Debian.gz
linux-image-2.6.24-16-generic: /usr/share/doc/linux-image-2.6.24-16-generic/copyright
linux-image-generic: /usr/share/doc/linux-image-generic
linux-image-2.6.22-14-generic: /usr/share/doc/linux-image-2.6.22-14-generic/copyright
linux-image-2.6.22-14-generic: /usr/share/doc/linux-image-2.6.22-14-generic/changelog.Debian.gz
linux-image-2.6.24-16-generic: /usr/share/doc/linux-image-2.6.24-16-generic
linux-image-2.6.22-14-generic: /usr/share/doc/linux-image-2.6.22-14-generic
linux-image-2.6.24-17-generic: /usr/share/doc/linux-image-2.6.24-17-generic
linux-image-generic: /usr/share/doc/linux-image-generic/changelog.gz

```

seeing what dpkg was and saw --status cmd, of any use?
```
tim@tim-desktop:~$ dpkg --status linux-image-2.6.24-17-generic
Package: linux-image-2.6.**24-17**-generic
Status: install ok installed
Priority: optional
Section: base
Installed-Size: 60356
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux
Version: 2.6.24-17.31
Provides: fuse-module, ivtv-modules, kvm-api-4, linux-image, linux-image-2.6, redhat-cluster-modules
Depends: coreutils | fileutils (>= 4.0), initramfs-tools (>= 0.36ubuntu6), module-init-tools (>= 3.3-pre11-4ubuntu3)
Pre-Depends: dpkg (>= 1.10.24)
Recommends: lilo (>= 19.1) | grub
Suggests: fdutils, linux-doc-2.6.24 | linux-source-2.6.24
Conflicts: hotplug (<< 0.0.20040105-1)
Description: Linux kernel image for version 2.6.24 on x86/x86_64
 This package contains the Linux kernel image for version 2.6.24 on
 x86/x86_64.
 .
 Also includes the corresponding System.map file, the modules built by the
 packager, and scripts that try to ensure that the system is not left in an
 unbootable state after an update.
 .
 Supports Generic processors.
 .
 Geared toward desktop systems.
 .
 You likely do not want to install this package directly. Instead, install
 the linux-generic meta-package, which will ensure that upgrades work
 correctly, and that supporting packages are also installed.
tim@tim-desktop:~$
```

and:
```
tim@tim-desktop:~$ dpkg --status linux-image-2.6.24-16-generic
Package: linux-image-2.6.**24-16**-generic
Status: install ok installed
Priority: optional
Section: base
Installed-Size: 60332
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux
Version: 2.6.24-16.30
Provides: fuse-module, ivtv-modules, kvm-api-4, linux-image, linux-image-2.6, redhat-cluster-modules
Depends: coreutils | fileutils (>= 4.0), initramfs-tools (>= 0.36ubuntu6), module-init-tools (>= 3.3-pre11-4ubuntu3)
Pre-Depends: dpkg (>= 1.10.24)
Recommends: lilo (>= 19.1) | grub
Suggests: fdutils, linux-doc-2.6.24 | linux-source-2.6.24
Conflicts: hotplug (<< 0.0.20040105-1)
Description: Linux kernel image for version 2.6.24 on x86/x86_64
 This package contains the Linux kernel image for version 2.6.24 on
 x86/x86_64.

```

_also tried cmd in Arthur Archnix post:_
```
(the *apt-get update* o/p)...Reading package lists... Done
tim@tim-desktop:~$ sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Starting
Starting 2
Done
Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tim@tim-desktop:~$ uname -a
Linux tim-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
tim@tim-desktop:~$ 

```

The output you posted shows that the kernel 2.6.24-17-generic was successfully installed. You probably need to reboot in order to use the new kernel.

---

### Post by Timal on 2008-05-27
ibutho - Thanks for getting back on this. Rebooted and was only presented with 24-16 in grub menu.
1. Is there a way to put 24-17 reference into menu.lst?
2. poss to backout *apparent* 24-17 upate and force or? another update?
3. if do (2) then menu.lst may still remain as currently is?
4. used *sudo gedit /boot/grub/menu.lst* maybe this is incorrect?
5. maybe can rollback to virgin menu.lst...

6. From what you say 24-17 installed. Why refs to 24-16 still exist?

tia

```
tim@tim-desktop:~$ uname -a
Linux tim-desktop 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
tim@tim-desktop:~$ 

```

dpkg -S linux-image
gives same o/p

dpkg --status linux-image-2.6.24-16-generic
dpkg --status linux-image-2.6.24-17-generic
gives same o/p

---

### Post by ibutho on 2008-05-27
Try uninstalling and then reinstalling linux-image-2.6.24-17-generic e.g.
```
sudo aptitude remove linux-image-2.6.24-17-generic
sudo aptitude install linux-image-2.6.24-17-generic
```

---

### Post by skip mcshwang on 2008-05-27
I just manually edited menu.lst to boot 2.6.24-17-generic. Seems to have worked.

```
skip@skip-desktop:~$ uname -r
2.6.24-17-generic
```

---

### Post by wariskampar on 2008-05-28
Sorry for my noob question; how you manually edit menu.lst . 
sudo gedit menu.lst?

---

### Post by Arthur Archnix on 2008-05-28
```
gksudo gedit /boot/grub/menu.lst
```
Change the default value to the number you want. Grub starts counting at zero, so the first entry you see (scroll way down) is number zero. Look for the new kernel, count which position its in, subtract 1 and make that the new default.

---

### Post by Timal on 2008-05-28
> **ibutho said:**
> Try uninstalling and then reinstalling linux-image-2.6.24-17-generic e.g.
```
sudo aptitude remove linux-image-2.6.24-17-generic
sudo aptitude install linux-image-2.6.24-17-generic
```

Thanks ibutho, o/p for *remove* below and I said **q** cause seems major? backout...
Please reconfirm that I should do remove > install
Thank you

```
tim@tim-desktop:~$ sudo aptitude remove linux-image-2.6.24-17-generic
[sudo] password for tim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following packages are BROKEN:
  linux-image-generic linux-restricted-modules-2.6.24-17-generic 
  linux-ubuntu-modules-2.6.24-17-generic 
The following packages have been kept back:
  gnome-about gnome-desktop-data libgnome-desktop-2 
The following packages will be REMOVED:
  linux-image-2.6.24-17-generic 
0 packages upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 61.8MB will be freed.
The following packages have unmet dependencies:
  linux-image-generic: Depends: linux-image-2.6.24-17-generic but it is not installable
  linux-restricted-modules-2.6.24-17-generic: Depends: linux-image-2.6.24-17-generic but it is not installable
  linux-ubuntu-modules-2.6.24-17-generic: Depends: linux-image-2.6.24-17-generic but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux-generic
linux-image-generic
linux-restricted-modules-2.6.24-17-generic
linux-ubuntu-modules-2.6.24-17-generic

Downgrade the following packages:
linux-restricted-modules-generic [2.6.24.17.19 (hardy-updates, now) ->
2.6.24.16.18 (hardy)]

Score is 356

Accept this solution? [Y/n/q/?] 

```

---

### Post by Arthur Archnix on 2008-05-28
First of all timal, don't use aptitude. There are two methods, apt and aptitude. Use one or the other. And aptitude has a bit of a learning  curve, and everyone on the forums pretty much just uses apt. So anytime you see "aptitude" anything, just replace it with the apt-get command, or apt-cache if you're just searching for packages.

Secondly, if you've successfully updated the kernel but got a debconf question thingy like the OP did, then you had probably made significant changes to your boot meny list. Things like removing the commented lines it suggested you don't uncomment or remove. That sort of thing.

If this is what's happened then reinstalling the kernel won't help. You'll just get asked the same question, and if you answer it the same will be right back where you started. Instead, you need to either automagically add an entry for the installed kernel or manually add it.

To try and add it automatically do this:
```
sudo update-grub
```
If that doesn't work, then post the output of 
```
cd /boot && ls
```
And also the current output of 
```
cat /boot/grub/menu.lst
```

---

### Post by Timal on 2008-05-28
Ok Arthur, finally uname -a gives 24-17.
I ended up finding base menu.lst and did apt-get remove,install and update-grub for good measure. Eventually, menu.lst updated and now has 22-17,16,14 versions with generic and generic (recovery mode) each + memtest, separator title and windows. and... debconf never ran either.

Yes... I did mod menu.lst originally. Two mods. c/10/3/ and c/0/4/ for timeout and default respectively. For each mod I added comment line stating what done.

(0)
Are all the menu.lst Title'd entries needed - do they come useful or is not really what I need mess with?

(1)
Please tell me this - IF mod menu.lst to alter timeout and default THEN am I causing system to see saved/updated file as foreign? ie, this going to always happen?

(2)
Is possible to say reinsert/make known or whatever is terminology menu.lst so that no issues...

TBH, I'd quite happily take shotgun to my box and start anew with **only linux** but reality is different and work life is knitted into that pseudo OS which is the bane of many peoples life. In a nutshell, until I get MetaTrader 'trading' as it does in win (that includes  MetaEditor's inline syntax help, fonts, popups, ie, 100% identical functionality), then all of my yearnings to come over to the true OS universe is simply not going to happen.

(3)
Should you or for that matter anyone else be experiencing live trading using MetaTrader under wine or water or ... ;), please do tell all.

In meantime - please accept my complete thank you's for all posters that have kept throwing stuff into the cook pot and allowing for me to [apparently:] get back on track... You all give of your physical and mental time - such help is invaluable and [for me at least] shows that global netizens are the 'Right Stuff' :cool:

I do so hope that others have had some success too.

Regards

;)

---

### Post by wariskampar on 2008-05-28
i still dont get it. i do sudo update-grub but afterward still running on 2.6.24.16 kernel. 

aznan@aznan-laptop:~$ cd /boot && ls
abi-2.6.24-16-generic             initrd.img-2.6.24-17-generic
abi-2.6.24-17-generic             initrd.img-2.6.24-17-generic.bak
config-2.6.24-16-generic          memtest86+.bin
config-2.6.24-17-generic          System.map-2.6.24-16-generic
grub                              System.map-2.6.24-17-generic
initrd.img-2.6.24-16-generic      vmlinuz-2.6.24-16-generic
initrd.img-2.6.24-16-generic.bak  vmlinuz-2.6.24-17-generic

aznan@aznan-laptop:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=a3972a39-4b18-43b1-9848-f5788689ccbf ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=false

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=false

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=a3972a39-4b18-43b1-9848-f5788689ccbf ro pci=routeirq
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

aznan@aznan-laptop:~$

---

### Post by wariskampar on 2008-05-28
OK. Problem solve. I manually edit my menu.lst. below 2.6.24-16, i add entry for 2.6.24-17. it solves my problem. now, i can choose between 16 and 17 in the Startup Manager and during re-boot. However, during reboot,2.6.24-17 kernel is placed below 16. How do I make 17 on top so that my sys will straight away boot to it if i forgot to choose. I believe
Arthur Archnix already explain it but still not understand.

---

### Post by Timal on 2008-05-28
wariskampar
afaik, you have two choices:
(1) the added 24-17 entry can be cut and repasted _above_ the 24-16 entry or
(2) near top of file is a line having the command word **default** and a number.
This number is the *entry number* which is selected by Grub.
Probably the number is **0** (counting starts from zero and is the number of entries and each entry has **Title** keyword, yes?) If you count all 'Title' keywords you will have the number of entries.

In your case you say that get choice of 2: 16 and then 17.
Ok then, that's two entries, entry 1 and entry 2.

Since Grub counts starting from _zero_ it will see entry 1 (the 24-16) as **0**. Similarly, Grub sees entry 2 (the 24-17 which you put *after* 16) as **1**

So going back to the line near top of file, having the command word **default** and a number - that number is the number that Grub sees, the entry number. 0,1,2,...

Note that in my menu.lst is a separator Title line with words like "other operating systems", ok?
After that separator Title line entry, I have proper entry for windows...
So, looks like you have 16, 17, a separator Title line, windows, yes? That makes 1,2,3,4 if count Title keywords and 0,1,2,3 as seen by Grub.

You must count this Title entry just like proper entries like your 16,17 ones. Is just way to allow comments to be printed on boot menu afaik.

hth

---

