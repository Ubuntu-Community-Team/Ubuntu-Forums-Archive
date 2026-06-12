---
title: "Can't upgrade software because /boot is full"
date: 2017-08-06
forum: Installation &amp; Upgrades
---

### Post by ts1971 on 2017-08-06
Hi,

I am unable to install ubuntu's suggested updates because my /boot partition is full.

Here's the relevant df / ls output:

```
fred@fred-ThinkPad-P70:/boot$ df /boot
Filesystem     1K-blocks   Used Available Use% Mounted on
/dev/sda1         482922 475240         0 100% /boot


fred@fred-ThinkPad-P70:/boot$ ls -l /boot
total 465811
-rw-r--r-- 1 root root  1245512 Mar  3 11:25 abi-4.4.0-66-generic
-rw-r--r-- 1 root root  1245659 Mar 22 09:11 abi-4.4.0-70-generic
-rw-r--r-- 1 root root  1245659 Mar 24 08:20 abi-4.4.0-71-generic
-rw-r--r-- 1 root root  1245659 Mar 31 10:14 abi-4.4.0-72-generic
-rw-r--r-- 1 root root  1246246 Apr 20 05:02 abi-4.4.0-75-generic
-rw-r--r-- 1 root root  1246312 Apr 27 11:24 abi-4.4.0-78-generic
-rw-r--r-- 1 root root  1246311 May 17 15:09 abi-4.4.0-79-generic
-rw-r--r-- 1 root root  1246311 Jun 14 05:24 abi-4.4.0-81-generic
-rw-r--r-- 1 root root  1246511 Jun 26 12:45 abi-4.4.0-83-generic
-rw-r--r-- 1 root root  1246670 Jul 18 08:00 abi-4.4.0-87-generic
-rw-r--r-- 1 root root   190247 Mar  3 11:25 config-4.4.0-66-generic
-rw-r--r-- 1 root root   190236 Mar 22 09:11 config-4.4.0-70-generic
-rw-r--r-- 1 root root   190236 Mar 24 08:20 config-4.4.0-71-generic
-rw-r--r-- 1 root root   190236 Mar 31 10:14 config-4.4.0-72-generic
-rw-r--r-- 1 root root   190214 Apr 20 05:02 config-4.4.0-75-generic
-rw-r--r-- 1 root root   190355 Apr 27 11:24 config-4.4.0-78-generic
-rw-r--r-- 1 root root   190356 May 17 15:09 config-4.4.0-79-generic
-rw-r--r-- 1 root root   190356 Jun 14 05:24 config-4.4.0-81-generic
-rw-r--r-- 1 root root   190356 Jun 26 12:45 config-4.4.0-83-generic
-rw-r--r-- 1 root root   190356 Jul 18 08:00 config-4.4.0-87-generic
drwxr-xr-x 5 root root     1024 Jul 25 10:40 grub
-rw-r--r-- 1 root root 38927746 Mar  8 05:08 initrd.img-4.4.0-66-generic
-rw-r--r-- 1 root root 38933912 Mar 28 01:16 initrd.img-4.4.0-70-generic
-rw-r--r-- 1 root root 38934736 Mar 30 02:37 initrd.img-4.4.0-71-generic
-rw-r--r-- 1 root root 38933645 Apr  5 03:24 initrd.img-4.4.0-72-generic
-rw-r--r-- 1 root root 38935798 Apr 25 04:25 initrd.img-4.4.0-75-generic
-rw-r--r-- 1 root root 38935726 May 16 11:25 initrd.img-4.4.0-78-generic
-rw-r--r-- 1 root root 38935052 Jun  6 09:17 initrd.img-4.4.0-79-generic
-rw-r--r-- 1 root root 38934437 Jun 19 13:50 initrd.img-4.4.0-81-generic
-rw-r--r-- 1 root root 38938304 Jun 29 12:28 initrd.img-4.4.0-83-generic
drwx------ 2 root root    12288 Oct 31  2016 lost+found
-rw-r--r-- 1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r-- 1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r-- 1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw------- 1 root root  3883990 Mar  3 11:25 System.map-4.4.0-66-generic
-rw------- 1 root root  3882277 Mar 22 09:11 System.map-4.4.0-70-generic
-rw------- 1 root root  3882277 Mar 24 08:20 System.map-4.4.0-71-generic
-rw------- 1 root root  3882277 Mar 31 10:14 System.map-4.4.0-72-generic
-rw------- 1 root root  3883390 Apr 20 05:02 System.map-4.4.0-75-generic
-rw------- 1 root root  3882872 Apr 27 11:24 System.map-4.4.0-78-generic
-rw------- 1 root root  3883279 May 17 15:09 System.map-4.4.0-79-generic
-rw------- 1 root root  3883391 Jun 14 05:24 System.map-4.4.0-81-generic
-rw------- 1 root root  3883887 Jun 26 12:45 System.map-4.4.0-83-generic
-rw------- 1 root root  3884173 Jul 18 08:00 System.map-4.4.0-87-generic
-rw------- 1 root root  7087024 Mar  3 11:25 vmlinuz-4.4.0-66-generic
-rw------- 1 root root  7083344 Mar 22 09:11 vmlinuz-4.4.0-70-generic
-rw------- 1 root root  7083344 Mar 24 08:20 vmlinuz-4.4.0-71-generic
-rw------- 1 root root  7083248 Mar 31 10:14 vmlinuz-4.4.0-72-generic
-rw------- 1 root root  7081872 Apr 20 05:02 vmlinuz-4.4.0-75-generic
-rw------- 1 root root  7089552 Apr 27 11:24 vmlinuz-4.4.0-78-generic
-rw------- 1 root root  7091696 May 17 15:09 vmlinuz-4.4.0-79-generic
-rw------- 1 root root  7092784 Jun 14 05:24 vmlinuz-4.4.0-81-generic
-rw------- 1 root root  7092720 Jun 26 12:45 vmlinuz-4.4.0-83-generic
-rw------- 1 root root  7095888 Jul 18 08:00 vmlinuz-4.4.0-87-generic

```

I guess that the initrd.img-x.x.x-xx-generic files are old kernels and that that's the problem.  Here is unaame -r:

```
fred@fred-ThinkPad-P70:/boot$ uname -r
4.4.0-75-generic

```

After googling around  a bit I tried this to no avail:

```
fred@fred-ThinkPad-P70:/boot$ sudo apt-get purge linux-image-4.4.0-66-generic 
[sudo] password for fred: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-66-generic : Depends: linux-image-4.4.0-66-generic but it is not going to be installed
 linux-image-extra-4.4.0-89-generic : Depends: linux-image-4.4.0-89-generic but it is not going to be installed
 linux-image-generic : Depends: linux-image-4.4.0-89-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Can someone plesae point me in the right direction here?  Can I just rm the old files or will that mess up some kind of database?

Thanks!

---

### Post by QIII on 2017-08-06
It is very, very dangerous to rm system files.  You may end up with an unusable machine.

You have a number of older kernels taking up space.  If you clear them up, you will make more space.

Please try

```
sudo apt-get autoremove
``` if you are using a release prior to 16.04 or ```
sudo apt autoremove
``` for a later release.

If that does not work, you may use your software management GUI to remove older kernels -- but please ask for a bit more guidance before you do so.

---

### Post by ts1971 on 2017-08-06
Thanks for the quick reply.  According to the system details I am running 16.04 LTS.  I tried the 'apt autoremove' but it failed because of some unmet dependencies on the newest kernel.  I'm guessing it must have run out of disk on the most recent update and that's what left it in this state.  It then suggested that I try the '-f' flag, but that failed as well because of the full /boot partition.    Here is the whole session:

```

fred@fred-ThinkPad-P70:/boot$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-89-generic : Depends: linux-image-4.4.0-89-generic but it is not installed
 linux-image-generic : Depends: linux-image-4.4.0-89-generic but it is not installed
E: Unmet dependencies. Try using -f.
fred@fred-ThinkPad-P70:/boot$ 
fred@fred-ThinkPad-P70:/boot$ 
fred@fred-ThinkPad-P70:/boot$ sudo apt -f autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-image-4.4.0-89-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following packages will be REMOVED:
  deluge-common libappindicator1 libblas-common libblas3 libgfortran3 libglade2-0 libindicator7 liblapack3 libllvm3.8 libmikmod3 libmircommon5 libportmidi0 libsdl-image1.2 libsdl-mixer1.2
  libsdl-ttf2.0-0 libsmpeg0 libtorrent-rasterbar8 linux-headers-4.4.0-66 linux-headers-4.4.0-66-generic linux-headers-4.4.0-70 linux-headers-4.4.0-70-generic linux-headers-4.4.0-71
  linux-headers-4.4.0-71-generic linux-headers-4.4.0-72 linux-headers-4.4.0-72-generic linux-headers-4.4.0-78 linux-headers-4.4.0-78-generic linux-headers-4.4.0-79 linux-headers-4.4.0-79-generic
  linux-headers-4.4.0-81 linux-headers-4.4.0-81-generic linux-image-4.4.0-66-generic linux-image-4.4.0-70-generic linux-image-4.4.0-71-generic linux-image-4.4.0-72-generic linux-image-4.4.0-78-generic
  linux-image-4.4.0-79-generic linux-image-4.4.0-81-generic linux-image-extra-4.4.0-66-generic linux-image-extra-4.4.0-70-generic linux-image-extra-4.4.0-71-generic linux-image-extra-4.4.0-72-generic
  linux-image-extra-4.4.0-78-generic linux-image-extra-4.4.0-79-generic linux-image-extra-4.4.0-81-generic python-appindicator python-attr python-cairo python-cffi-backend python-chardet
  python-cryptography python-enum34 python-gi python-glade2 python-gobject python-gobject-2 python-gtk2 python-idna python-ipaddress python-notify python-numpy python-openssl python-pam python-pyasn1
  python-pyasn1-modules python-pygame python-serial python-service-identity python-six python-twisted-bin python-twisted-core python-twisted-web python-xdg python-zope.interface snap-confine
The following NEW packages will be installed:
  linux-image-4.4.0-89-generic
0 upgraded, 1 newly installed, 75 to remove and 13 not upgraded.
13 not fully installed or removed.
Need to get 0 B/21.9 MB of archives.
After this operation, 2,111 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 508225 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-89-generic_4.4.0-89.112_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
Done.
Unpacking linux-image-4.4.0-89-generic (4.4.0-89.112) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-89-generic_4.4.0-89.112_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-4.4.0-89-generic' to '/boot/System.map-4.4.0-89-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-89-generic_4.4.0-89.112_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by vocx on 2017-08-06
> **ts1971 said:**
> Hi,

I am unable to install ubuntu's suggested updates because my /boot partition is full.

Here's the relevant df / ls output:

```

-rw------- 1 root root  7087024 Mar  3 11:25 vmlinuz-4.4.0-66-generic
-rw------- 1 root root  7083344 Mar 22 09:11 vmlinuz-4.4.0-70-generic
-rw------- 1 root root  7083344 Mar 24 08:20 vmlinuz-4.4.0-71-generic
-rw------- 1 root root  7083248 Mar 31 10:14 vmlinuz-4.4.0-72-generic
-rw------- 1 root root  7081872 Apr 20 05:02 vmlinuz-4.4.0-75-generic
-rw------- 1 root root  7089552 Apr 27 11:24 vmlinuz-4.4.0-78-generic
-rw------- 1 root root  7091696 May 17 15:09 vmlinuz-4.4.0-79-generic
-rw------- 1 root root  7092784 Jun 14 05:24 vmlinuz-4.4.0-81-generic
-rw------- 1 root root  7092720 Jun 26 12:45 vmlinuz-4.4.0-83-generic
-rw------- 1 root root  7095888 Jul 18 08:00 vmlinuz-4.4.0-87-generic

```

I guess that the initrd.img-x.x.x-xx-generic files are old kernels and that that's the problem.  Here is unaame -r:

```
fred@fred-ThinkPad-P70:/boot$ uname -r
4.4.0-75-generic

```

You have many kernels, old and new, but you are not using the oldest one nor the newest one, why?

Usually when people have this problem they run the latest kernel, say 4.4.0-87, and when they try to upgrade to the newest one, say, 4.4.0-89, they experience the problem. But according to your "uname" output, you are running a kernel in the middle, not -66, and not -87, you are running -75. Why is this?

Anyways, I'm surprised the "purge" command didn't work for you. Looking at the output you posted, the system reports missing dependencies for two kernels, the oldest one -66, and the newest one -89. This seems to me like many months ago the system never finished properly installing the old kernel -66. It's not a big issue but I find it strange that this happens. Did you ignore some past warnings?

I'd suggest trying to run the "apt purge" command again in all kernels that you are currently not using. That is, if you can boot fine with 4.4.0-87, then try to purge all others.
```

sudo apt purge linux-image-4.4.0-66-generic
sudo apt purge linux-image-4.4.0-70-generic
sudo apt purge linux-image-4.4.0-71-generic
sudo apt purge linux-image-4.4.0-72-generic
# etc.

```
Of course, you should not attempt to purge the -75 kernel if that is the only one you can boot correctly.

If you really cannot purge any of them because APT throws errors, then you can try the brute force approach, which is simply deleting the kernels. Do this only for the old kernels that you will not boot anymore.
```

sudo rm /boot/vmlinuz-4.4.0-66-generic
sudo rm /boot/initrd.img-4.4.0-66-generic
sudo rm /boot/abi-4.4.0-66-generic
# be very careful. Don't remove the version you are currently using!

```

Doing this is dirty, obviously, because there are many files that will not be removed completely, however, it is fine. If you can safely boot one kernel (say -75 or -87), the other kernels, and their files, are not used at all, and just take space in your system. You only need to get enough space in the "/boot" partition so that "apt" stops showing errors. Once you have liberated the space, you should use "apt" as usual to "purge" the other kernels. And of course use "autoremove" to cleanly remove any other old packages.

Here is another thread with a similar problem and similar solution
[https://ubuntuforums.org/showthread.php?t=2367547&p=13671564#post13671564](https://ubuntuforums.org/showthread.php?t=2367547&p=13671564#post13671564)

---

### Post by ubfan1 on 2017-08-06
If you are running the 4.4.0-75-generic kernel, with at least 6 kernels installed or partially installed after it (78,79,81,83,87,89), do they all show up in the grub boot menu, and what's the latest kernel you can run (I assume 87 with no initrd and 89 mostly missing cannot run)?  The usual approach is to keep the running kernel running and the latest runnable, so lets start and identity which ones to keep.

---

### Post by ajgreeny on 2017-08-06
As you have run out of space in /boot you may have to resort to using dpkg to remove one or two kernels and then the autoremove command may work. Can you show us the output of ```
dpkg -l linux-image*
```which will show us the state of your kernel installations at present and we can then try to get rid of the unnecessary ones.

Start with ```
sudo dpkg -P linux-image-4.4.0-66-generic
```to see if that works. Assuming it is successful you can try again with the ```
sudo apt-get autoremove
``` command.
If autoremove is still not successful let's get rid of another kernel with ```
sudo dpkg -P linux-image-4.4.0-70-generic
```
I am sure eventually the autoremove command should work for you, but it does need quite a lot of headroom for success.

---

### Post by ubfan1 on 2017-08-06
As QIII mentioned, don't just rm the files, that will leave the package manager in a confused state, and prevent its functioning.  Try ajgreeny's suggestions, and only if necessary, try the brute force of manually reducing some of the older files to zero length -- that's enough to keep the package manager happy, and will give you the necessary room for the more standard purges by the package mamager.

---

### Post by ts1971 on 2017-08-06
Thanks vocx for taking the time to reply.  I agree that it's strange that I am running a random kernel from the middle of the list.  Frankly though I have no idea why that's the case as I am not a particularly sophisticated Ubuntu user.  I installed ubuntu a couple of years ago and only use this laptop to surf the web.  I generally just do whatever update the gui package manager tells me are available and have never paid any attention to kernels.  Maybe I should start :)

> **ubfan1 said:**
> If you are running the 4.4.0-75-generic kernel, with at least 6 kernels installed or partially installed after it (78,79,81,83,87,89), do they all show up in the grub boot menu, and what's the latest kernel you can run (I assume 87 with no initrd and 89 mostly missing cannot run)?  The usual approach is to keep the running kernel running and the latest runnable, so lets start and identity which ones to keep.

Yes, they all show up in the grub boot menu (three entries - blank / upstart / recovery mode - for each.  I just verified that 83 seems to run fine.  Thanks!

> **ajgreeny said:**
> Can you show us the output of ```
dpkg -l linux-image*
```.

Here you go:

```
fred@fred-ThinkPad-P70:~$ dpkg -l linux-image*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture                Description
+++-=============================================-===========================-===========================-===============================================================================================
un  linux-image                                   <none>                      <none>                      (no description available)
rc  linux-image-4.4.0-31-generic                  4.4.0-31.50                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-45-generic                  4.4.0-45.66                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-47-generic                  4.4.0-47.68                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-51-generic                  4.4.0-51.72                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-53-generic                  4.4.0-53.74                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-57-generic                  4.4.0-57.78                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-59-generic                  4.4.0-59.80                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-62-generic                  4.4.0-62.83                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-63-generic                  4.4.0-63.84                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-64-generic                  4.4.0-64.85                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-65-generic                  4.4.0-65.86                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-66-generic                  4.4.0-66.87                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-70-generic                  4.4.0-70.91                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-71-generic                  4.4.0-71.92                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-72-generic                  4.4.0-72.93                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-75-generic                  4.4.0-75.96                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-78-generic                  4.4.0-78.99                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-79-generic                  4.4.0-79.100                amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-81-generic                  4.4.0-81.104                amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-83-generic                  4.4.0-83.106                amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-87-generic                  4.4.0-87.110                amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
in  linux-image-4.4.0-89-generic                  <none>                      amd64                       (no description available)
rc  linux-image-extra-4.4.0-31-generic            4.4.0-31.50                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-45-generic            4.4.0-45.66                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-47-generic            4.4.0-47.68                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-51-generic            4.4.0-51.72                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-53-generic            4.4.0-53.74                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-57-generic            4.4.0-57.78                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-59-generic            4.4.0-59.80                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-62-generic            4.4.0-62.83                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-63-generic            4.4.0-63.84                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-64-generic            4.4.0-64.85                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-65-generic            4.4.0-65.86                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-66-generic            4.4.0-66.87                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-70-generic            4.4.0-70.91                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-71-generic            4.4.0-71.92                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-72-generic            4.4.0-72.93                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-75-generic            4.4.0-75.96                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-78-generic            4.4.0-78.99                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-79-generic            4.4.0-79.100                amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-81-generic            4.4.0-81.104                amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-83-generic            4.4.0-83.106                amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-87-generic            4.4.0-87.110                amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-89-generic            4.4.0-89.112                amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                           4.4.0.89.95                 amd64                       Generic Linux kernel image


```

---

### Post by BenginM on 2017-08-06
Safely Removing Old Kernels section here  ...

[https://help.ubuntu.com/community/RemoveOldKernels](https://help.ubuntu.com/community/RemoveOldKernels)

---

### Post by ts1971 on 2017-08-06
> **ajgreeny said:**
> 
Start with ```
sudo dpkg -P linux-image-4.4.0-66-generic
```to see if that works. Assuming it is successful you can try again with the ```
sudo apt-get autoremove
``` command.
If autoremove is still not successful let's get rid of another kernel with ```
sudo dpkg -P linux-image-4.4.0-70-generic
```
I am sure eventually the autoremove command should work for you, but it does need quite a lot of headroom for success.

I tried that command against first 66 and then 70 and they both failed over dependency issue.  Here is the session:

```
fred@fred-ThinkPad-P70:~$ sudo dpkg -P linux-image-4.4.0-66-generic
[sudo] password for fred: 
dpkg: dependency problems prevent removal of linux-image-4.4.0-66-generic:
 linux-image-extra-4.4.0-66-generic depends on linux-image-4.4.0-66-generic.

dpkg: error processing package linux-image-4.4.0-66-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-4.4.0-66-generic
fred@fred-ThinkPad-P70:~$ sudo dpkg -P linux-image-4.4.0-70-generic
dpkg: dependency problems prevent removal of linux-image-4.4.0-70-generic:
 linux-image-extra-4.4.0-70-generic depends on linux-image-4.4.0-70-generic.

dpkg: error processing package linux-image-4.4.0-70-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-4.4.0-70-generic
fred@fred-ThinkPad-P70:~$ 


```

Thanks

---

### Post by ajgreeny on 2017-08-06
Ah! 

I forgot the possibility of the dependency problem with the linux-image-extra-4.4.0-66-generic, etc etc, so let's try again with ```
sudo dpkg -P linux-image-extra-4.4.0-66-generic linux-image-4.4.0-66-generic
``` which should work this time.
If this succeeds try again with the 4.4.0-70 versions, and finally try the ```
sudo -apt-get autoremove
``` command again.
PS:
The compound command ```
sudo dpkg -P linux-image{,-extra}-4.4.0-{66,70}-generic
``` should also do this in one action.

---

### Post by ts1971 on 2017-08-06
> **ajgreeny said:**
> Ah! 

I forgot the possibility of the dependency problem with the linux-image-extra-4.4.0-66-generic, etc etc, so let's try again with ```
sudo dpkg -P linux-image-extra-4.4.0-66-generic linux-image-4.4.0-66-generic
``` which should work this time.
If this succeeds try again with the 4.4.0-70 versions, and finally try the ```
sudo -apt-get autoremove
``` command again.
PS:
The compound command ```
sudo dpkg -P linux-image{,-extra}-4.4.0-{66,70}-generic
``` should also do this in one action.

Thanks again for your time here.  Anyway, the output from the first command did include a couple of errors related to disk space, but it does seem to have eliminated the corresponding files from /boot and df shows usage down to 93%.  I then reran it against 70 and this one completed with no errors so so things are looking up.  The autoremove still fails though because of missing dependencies.  The output suggests that I rerun it with -f.  Does that seem like a good idea?  Thanks and I've copied the whole term session below.

```
fred@fred-ThinkPad-P70:~$ sudo dpkg -P linux-image-extra-4.4.0-66-generic linux-image-4.4.0-66-generic
[sudo] password for fred: 
(Reading database ... 508224 files and directories currently installed.)
Removing linux-image-extra-4.4.0-66-generic (4.4.0-66.87) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-66-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-66-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-66-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-66-generic (4.4.0-66.87) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-66-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-75-generic
Found initrd image: /boot/initrd.img-4.4.0-75-generic
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found initrd image: /boot/initrd.img-4.4.0-70-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-4.4.0-66-generic (4.4.0-66.87) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
Errors were encountered while processing:
 linux-image-extra-4.4.0-66-generic
fred@fred-ThinkPad-P70:~$ 
fred@fred-ThinkPad-P70:~$ 
fred@fred-ThinkPad-P70:~$ sudo dpkg -P linux-image-extra-4.4.0-70-generic linux-image-4.4.0-70-generic
(Reading database ... 502611 files and directories currently installed.)
Removing linux-image-extra-4.4.0-70-generic (4.4.0-70.91) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-70-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-75-generic
Found initrd image: /boot/initrd.img-4.4.0-75-generic
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found linux image: /boot/vmlinuz-4.4.0-70-generic
Found initrd image: /boot/initrd.img-4.4.0-70-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-extra-4.4.0-70-generic (4.4.0-70.91) ...
Removing linux-image-4.4.0-70-generic (4.4.0-70.91) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-70-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-75-generic
Found initrd image: /boot/initrd.img-4.4.0-75-generic
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Purging configuration files for linux-image-4.4.0-70-generic (4.4.0-70.91) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-70-generic /boot/vmlinuz-4.4.0-70-generic
fred@fred-ThinkPad-P70:~$ 
fred@fred-ThinkPad-P70:~$ 
fred@fred-ThinkPad-P70:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-66-generic : Depends: linux-image-4.4.0-66-generic but it is not installed
 linux-image-extra-4.4.0-89-generic : Depends: linux-image-4.4.0-89-generic but it is not installed
 linux-image-generic : Depends: linux-image-4.4.0-89-generic but it is not installed
E: Unmet dependencies. Try using -f.
fred@fred-ThinkPad-P70:~$ 


```

---

### Post by ts1971 on 2017-08-06
> **ts1971 said:**
> The output suggests that I rerun it with -f.  Does that seem like a good idea? 

So I went ahead and ran it and it seems to have progressed pretty far but finally failed with more errors about disk space.  The boot partition is back up to 98% full which means that the autoremove actually added contents to the partition.  Are there any other options here?  I've included the most recent terminal session below in case anyone wants to look at it.  Thanks again.

```
fred@fred-ThinkPad-P70:/boot$ sudo apt-get -f autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-image-4.4.0-66-generic linux-image-4.4.0-89-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following packages will be REMOVED:
  linux-headers-4.4.0-75 linux-headers-4.4.0-75-generic linux-image-4.4.0-75-generic linux-image-extra-4.4.0-75-generic
The following NEW packages will be installed:
  linux-image-4.4.0-66-generic linux-image-4.4.0-89-generic
0 upgraded, 2 newly installed, 4 to remove and 13 not upgraded.
14 not fully installed or removed.
Need to get 57.8 MB/79.7 MB of archives.
After this operation, 164 MB disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-4.4.0-66-generic amd64 4.4.0-66.87 [21.8 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-extra-4.4.0-66-generic amd64 4.4.0-66.87 [36.0 MB]
Fetched 57.8 MB in 3s (16.3 MB/s)                             
(Reading database ... 496997 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-89-generic_4.4.0-89.112_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
Done.
Unpacking linux-image-4.4.0-89-generic (4.4.0-89.112) ...
Selecting previously unselected package linux-image-4.4.0-66-generic.
Preparing to unpack .../linux-image-4.4.0-66-generic_4.4.0-66.87_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
Done.
Unpacking linux-image-4.4.0-66-generic (4.4.0-66.87) ...
(Reading database ... 499144 files and directories currently installed.)
Removing linux-headers-4.4.0-75-generic (4.4.0-75.96) ...
Removing linux-headers-4.4.0-75 (4.4.0-75.96) ...
Removing linux-image-extra-4.4.0-75-generic (4.4.0-75.96) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-75-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-89-generic
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-75-generic
Found initrd image: /boot/initrd.img-4.4.0-75-generic
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Removing linux-image-4.4.0-75-generic (4.4.0-75.96) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-75-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-75-generic /boot/vmlinuz-4.4.0-75-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-89-generic
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: deferring update (trigger activated)
Setting up libllvm4.0:amd64 (1:4.0-1ubuntu1~16.04.2) ...
Setting up linux-firmware (1.157.11) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-83-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-81-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-79-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-78-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-72-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-71-generic
Setting up linux-image-4.4.0-89-generic (4.4.0-89.112) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-89-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-89-generic
Found initrd image: /boot/initrd.img-4.4.0-89-generic
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-extra-4.4.0-89-generic (4.4.0-89.112) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-89-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-89-generic /boot/vmlinuz-4.4.0-89-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-89-generic
Found initrd image: /boot/initrd.img-4.4.0-89-generic
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-generic (4.4.0.89.95) ...
Setting up linux-headers-4.4.0-89 (4.4.0-89.112) ...
Setting up linux-headers-4.4.0-89-generic (4.4.0-89.112) ...
Setting up linux-headers-generic (4.4.0.89.95) ...
Setting up linux-generic (4.4.0.89.95) ...
Setting up linux-image-4.4.0-87-generic (4.4.0-87.110) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-87-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-89-generic
Found initrd image: /boot/initrd.img-4.4.0-89-generic
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found initrd image: /boot/initrd.img-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
Setting up linux-image-4.4.0-66-generic (4.4.0-66.87) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-66-generic /boot/vmlinuz-4.4.0-66-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-89-generic
Found initrd image: /boot/initrd.img-4.4.0-89-generic
Found linux image: /boot/vmlinuz-4.4.0-87-generic
Found initrd image: /boot/initrd.img-4.4.0-87-generic
Found linux image: /boot/vmlinuz-4.4.0-83-generic
Found initrd image: /boot/initrd.img-4.4.0-83-generic
Found linux image: /boot/vmlinuz-4.4.0-81-generic
Found initrd image: /boot/initrd.img-4.4.0-81-generic
Found linux image: /boot/vmlinuz-4.4.0-79-generic
Found initrd image: /boot/initrd.img-4.4.0-79-generic
Found linux image: /boot/vmlinuz-4.4.0-78-generic
Found initrd image: /boot/initrd.img-4.4.0-78-generic
Found linux image: /boot/vmlinuz-4.4.0-72-generic
Found initrd image: /boot/initrd.img-4.4.0-72-generic
Found linux image: /boot/vmlinuz-4.4.0-71-generic
Found initrd image: /boot/initrd.img-4.4.0-71-generic
Found linux image: /boot/vmlinuz-4.4.0-66-generic
Found initrd image: /boot/initrd.img-4.4.0-66-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done
dpkg: error processing package linux-image-extra-4.4.0-66-generic (--configure):
 package linux-image-extra-4.4.0-66-generic is not ready for configuration
 cannot configure (current status 'half-installed')
Setting up linux-image-extra-4.4.0-83-generic (4.4.0-83.106) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-83-generic /boot/vmlinuz-4.4.0-83-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-83-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-83-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-83-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-image-extra-4.4.0-87-generic (4.4.0-87.110) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-87-generic /boot/vmlinuz-4.4.0-87-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-87-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-87-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-87-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-libc-dev:amd64 (4.4.0-89.112) ...
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-89-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-89-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin (2.23-0ubuntu9) ...
Errors were encountered while processing:
 linux-image-extra-4.4.0-66-generic
 linux-image-extra-4.4.0-83-generic
 linux-image-extra-4.4.0-87-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by ubfan1 on 2017-08-06
So the uininstall of ...66 was not complete, and an attempt was made to reinstall, and the ...89 which was in the queue, attempted to install in the free space, and it ran out again.
Take a look at [https://askubuntu.com/questions/911563/boot-partition-is-100-full-cant-remove-old-packages-to-make-space/912367#912367](https://askubuntu.com/questions/911563/boot-partition-is-100-full-cant-remove-old-packages-to-make-space/912367#912367) for an answer to free up some space, to allow the package manager to work.  Don't remove the running kernel, but the 66 and low 70s may be zeroed.   A separate boot partition may be needed (raid, encrypted lvm, hugh disk the BIOS cannot fully address, etc.) but if you don't need one, better not to have one -- just leave /boot as a directory in the root partition.

---

