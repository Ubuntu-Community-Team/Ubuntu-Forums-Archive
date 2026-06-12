---
title: "Apport error from long ago"
date: 2017-07-27
forum: Installation &amp; Upgrades
---

### Post by Alligator on 2017-07-27
I've had a system error when ever I restart (from windows) for some time and always expected it would be fixed with the next version of a kernel.  Well now I can't update the kernel, so it's time to fix it - with your help. Below is the sout from the last update.

```

Hit:1 http://mirrors.accretive-networks.net/ubuntu xenial InRelease
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease                   
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Get:4 http://mirrors.accretive-networks.net/ubuntu xenial-updates InRelease [102 kB]
Hit:5 http://dl.google.com/linux/chrome/deb stable Release                     
Get:7 http://mirrors.accretive-networks.net/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [5,888 B]
Get:8 http://mirrors.accretive-networks.net/ubuntu xenial-updates/main amd64 Packages [583 kB]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [59.2 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [54.7 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [40.6 kB]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [56.2 kB]
Get:13 http://mirrors.accretive-networks.net/ubuntu xenial-updates/main i386 Packages [563 kB]
Get:14 http://mirrors.accretive-networks.net/ubuntu xenial-updates/main amd64 DEP-11 Metadata [304 kB]
Get:15 http://mirrors.accretive-networks.net/ubuntu xenial-updates/main DEP-11 64x64 Icons [203 kB]
Get:16 http://mirrors.accretive-networks.net/ubuntu xenial-updates/universe amd64 Packages [506 kB]
Hit:17 http://archive.canonical.com/ubuntu xenial InRelease                    
Get:18 http://mirrors.accretive-networks.net/ubuntu xenial-updates/universe i386 Packages [490 kB]
Get:19 http://mirrors.accretive-networks.net/ubuntu xenial-updates/universe Translation-en [197 kB]
Get:20 http://mirrors.accretive-networks.net/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [163 kB]
Get:21 http://mirrors.accretive-networks.net/ubuntu xenial-updates/universe DEP-11 64x64 Icons [207 kB]
Fetched 3,637 kB in 7s (475 kB/s)                                              
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-81 linux-headers-4.4.0-81-generic linux-image-4.4.0-81-generic linux-image-extra-4.4.0-81-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  imagemagick imagemagick-6.q16 imagemagick-common libimage-magick-perl libimage-magick-q16-perl libmagick++-6.q16-5v5 libmagickcore-6.q16-2 libmagickcore-6.q16-2-extra
  libmagickwand-6.q16-2 perlmagick xserver-common xserver-xephyr xserver-xorg-core xserver-xorg-legacy
14 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 5,053 kB of archives.
After this operation, 4,096 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://security.ubuntu.com/ubuntu xenial-security/main amd64 libmagickwand-6.q16-2 amd64 8:6.8.9.9-7ubuntu5.8 [289 kB]
Get:2 http://security.ubuntu.com/ubuntu xenial-security/main amd64 libmagickcore-6.q16-2 amd64 8:6.8.9.9-7ubuntu5.8 [1,576 kB]
Get:3 http://security.ubuntu.com/ubuntu xenial-security/main amd64 imagemagick-common all 8:6.8.9.9-7ubuntu5.8 [41.3 kB]
Get:4 http://security.ubuntu.com/ubuntu xenial-security/main amd64 imagemagick amd64 8:6.8.9.9-7ubuntu5.8 [44.9 kB]
Get:5 http://security.ubuntu.com/ubuntu xenial-security/main amd64 imagemagick-6.q16 amd64 8:6.8.9.9-7ubuntu5.8 [387 kB]
Get:6 http://security.ubuntu.com/ubuntu xenial-security/main amd64 libimage-magick-q16-perl amd64 8:6.8.9.9-7ubuntu5.8 [109 kB]
Get:7 http://security.ubuntu.com/ubuntu xenial-security/main amd64 libimage-magick-perl all 8:6.8.9.9-7ubuntu5.8 [62.4 kB]
Get:8 http://security.ubuntu.com/ubuntu xenial-security/main amd64 libmagick++-6.q16-5v5 amd64 8:6.8.9.9-7ubuntu5.8 [136 kB]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/main amd64 libmagickcore-6.q16-2-extra amd64 8:6.8.9.9-7ubuntu5.8 [59.4 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 perlmagick all 8:6.8.9.9-7ubuntu5.8 [12.5 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/main amd64 xserver-common all 2:1.18.4-0ubuntu0.3 [27.3 kB]
Get:12 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 xserver-xephyr amd64 2:1.18.4-0ubuntu0.3 [924 kB]
Get:13 http://security.ubuntu.com/ubuntu xenial-security/main amd64 xserver-xorg-legacy amd64 2:1.18.4-0ubuntu0.3 [36.0 kB]                                                                   
Get:14 http://security.ubuntu.com/ubuntu xenial-security/main amd64 xserver-xorg-core amd64 2:1.18.4-0ubuntu0.3 [1,347 kB]                                                                    
Fetched 5,053 kB in 8s (587 kB/s)                                                                                                                                                             
Preconfiguring packages ...
setting xserver-xorg-legacy/xwrapper/allowed_users from configuration file
(Reading database ... 362158 files and directories currently installed.)
Preparing to unpack .../libmagickwand-6.q16-2_8%3a6.8.9.9-7ubuntu5.8_amd64.deb ...
Unpacking libmagickwand-6.q16-2:amd64 (8:6.8.9.9-7ubuntu5.8) over (8:6.8.9.9-7ubuntu5.7) ...
Preparing to unpack .../libmagickcore-6.q16-2_8%3a6.8.9.9-7ubuntu5.8_amd64.deb ...
Unpacking libmagickcore-6.q16-2:amd64 (8:6.8.9.9-7ubuntu5.8) over (8:6.8.9.9-7ubuntu5.7) ...
Preparing to unpack .../imagemagick-common_8%3a6.8.9.9-7ubuntu5.8_all.deb ...
Unpacking imagemagick-common (8:6.8.9.9-7ubuntu5.8) over (8:6.8.9.9-7ubuntu5.7) ...
Preparing to unpack .../imagemagick_8%3a6.8.9.9-7ubuntu5.8_amd64.deb ...
Unpacking imagemagick (8:6.8.9.9-7ubuntu5.8) over (8:6.8.9.9-7ubuntu5.7) ...
Preparing to unpack .../imagemagick-6.q16_8%3a6.8.9.9-7ubuntu5.8_amd64.deb ...
Unpacking imagemagick-6.q16 (8:6.8.9.9-7ubuntu5.8) over (8:6.8.9.9-7ubuntu5.7) ...
Preparing to unpack .../libimage-magick-q16-perl_8%3a6.8.9.9-7ubuntu5.8_amd64.deb ...
Unpacking libimage-magick-q16-perl (8:6.8.9.9-7ubuntu5.8) over (8:6.8.9.9-7ubuntu5.7) ...
Preparing to unpack .../libimage-magick-perl_8%3a6.8.9.9-7ubuntu5.8_all.deb ...
Unpacking libimage-magick-perl (8:6.8.9.9-7ubuntu5.8) over (8:6.8.9.9-7ubuntu5.7) ...
Preparing to unpack .../libmagick++-6.q16-5v5_8%3a6.8.9.9-7ubuntu5.8_amd64.deb ...
Unpacking libmagick++-6.q16-5v5:amd64 (8:6.8.9.9-7ubuntu5.8) over (8:6.8.9.9-7ubuntu5.7) ...
Preparing to unpack .../libmagickcore-6.q16-2-extra_8%3a6.8.9.9-7ubuntu5.8_amd64.deb ...
Unpacking libmagickcore-6.q16-2-extra:amd64 (8:6.8.9.9-7ubuntu5.8) over (8:6.8.9.9-7ubuntu5.7) ...
Preparing to unpack .../perlmagick_8%3a6.8.9.9-7ubuntu5.8_all.deb ...
Unpacking perlmagick (8:6.8.9.9-7ubuntu5.8) over (8:6.8.9.9-7ubuntu5.7) ...
Preparing to unpack .../xserver-common_2%3a1.18.4-0ubuntu0.3_all.deb ...
Unpacking xserver-common (2:1.18.4-0ubuntu0.3) over (2:1.18.4-0ubuntu0.2) ...
Preparing to unpack .../xserver-xephyr_2%3a1.18.4-0ubuntu0.3_amd64.deb ...
Unpacking xserver-xephyr (2:1.18.4-0ubuntu0.3) over (2:1.18.4-0ubuntu0.2) ...
Preparing to unpack .../xserver-xorg-legacy_2%3a1.18.4-0ubuntu0.3_amd64.deb ...
Unpacking xserver-xorg-legacy (2:1.18.4-0ubuntu0.3) over (2:1.18.4-0ubuntu0.2) ...
Preparing to unpack .../xserver-xorg-core_2%3a1.18.4-0ubuntu0.3_amd64.deb ...
Unpacking xserver-xorg-core (2:1.18.4-0ubuntu0.3) over (2:1.18.4-0ubuntu0.2) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Setting up linux-image-extra-4.4.0-87-generic (4.4.0-87.110) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-87-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-87-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-87-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-4.4.0-87-generic; however:
  Package linux-image-extra-4.4.0-87-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.87.93); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up imagemagick-common (8:6.8.9.9-7ubuntu5.8) ...



NO APPORT REPORT WRITTEN BECAUSE THE ERROR MESSAGE INDICATES ITS A FOLLOWUP ERROR FROM A PREVIOUS FAILURE.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
Setting up libmagickcore-6.q16-2:amd64 (8:6.8.9.9-7ubuntu5.8) ...
Setting up libmagickwand-6.q16-2:amd64 (8:6.8.9.9-7ubuntu5.8) ...
Setting up imagemagick-6.q16 (8:6.8.9.9-7ubuntu5.8) ...
Setting up imagemagick (8:6.8.9.9-7ubuntu5.8) ...
Setting up libimage-magick-q16-perl (8:6.8.9.9-7ubuntu5.8) ...
Setting up libimage-magick-perl (8:6.8.9.9-7ubuntu5.8) ...
Setting up libmagick++-6.q16-5v5:amd64 (8:6.8.9.9-7ubuntu5.8) ...
Setting up libmagickcore-6.q16-2-extra:amd64 (8:6.8.9.9-7ubuntu5.8) ...
Setting up perlmagick (8:6.8.9.9-7ubuntu5.8) ...
Setting up xserver-common (2:1.18.4-0ubuntu0.3) ...
Setting up xserver-xephyr (2:1.18.4-0ubuntu0.3) ...
Setting up xserver-xorg-legacy (2:1.18.4-0ubuntu0.3) ...
setting xserver-xorg-legacy/xwrapper/allowed_users from configuration file
Setting up xserver-xorg-core (2:1.18.4-0ubuntu0.3) ...
Processing triggers for libc-bin (2.23-0ubuntu9) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Errors were encountered while processing:
 linux-image-extra-4.4.0-87-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
 

```

I cap'd the apport error.

---

### Post by oldos2er on 2017-07-27
> gzip: stdout: No space left on device Can you please post the output of ```
df -h
```

---

### Post by Alligator on 2017-07-27
```

ron@Cronluath:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           785M  9.7M  775M   2% /run
/dev/md0        720G  316G  368G  47% /
tmpfs           3.9G   41M  3.8G   2% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sdb1       331M  296M   17M  95% /boot
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           785M  132K  785M   1% /run/user/1001
tmpfs           785M   76K  785M   1% /run/user/1000

```

---

### Post by Alligator on 2017-07-27
I see that /boot is 95% used.  Here is what's in it.

```

ron@Cronluath:~$ uname -r
4.4.0-83-generic
ron@Cronluath:~$ cd -
/boot
ron@Cronluath:/boot$ ls -la
total 296046
drwxr-xr-x  4 root root     6144 Jul 27 10:20 .
drwxr-xr-x 25 root root     4096 Jul 25 08:10 ..
-rw-r--r--  1 root root  1246311 Jun 14 06:24 abi-4.4.0-81-generic
-rw-r--r--  1 root root  1246511 Jun 26 13:45 abi-4.4.0-83-generic
-rw-r--r--  1 root root  1246670 Jul 18 09:00 abi-4.4.0-87-generic
-rw-r--r--  1 root root   190356 Jun 14 06:24 config-4.4.0-81-generic
-rw-r--r--  1 root root   190356 Jun 26 13:45 config-4.4.0-83-generic
-rw-r--r--  1 root root   190356 Jul 18 09:00 config-4.4.0-87-generic
drwxr-xr-x  5 root root     8192 Jul 25 08:12 grub
-rw-r--r--  1 root root  9962636 Jun 21 11:51 initrd.img-3.13.0-57-generic
-rw-r--r--  1 root root  9962758 Jun 21 11:51 initrd.img-3.13.0-58-generic
-rw-r--r--  1 root root  9962739 Jun 21 11:51 initrd.img-3.13.0-59-generic
-rw-r--r--  1 root root  9962739 Jun 21 11:51 initrd.img-3.13.0-61-generic
-rw-r--r--  1 root root  9962062 Jun 21 11:51 initrd.img-3.13.0-62-generic
-rw-r--r--  1 root root  9962497 Jun 21 11:51 initrd.img-3.13.0-63-generic
-rw-r--r--  1 root root  9962739 Jun 21 11:51 initrd.img-3.13.0-65-generic
-rw-r--r--  1 root root  9962771 Jun 21 11:51 initrd.img-3.13.0-66-generic
-rw-r--r--  1 root root  9962352 Jun 21 11:51 initrd.img-3.13.0-67-generic
-rw-r--r--  1 root root  9962749 Jun 21 11:51 initrd.img-3.13.0-68-generic
-rw-r--r--  1 root root  9962592 Jun 21 11:51 initrd.img-3.13.0-74-generic
-rw-r--r--  1 root root  9962796 Jun 21 11:51 initrd.img-3.13.0-76-generic
-rw-r--r--  1 root root  9962394 Jun 21 11:51 initrd.img-3.13.0-79-generic
-rw-r--r--  1 root root  9962744 Jun 21 11:50 initrd.img-3.13.0-83-generic
-rw-r--r--  1 root root  9962134 Jun 21 11:50 initrd.img-4.4.0-45-generic
-rw-r--r--  1 root root 38217421 Jun 21 11:54 initrd.img-4.4.0-81-generic
-rw-r--r--  1 root root 38219790 Jul 21 07:39 initrd.img-4.4.0-83-generic
-rw-r--r--  1 root root 38216411 Jul 25 08:12 initrd.img-4.4.0-87-generic
drwx------  2 root root    12288 May 31  2011 lost+found
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3883391 Jun 14 06:24 System.map-4.4.0-81-generic
-rw-------  1 root root  3883887 Jun 26 13:45 System.map-4.4.0-83-generic
-rw-------  1 root root  3884173 Jul 18 09:00 System.map-4.4.0-87-generic
-rw-------  1 root root  7092784 Jun 14 06:24 vmlinuz-4.4.0-81-generic
-rw-------  1 root root  7092720 Jun 26 13:45 vmlinuz-4.4.0-83-generic
-rw-------  1 root root  7095888 Jul 18 09:00 vmlinuz-4.4.0-87-generic

```

Here is the procedure I use to clear /boot when upgrading.

```

Command line method:

First check your kernel version, so you won't delete the in-use kernel image, running:

uname -r
Now run this command for a list of installed kernels:

sudo dpkg --list 'linux-image*'
and delete the kernels you don't want/need anymore by running this:

sudo apt-get remove linux-image-VERSION
Replace VERSION with the version of the kernel you want to remove.

When you're done removing the older kernels, you can run this to remove ever packages you won't need anymore:

sudo apt-get autoremove
And finally you can run this to update grub kernel list:

sudo update-grub

```

---

### Post by vocx on 2017-07-27
> **Alligator said:**
> I see that /boot is 95% used.  Here is what's in it.

```

ron@Cronluath:~$ uname -r
4.4.0-83-generic
ron@Cronluath:~$ cd -
/boot
ron@Cronluath:/boot$ ls -la
total 296046
...
-rw-r--r--  1 root root  9962636 Jun 21 11:51 initrd.img-3.13.0-57-generic
-rw-r--r--  1 root root  9962758 Jun 21 11:51 initrd.img-3.13.0-58-generic
-rw-r--r--  1 root root  9962739 Jun 21 11:51 initrd.img-3.13.0-59-generic
-rw-r--r--  1 root root  9962739 Jun 21 11:51 initrd.img-3.13.0-61-generic
-rw-r--r--  1 root root  9962062 Jun 21 11:51 initrd.img-3.13.0-62-generic
-rw-r--r--  1 root root  9962497 Jun 21 11:51 initrd.img-3.13.0-63-generic
-rw-r--r--  1 root root  9962739 Jun 21 11:51 initrd.img-3.13.0-65-generic
-rw-r--r--  1 root root  9962771 Jun 21 11:51 initrd.img-3.13.0-66-generic
-rw-r--r--  1 root root  9962352 Jun 21 11:51 initrd.img-3.13.0-67-generic
-rw-r--r--  1 root root  9962749 Jun 21 11:51 initrd.img-3.13.0-68-generic
-rw-r--r--  1 root root  9962592 Jun 21 11:51 initrd.img-3.13.0-74-generic
-rw-r--r--  1 root root  9962796 Jun 21 11:51 initrd.img-3.13.0-76-generic
-rw-r--r--  1 root root  9962394 Jun 21 11:51 initrd.img-3.13.0-79-generic
-rw-r--r--  1 root root  9962744 Jun 21 11:50 initrd.img-3.13.0-83-generic
...

```

I'm sorry, but did you, or did you not solve the problem? It's not clear.

If you still have "/boot" full it is because of all the "initrd.img-" files from the 3.13 kernels. If you ran "sudo apt autoremove", and these are still there, it means they were not cleared up, so just delete them manually.
```

sudo rm /boot/initrd.img-3.13.*

# Be careful not to delete the 4.4.x files!

```

---

### Post by Alligator on 2017-07-27
I cleanup /boot and the update went off with out an error.  However, update-manager -d did not.  AND the "system program problem detected' error on reboot occurs

com.ubuntu.apport.apport-gtk-root

Vendor: Apport

```

ron@Cronluath:~$ sudo update-manager -d
[sudo] password for ron: 
Sorry, try again.
[sudo] password for ron: 
/usr/bin/update-manager:28: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk
/usr/lib/python3/dist-packages/UpdateManager/UnitySupport.py:29: PyGIWarning: Dbusmenu was imported without specifying a version first. Use gi.require_version('Dbusmenu', '0.4') before import to ensure that the right version gets loaded.
  from gi.repository import Dbusmenu, Unity
/usr/lib/python3/dist-packages/UpdateManager/UnitySupport.py:29: PyGIWarning: Unity was imported without specifying a version first. Use gi.require_version('Unity', '7.0') before import to ensure that the right version gets loaded.
  from gi.repository import Dbusmenu, Unity
ERROR:root:parse failed for '/var/lib/update-manager/meta-release-lts-development'
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 368, in download
    self.parse()
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 239, in parse
    while index_tag.step():
SystemError: E:Unable to parse package file  (1)

```

---

### Post by ajgreeny on 2017-07-27
We really need to know what kernels are still sitting on your machine so please show us the full output of ```
dpkg -l linux-image* linux-headers*
```
You may have the old 3 series kernels remaining from a previous Ubuntu version and they may not be so easily removable as the apt/synaptic package manager may not know of their existence so we may need to get down and dirty using dpkg to remove them as a start and then clean up as much as possible.

One step at a time!
Let's see the output of that command, but until we know the full situation do not start manually removing anything from /boot; we may have to do so later but not just yet.

---

### Post by vocx on 2017-07-27
> **Alligator said:**
> I cleanup /boot and the update went off with out an error.  However, update-manager -d did not.  AND the "system program problem detected' error on reboot occurs

com.ubuntu.apport.apport-gtk-root

Vendor: Apport

```

ron@Cronluath:~$ sudo update-manager -d
[sudo] password for ron: 
Sorry, try again.
[sudo] password for ron: 
/usr/bin/update-manager:28: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk
/usr/lib/python3/dist-packages/UpdateManager/UnitySupport.py:29: PyGIWarning: Dbusmenu was imported without specifying a version first. Use gi.require_version('Dbusmenu', '0.4') before import to ensure that the right version gets loaded.
  from gi.repository import Dbusmenu, Unity
/usr/lib/python3/dist-packages/UpdateManager/UnitySupport.py:29: PyGIWarning: Unity was imported without specifying a version first. Use gi.require_version('Unity', '7.0') before import to ensure that the right version gets loaded.
  from gi.repository import Dbusmenu, Unity
ERROR:root:parse failed for '/var/lib/update-manager/meta-release-lts-development'
Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 368, in download
    self.parse()
  File "/usr/lib/python3/dist-packages/UpdateManager/Core/MetaRelease.py", line 239, in parse
    while index_tag.step():
SystemError: E:Unable to parse package file  (1)

```
Stop.

Do not use "update-manager -d". What are you trying to accomplish?

The command "update-manager -d" upgrades your system to the latest development version, which is unstable. You probably don't want that.

If you want to have your system reasonable up to date, just use the normal apt commands
```

sudo apt update
sudo apt upgrade

```

If you already have the latest updates, and really wish to upgrade the entire system, that is, from Ubuntu 16.10 to 17.04, for example, then you do
```

sudo do-release-upgrade -d

```

But again, it is not clear from your posts what you ultimately intend to do. Do you want the latest version? Why?

Based on the 4.4.x kernels seen in your "/boot", you seem to be using Ubuntu 16.04 currently. This is a long term support (LTS) version, and you can stay there for a while. If you upgrade successively, you will go to 16.10, and then to 17.04, is this really what you want?

---

### Post by Alligator on 2017-07-27
```

ron@Cronluath:~$ dpkg -l linux-image* linux-headers*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  linux-headers  <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
ii  linux-headers- 4.2.0-34.39  all          Header files related to Linux ker
ii  linux-headers- 4.2.0-34.39  amd64        Linux kernel headers for version 
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
ii  linux-headers- 4.4.0-81.104 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-81.104 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-83.106 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-83.106 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0-87.110 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-87.110 amd64        Linux kernel headers for version 
ii  linux-headers- 4.4.0.87.93  amd64        Generic Linux kernel headers
un  linux-image    <none>       <none>       (no description available)
un  linux-image-4. <none>       <none>       (no description available)
rc  linux-image-4. 4.4.0-28.47  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-31.50  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-34.53  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-36.55  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-38.57  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-42.62  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-43.63  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-45.66  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-47.68  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-51.72  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-53.74  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-59.80  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-62.83  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-63.84  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-64.85  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-65.86  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-66.87  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-70.91  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-71.92  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-72.93  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-75.96  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-77.98  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-78.99  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-79.100 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-81.104 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-83.106 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-87.110 amd64        Linux kernel image for version 4.
rc  linux-image-ex 4.2.0-34.39  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-28.47  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-31.50  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-34.53  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-36.55  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-38.57  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-42.62  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-43.63  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-45.66  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-47.68  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-51.72  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-53.74  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-59.80  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-62.83  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-63.84  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-64.85  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-65.86  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-66.87  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-70.91  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-71.92  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-72.93  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-75.96  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-77.98  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-78.99  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-79.100 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-81.104 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-83.106 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-87.110 amd64        Linux kernel extra modules for ve
ii  linux-image-ge 4.4.0.87.93  amd64        Generic Linux kernel image

```

---

### Post by Alligator on 2017-07-27
Just trying to keep the latest kernel for 16.04 LTS.  Sometime ago I got this apport error.  I no longer know enough to be effective, just dangerous.

---

### Post by vocx on 2017-07-27
> **Alligator said:**
> Just trying to keep the latest kernel for 16.04 LTS.  Sometime ago I got this apport error.  I no longer know enough to be effective, just dangerous.
Okay, please do not just run every command you see without not knowing what it does. You could leave your system in an unstable state.

You already have the latest kernel for 16.04, according to the output of this command:
> **Alligator said:**
> ```

ron@Cronluath:~$ dpkg -l linux-image* linux-headers*

```


You have three kernels installed from the 4.4 series. The numbers -81, -83, and -87 just indicate minor incremental versions due to normal security updates.
```

linux-image-4.4.0-81-generic
linux-image-4.4.0-83-generic
linux-image-4.4.0-87-generic

```

You should be fine with running the one ending in -87. To confirm, run "uname -r".

Normally having one or two extra kernels is not a problem. If at some point in the future you experience a problem with the latest kernel, you may be able to solve it by going back to the previous version. So, using -87, and keeping -83 and -81 around is not an issue. As you get new updates, the old kernels will be deleted when you run "sudo apt autoremove". So, if in the future, one kernel -90 appears, you will keep -83, -87, -90, and -81 will be removed. Your original problem appeared because you had too many old kernels from the 3.13 series, but I think now you should not have them, right? Confirm with "ls -lah /boot".

Do not run "update-manager -d" if you just want to keep your system working properly. The previous output that you showed already had some strange errors, so I wonder if there are already some inconsistencies in your packages.

---

### Post by Alligator on 2017-07-27
```

ron@Cronluath:~$ uname -r
4.4.0-87-generic
ron@Cronluath:~$ cd /boot
ron@Cronluath:/boot$ ls -lah
total 156M
drwxr-xr-x  4 root root 6.0K Jul 27 13:27 .
drwxr-xr-x 25 root root 4.0K Jul 25 08:10 ..
-rw-r--r--  1 root root 1.2M Jun 14 06:24 abi-4.4.0-81-generic
-rw-r--r--  1 root root 1.2M Jun 26 13:45 abi-4.4.0-83-generic
-rw-r--r--  1 root root 1.2M Jul 18 09:00 abi-4.4.0-87-generic
-rw-r--r--  1 root root 186K Jun 14 06:24 config-4.4.0-81-generic
-rw-r--r--  1 root root 186K Jun 26 13:45 config-4.4.0-83-generic
-rw-r--r--  1 root root 186K Jul 18 09:00 config-4.4.0-87-generic
drwxr-xr-x  5 root root 8.0K Jul 27 13:27 grub
-rw-r--r--  1 root root 9.6M Jun 21 11:50 initrd.img-4.4.0-45-generic
-rw-r--r--  1 root root  37M Jun 21 11:54 initrd.img-4.4.0-81-generic
-rw-r--r--  1 root root  37M Jul 21 07:39 initrd.img-4.4.0-83-generic
-rw-r--r--  1 root root  37M Jul 27 13:27 initrd.img-4.4.0-87-generic
drwx------  2 root root  12K May 31  2011 lost+found
-rw-r--r--  1 root root 179K Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root 181K Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root 181K Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root 3.8M Jun 14 06:24 System.map-4.4.0-81-generic
-rw-------  1 root root 3.8M Jun 26 13:45 System.map-4.4.0-83-generic
-rw-------  1 root root 3.8M Jul 18 09:00 System.map-4.4.0-87-generic
-rw-------  1 root root 6.8M Jun 14 06:24 vmlinuz-4.4.0-81-generic
-rw-------  1 root root 6.8M Jun 26 13:45 vmlinuz-4.4.0-83-generic
-rw-------  1 root root 6.8M Jul 18 09:00 vmlinuz-4.4.0-87-generic

```

---

### Post by vocx on 2017-07-27
> **Alligator said:**
> ```

ron@Cronluath:~$ uname -r
4.4.0-87-generic
ron@Cronluath:~$ cd /boot
ron@Cronluath:/boot$ ls -lah
-rw-r--r--  1 root root 9.6M Jun 21 11:50 initrd.img-4.4.0-45-generic
-rw-r--r--  1 root root  37M Jun 21 11:54 initrd.img-4.4.0-81-generic
-rw-r--r--  1 root root  37M Jul 21 07:39 initrd.img-4.4.0-83-generic
-rw-r--r--  1 root root  37M Jul 27 13:27 initrd.img-4.4.0-87-generic

```
Everything looks fine, at least from the kernel side.

You still seems to have one additional "initrd" file so you can remove it.
```

sudo rm /boot/initrd.img-4.4.0-45-generic 

```

> **Alligator said:**
> ```

ron@Cronluath:~$ dpkg -l linux-image* linux-headers*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  linux-headers  <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
ii  linux-headers- 4.2.0-34.39  all          Header files related to Linux ker
ii  linux-headers- 4.2.0-34.39  amd64        Linux kernel headers for version 

```

From the previous output it seems you have some "linux-headers" for an old kernel version, so you can remove those as well, just to save some space.
```

sudo apt purge linux-headers-4.2.0-34
sudo apt purge linux-headers-4.2.0-34-generic

```

Remember you have the latest three kernels, 4.4.0-81, -83, and -87. You normally boot up the last one. If there is a new kernel update, the number may increase, so just remember to run "sudo apt autoremove", to remove the older kernels, so your "/boot" partition doesn't fill up again.

---

### Post by deadflowr on 2017-07-28
> The command "update-manager -d" upgrades your system to the latest development version, which is unstable. You probably don't want that.

Only if you're in the latest stable version.
Which they are not.

Anyway the command doesn't do anything, it only adds the option to upgrade to the development release, --when you can upgrade to the development release. (It also allows early uprades of lts to lts before the new lts hits the first point release, but that isn't anything to do with this since there is no new lts, and certainly no lts currently in the duration between the initial release and first point release period, fwiw)

When ran, the command will show the upgrade button at which point the user can click  through all the pages until the user gets to the last page, which shows the Details dropdown button and gives a brief rundown of what the download size will be and how long (based on user current network speed) it will take.
At any point before that page (And even at that page, you can still cancel) the user can opt out and cancel the upgrade with no harm no foul.

Also there is no need to ever run either update-manager or do-release-upgrade with sudo, as, unlike apt, the release upgrader has built authentication and you will be prompted for a password when the time comes.

(Bonus note: there is no more upgrade option to go to 16.10, unless your system is out-of-date somehow.
They now skip over dead releases.)

The update-manager error seen could be a number of things, but since we do not have the full detail of how the updates were ran:
> I cleanup /boot and the update went off with out an error. 

it will be hard. 
Please post what is meant by the updates ran without an error, as in how did you run/install the updates (command line, update manager, magic?)
It might help (or not)

And...
 per the thread title, all apport reports are in /var/crash and there is an apport log at /var/log/apport.log ,which from memory should output what happens with regards to apport, not with the actual crash that apport creates in /var/crash.

Hope it helps
or that I am not repeating anything anyone else has said.

---

### Post by Alligator on 2017-07-28
While doing the lastest update, I didn't get an error indicating the /boot directory was full,  see the top of this thread for the actual error msg.  The apport error comes up after returning from Windows 7.  I have a bagpipe program and CNC carving programs which I would love to have run in wine. Not a Windows fan.

Question: I have Ubuntu 16.04 LTS on my laptop as well and I don't get the 2 or 3 requests a week to update.  Why is that?

Thank you for your assistance.  
Ron

---

### Post by Alligator on 2017-07-28
I did the following
sudo apt-get update && sudo apt-get dist-upgrade

sudo apt autoremove (this was requested to remove some headers)

sudo reboot

I got the same same system error to be reported, pointing to apport.  I checked /var/crash and /var/log ( for an apport log) and there is no entry in the crash file for todays date.

```

ron@Cronluath:/var/crash$ ls -lah
total 708K
drwxrwsrwt  2 root whoopsie 4.0K Jul 27 07:35 .
drwxr-xr-x 15 root root     4.0K Jul 28  2016 ..
-rw-------  1 root whoopsie 157K Jul 25 08:12 linux-image-extra-4.4.0-87-generic.0.crash
-rw-r-----  1 root whoopsie 529K Jul 21 07:40 _usr_sbin_cupsd.0.crash
ron@Cronluath:/var/crash$ uname -r
4.4.0-87-generic

```

/var/log

```
-rw-r-----  1 root              adm       0 Jul 27 07:35 apport.log
-rw-r-----  1 root              adm     519 Jul 26 12:24 apport.log.1
-rw-r-----  1 root              adm     277 Jul 22 20:47 apport.log.2.gz
-rw-r-----  1 root              adm     241 Jul 21 07:40 apport.log.3.gz

```

---

### Post by vocx on 2017-07-28
> **deadflowr said:**
> ...
Hope it helps
or that I am not repeating anything anyone else has said.
I think you are not following this conversation well. The original poster had different issues, one of them was that he had too many old kernels, due to having upgraded his system since 14.04, probably. It's not so important at the moment, as long as he has a working 16.04. The apport error can be investigated next.

> **Alligator said:**
> ...

I got the same same system error to be reported, pointing to apport.  I checked /var/crash and /var/log ( for an apport log) and there is no entry in the crash file for todays date.

```

ron@Cronluath:/var/crash$ ls -lah
total 708K
drwxrwsrwt  2 root whoopsie 4.0K Jul 27 07:35 .
drwxr-xr-x 15 root root     4.0K Jul 28  2016 ..
-rw-------  1 root whoopsie 157K Jul 25 08:12 linux-image-extra-4.4.0-87-generic.0.crash
-rw-r-----  1 root whoopsie 529K Jul 21 07:40 _usr_sbin_cupsd.0.crash
ron@Cronluath:/var/crash$ uname -r
4.4.0-87-generic

```

/var/log

```
-rw-r-----  1 root              adm       0 Jul 27 07:35 apport.log
-rw-r-----  1 root              adm     519 Jul 26 12:24 apport.log.1
-rw-r-----  1 root              adm     277 Jul 22 20:47 apport.log.2.gz
-rw-r-----  1 root              adm     241 Jul 21 07:40 apport.log.3.gz

```
Okay. So, we solved the issue with having old kernels. But, do you still have a problem? Can you describe this problem in detail?

As far as I got:
1. You boot Windows
2. You reboot, and this time you boot Ubuntu
3. You get a graphical pop-up error message, saying something about "Apport"
4. You click continue, and the system continues working.
5. Do you experience any problems after this? Or just that initial pop-up message?

Is this the behavior you are experiencing? If not, please clarify. Can you reproduce this error, or did it only happen once or twice?

Also, what happens if you are in Ubuntu, reboot, and boot Ubuntu again? Do you see the error? You mentioned you saw this problem when you booted Windows, and then rebooted into Ubuntu. It may have something to do with hibernating the Windows partition. I don't recommend you hibernate one system and boot the other, it's better to completely turn off the OS, before booting into the other.

The Apport crash reports that you show are from a few days ago. You can safely delete them, if you don't experience the crash anymore.
```

sudo rm /var/crash/_usr_sbin_cupsd.0.crash
sudo rm /var/crash/linux-image-extra-4.4.0-87-generic.0.crash
sudo rm /var/log/apport.log.3.gz
sudo rm /var/log/apport.log.2.gz
sudo rm /var/log/apport.log.1.gz

```

> **Alligator said:**
> 
...
Question: I have Ubuntu 16.04 LTS on my laptop as well and I don't get the 2 or 3 requests a week to update.  Why is that?

Thank you for your assistance.  
Ron

This may depend on the way the updates are configured. I believe there are options in the graphical interface "Settings > Software and Updates", to control how many update options it shows. It may also show you a distribution update, for example, from 16.04 to 17.04. It really depends on the configuration. If you are running 16.04, you should normally only get updates for the next LTS version which will be 18.04, but that will take time. So, I suggest you check your options and set them to something like "check once every week".

---

### Post by Alligator on 2017-07-28
It doesn't matter if I restart from Windows or just simply do a reboot of Ubuntu.  I get a pop up window stating that there is a program error and if I want to report it.  Doing so brings up another window to authenticate and when you view the details I get the line "com.ubuntu.apport.apport-gtk.root"  and the Vendor is Apport.
Fortunately is doesn't do it on my wife's account, only mine.

---

### Post by vocx on 2017-07-28
> **Alligator said:**
> It doesn't matter if I restart from Windows or just simply do a reboot of Ubuntu.  I get a pop up window stating that there is a program error and if I want to report it.  Doing so brings up another window to authenticate and when you view the details I get the line "com.ubuntu.apport.apport-gtk.root"  and the Vendor is Apport.
Fortunately is doesn't do it on my wife's account, only mine.
Okay. What is the exact message? Maybe you can take a screenshot at this time?

I don't think you need to click "Report" or "Continue", but I believe there is a "Details" arrow that shows which files caused the crashed. Then you can "Cancel" the message.
I'm not sure but it may look like the two images in this link [https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

After this pop-up disappears, is everything working fine? Or the computer shows another problem?

It may be something crashing at the beginning, but then everything else working correctly, so it may be a relatively minor issue.

---

### Post by oldos2er on 2017-07-28
Alligator, have you tried disabling apport?

---

### Post by Alligator on 2017-07-28
ok, I don't have a screenshot, on my todo list.  I read over the Apport page and did a restart.  Here is some of the info. hopefully this will be enough for you.

```

ExecutablePath
	/usr/sbin/cupsd
Package
	cups-daemon 2.1.3-ubuntu0.2[origin:unknown]
Problem Type
	Crash
Title
	Cupsd crashed with SIGSEGV in avahi_entry_group_free()
Apport Version
	2.20.1-0unbuntu2.10


UnreportableReason
You have some obsolete package versions installed, Pleas upgrade the following package

libkmod2

```

---

### Post by vocx on 2017-07-28
> **Alligator said:**
> ok, I don't have a screenshot, on my todo list.  I read over the Apport page and did a restart.  Here is some of the info. hopefully this will be enough for you.

```

ExecutablePath
    /usr/sbin/cupsd
Package
    cups-daemon 2.1.3-ubuntu0.2[origin:unknown]
Problem Type
    Crash
Title
    Cupsd crashed with SIGSEGV in avahi_entry_group_free()
Apport Version
    2.20.1-0unbuntu2.10


UnreportableReason
You have some obsolete package versions installed, Pleas upgrade the following package

libkmod2

```

Okay, initially there were some messages about "cups" but since you had many messages it was not clear if it was part of the problem. Here it seems it's the "cups-daemon" crashing. CUPS is the Common Unix Printing System, meaning it's some service that makes your printing work. Maybe if you try printing now you'll realize it doesn't work, but maybe it does, who knows.

Anyways, I would reinstall cups. Also, the last message tells you to upgrade the "libkmod2" package as well.
```

sudo apt install --reinstall cups-daemon
sudo apt install --reinstall libkmod2

```

I am not sure if you have the correct versions for your system. Maybe when you ran "dist-upgrade" and some of those commands, some of your packages were left in an inconsistent state. But if your reinstall the package, you will get the correct version for 16.04.
```

apt policy cups-daemon
apt policy libkmod2

```
```

cups-daemon:
  Installed: 2.1.3-4
  Candidate: 2.1.3-4
  Version table:
 *** 2.1.3-4 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status

libkmod2:
  Installed: 22-1ubuntu5
  Candidate: 22-1ubuntu5
  Version table:
 *** 22-1ubuntu5 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     22-1ubuntu4 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages

```

---

### Post by Alligator on 2017-07-28
It's a fix.  THANK YOU.  I told you I was dangerous.  I'll delete the logs and endeavour to just update.  I don't know how to put a "Solved" on the thread.  Thanks again.
Ron

---

### Post by QIII on 2017-07-28
Hello!

Good deal!

Go up to Thread Tools and select "Mark this thread as solved"

---

### Post by vocx on 2017-07-28
> **Alligator said:**
> It's a fix.  THANK YOU.  I told you I was dangerous.  I'll delete the logs and endeavour to just update.  I don't know how to put a "Solved" on the thread.  Thanks again.
Ron
Keep your system up to date by running the normal update commands.
```

sudo apt update
sudo apt upgrade

```

Ubuntu 16.04 is a long term support (LTS) release, so you should be able to use it without problems for a few more years. It is supported until 2021.

In 2018 the new LTS will arrive, 18.04. At that point you may wish to upgrade to that version, or keep using 16.04 as you do now. I suggest you do plan the transition to 18.04 before 2019, so that you are not stuck running significantly old (16.04) software by then. Even two years is a very long period of time if you consider the fast-paced Linux development, so you may want to experience the improved 18.04 in due time.

---

