---
title: "dependency not met linux-image-...-generic-pae"
date: 2013-05-03
forum: Installation &amp; Upgrades
---

### Post by wiseveri on 2013-05-03
I can't update my ubuntu server 12.04 system because I have this missing dependency to linux-image-..-generic-pae.

Running sudo apt-get -f install leads to
```
$ sudo apt-get -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-32 linux-headers-3.2.0-32-generic-pae linux-headers-3.2.0-33 linux-headers-3.2.0-33-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.2.0-41-generic-pae
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.2.0-41-generic-pae
0 upgraded, 1 newly installed, 0 to remove and 93 not upgraded.
3 not fully installed or removed.
Need to get 0 B/38.3 MB of archives.
After this operation, 113 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 152627 files and directories currently installed.)
Unpacking linux-image-3.2.0-41-generic-pae (from .../linux-image-3.2.0-41-generic-pae_3.2.0-41.66_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.2.0-41-generic-pae_3.2.0-41.66_i386.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/System.map-3.2.0-41-generic-pae': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-41-generic-pae /boot/vmlinuz-3.2.0-41-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-41-generic-pae /boot/vmlinuz-3.2.0-41-generic-pae
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.2.0-41-generic-pae_3.2.0-41.66_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

running dpkg --configure -a leads to
```

$ sudo dpkg --configure -a
Setting up initramfs-tools (0.99ubuntu13) ...
update-initramfs: deferring update (trigger activated)
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-41-generic-pae; however:
  Package linux-image-3.2.0-41-generic-pae is not installed.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.41.49); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-33-generic-pae


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-33-generic-pae with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-generic-pae
 linux-generic-pae
 initramfs-tools
```

Any hints how to fix this?

---

### Post by tgalati4 on 2013-05-03
failed in write on buffer copy for backend dpkg-deb during `./boot/System.map-3.2.0-41-generic-pae':** No space left on device**

Open a terminal, post the output of:

```
df -h
```

Disk space is like air--when you run out you die.

---

### Post by wiseveri on 2013-05-03
```

df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/greek--god-root  1.4T  1.3T   34G  98% /
udev                         488M  4.0K  488M   1% /dev
tmpfs                        199M  1.2M  198M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         496M  4.0K  496M   1% /run/shm
/dev/sda1                    228M  222M     0 100% /boot
/home/new-god/.Private       1.4T  1.3T   34G  98% /home/new-god

```

---

### Post by ibjsb4 on 2013-05-03
This may help

[http://ubuntuforums.org/showthread.php?t=2141370](http://ubuntuforums.org/showthread.php?t=2141370)

---

### Post by matt_symes on 2013-05-03
Hi

> /dev/sda1                    228M  222M     0 100% /boot

No space in your boot partition. You need to remove some old kernels.

Kind regards

---

### Post by wiseveri on 2013-05-03
> **matt_symes said:**
> Hi
No space in your boot partition. You need to remove some old kernels.

Kind regards

So finding out which kernels I have installed

```

$ dpkg --list | grep linux-image
rc  linux-image-3.0.0-12-generic-pae   3.0.0-12.20                      Linux kernel image for version 3.0.0 on x86
rc  linux-image-3.0.0-13-generic-pae   3.0.0-13.22                      Linux kernel image for version 3.0.0 on x86
ii  linux-image-3.0.0-14-generic-pae   3.0.0-14.23                      Linux kernel image for version 3.0.0 on x86
rc  linux-image-3.0.0-15-generic-pae   3.0.0-15.26                      Linux kernel image for version 3.0.0 on x86
rc  linux-image-3.0.0-16-generic-pae   3.0.0-16.29                      Linux kernel image for version 3.0.0 on x86
rc  linux-image-3.0.0-17-generic-pae   3.0.0-17.30                      Linux kernel image for version 3.0.0 on x86
ii  linux-image-3.2.0-24-generic-pae   3.2.0-24.39                      Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-25-generic-pae   3.2.0-25.40                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-26-generic-pae   3.2.0-26.41                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-27-generic-pae   3.2.0-27.43                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-29-generic-pae   3.2.0-29.46                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-31-generic-pae   3.2.0-31.50                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-32-generic-pae   3.2.0-32.51                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-33-generic-pae   3.2.0-33.52                      Linux kernel image for version 3.2.0 on 32 bit x86 SMP
iU  linux-image-generic-pae            3.2.0.41.49                      Generic Linux kernel image

```

But then trying to uninstall the ones with 'ii' leads to
```

$ sudo apt-get remove linux-image-3.0.0-14-generic-pae 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic-pae : Depends: linux-image-3.2.0-41-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

So I can't uninstall kernels, because I have unmet dependencies, which I can't meet because I haven't enough space?!

---

### Post by matt_symes on 2013-05-03
Hi 

Open a terminal and copy and past this line into it.

```
sudo dpkg -P linux-image-3.0.0-{12,13,14,15,16,17}-generic-pae
```

And then this one...

```
sudo dpkg -P linux-image-3.2.0-{24,25,26,27,29,31}-generic-pae
```

That'll leave two kernels for you.

After that, clean up any kernel headers you have installed.

Finally

```
sudo apt-get install -f
```

Kind regards

---

### Post by wiseveri on 2013-05-03
Thank you very much. This solved it!

---

