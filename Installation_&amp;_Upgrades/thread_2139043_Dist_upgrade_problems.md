---
title: "Dist upgrade problems"
date: 2013-04-25
forum: Installation &amp; Upgrades
---

### Post by jsmeche on 2013-04-25
Hi all,

I have been using 13.04 beta for months and decided to do a dist-upgrade yesterday. I got a few errors that I haven't been able to figure out. I have posted the the terminal output below:

Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-extra-3.8.0-19-generic (3.8.0-19.29) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.8.0-19-generic /boot/vmlinuz-3.8.0-19-generic
update-initramfs: Generating /boot/initrd.img-3.8.0-19-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-3.8.0-19-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-extra-3.8.0-19-generic.postinst line 1010.
dpkg: error processing linux-image-extra-3.8.0-19-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-3.8.0-19-generic; however:
  Package linux-image-extra-3.8.0-19-generic is not configured yet.

dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.8.0.19.35); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-3.8.0-19-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


I am running on a Dell Inspiron 1545, Core2 duo. 

Anybody have any ideas? Thanks.

---

### Post by fantab on 2013-04-25
You have a package that was not installed correctly or is broken. You have to remove [I]linux-image-extra-3.8.0-19-generic.
[/I]
The relevant error messages from your output are:
```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
...
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-extra-3.8.0-19-generic.postinst line 1010.
dpkg: error processing linux-image-extra-3.8.0-19-generic (--configure):
subprocess installed post-installation script returned error exit status 2
``` 

This should be quite effortless if you have 'Synaptic Package Manager' installed. If you don't then:

```
gksudo nautilus /var/lib/dpkg/info
```

Now find **ALL** files starting with names *linux-headers-3.8.0-19* and **DELETE** them **ALL**. Then:

```
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install linux
```

---

### Post by jsmeche on 2013-04-25
Thanks for your help, However I did a uname -a and it shows that I am running 3.8.0-19-generic as the current running kernel and I have read that I don't want to delete the kernel that I am using. 
Can you confirm this is correct?

---

### Post by snowpine on 2013-04-25
This might be a clue:

> **jsmeche said:**
> 
gzip: stdout: No space left on device

;)

---

### Post by fantab on 2013-04-25
Yes that is correct. What you can do is boot from Grub to an older kernel if you have one and follow instructions in my post #2. If you don't have an older kernel then boot into "Recovery Mode" from Grub Menu and fix dpkg.

EDIT: snowpine has a point. How big is your "/" partition?

---

### Post by jsmeche on 2013-04-25
I think it is 100MB, I am not accustomed to changing anything like that during the install and I think that is a pretty standard size.
I just read in other threads that people have recommended deleting older kernels to free up some space in /boot. I'm a little nervous, so I am backing up my files and then I will try that.

---

### Post by ibjsb4 on 2013-04-25
> **jsmeche said:**
> i just read in other threads that people have recommended deleting older kernels to free up some space in /boot. I'm a little nervous, so i am backing up my files and then i will try that.

> **fantab said:**
> this should be quite effortless if you have 'synaptic package manager' installed

   :)

---

### Post by jsmeche on 2013-04-25
Hey everybody, I deleted an older kernel and it completely fixed my problem. Just thought I would let you know.

---

