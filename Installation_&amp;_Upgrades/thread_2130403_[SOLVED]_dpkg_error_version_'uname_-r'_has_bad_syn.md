---
title: "[SOLVED] dpkg: error: version 'uname -r' has bad syntax: version string has embedd"
date: 2013-03-29
forum: Installation &amp; Upgrades
---

### Post by KillerKelvUK on 2013-03-29
Noticed the above error when upgrading via apt-get on my server.  I don't have any problems with the server, no symptoms but the message seems to be consistent so would like to address it.

Google only finds me this [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=369177](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=369177) link which is a clear bug report on this error but dates back to 2006 and is on an old dpkg version.

The below are the preceding lines output from 'apt-get upgrade', the final line is the end of the upgrade.  A 'uname -r' returns "3.2.0-39-generic".

> 
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
dpkg: error: version 'uname -r' has bad syntax: version string has embedded spaces
dpkg: error: version 'uname -r' has bad syntax: version string has embedded spaces
update-initramfs: Generating /boot/initrd.img-3.2.0-39-generic


Please can someone point me in the right direction, maybe I'm googling the wrong terms...I'm not a linux expert so am learning as I go.

Thanks,

K

---

### Post by matt_symes on 2013-03-29
Hi

Can you post the output of

```
dpkg -C
```

capital C above and

```
grep -rv ^# /etc/apt/sources.list{,.d}
```

Kind regards

---

### Post by KillerKelvUK on 2013-03-29
"dpkg -C" returns nothing i.e. no broken packages

"grep -rv ^# /etc/apt/sources.list{,.d}" as below...

> /etc/apt/sources.list:
/etc/apt/sources.list:
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted
/etc/apt/sources.list:deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted
/etc/apt/sources.list:deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates main restricted
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe
/etc/apt/sources.list:deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates universe
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
/etc/apt/sources.list:deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise multiverse
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse
/etc/apt/sources.list:deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
/etc/apt/sources.list:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
/etc/apt/sources.list:
/etc/apt/sources.list:
/etc/apt/sources.list:
/etc/apt/sources.list.d/jcfp-ppa-precise.list.save:deb [http://ppa.launchpad.net/jcfp/ppa/ubuntu](http://ppa.launchpad.net/jcfp/ppa/ubuntu) precise main
/etc/apt/sources.list.d/jcfp-ppa-precise.list.save:deb-src [http://ppa.launchpad.net/jcfp/ppa/ubuntu](http://ppa.launchpad.net/jcfp/ppa/ubuntu) precise main
/etc/apt/sources.list.d/jcfp-ppa-precise.list:deb [http://ppa.launchpad.net/jcfp/ppa/ubuntu](http://ppa.launchpad.net/jcfp/ppa/ubuntu) precise main
/etc/apt/sources.list.d/jcfp-ppa-precise.list:deb-src [http://ppa.launchpad.net/jcfp/ppa/ubuntu](http://ppa.launchpad.net/jcfp/ppa/ubuntu) precise main
/etc/apt/sources.list.d/tbfr-zabbix-precise.list:deb [http://ppa.launchpad.net/tbfr/zabbix/ubuntu](http://ppa.launchpad.net/tbfr/zabbix/ubuntu) precise main
/etc/apt/sources.list.d/tbfr-zabbix-precise.list:deb-src [http://ppa.launchpad.net/tbfr/zabbix/ubuntu](http://ppa.launchpad.net/tbfr/zabbix/ubuntu) precise main

---

### Post by matt_symes on 2013-03-29
Hi

Maybe a ppa problem ? Have you tried disabling the ppas to implicate/eliminate them ?

This is not an error i have seen before.

Anyway, can you post the full output of

```
sudo apt-get install -f
```

Kind regards

---

### Post by KillerKelvUK on 2013-03-29
Sorry should have said thanks on my first reply so thanks :D

> **matt_symes said:**
> Maybe a ppa problem ? Have you tried disabling the ppas to implicate/eliminate them ?

What's the best way to do this...just comment out the lines in the sources.list file?

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install -f[/FONT][/COLOR]
``` gives me...

> 
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


---

### Post by schragge on 2013-03-29
Interesting. Looks like some script erroneously uses single quotes instead of backticks, i.e. ```
[COLOR=red]'[/COLOR]uname -r[COLOR=red]'[/COLOR]
``` instead of ```
[COLOR=red]`[/COLOR]uname -r[COLOR=red]`[/COLOR]
``` Could you please post the output of
```
grep 'uname -r' /usr/sbin/update-initramfs /var/lib/dpkg/info/*
```

---

### Post by KillerKelvUK on 2013-03-29
Sure..."[COLOR=#000000][FONT=Ubuntu Mono]grep 'uname -r' /var/lib/dpkg/info/*" gives me...[/FONT][/COLOR]

> 
/var/lib/dpkg/info/keyboard-configuration.config:    kern=`uname -r`
/var/lib/dpkg/info/keyboard-configuration.postinst:    kern=`uname -r`
/var/lib/dpkg/info/libc6:amd64.preinst:        kernel_rev=$(uname -r | sed 's/\([0-9]*\.\)\{1,2\}\([0-9]*\)\(.*\)/\2/')
/var/lib/dpkg/info/libc6:amd64.preinst:        kernel_ver=`uname -r`
/var/lib/dpkg/info/libc6:amd64.preinst:        kernel_ver=`uname -r`
/var/lib/dpkg/info/linux-image-3.2.0-38-generic.prerm:chop($running=`uname -r`);
/var/lib/dpkg/info/linux-image-3.2.0-39-generic.prerm:chop($running=`uname -r`);
/var/lib/dpkg/info/makedev.postinst:kern_rev1=`uname -r | sed -e 's@^\([^.]*\)\..*@\1@'`
/var/lib/dpkg/info/makedev.postinst:kern_rev2=`uname -r | sed -e 's@^[^.]*\.\([^.]*\)\..*@\1@'`
/var/lib/dpkg/info/postfix.preinst:     if dpkg --compare-versions "`uname -r`" lt 2.6.0 ; then


---

### Post by schragge on 2013-03-29
Nothing unusual so far. Try
```
grep 'uname -r' `which update-initramfs`
```

BTW, why do you have *makedev* installed? It's usually not needed on a modern Linux system that uses [udev](http://manpages.ubuntu.com/manpages/precise/en/man7/udev.7.html).

---

### Post by KillerKelvUK on 2013-03-29
;)...

> 
        if [ -f /boot/initrd.img-`uname -r` ]; then
                version=`uname -r`


---

### Post by matt_symes on 2013-03-29
Hi

This is an odd one schragge. I've never come across this one before. It's a good idea to search the scripts.

@OP. This command below will rename all your ppa files from *.list to *.old. It's reversible easily enough.

You can copy and paste into the terminal. It will cut the search down.

```
sudo rename -v 's/\.list$/\.old/' /etc/apt/sources.list.d/*.list
```

```
sudo apt-get update
```

You can then run the same command that was giving you the error before.

Kind regards

---

### Post by KillerKelvUK on 2013-03-29
@matt_symes...

Happy to do as you suggest but atm I've no easy way to replicate the message on demand...its so far only presented when I've got updates to apply (sudo apt-get upgrade).  Is there a way I can quickly "re-do" (my words) the initramfs set up which seems to be linked to this problem, I'm thinking this might generate the error and allow an easy test of your suggestion?

---

### Post by steeldriver on 2013-03-29
... I wonder if the OP has a kernel file or initrd.img file in /boot that somehow got renamed something like "initrd.img-uname -r-generic-pae" or "vmlinuz-(uname -r)-generic" due to some previous mishap, and a script is tripping over that?

---

### Post by KillerKelvUK on 2013-03-29
> **steeldriver said:**
> ... I wonder if the OP has a kernel file or initrd.img file in /boot that somehow got renamed something like "initrd.img-uname -r-generic-pae" or "vmlinuz-(uname -r)-generic" due to some previous mishap, and a script is tripping over that?

Erm...I'm not fully understanding but...

> 
me@myserver/boot$ ls -la
total 50182
drwxr-xr-x  5 root root     1024 Mar 29 14:24 .
drwxr-xr-x 25 root root     4096 Mar 23 18:37 ..
-rw-r--r--  1 root root   792830 Feb 19 12:58 abi-3.2.0-38-generic
-rw-r--r--  1 root root   792830 Feb 28 01:09 abi-3.2.0-39-generic
-rw-r--r--  1 root root   140488 Feb 19 12:58 config-3.2.0-38-generic
-rw-r--r--  1 root root   140488 Feb 28 01:09 config-3.2.0-39-generic
drwxr-xr-x  3 root root     2048 Jan  1  1970 efi
drwxr-xr-x  3 root root     4096 Mar 23 18:37 grub
-rw-r--r--  1 root root 15169141 Mar 23 18:34 initrd.img-3.2.0-38-generic
-rw-r--r--  1 root root 15170883 Mar 29 14:24 initrd.img-3.2.0-39-generic
-rw-r--r--  1 root root  2867173 Jan 13 12:28 initrd.img-uname -r
drwxr-xr-x  2 root root    12288 Jan 11 23:41 lost+found
-rw-r--r--  1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r--  1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw-------  1 root root  2887333 Feb 19 12:58 System.map-3.2.0-38-generic
-rw-------  1 root root  2888361 Feb 28 01:09 System.map-3.2.0-39-generic
-rw-------  1 root root  4968592 Feb 19 12:58 vmlinuz-3.2.0-38-generic
-rw-------  1 root root  4971472 Feb 28 01:09 vmlinuz-3.2.0-39-generic


Note the "-rw-r--r--  1 root root  2867173 Jan 13 12:28 initrd.img-uname -r"...is this it?

---

### Post by schragge on 2013-03-29
Yep. Good call, **steeldriver**. @**OP**: just remove that file:
```

sudo rm /boot/initrd.img-uname*

```

---

### Post by KillerKelvUK on 2013-03-29
Great guys thanks...but how do I check it worked?

:guitar:

---

### Post by matt_symes on 2013-03-29
Hi

Assuming it's happening when generating an initramfs you can use

```
sudo update-initramfs -u
```

This will rebuild the initial ram disk for you current kernel.

EDIT: 

Good call steeldriver. That may well be it.

Kind regards

---

### Post by KillerKelvUK on 2013-03-29
okay so not quite...

> sudo update-initramfs -u
dpkg: error: version 'uname -r' has bad syntax: version string has embedded spaces
dpkg: error: version 'uname -r' has bad syntax: version string has embedded spaces
update-initramfs: Generating /boot/initrd.img-3.2.0-39-generic

But I guess now we have a check that replicates the problem...

Appreciate the effort guys, what do I try next?

---

### Post by schragge on 2013-03-29
Check that you actually have removed that file. If not, remove it again:
```
sudo rm -v /boot/initrd.img-uname*
``` then re-run *update-initramfs*, also with -v (--verbose) to see what happens:
```
sudo update-initramfs -uv
``` If the file appears again, try
```
sudo update-initramfs -d 'uname -r'
``` Note the single quotes, be cautious not to remove the initrd for current kernel.

---

### Post by KillerKelvUK on 2013-03-29
Definitely removed...result of your command...rm: cannot remove `/boot/initrd.img-uname*': No such file or directory

---

### Post by schragge on 2013-03-29
Also check the directory */var/lib/initramfs-tools/*, it may contain checksum for the wrong version. Now, I guess the only proper way to remove an initrd is
```
sudo update-initramfs -d 'uname -r'
``` Note single quotes around uname -r, be cautious not to remove initrd for the current kernel. If this doesn't work, try:
```
sudo rm -v /var/lib/initramfs-tools/uname*
```

---

### Post by KillerKelvUK on 2013-03-29
yup...

> 
/var/lib/initramfs-tools$ ls -l
total 12
-rw-r--r-- 1 root root 76 Mar 23 18:34 3.2.0-38-generic
-rw-r--r-- 1 root root 76 Mar 29 20:19 3.2.0-39-generic
-rw-r--r-- 1 root root 68 Jan 13 12:28 uname -r


but...

> 
sudo update-initramfs -d 'uname -r'
Invalid argument for option -k.
Usage: /usr/sbin/update-initramfs [OPTION]...


Options:
 -k [version]   Specify kernel version or 'all'
 -c             Create a new initramfs
 -u             Update an existing initramfs
 -d             Remove an existing initramfs
 -t             Take over a custom initramfs with this one
 -b             Set alternate boot directory
 -v             Be verbose
 -h             This message


---

### Post by schragge on 2013-03-29
Then just remove the checksum file
```
sudo rm -v /var/lib/initramfs-tools/uname*
``` and re-run
```
sudo update-initramfs -u
```

---

### Post by KillerKelvUK on 2013-03-29
Worked a treat, many thanks!

Think I may have borked this when trying to remove old kernel versions.

I appreciate the effort both, thanks.

K

---

