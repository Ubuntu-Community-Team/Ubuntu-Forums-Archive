---
title: "Error: Brokencount"
date: 2011-07-24
forum: Installation &amp; Upgrades
---

### Post by happyisland on 2011-07-24
My wife just handed me her laptop and said "fix this". 

Help!

Here's the totaly output of the error message when following the system's instructions. There's now a red circle with a horizontal line through it on the top panel, and the system won't allow the installation or upgrade of any packages. What gives?

```
installArchives() failed: (Reading database ... 
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
(Reading database ... 381173 files and directories currently installed.)

Unpacking linux-image-2.6.35-30-generic (from .../linux-image-2.6.35-30-generic_2.6.35-30.56_i386.deb) ...

Done.

dpkg: error processing /var/cache/apt/archives/linux-image-2.6.35-30-generic_2.6.35-30.56_i386.deb (--unpack):

 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-2.6.35-30-generic': No space left on device

No apport report written because MaxReports is reached already
dpkg-deb: subprocess paste killed by signal (Broken pipe)

Running postrm hook script /sbin/update-grub.

Searching for GRUB installation directory ... found: /boot/grub

Searching for default file ... found: /boot/grub/default

Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst

Searching for splash image ... none found, skipping ...

Found kernel: /vmlinuz-2.6.35-29-generic

Found kernel: /vmlinuz-2.6.35-28-generic

Found kernel: /vmlinuz-2.6.35-27-generic

Found kernel: /vmlinuz-2.6.35-26-generic

Found kernel: /vmlinuz-2.6.35-25-generic

Found kernel: /vmlinuz-2.6.35-24-generic

Found kernel: /vmlinuz-2.6.35-23-generic

Found kernel: /vmlinuz-2.6.35-22-generic

Found kernel: /vmlinuz-2.6.32-25-generic

Found kernel: /vmlinuz-2.6.31-22-generic

Found kernel: /vmlinuz-2.6.28-16-generic

Found kernel: /vmlinuz-2.6.27-14-generic

Found kernel: /vmlinuz-2.6.24-24-generic

Found kernel: /memtest86+.bin

Updating /boot/grub/menu.lst ... done



Examining /etc/kernel/postrm.d .

run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic

Errors were encountered while processing:

 /var/cache/apt/archives/linux-image-2.6.35-30-generic_2.6.35-30.56_i386.deb

Setting up initramfs-tools (0.98.1ubuntu6.1) ...

update-initramfs: deferring update (trigger activated)

dpkg: dependency problems prevent configuration of linux-image-generic:

 linux-image-generic depends on linux-image-2.6.35-30-generic; however:

  Package linux-image-2.6.35-30-generic is not installed.

dpkg: error processing linux-image-generic (--configure):

 dependency problems - leaving unconfigured

dpkg: dependency problems prevent configuration of linux-generic:

 linux-generic depends on linux-image-generic (= 2.6.35.30.38); however:

  Package linux-image-generic is not configured yet.

dpkg: error processing linux-generic (--configure):

 dependency problems - leaving unconfigured

Processing triggers for initramfs-tools ...

update-initramfs: Generating /boot/initrd.img-2.6.35-29-generic



gzip: stdout: No space left on device

cpio: write error: Broken pipe

E: mkinitramfs failure cpio 1 gzip 1

update-initramfs: failed for /boot/initrd.img-2.6.35-29-generic

dpkg: error processing initramfs-tools (--configure):

 subprocess installed post-installation script returned error exit status 1


```

---

### Post by plucky on 2011-07-25
> gzip: stdout: No space left on device


Do you have a separate /boot partition?

> Found kernel: /vmlinuz-2.6.35-29-generic

Found kernel: /vmlinuz-2.6.35-28-generic

Found kernel: /vmlinuz-2.6.35-27-generic

Found kernel: /vmlinuz-2.6.35-26-generic

Found kernel: /vmlinuz-2.6.35-25-generic

Found kernel: /vmlinuz-2.6.35-24-generic

Found kernel: /vmlinuz-2.6.35-23-generic

Found kernel: /vmlinuz-2.6.35-22-generic

Found kernel: /vmlinuz-2.6.32-25-generic

Found kernel: /vmlinuz-2.6.31-22-generic

Found kernel: /vmlinuz-2.6.28-16-generic

Found kernel: /vmlinuz-2.6.27-14-generic

Found kernel: /vmlinuz-2.6.24-24-generic


There are a lot of installed kernels which can be removed using Synaptic Package Manager.

To create space,open a terminal and run ```
sudo apt-get clean
```

Then run SPM and remove the older kernels making sure you leave the latest kernel and one older kernel.

Good Luck

---

### Post by happyisland on 2011-08-05
That seems to have done the trick. Thanks plucky!

Crazy, but I think her laptop had over a GB of unused linux kernels on it. Removed them and it's smooth sailing.

---

