---
title: "Stuck with error upgrading linux-headers"
date: 2013-08-22
forum: Installation &amp; Upgrades
---

### Post by Jocke_fi on 2013-08-22
Hi, 
 I am stuck with an error updating linux headers that I am not able to resolve. When I type in

```
sudo apt-get -f upgrade
```

Lubuntu proceeds to fetch the required packages, but then I get the following message:

[HTML]Unpacking linux-headers-3.8.0-29 (from .../linux-headers-3.8.0-29_3.8.0-29.42_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.8.0-29_3.8.0-29.42_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.8.0-29/arch/arm/mach-omap1/include/mach/flash.h.dpkg-new' (while processing `./usr/src/linux-headers-3.8.0-29/arch/arm/mach-omap1/include/mach/flash.h'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-headers-3.8.0-29-generic (from .../linux-headers-3.8.0-29-generic_3.8.0-29.42_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.8.0-29-generic_3.8.0-29.42_i386.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.8.0-29-generic/include/config/rtl8192cu.h.dpkg-new' (while processing `./usr/src/linux-headers-3.8.0-29-generic/include/config/rtl8192cu.h'): No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to replace login 1:4.1.5.1-1ubuntu4 (using .../login_1%3a4.1.5.1-1ubuntu4.1_i386.deb) ...
Unpacking replacement login ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.8.0-29_3.8.0-29.42_all.deb
 /var/cache/apt/archives/linux-headers-3.8.0-29-generic_3.8.0-29.42_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/HTML]

In the message it says: "No space left on device". I don't get that, because when I run

```
df -h
```

[HTML]Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             4,5G  1,2G  3,1G  28% /
none                  4,0K     0  4,0K   0% /sys/fs/cgroup
udev                  483M  4,0K  483M   1% /dev
tmpfs                 100M  996K   99M   1% /run
none                  5,0M     0  5,0M   0% /run/lock
none                  498M  4,0K  498M   1% /run/shm
none                  100M  8,0K  100M   1% /run/user
/dev/sda10            1,7G  2,6M  1,6G   1% /opt
/dev/sda7             1,9G  756M  994M  44% /var
/dev/sda8             3,7G  2,8G  675M  81% /usr
/dev/sda9             1,4G  2,2M  1,3G   1% /tmp
/dev/sda11            1,2G  1,9M  1,1G   1% /srv
/dev/sda5             129G   23G   99G  19% /home
/dev/sda12            1,3G  2,7M  1,3G   1% /usr/local
/home/jocke/.Private  129G   23G   99G  19% /home/jocke
[/HTML]

...which seems to suggest that there is plenty of space for the updates.

Thanks in advance!

---

### Post by ibjsb4 on 2013-08-22
> unable to create `/usr/src/linux-headers-3.8.0-29-generic/include/config/rtl8192cu.h.dpkg-new' (while processing `./usr/src/
linux-headers-3.8.0-29-generic/include/config/rtl8192cu.h'): [COLOR=#ff0000]No space left on device[/COLOR]

I would guess that /boot is full.

[http://ubuntuforums.org/showthread.php?t=2168390&p=12761126&viewfull=1#post12761126](http://ubuntuforums.org/showthread.php?t=2168390&p=12761126&viewfull=1#post12761126)

---

### Post by Jocke_fi on 2013-08-24
Thanks, removing some old kernels with Synaptic Package Manager solved the problem.

---

