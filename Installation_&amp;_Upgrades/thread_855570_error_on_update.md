---
title: "error on update"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by tom79 on 2008-07-10
Hi,
I have an error when I update.


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I'm a complete newbie. Can anyone explain what this means, and what I shud do to fix the problem.

---

### Post by cpetercarter on 2008-07-10
Applications > Accessories > Terminal

Then in the terminal type:

```
sudo dpkg --configure -a
```

You will be asked for your password. type it in and press enter. (You wont see your password on the screen as you type it. Don't worry. That's normal.)

---

### Post by tom79 on 2008-07-10
Hi cpetercarter,
thanks!!! that solved the problem. i maybe asking for too much here, but can u explain what went wrong? 

thanks again!

---

### Post by cpetercarter on 2008-07-10
Not really. But this is a very common error message when a download is interrupted for some reason. Someday, someone will develop a little routine which will actually run "dpkg --configure" etc for you instead of telling you to do it yourself. Until then .....

---

### Post by tom79 on 2008-07-10
understand. Thanks!

---

### Post by Rhshea21 on 2008-07-10
OK so i have the same problem but when i run that command in the terminal i get this and the problem doesnt seem to be fixed... any help would be greatly appreciated...

robert@robert-laptop:~$ sudo dpkg --configure -a
[sudo] password for robert: 
Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-image-2.6.24-18-generic (2.6.24-18.32) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-18-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.24-18-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-18-generic:
 linux-restricted-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-18-generic:
 linux-ubuntu-modules-2.6.24-18-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-18-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-18-generic; however:
  Package linux-image-2.6.24-18-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-18-generic; however:
  Package linux-ubuntu-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-18-generic; however:
  Package linux-restricted-modules-2.6.24-18-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.18.20); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.18.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: subprocess post-installation script returned error exit status 1
robert@robert-laptop:~$ 


Thanks for any help!
Robert

---

### Post by iaculallad on 2008-07-10
For Robert:

> gzip: stdout: No space left on device

Try to delete OLD kernel backup files in your /boot directory.

```
sudo rm /boot/*.bak
```

Then, redo you're:

```
sudo dpkg --configure -a
```

---

