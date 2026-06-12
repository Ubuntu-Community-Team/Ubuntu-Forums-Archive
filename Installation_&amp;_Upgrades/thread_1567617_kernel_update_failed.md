---
title: "kernel update failed"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by dewdrop_world on 2010-09-04
I tried to install updates via update manager and it said the linux-image package was in a "very bad, inconsistent" state. (Sorry, I forgot to save the full text.)

Then I tried to install gstreamer-ffmpeg and that failed too:

> installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 173070 files and directories currently installed.)
Preparing to replace linux-image-2.6.32-24-generic 2.6.32-24.42 (using .../linux-image-2.6.32-24-generic_2.6.32-24.42_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.32-24-generic ...
dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.32-24-generic_2.6.32-24.42_amd64.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./boot/vmlinuz-2.6.32-24-generic')
No apport report written because the error message indicates a dpkg I/O error
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Windows 7 (loader) on /dev/sda3
done
Selecting previously deselected package gstreamer0.10-ffmpeg.
Unpacking gstreamer0.10-ffmpeg (from .../gstreamer0.10-ffmpeg_0.10.10-1_amd64.deb) ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.32-24-generic_2.6.32-24.42_amd64.deb
Setting up linux-image-2.6.32-24-generic (2.6.32-24.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-24.41 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-24.41 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Windows 7 (loader) on /dev/sda3
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic

Setting up gstreamer0.10-ffmpeg (0.10.10-1) ...


Next steps?

---

### Post by akoskm on 2010-09-04
> **dewdrop_world said:**
> I tried to install updates via update manager and it said the linux-image package was in a "very bad, inconsistent" state. (Sorry, I forgot to save the full text.)

Then I tried to install gstreamer-ffmpeg and that failed too:



Next steps?

It looks like to me that it's failed because the broken kernel update.
What is the output of:
```

sudo apt-get check

```?

---

### Post by dewdrop_world on 2010-09-04
***@*****:~$ sudo apt-get check
[sudo] password for ***: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done

^^ Seems OK.

---

### Post by akoskm on 2010-09-04
Regarding to this line from the error message:
```

dpkg: error processing /var/cache/apt/archives/linux-image-2.6.32-24-generic_2.6.32-24.42_amd64.deb (--unpack):

``` I suggest you to do a 
```

aptitude clean
aptitude update
aptitude safe-upgrade

```.
Anyway, maybe something went wrong during the kernel update, but *gstreamer0.10-ffmpeg* is installed, and *check* isn't showing any error.
I think, it's OK.

---

### Post by dewdrop_world on 2010-09-05
Update still fails after the 3 commands:

(no errors during clean/update - safe upgrade downloads successfully then...)

> Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 171881 files and directories currently installed.)
Preparing to replace tzdata-java 2010k-0ubuntu0.10.04 (using .../tzdata-java_2010l-0ubuntu0.10.04_all.deb) ...
Unpacking replacement tzdata-java ...
Preparing to replace tzdata 2010k-0ubuntu0.10.04 (using .../tzdata_2010l-0ubuntu0.10.04_all.deb) ...
Unpacking replacement tzdata ...
E: Sub-process /usr/bin/dpkg exited unexpectedly
A package failed to install.  Trying to recover:
dpkg: error processing tzdata (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
dpkg: dependency problems prevent configuration of tzdata-java:
 tzdata-java depends on tzdata (= 2010l-0ubuntu0.10.04); however:
  Package tzdata is not configured yet.
dpkg: error processing tzdata-java (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 tzdata-java
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

Current status: 40 updates [-2].


---

### Post by akoskm on 2010-09-05
> **dewdrop_world said:**
> Update still fails after the 3 commands:
```

dpkg: error processing tzdata (--configure):
Package is in a very bad inconsistent state - you should
reinstall it before attempting configuration.

```
(no errors during clean/update - safe upgrade downloads successfully then...)

```

sudo aptitude reinstall tzdata

```
after this install *tzdata-java* separately
```

sudo aptitude install tzdata-java

```.
Hope this help.

---

