---
title: "Boot FULL again"
date: 2017-02-22
forum: Installation &amp; Upgrades
---

### Post by Alligator on 2017-02-22
It seems that about every 2nd image upgrade I get a boot full (pun intended) Anyway this is the process I use.

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

The results from this.

```


ron@Cronluath:~$ uname -r
4.4.0-62-generic


ron@Cronluath:~$ sudo dpkg --list 'linux-image*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                        Version                    Architecture               Description
+++-===========================================-==========================-==========================-============================================================================================
un  linux-image                                 <none>                     <none>                     (no description available)
un  linux-image-3.0                             <none>                     <none>                     (no description available)
rc  linux-image-4.2.0-34-generic                4.2.0-34.39                amd64                      Linux kernel image for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-28-generic                4.4.0-28.47                amd64                      Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-31-generic                4.4.0-31.50                amd64                      Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-34-generic                4.4.0-34.53                amd64                      Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-36-generic                4.4.0-36.55                amd64                      Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-38-generic                4.4.0-38.57                amd64                      Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-42-generic                4.4.0-42.62                amd64                      Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-43-generic                4.4.0-43.63                amd64                      Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-45-generic                4.4.0-45.66                amd64                      Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-47-generic                4.4.0-47.68                amd64                      Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-51-generic                4.4.0-51.72                amd64                      Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-53-generic                4.4.0-53.74                amd64                      Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-59-generic                4.4.0-59.80                amd64                      Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-62-generic                4.4.0-62.83                amd64                      Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-63-generic                4.4.0-63.84                amd64                      Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.2.0-34-generic          4.2.0-34.39                amd64                      Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-28-generic          4.4.0-28.47                amd64                      Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-31-generic          4.4.0-31.50                amd64                      Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-34-generic          4.4.0-34.53                amd64                      Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-36-generic          4.4.0-36.55                amd64                      Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-38-generic          4.4.0-38.57                amd64                      Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-42-generic          4.4.0-42.62                amd64                      Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-43-generic          4.4.0-43.63                amd64                      Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-45-generic          4.4.0-45.66                amd64                      Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-47-generic          4.4.0-47.68                amd64                      Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-51-generic          4.4.0-51.72                amd64                      Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-53-generic          4.4.0-53.74                amd64                      Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-59-generic          4.4.0-59.80                amd64                      Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-62-generic          4.4.0-62.83                amd64                      Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-63-generic          4.4.0-63.84                amd64                      Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                         4.4.0.63.67                amd64                      Generic Linux kernel image
ron@Cronluath:~$ sudo apt-get remove linux-image-4.4.0-28-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'linux-image-4.4.0-28-generic' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
ron@Cronluath:~$ sudo apt-get remove linux-image-4.4.0-53-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'linux-image-4.4.0-53-generic' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
ron@Cronluath:~$ sudo apt-get remove linux-image-4.4.0-59-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'linux-image-4.4.0-59-generic' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.

________________________________________________________________________-

ron@Cronluath:/boot$ ls -la
total 245687
drwxr-xr-x  4 root root     6144 Feb 22 06:13 .
drwxr-xr-x 25 root root     4096 Feb 21 16:55 ..
-rw-r--r--  1 root root  1244118 Jan 18 09:59 abi-4.4.0-62-generic
-rw-r--r--  1 root root  1245512 Feb  1 13:39 abi-4.4.0-63-generic
-rw-r--r--  1 root root   190047 Jan 18 09:59 config-4.4.0-62-generic
-rw-r--r--  1 root root   190247 Feb  1 13:39 config-4.4.0-63-generic
drwxr-xr-x  5 root root     8192 Feb 22 06:16 grub
-rw-r--r--  1 root root  9962027 Feb 12 11:53 initrd.img-3.13.0-57-generic
-rw-r--r--  1 root root  9962019 Feb 12 11:53 initrd.img-3.13.0-58-generic
-rw-r--r--  1 root root  9962013 Feb 12 11:53 initrd.img-3.13.0-59-generic
-rw-r--r--  1 root root  9962014 Feb 12 11:53 initrd.img-3.13.0-61-generic
-rw-r--r--  1 root root  9962001 Feb 12 11:53 initrd.img-3.13.0-62-generic
-rw-r--r--  1 root root  9961548 Feb 12 11:53 initrd.img-3.13.0-63-generic
-rw-r--r--  1 root root  9961557 Feb 12 11:52 initrd.img-3.13.0-65-generic
-rw-r--r--  1 root root  9961623 Feb 12 11:52 initrd.img-3.13.0-66-generic
-rw-r--r--  1 root root  9961621 Feb 12 11:52 initrd.img-3.13.0-67-generic
-rw-r--r--  1 root root  9961730 Feb 12 11:52 initrd.img-3.13.0-68-generic
-rw-r--r--  1 root root  9961591 Feb 12 11:52 initrd.img-3.13.0-74-generic
-rw-r--r--  1 root root  9961559 Feb 12 11:52 initrd.img-3.13.0-76-generic
-rw-r--r--  1 root root  9961666 Feb 12 11:52 initrd.img-3.13.0-79-generic
-rw-r--r--  1 root root  9961549 Feb 12 11:52 initrd.img-3.13.0-83-generic
-rw-r--r--  1 root root  9961630 Feb 12 11:52 initrd.img-4.4.0-45-generic
-rw-r--r--  1 root root 37887326 Feb 12 11:53 initrd.img-4.4.0-62-generic
-rw-r--r--  1 root root 37877152 Feb 22 06:13 initrd.img-4.4.0-63-generic
drwx------  2 root root    12288 May 31  2011 lost+found
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3875553 Jan 18 09:59 System.map-4.4.0-62-generic
-rw-------  1 root root  3883990 Feb  1 13:39 System.map-4.4.0-63-generic
-rw-------  1 root root  7070992 Jan 18 09:59 vmlinuz-4.4.0-62-generic
-rw-------  1 root root  7087088 Feb  1 13:39 vmlinuz-4.4.0-63-generic


```

Note the difference between listing images and the /boot directory.

---

### Post by Impavidus on 2017-02-22
There's no need to uninstall linux-image-4.4.0-28-generic etc., as that package is not installed. It's listed with status **rc**, meaning removed, configuration files remaining. But in fact, this package doesn't have any configuration files. You can purge the package anyway using```
sudo apt-get purge  linux-image-4.4.0-28-generic
```which will do nothing more than remove some clutter in dpkg's output.

All your /boot/initrd.img-3.13.0-* files are leftovers from an older version of Ubuntu. They should have been removed during the release upgrade by the post removal script (specifically, by /usr/sbin/update-initramfs). The files are not part of any currently installed package and in fact have never been. I'm not sure of the cleanest way to remove them, but I do know that you no longer need them.

---

### Post by SeijiSensei on 2017-02-22
> **Impavidus said:**
> I'm not sure of the cleanest way to remove them, but I do know that you no longer need them.
You can just delete them with
```
sudo rm -f /boot/initrd.img-3.*
```

The kernel updating scripts are supposed to leave you with two kernels, the new one and the current one being replaced.  Sometimes they work, sometimes they don't. The current kernel is preserved in case the new one fails for some reason.

---

### Post by oldfred on 2017-02-22
It looks like you upgraded, not a new clean install.
But your old install had many kernels that are now not in the new version's dpkg.
Best to thoroughly houseclean before upgrading or do a new clean install.

 You may have to manually remove the files manually with rm.

 Use dpkg -S to see which .dkms files were not placed by the package manager
dpkg -S /full/path/to/file
Only use rm on files not in dpkg

 kernel files by version  - initrd, vmlinuz, abi, system.map 
dpkg -S /lib/modules | sed s/:.\*//
uname --kernel-release
 
Kernel files also are in other places normally removed.
Did you also check /var/cache/apt/archives? You may have the old .deb's taking up space.
 /var/cache/apt/archives 

        kernel house clean
/usr/src/*
[http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this](http://askubuntu.com/questions/301466/files-are-piling-up-in-usr-src-how-can-i-stop-this) 
    
 But older kernels may still not be removed & other info , scripts to remove - schragge
[http://ubuntuforums.org/showthread.php?t=2256452&p=13186077#post13186077](http://ubuntuforums.org/showthread.php?t=2256452&p=13186077#post13186077)

---

### Post by Alligator on 2017-02-22
Thank you all for your help.  I will have to do some reading before attempting to clean house (OLDFRED)  I cleaned up the /boot directory, the dpkg --list is still a mess.

---

### Post by Alligator on 2017-02-22
I did a sudo apt-get && sudo apt-get dist-upgrade, followed by a sudo reboot and I got an error. I was at version 62 going to 63 and now 64 is it. I sent an error report but here it is.

linux-image-extra-4.4.0-63-generic 4.4.0-63.84

Error:command['pacmd','list'] failed with exit code 1: No PulseAudio daemon running, or not running as session daemon.

Is there a way to copy the entire crash details to cut and paste?

---

