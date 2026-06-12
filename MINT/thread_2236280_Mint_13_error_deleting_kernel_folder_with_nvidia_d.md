---
title: "Mint 13 error deleting kernel folder with nvidia driver when a kernel is deleted."
date: 2014-07-25
forum: MINT
---

### Post by Cavsfan on 2014-07-25
Does any one know why I get this over and over every time I delete an old kernel:

```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get purge linux-headers-3.2.0-64 linux-headers-3.2.0-64-generic linux-image-3.2.0-64-generic
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.2.0-64* linux-headers-3.2.0-64-generic* linux-image-3.2.0-64-generic*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 218 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 238747 files and directories currently installed.)
Removing linux-headers-3.2.0-64-generic ...
Removing linux-headers-3.2.0-64 ...
Removing linux-image-3.2.0-64-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-64-generic /boot/vmlinuz-3.2.0-64-generic
dkms: removing: nvidia-331 331.20 (3.2.0-64-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  nvidia-331
Version: 331.20
Kernel:  3.2.0-64-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia_331.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-64-generic/kernel/drivers/char/drm/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod......

DKMS: uninstall completed.
dkms: removing: virtualbox-guest 4.1.12 (3.2.0-64-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  virtualbox-guest
Version: 4.1.12
Kernel:  3.2.0-64-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxguest.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-64-generic/updates/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxsf.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-64-generic/updates/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxvideo.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-64-generic/updates/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-64-generic /boot/vmlinuz-3.2.0-64-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-64-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-64-generic /boot/vmlinuz-3.2.0-64-generic
Generating grub.cfg ...
Found background image: skull-wallpapers-23.jpg
Adding Precise Pangolin 12.04, Trusty Tahr 14.04, Utopic Unicorn 14.10 (Devel Branch), Mint 13 Maya, Mint 17 Qiana and Windows 7
done
Purging configuration files for linux-image-3.2.0-64-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-64-generic /boot/vmlinuz-3.2.0-64-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-64-generic /boot/vmlinuz-3.2.0-64-generic
[COLOR=#ff0000]dpkg: warning: while removing linux-image-3.2.0-64-generic, directory '/lib/modules/3.2.0-64-generic/kernel/drivers/char' not empty so not removed.[/COLOR]

```

Look for the red line at the bottom. I always end up having to do this to remove the folder:
```
cavsfan@cavsfan-MS-7529:~$ sudo rm -r -v /lib/modules/3.2.0-64-generic/kernel/drivers/char
[sudo] password for cavsfan: 
removed directory: `/lib/modules/3.2.0-64-generic/kernel/drivers/char/drm'
removed directory: `/lib/modules/3.2.0-64-generic/kernel/drivers/char'
```

And I know that is not right. It should be automagically removed.

---

### Post by oldfred on 2014-07-25
I do not have a drm folder in my /lib/modules/3.2.0-64-generic/kernel/drivers/char folder. 
I have not deleted that kernel yet myself.

Are you installing something that creates that folder and since not uninstalled it does not get deleted and creates an issue?

---

### Post by Cavsfan on 2014-07-27
> **oldfred said:**
> I do not have a drm folder in my /lib/modules/3.2.0-64-generic/kernel/drivers/char folder. 
I have not deleted that kernel yet myself.

Are you installing something that creates that folder and since not uninstalled it does not get deleted and creates an issue?

It appears to have this file in each kernel for that folder: /lib/modules/3.2.0-67-generic/kernel/drivers/char/drm/[COLOR=#ff0000]nvidia_331.ko[/COLOR] 
You can see from the output in the first post that this file is deleted by DKMS during kernel deletion but the folder does not get deleted.
It's been doing this ever time I remove a kernel.

I have the Nvidia driver 331-20 and xorg-edgers ppa installed.
```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
ii  nvidia-331                                331.20-0ubuntu1~xedgers~precise1                     NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                             1:0.2.44.2                                           Find obsolete NVIDIA drivers
ii  nvidia-persistenced                       331.20-0ubuntu1~xedgers~precise1                     Load the NVIDIA kernel driver and create device files
ii  nvidia-settings-331                       331.20-0ubuntu1~xedgers~precise1                     Tool for configuring the NVIDIA graphics driver
```

---

### Post by oldfred on 2014-07-27
Mint must not put nVidia in the same place when installed, but then did not update uninstaller.

My nVidia is in ( I have the updates version)
/lib/modules/3.2.0-67-generic/updates/dkms/nvidia_331_updates.ko

---

### Post by Cavsfan on 2014-07-27
I looked at my Precise install and it had the same driver as you have. So, I removed the x-swat/x-updates drivers and installed nvidia-331-updates but it put it in the same directory as the problematic on was in:
Look for the red. So it looks like this may not have solved the problem. I don't know why it is installing the driver in a different location than your install is and my precise install is.
```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get install nvidia-331-updates
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  lib32gcc1 libc6-i386 nvidia-settings
Suggested packages:
  nvidia-331-updates-uvm
The following NEW packages will be installed:
  lib32gcc1 libc6-i386 nvidia-331-updates nvidia-settings
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 80.8 MB of archives.
After this operation, 247 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com/ubuntu/ precise-updates/main libc6-i386 amd64 2.15-0ubuntu10.5 [3,992 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ precise/main lib32gcc1 amd64 1:4.6.3-1ubuntu5 [54.1 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ precise-updates/restricted nvidia-331-updates amd64 331.38-0ubuntu0.0.1 [75.8 MB]
Get:4 http://archive.ubuntu.com/ubuntu/ precise-updates/main nvidia-settings amd64 331.20-0ubuntu0.0.1 [971 kB]                                                      
Fetched 80.8 MB in 58s (1,388 kB/s)                                                                                                                                  
Selecting previously unselected package libc6-i386.
(Reading database ... 212232 files and directories currently installed.)
Unpacking libc6-i386 (from .../libc6-i386_2.15-0ubuntu10.5_amd64.deb) ...
Selecting previously unselected package lib32gcc1.
Unpacking lib32gcc1 (from .../lib32gcc1_1%3a4.6.3-1ubuntu5_amd64.deb) ...
Selecting previously unselected package nvidia-331-updates.
Unpacking nvidia-331-updates (from .../nvidia-331-updates_331.38-0ubuntu0.0.1_amd64.deb) ...
Selecting previously unselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_331.20-0ubuntu0.0.1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up libc6-i386 (2.15-0ubuntu10.5) ...
Setting up lib32gcc1 (1:4.6.3-1ubuntu5) ...
Setting up nvidia-331-updates (331.38-0ubuntu0.0.1) ...
update-alternatives: using /usr/lib/nvidia-331-updates/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/nvidia-331-updates/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/share/nvidia-331-updates/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-331-updates
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
Loading new nvidia-331-updates-331.38 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-67-generic
Building for architecture x86_64
Building initial module for 3.2.0-67-generic
Done.

nvidia_331_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to [COLOR=#ff0000]/lib/modules/3.2.0-67-generic/kernel/drivers/char/drm/
[/COLOR]
depmod....

DKMS: install completed.
Setting up nvidia-settings (331.20-0ubuntu0.0.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-67-generic

```

```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep nvidia
ii  nvidia-331-updates                        331.38-0ubuntu0.0.1                                  NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-common                             1:0.2.44.2                                           Find obsolete NVIDIA drivers
ii  nvidia-settings                           331.20-0ubuntu0.0.1                                  Tool for configuring the NVIDIA graphics driver

```

Edit: I had x-swat/x-updates ppa not xorg-edgers ppa.

---

### Post by Cavsfan on 2014-07-27
I'm hoping that since it installed the driver in **/lib/modules/3.2.0-67-generic/kernel/drivers/char/drm/nvidia_331_updates.ko** that it knows that and uninstalls it from that directory. 
Not sure if that will happen. Guess I have to wait until the that kernel needs removed.

---

### Post by oldfred on 2014-07-27
I do not use ppa, but just the repository.

Perhaps that is why we have to always make sure we purge installs of nVidia when installed from a different source as they install to different locations?

---

### Post by Cavsfan on 2014-07-27
> **oldfred said:**
> I do not use ppa, but just the repository.

Perhaps that is why we have to always make sure we purge installs of nVidia when installed from a different source as they install to different locations?

I didn't use any ppa with Precise and didn't think I did with Mint 13 but when I checked yep I sure did.

I purged the ppa and removed the driver from the ppa and re-installed one one from the repos. It still installed it in the same folder that I had the problem with so maybe I'll need to try that again.

My machine is not that new any more and my Geforce 9800GT 1GB card is not too bad but it's definitely not top of the line and doesn't need cutting edge drivers. 
I cannot even update my Windows 7 driver or it will mess my system up.

I'll take another look at Mint 13 when I get a chance and report back.

---

### Post by Cavsfan on 2014-07-28
I purged the other driver and installed nvidia-331 (331.20) but it still put it in that odd directory:

```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get install nvidia-331
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  nvidia-settings
Suggested packages:
  nvidia-331-uvm
The following NEW packages will be installed:
  nvidia-331 nvidia-settings
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 76.3 MB of archives.
After this operation, 236 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://archive.ubuntu.com/ubuntu/ precise-updates/restricted nvidia-331 amd64 331.20-0ubuntu0.0.2 [75.4 MB]
Get:2 http://archive.ubuntu.com/ubuntu/ precise-updates/main nvidia-settings amd64 331.20-0ubuntu0.0.1 [971 kB]                                                                                                                              
Fetched 76.3 MB in 5min 58s (213 kB/s)                                                                                                                                                                                                       
Selecting previously unselected package nvidia-331.
(Reading database ... 212588 files and directories currently installed.)
Unpacking nvidia-331 (from .../nvidia-331_331.20-0ubuntu0.0.2_amd64.deb) ...
Selecting previously unselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_331.20-0ubuntu0.0.1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up nvidia-331 (331.20-0ubuntu0.0.2) ...
update-alternatives: using /usr/lib/nvidia-331/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/nvidia-331/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/share/nvidia-331/glamor.conf to provide /usr/share/X11/xorg.conf.d/glamoregl.conf (glamor_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia-331
DEBUG:Parsing /usr/share/nvidia-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/nvidia-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/nvidia-common/quirks/dell_latitude
Loading new nvidia-331-331.20 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-67-generic
Building for architecture x86_64
Building initial module for 3.2.0-67-generic
Done.

nvidia_331:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-67-generic/kernel/drivers/char/[COLOR=#ff0000]drm[/COLOR]/

depmod....

DKMS: install completed.
Setting up nvidia-settings (331.20-0ubuntu0.0.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-67-generic

```

It suggests nvidia-331-uvm do you think I need that or any other packages?

---

### Post by Cavsfan on 2014-07-28
Went ahead and installed nvidia-331-uvm but it put the driver in the same folder as before.

---

### Post by Cavsfan on 2014-07-29
I guess I'm not going to worry about it. If I have to delete that directory manually I will. It's hardly worth doing a clean install.
Just glad I can use this command **sudo rm -r -v /lib/modules/3.2.0-64-generic/kernel/drivers/char** because it complains about deleting a folder with something in it otherwise.

I do everything though CLI so I can see if the folder is not deleted when the kernel is.

---

### Post by Cavsfan on 2014-08-09
Is it just me or what? :p Mint 17 Qiana also puts the nvidia driver in **/lib/modules/3.13.0-24-generic/kernel/drivers/char/drm/nvidia_331.ko**.
I never added any ppa or anything.

But it does successfully remove and replace it when it gets updated, Mint 13 does not. But still I can live with it.

---

