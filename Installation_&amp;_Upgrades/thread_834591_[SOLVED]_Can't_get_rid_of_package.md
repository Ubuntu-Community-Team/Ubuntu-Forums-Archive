---
title: "[SOLVED] Can't get rid of package"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by krokodil on 2008-06-19
I have a package that I can't uninstall. Think I ran out of hard drive space the first time I tried to uninstall it. Problem is now I can't install anything else until I get rid of it.

Here is what happens when I try to run aptitude:

```
Removing linux-ubuntu-modules-2.6.24-17-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-17-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic
Cannot find /lib/modules/2.6.24-17-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-17-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

Anybody have any ideas how to get rid of this?

---

### Post by VMC on 2008-06-19
type this to see how much space is left: 

```
df -h
```

Then try this

```
sudo apt-get clean
```

If that helped, then use this

```
sudo apt-get autoremove
```

---

### Post by krokodil on 2008-06-19
Thanks for the help, but unfortunately the package is still stuck. Here's what happened when I ran apt-get autoremove:

```
krokodil@Hermit:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-17-generic
0 upgraded, 0 newly installed, 1 to remove and 41 not upgraded.
1 not fully installed or removed.
After this operation, 15.3MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 168618 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-17-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-17-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic
Cannot find /lib/modules/2.6.24-17-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-17-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by krokodil on 2008-06-21
bump?

---

### Post by hal8000 on 2008-06-21
> **krokodil said:**
> Thanks for the help, but unfortunately the package is still stuck. Here's what happened when I ran apt-get autoremove:

```
krokodil@Hermit:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-17-generic
0 upgraded, 0 newly installed, 1 to remove and 41 not upgraded.
1 not fully installed or removed.
After this operation, 15.3MB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 168618 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-17-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-17-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic
Cannot find /lib/modules/2.6.24-17-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-17-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


The errors are referring to remove an older kernel image and module which apparaently doesnt exist on your system. Can you please provide the following information:

df -h

uname -a

ls -lh /boot


You can apply these commands as a normal user from a terminal.
Also have you manually deleted any software using the rm command?

---

### Post by krokodil on 2008-06-21
I only have 100MB for /boot and for the last few years (going back to Breezy) that has been more than enough. With Hardy though I started using the rt kernel from Ubuntu Studio, but I never stopped installing the generic as well so I ran out of space - essentially I as installing two kernels for each kernel upgrade.

I tried to clear up some space by aptitude purging all extra and old kernels I had installed. Due to lack of space on /boot I struggled but managed to get the 16 kernels out completely, but the 17 kernel it seems got half uninstalled and is now stuck.

At this point I honestly don't mind if there are little bits of the 17 kernel still hanging around, I just want my apt to work. So if there is a text file somewhere I can edit to make apt think the 17 kernel is gone I'll happily do that.

Below is the output of the commands (you can see I have the 19 kernel installed but haven't rebooted yet):

```
krokodil@Hermit:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdd3              14G  3.7G   11G  27% /
varrun                503M  128K  503M   1% /var/run
varlock               503M     0  503M   0% /var/lock
udev                  503M   88K  503M   1% /dev
devshm                503M  228K  503M   1% /dev/shm
lrm                   503M   38M  465M   8% /lib/modules/2.6.24-18-rt/volatile
/dev/sdd1              92M   42M   45M  49% /boot
/dev/sdd4             216G   26G  191G  12% /home
gvfs-fuse-daemon       14G  3.7G   11G  27% /home/krokodil/.gvfs
/dev/sde1             149G  146G  3.4G  98% /media/Ant
/dev/sdb3             166G  153G   14G  92% /media/disk
tmpfs                 503M   38M  466M   8% /lib/modules/2.6.24-19-rt/volatile
/dev/sdc1             233G  230G  3.5G  99% /media/disk-1
krokodil@Hermit:~$ uname -a
Linux Hermit 2.6.24-18-rt #1 SMP PREEMPT RT Wed May 28 23:38:58 UTC 2008 i686 GNU/Linux
krokodil@Hermit:~$ ls -lh /boot
total 36M
-rw-r--r-- 1 root root  84K 2008-05-29 04:57 config-2.6.24-18-rt
-rw-r--r-- 1 root root  84K 2008-06-04 23:04 config-2.6.24-19-rt
drwxr-xr-x 2 root root 1.0K 2008-06-19 23:29 grub
-rw-r--r-- 1 root root 7.5M 2008-06-16 13:00 initrd.img-2.6.24-18-rt
-rw-r--r-- 1 root root 7.5M 2008-06-05 22:04 initrd.img-2.6.24-18-rt.bak
-rw-r--r-- 1 root root 7.5M 2008-06-17 22:35 initrd.img-2.6.24-19-rt
-rw-r--r-- 1 root root 7.5M 2008-06-17 22:35 initrd.img-2.6.24-19-rt.bak
drwx------ 2 root root  12K 2008-04-30 00:25 lost+found
-rw-r--r-- 1 root root 101K 2007-09-28 12:06 memtest86+.bin
-rw-r--r-- 1 root root 904K 2008-05-29 04:57 System.map-2.6.24-18-rt
-rw-r--r-- 1 root root 907K 2008-06-04 23:04 System.map-2.6.24-19-rt
-rw-r--r-- 1 root root 1.9M 2008-05-29 04:57 vmlinuz-2.6.24-18-rt
-rw-r--r-- 1 root root 1.9M 2008-06-04 23:04 vmlinuz-2.6.24-19-rt

```

---

### Post by krokodil on 2008-06-21
As an after thought, obviously cleanly removing the 17 kernel would be first prize, but if I can just get apt to work again I'll be happy.

---

### Post by Pumalite on 2008-06-21
Edit /var/lib/dpkg/status and make the package: installed...ok...installed
Then try again.

---

### Post by krokodil on 2008-06-21
> **Pumalite said:**
> Edit /var/lib/dpkg/status and make the package: installed...ok...installed

Thanks that worked. With one minor change, no 'ed' on the first install, so its: install ok installed

---

### Post by Pumalite on 2008-06-21
> **krokodil said:**
> Thanks that worked. With one minor change, no 'ed' on the first install, so its: install ok installed
Glad you got it working. Sorry for the typo.

---

### Post by krokodil on 2008-06-21
I spoke too soon. Although the above change did stop aptitude from prompting me to remove kernel 17, once it got to installing the updates I got the following error:

```
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 14923 package `linux-ubuntu-modules-2.6.24-17-generic':
 Configured-Version for package with inappropriate Status
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/status' near line 14923 package `linux-ubuntu-modules-2.6.24-17-generic':
 Configured-Version for package with inappropriate Status
```

After wandering around /var/lib/dpkg/status a little, I changed the status of linux-ubuntu-modules-2.6.24-17-generic to: deinstall ok config-files

Aptitude has now completed a dist-upgrade without any errors. I think it may be fixed. Thanks again for all the help!

---

