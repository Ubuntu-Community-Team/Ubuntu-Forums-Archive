---
title: "errors upgrading image-2.6.24-19-generic_2.6.24-19.34_i386.deb"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by lordmorgoth on 2008-06-23
hello,

i was updating my Hardy installation using apt, previously an update to the linux generic kernel 2.6.24-19 was released; today a new release was issued to update, But it generated a problem :


Do you want to continue [Y/n]? y
(Reading database ... 161816 files and directories currently installed.)
Preparing to replace linux-image-2.6.24-19-generic 2.6.24-19.33 (using .../linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.24-19-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./boot/abi-2.6.24-19-generic': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... found: (hd0,0)/grub/splashimages/36909-soft-tux.xpm.gz

Found kernel: /vmlinuz-2.6.24-19-generic
Found kernel: /vmlinuz-2.6.24-18-generic
Found kernel: /vmlinuz-2.6.24-17-generic
Found kernel: /vmlinuz-2.6.24-16-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



Any ideas ??

---

### Post by lordmorgoth on 2008-06-23
problem: no more space in /boot

solution delete some files:

```
sudo nautilus
```

go to /boot

remove initrd.img-2.6.24-1*-generic.bak where * = 6,7 or 8

---

### Post by fishtoprecords on 2008-06-23
I'm also getting errors, altho not from lack of space on boot.

```
root@tools:/boot# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-image-2.6.24-19-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.4MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: Perl may be unconfigured (Can't locate Debconf/Log.pm in @INC (@INC contains: /usr/local/lib/perl5/5.10.0/i686-linux /usr/local/lib/perl5/5.10.0 /usr/local/lib/perl5/site_perl/5.10.0/i686-linux /usr/local/lib/perl5/site_perl/5.10.0 .) at (eval 1) line 4.
BEGIN failed--compilation aborted at (eval 1) line 4.
) -- aborting
(Reading database ... 139418 files and directories currently installed.)
Preparing to replace linux-image-2.6.24-19-generic 2.6.24-19.33 (using .../linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb) ...
Can't locate Debconf/Client/ConfModule.pm in @INC (@INC contains: /usr/local/lib/perl5/5.10.0/i686-linux /usr/local/lib/perl5/5.10.0 /usr/local/lib/perl5/site_perl/5.10.0/i686-linux /usr/local/lib/perl5/site_perl/5.10.0 .) at /var/lib/dpkg/tmp.ci/preinst line 20.
BEGIN failed--compilation aborted at /var/lib/dpkg/tmp.ci/preinst line 20.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Running postrm hook script /sbin/update-grub.
Can't locate Debconf/Db.pm in @INC (@INC contains: /usr/local/lib/perl5/5.10.0/i686-linux /usr/local/lib/perl5/5.10.0 /usr/local/lib/perl5/site_perl/5.10.0/i686-linux /usr/local/lib/perl5/site_perl/5.10.0 .) at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
User postrm hook script [/sbin/update-grub] exited with value 2
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.34_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@tools:/boot# 
```

Also, I'm not sure why its trying to do this upgrade. as I'm already running the kernel
```
root@tools:/boot# uname -a
Linux tools 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 i686 GNU/Linux

```

---

### Post by fishtoprecords on 2008-06-23
Followup: I'm running perl 5.10, rather than the standard 5.8

---

### Post by apoth on 2008-06-24
I then had to rm -rf /boot/.Trash-0 - presumably because I used nautilus to delete the old stuff.

---

### Post by fishtoprecords on 2008-06-26
I ended up nuking perl 5.10 and using the old 5.8 that comes with the default distribution.

So its working, but I don't grok why it failed, or how I can get 5.10 and have ubuntu upgrades work

---

