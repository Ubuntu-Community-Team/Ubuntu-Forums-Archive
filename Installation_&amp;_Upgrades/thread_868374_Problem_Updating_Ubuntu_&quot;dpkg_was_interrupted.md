---
title: "Problem Updating Ubuntu &quot;dpkg was interrupted&quot;"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by walkman79 on 2008-07-23
Hello, I hope someone help me with this problem.

I have rented a server from OVH.com, a kimsufi with Ubuntu 8.0.4 LTS as the OS. Every thing was fine till I tried to update the system. Now, **apt-get doesn't work at all**:

> $ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Neither Synaptic or the Update Manager :(. I can't install any program unless I do it manually of course. Every time I want to use any of the package/update manager I get this:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

But if I run that command:

> $ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Cannot find /lib/modules/2.6.24-16-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1

I looked into that folder and I actually don't have "/lib/modules/2.6.24-16-generic": 

> $ ls -la /lib/modules/
total 12
drwxr-xr-x  3 root root 4096 2008-06-03 08:27 .
drwxr-xr-x 15 root root 4096 2008-07-24 01:31 ..
drwxr-xr-x  2 root root 4096 2008-06-03 08:27 2.6.24-17-generic

Btw, **I don't have GRUB installed**, I don't have physical access to the server, and as I said **apt-get doesn't work at all**. 

Could anyone please tell me how to fix this ?

Any help would be greatly appreciated.

---

### Post by Joeb454 on 2008-07-23
From a terminal run the following ```
sudo dpkg --configure -a
```

Oh wait, I just re-read and see you did...I had that issue once, I'll try and remember how I fixed it.

---

### Post by iaculallad on 2008-07-23
The work around for this problem is by removing the postrm scripts files that
fail apt from removing/reconfiguring these packages.  
If you're really not going to use the 2.6.24-16 kernel, remove it:

```
sudo rm /var/lib/dpkg/info/linux-backports-modules-2.6.24-16-generic.postrm
sudo rm /var/lib/dpkg/info/linux-ubuntu-modules-2.6.24-16-generic.postrm
sudo apt-get remove linux-ubuntu-modules-2.6.24-16-generic                      
sudo apt-get removelinux-backports-modules-2.6.24-16-generic
```

Then:

```
sudo dpkg --configure -a
```

---

### Post by walkman79 on 2008-07-23
> **iaculallad said:**
> The work around for this problem is by removing the postrm scripts files that
fail apt from removing/reconfiguring these packages.  
If you're really not going to use the 2.6.24-16 kernel, remove it:

```
sudo rm /var/lib/dpkg/info/linux-backports-modules-2.6.24-16-generic.postrm
sudo rm /var/lib/dpkg/info/linux-ubuntu-modules-2.6.24-16-generic.postrm
sudo apt-get remove linux-ubuntu-modules-2.6.24-16-generic                      
sudo apt-get removelinux-backports-modules-2.6.24-16-generic
```

Then:

```
sudo dpkg --configure -a
```


Thanks for your reply, I did what you said:

> $ sudo rm /var/lib/dpkg/info/linux-backports-modules-2.6.24-16-generic.postrm
rm: cannot remove `/var/lib/dpkg/info/linux-backports-modules-2.6.24-16-generic.postrm': No such file or directory

$ sudo rm /var/lib/dpkg/info/linux-ubuntu-modules-2.6.24-16-generic.postrm
rm: cannot remove `/var/lib/dpkg/info/linux-ubuntu-modules-2.6.24-16-generic.postrm': No such file or directory

Also as I said **[SIZE="3"]apt-get doesn't work[/SIZE]** (<-- Actually, this is my main problem):
> $ sudo apt-get remove linux-ubuntu-modules-2.6.24-16-generic
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
$ sudo apt-get removelinux-backports-modules-2.6.24-16-generic
E: Invalid operation removelinux-backports-modules-2.6.24-16-generic
$ sudo apt-get remove linux-backports-modules-2.6.24-16-generic
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

These are the things which begins with "linux-" I have on that folder:
> $ ls -la /var/lib/dpkg/info/linux-
linux-headers-2.6.24-16-generic.list               linux-restricted-modules-2.6.24-12-generic.postrm
linux-headers-2.6.24-16-generic.md5sums            linux-restricted-modules-common.conffiles
linux-headers-2.6.24-16-generic.postinst           linux-restricted-modules-common.list
linux-headers-2.6.24-16.list                       linux-restricted-modules-common.md5sums
linux-headers-2.6.24-16.md5sums                    linux-restricted-modules-common.postinst
linux-headers-2.6.24-17-generic.list               linux-restricted-modules-common.postrm
linux-headers-2.6.24-17-generic.md5sums            linux-sound-base.config
linux-headers-2.6.24-17-generic.postinst           linux-sound-base.list
linux-headers-2.6.24-17.list                       linux-sound-base.md5sums
linux-headers-2.6.24-17.md5sums                    linux-sound-base.postinst
linux-headers-generic.list                         linux-sound-base.postrm
linux-headers-generic.md5sums                      linux-sound-base.templates
linux-libc-dev.list                                linux-ubuntu-modules-2.6.24-12-generic.list
linux-libc-dev.md5sums                             linux-ubuntu-modules-2.6.24-12-generic.postrm
linux-restricted-modules-2.6.24-12-generic.list

---

