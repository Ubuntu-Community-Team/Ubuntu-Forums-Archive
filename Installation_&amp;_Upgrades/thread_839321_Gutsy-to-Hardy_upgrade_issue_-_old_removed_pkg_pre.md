---
title: "Gutsy-to-Hardy upgrade issue - old removed pkg preventing updates"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by jon.forums on 2008-06-24
Upgraded Xubuntu from Gutsy to Hardy via Update Manager and everything is working fine except I'm now not able to do further updates.

Looks like the pkg system still thinks a previously removed pkg (linux-ubuntu-modules-2.6.22-14-generic) still exists, and then bombs when it can't find the files to uninstall.  No files corresponding to this pkg exist in /boot or /lib/modules

I've tried all I know with 'Update Manager', 'aptitude', 'dpkg --purge', 'apg-get -f purge' but can't get the packaging system to forget about the pkg that appears to be long gone.

For example...

```

jon@pixie:~$ sudo apt-get -f purge linux-ubuntu-modules-2.6.22-14-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.22-14-generic
0 upgraded, 0 newly installed, 1 to remove and 13 not upgraded.
1 not fully installed or removed.
After this operation, 9966kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 97795 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-14-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-14-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Cannot find /lib/modules/2.6.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I'm unfortunately at the end of my expertise on what to do next and haven't yet found a similar forum post.

Thanks in advance....Jon

---

### Post by niyonk on 2008-06-24
'sudo apt-get -f install' to fix broken packages

:-k

---

### Post by jon.forums on 2008-06-24
whoa..that was quick!

does it make sense to install this old pkg first even though my current system is running a newer kernel?

```

jon@pixie:~$ uname -a
Linux pixie 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 i686 GNU/Linux

```

---

### Post by jon.forums on 2008-06-24
'sudo apt-get -f install' (with or without pkg name arg) didn't work...

```

jon@pixie:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.22-14-generic
0 upgraded, 0 newly installed, 1 to remove and 13 not upgraded.
1 not fully installed or removed.
After this operation, 9966kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 97795 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-14-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-14-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Cannot find /lib/modules/2.6.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

other ideas?

---

### Post by jon.forums on 2008-06-24
any other suggestions on how to fix?

---

### Post by avtolle on 2008-06-24
Don't know if this will fix it, but as it hasn't been tried yet```
sudo apt-get clean
``` to clean your cache and ```
sudo apt-get autoclean
```to get rid of dependencies, etc.

---

### Post by jon.forums on 2008-06-24
thanks...sadly the 'apt-get clean' and 'apt-get autoclean' dance didn't do the trick

---

### Post by jon.forums on 2008-06-24
I also quickly looked through /etc/apt/apt.conf.d and /etc/dpkg but didn't spot anything that looked like it could help

---

### Post by jon.forums on 2008-06-26
anyone else got any experiments for me to try?

---

### Post by jon.forums on 2008-07-10
is there a different forum that would be a better place to post this problem?

---

### Post by jon.forums on 2008-07-10
well, the following seemed to do the trick...

```

cd /var/lib/dpkg
sudo cp status status-prefix
sudo vim status
<delete the record corresponding to linux-ubuntu-modules-2.6.22-14-generic and save>
sudo aptitude

```

---

