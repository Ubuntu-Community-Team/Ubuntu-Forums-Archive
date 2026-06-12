---
title: "E: Sub-process error (1) after do-release-upgrade"
date: 2012-05-29
forum: Installation &amp; Upgrades
---

### Post by mytinytown on 2012-05-29
Hello,

I am not a Linux master, but I know enough to get by, so it could be a simple fix and I just don't know.

During the do-release-upgrade process from 11.11 Server to 12.04 I had an error. I can not tell you the exact error, but it was very similar, if not the same as this error:
```

@Theserver:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]?
Setting up initramfs-tools (0.99ubuntu13) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-24-generic-pae with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


I have tried:
```

@Theserver:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up initramfs-tools (0.99ubuntu13) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-24-generic-pae with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

and this:

```

@Theserver:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.99ubuntu13) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-24-generic-pae with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools

```

Finally I tried:
```

@Theserver:~$ sudo apt-get install --reinstall initramfs-tools
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up initramfs-tools (0.99ubuntu13) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.2.0-24-generic-pae with 1.
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

There is 9+ GB available on the partition.

---

### Post by drmrgd on 2012-05-29
Are you positive that there is more than 9 GB available?  The error really does suggest that there is not enough space on the partition you're trying to install to.  What is the output of ```
df -h
```?

---

### Post by mytinytown on 2012-05-29
Samba shows 9GB available and I did remove a few items too.

Here is what I got:
```

@Theserver:~$ df -h
Filesystem                  Size  Used Avail Use% Mounted on
/dev/mapper/Theserver-root   16G  5.2G  9.2G  37% /
udev                        115M  4.0K  115M   1% /dev
tmpfs                        49M  1.7M   47M   4% /run
none                        5.0M     0  5.0M   0% /run/lock
none                        122M     0  122M   0% /run/shm
/dev/sda1                   228M  216M  437K 100% /boot
/dev/sdb1                    37G   24G   12G  68% /Public
192.168.2.2:/Public          37G   24G   12G  68% /Fileserver

```

---

### Post by itzpraveenv on 2012-05-29
try this 
sudo

sudo rm -f /var/lib/dpkg/info/initramfs-tools.post*
sudo rm -f /var/lib/dpkg/info/initramfs-tools.pre*

sudo rm -f /var/lib/dpkg/info/bcmwl-kernel-source.post*
sudo rm -f /var/lib/dpkg/info/bcmwl-kernel-source.pre*

sudo dpkg --configure -a

---

### Post by mytinytown on 2012-05-30
OK
```

@Theserver:~$ sudo rm -f /var/lib/dpkg/info/initramfs-tools.post*
[sudo] password for mdius:
@Theserver:~$ sudo rm -f /var/lib/dpkg/info/initramfs-tools.pre*
@Theserver:~$ sudo rm -f /var/lib/dpkg/info/bcmwl-kernel-source.post*
@Theserver:~$ sudo rm -f /var/lib/dpkg/info/bcmwl-kernel-source.pre*
@Theserver:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.99ubuntu13) ...

```

After I ran apt-get upgrade and got:
```

@Theserver:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

It appears to be fixed!
Thank you!!!!

---

