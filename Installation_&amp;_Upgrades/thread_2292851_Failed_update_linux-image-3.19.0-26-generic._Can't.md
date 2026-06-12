---
title: "Failed update linux-image-3.19.0-26-generic. Can't boot."
date: 2015-08-31
forum: Installation &amp; Upgrades
---

### Post by kayoticsully on 2015-08-31
Hello!  I have tried searching around for this but I can't seem to find any solutions for my specific problem.  My laptop is having trouble installing the package linux-image-3.19.0-26-generic. And not my system can not boot (that was mostly my fault in trying to fix this problem. I had un-installed previous kernels, and now I'm hosed since I cant get this to install).

The error output from *apt-get upgrade* is:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
E: Can not write log (Is /dev/pts mounted?) - posix_openpt (2: No such file or directory)
Setting up linux-image-3.19.0-26-generic (3.19.0-26.28) ...
Running depmod.

Usage: /usr/sbin/mkinitramfs [OPTION]... -o outfile [version]

Options:
  -c compress    Override COMPRESS setting in initramfs.conf.
  -d confdir    Specify an alternative configuration directory.
  -k        Keep temporary directory used to make the image.
  -o outfile    Write to outfile.
  -r root    Override ROOT setting in initramfs.conf.

See mkinitramfs(8) for further details.
Failed to create initrd image.
dpkg: error processing package linux-image-3.19.0-26-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-3.19.0-26-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have tried rebuilding my initrd image.  I have tried running *dpkg --configure -a* which gives me no output at all.  And when I run *depmod* manually (with no options.. i don't know much about depmod) I get the output:
```
depmod: ERROR: could not open directory /lib/modules/3.19.0-15-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
```

Some more info:
I have two encrypted drives that I am mounting at boot.  Right now when I try to boot I can get to grub and start the boot process.  It hangs at loading the initramfs and I never get prompted for my encrypted drive passwords. That could be a different issue all together, but figured I would mention it just in case it helps diagnose this problem as well.

Thanks in advance, any help is appreciated!

---

### Post by TheFu on 2015-08-31
Shot in the dark - was/is /boot full?

---

### Post by kayoticsully on 2015-08-31
I just checked.  No my boot is only 4% full.  I gave it plenty of space because I have run into that in the past.  Good thought though, I hadn't checked that yet.

```
root@ubuntu:/# df -h
Filesystem                Size  Used Avail Use% Mounted on
/dev/mapper/vgsys-lvroot   20G  5.0G   14G  27% /
/dev/mapper/vgsys-lvhome   34G  2.3G   30G   7% /home
/dev/sda2                 976M   35M  875M   4% /boot
/dev/sda1                 197M  3.4M  194M   2% /boot/efi
udev                      3.8G     0  3.8G   0% /dev
```

---

### Post by TheFu on 2015-08-31
Well - that's the end of my knowledge for how to fix this ... if you don't need a solution immediately, I'd wait another day or so for others to respond.  Might be a trivial fix. I dunno.

OTOH, if you need it back ASAP and need some action now, 
* ensure the last backup has everything
* do a fresh install then 
* restore your stuff

---

### Post by kayoticsully on 2015-09-01
I ended up re-installing to solve the problem.  It was just faster and easier than having the computer out of commission for a few days.  If anyone could venture a guess as to what caused the issue it would be much appreciated :)  

Otherwise, thank you for your help, hopefully this doesn't happen again!

---

