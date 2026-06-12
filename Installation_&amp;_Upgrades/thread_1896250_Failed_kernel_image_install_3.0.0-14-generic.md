---
title: "Failed kernel image install 3.0.0-14-generic"
date: 2011-12-16
forum: Installation &amp; Upgrades
---

### Post by HousieMousie2 on 2011-12-16
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up linux-image-3.0.0-14-generic (3.0.0-14.23) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
/etc/default/grub: 35: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-14-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-14-generic; however:
  Package linux-image-3.0.0-14-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.0.0.14.16); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
    No apport report written because the error message indicates its a followup error from a previous failure.
        Errors were encountered while processing:
 linux-image-3.0.0-14-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

This is what apt-get had to say after the GUI failed to install the new kernel.

Any help would be most appreciated... scrapping it and starting over is such a pain, I still have dismal memories of Windows.

Thanks for your time!


----------------------------------------------------
**March 29th 2012**
To save someone from a lot of extra reading...
If you are having this same issue, take a look at /etc/default/grub and see if there is a missing quotation mark at GRUB_CMDLINE_LINUX="" <--- this is what it should look like.

---

### Post by biohazardousguy on 2011-12-16
Open /etc/default/extlinux in Gedit 
```
sudo gedit /etc/default/extlinux
```
and find the line 'EXTLINUX_THEME="debian". Modify it to 'EXTLINUX_THEME="none". Install any package in synaptic and it should be fixed.
Cheers,
MM

---

### Post by HousieMousie2 on 2011-12-16
There is nothing in that file (may have just created it).

This is Kubuntu with various desktops (XFCE, LXDE, Gnome, etc)... typically run xfce or lxde, since it is a netbook.

Thanks for the suggestion though

---

### Post by YWELLC on 2011-12-16
Same!!!

---

### Post by fdrake on 2011-12-16
do you have build-essential installed?
```
sudo apt-get install build-essential gcc
```

---

### Post by HousieMousie2 on 2011-12-16
lol Yes.  I always install build-essential.

Thank you for the suggestion though.

---

### Post by vosa on 2011-12-18
same here

i have problems with these packages:

```

linux-image-3.0.0-14-generic
 linux-image-3.0.0-14-generic-pae
 linux-image-generic
 linux-generic
 linux-image-generic-pae
 linux-generic-pae

```

with this error
```

E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by HousieMousie2 on 2011-12-18
Anyone else have this problem or found a solution?

---

### Post by YWELLC on 2011-12-19
Ended up with an initramfs prompt after failed update (had to add delay to boot in /etc/default/grub to get to login screen), now usb keyboard / mouse not working.

RE-INSTALLing now...

---

### Post by amjjawad on 2011-12-22
> **HousieMousie2 said:**
> ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up linux-image-3.0.0-14-generic (3.0.0-14.23) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
/etc/default/grub: 35: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-14-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-14-generic; however:
  Package linux-image-3.0.0-14-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.0.0.14.16); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
    No apport report written because the error message indicates its a followup error from a previous failure.
        Errors were encountered while processing:
 linux-image-3.0.0-14-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```This is what apt-get had to say after the GUI failed to install the new kernel.

Any help would be most appreciated... scrapping it and starting over is such a pain, I still have dismal memories of Windows.

Thanks for your time!


Hello there,

You post is not clear, I need more information so that I can help :)

1- What command you issued over there? is it:

```
sudo apt-get dist-upgrade
```or

```
sudo apt-get update
```'apt-get update' does **not** upgrade Kernel by the way.

2- Could you please run this and post the output:

```
uname -a
```

3- Run this command:
```
sudo dpkg --configure -a
```That will help if you have a broken packages:
[https://help.ubuntu.com/community/SynapticHowto#How_to_fix_broken_packages](https://help.ubuntu.com/community/SynapticHowto#How_to_fix_broken_packages)


4- Were you trying to upgrade the Kernel via Update Manager and that failed?

---

### Post by amjjawad on 2011-12-22
> **vosa said:**
> same here

i have problems with these packages:

```

linux-image-3.0.0-14-generic
 linux-image-3.0.0-14-generic-pae
 linux-image-generic
 linux-generic
 linux-image-generic-pae
 linux-generic-pae

```with this error
```

E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Hello and Welcome to Ubuntu Forum :)

Kindly start your own thread and try to include more information. Check my signature, there is a helpful guide that will help you in each and every thread you start here :)

[http://ubuntuforums.org/showpost.php?p=11532952&postcount=349](http://ubuntuforums.org/showpost.php?p=11532952&postcount=349)

Thank you!

---

### Post by HousieMousie2 on 2011-12-31
Sorry I have not replied sooner, have been busy.

The kernel upgrade failed in the graphical update manager first, then in the terminal.

I tried dpkg --configure -a before, but nothing of use to report.

I did not try dist-upgrade (since it was just the linux image and not a full release upgrade) but I will have to try that and get back to you.

I will also get you the uname -a output... I am not in front of that machine just now.

Thank you for your assistance!

---

### Post by spacecheck on 2011-12-31
> **HousieMousie2 said:**
> ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up linux-image-3.0.0-14-generic (3.0.0-14.23) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
/etc/default/grub: 35: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-14-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-14-generic; however:
  Package linux-image-3.0.0-14-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.0.0.14.16); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
    No apport report written because the error message indicates its a followup error from a previous failure.
        Errors were encountered while processing:
 linux-image-3.0.0-14-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```This is what apt-get had to say after the GUI failed to install the new kernel.

Any help would be most appreciated... scrapping it and starting over is such a pain, I still have dismal memories of Windows.

Thanks for your time!

I have the exact same problem, but I updated Xubuntu 11.10 on a LiveUSBstick. In my instance, I suspect it is related to the Live squashfs used. Since it is a livesystem, certain folders are also not mounted/available in the manner initramfs-update seems to expect, and since it boots on fat32 before calling the persistence file, it may be having a problem creating usable symlinks.

I've not seen a solution yet for my (our?) problem, and have reinstalled diverse 11.10 versions only to have the same problem repeated. So I gave up updating the kernel (everything else updates fine).

---

### Post by amjjawad on 2011-12-31
> **HousieMousie2 said:**
> Sorry I have not replied sooner, have been busy.

The kernel upgrade failed in the graphical update manager first, then in the terminal.

I tried dpkg --configure -a before, but nothing of use to report.

I did not try dist-upgrade (since it was just the linux image and not a full release upgrade) but I will have to try that and get back to you.

I will also get you the uname -a output... I am not in front of that machine just now.

Thank you for your assistance!

Hi there,

First of all, Happy New Year to you :)

I'll be waiting for your reply when you be next to your machine ;)

---

### Post by HousieMousie2 on 2012-01-05
```
~$ uname -a
Linux [machinename] 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 i686 i386 GNU/Linux

```

After linux-image-3.0.0-14-generic failed to install via the graphical package manager and then via command line, we tried the pae and virtual, that is why this is so long, since it is failing three times...

```
~$ sudo dpkg --configure -a
Setting up linux-image-3.0.0-14-generic-pae (3.0.0-14.23) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-14-generic-pae /boot/vmlinuz-3.0.0-14-generic-pae
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-14-generic-pae /boot/vmlinuz-3.0.0-14-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-14-generic-pae /boot/vmlinuz-3.0.0-14-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-14-generic-pae /boot/vmlinuz-3.0.0-14-generic-pae
/etc/default/grub: 35: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-14-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.0.0-14-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.0.0-14-virtual (3.0.0-14.23) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-14-virtual /boot/vmlinuz-3.0.0-14-virtual
update-initramfs: Generating /boot/initrd.img-3.0.0-14-virtual
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-14-virtual /boot/vmlinuz-3.0.0-14-virtual
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-14-virtual /boot/vmlinuz-3.0.0-14-virtual
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-14-virtual /boot/vmlinuz-3.0.0-14-virtual
/etc/default/grub: 35: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-14-virtual.postinst line 1010.
dpkg: error processing linux-image-3.0.0-14-virtual (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.0.0-14-generic (3.0.0-14.23) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
/etc/default/grub: 35: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-14-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-3.0.0-14-generic-pae
 linux-image-3.0.0-14-virtual
 linux-image-3.0.0-14-generic

```

---

### Post by fdrake on 2012-01-05
you can also check with "sudo aptitude show packg_name" to see if you are meeting all the dependencies (or just copy then and try to reinstall all the dependencies).. for example:
> 
**sudo aptitude show linux-image-3.0.0-14-generic**
Package: linux-image-3.0.0-14-generic
New: yes
State: not installed
Version: 3.0.0-14.23~lucid1
Priority: optional
Section: admin
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Uncompressed Size: 116M
[B]Depends: initramfs-tools (>= 0.36ubuntu6), coreutils | fileutils (>= 4.0), module-init-tools (>= 3.3-pre11-4ubuntu3),
         wireless-crda
PreDepends: dpkg (>= 1.10.24)
Recommends: grub-pc | grub | lilo (>= 19.1)
Suggests: fdutils, linux-lts-backport-oneiric-doc-3.0.0 | linux-lts-backport-oneiric-source-3.0.0,
          linux-lts-backport-oneiric-tools
Conflicts: hotplug (< 0.0.20040105-1)
Breaks: lvm2 (< 2.02.54-1ubuntu3)[/B]
Provides: fuse-module, ivtv-modules, kvm-api-4, linux-image, linux-image-2.6, ndiswrapper-modules-1.9,
          redhat-cluster-modules
Description: Linux kernel image for version 3.0.0 on x86/x86_64
 This package contains the Linux kernel image for version 3.0.0 on x86/x86_64.


---

### Post by ptoche on 2012-01-12
I'm having a similar problem, so I figure I'd hijack this thread (it's a top hit on google), it occurred after a package update was interrupted by a power failure. Any suggestions? 

```
patrick@patrick-dv6:~$ sudo dpkg --configure -a
Setting up linux-image-3.0.0-14-generic (3.0.0-14.23) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
No such font or not readable by grub: /boot/DejaVuSansMono.pf2
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-14-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-14-generic; however:
  Package linux-image-3.0.0-14-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.0.0.14.16); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.0.0-14-generic
 linux-image-generic
 linux-generic

```

---

### Post by amjjawad on 2012-01-12
I'm not sure how to fix this issue, maybe someone with a good idea could step in? I must do some search before jumping in with some suggestions.

I never had this issue.

---

### Post by ptoche on 2012-01-12
@amjjawad

I thought downgrading the linux kernel might allow me to sidestep the issue, but I run into the same issues:

```
patrick@patrick-dv6:~$ sudo apt-get install linux-image-generic=3.0.0.12.14
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgtksourceview-3.0-0 gir1.2-peas-1.0 gir1.2-freedesktop gir1.2-gtk-3.0 libpeas-common gir1.2-gtksource-3.0
  libgtksourceview-3.0-common gir1.2-atk-1.0 gir1.2-gdkpixbuf-2.0 libpeas-1.0-0 gir1.2-pango-1.0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-generic
The following packages will be DOWNGRADED:
  linux-image-generic
0 upgraded, 0 newly installed, 1 downgraded, 1 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 2,364 B of archives.
After this operation, 32.8 kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://hk.archive.ubuntu.com/ubuntu/ oneiric/main linux-image-generic amd64 3.0.0.12.14 [2,364 B]
Fetched 2,364 B in 5s (419 B/s)                
(Reading database ... 296450 files and directories currently installed.)
Removing linux-generic ...
dpkg: warning: downgrading linux-image-generic from 3.0.0.14.16 to 3.0.0.12.14.
(Reading database ... 296448 files and directories currently installed.)
Preparing to replace linux-image-generic 3.0.0.14.16 (using .../linux-image-generic_3.0.0.12.14_amd64.deb) ...
Unpacking replacement linux-image-generic ...
Setting up linux-image-3.0.0-14-generic (3.0.0-14.23) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-14-generic /boot/vmlinuz-3.0.0-14-generic
No such font or not readable by grub: /boot/DejaVuSansMono.pf2
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-14-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-14-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-generic (3.0.0.12.14) ...
Errors were encountered while processing:
 linux-image-3.0.0-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
patrick@patrick-dv6:~$ 

```

---

### Post by amjjawad on 2012-01-12
Someone may correct me if I'm wrong but why to downgrade if you still can select the previous kernel from GRUB menu?

---

### Post by ptoche on 2012-01-12
why downgrade? no idea, it sounded about right at the time.

---

### Post by ptoche on 2012-01-12
I seem to have fixed the problem, but it very much looks like a setup-specific issue rather than a general problem. I looked at the error message and noticed that there was some problem with the font. It reminded me that I had once tried to get grub to use enlarged fonts in the grub menu, but had failed and left it at that. (The machine has worked without any problem since, for about 3 months therefore.) Anyhow, I deleted the problematic font from the grub directory and instructed grub not to use it. After that, I was able to update and ugrade without any error message. In truth, I haven't rebooted yet. I'm scared stiff about it. So I thought I should consign these thoughts here before logging off, in case I can never log in again...

If this is of use to someone, note the following steps which may help you get out of trouble, once you have identified the problematic package.

sudo rm /var/lib/dpkg/info/problematic-package-name.postrm
sudo rm /var/lib/dpkg/info/problematic-package-name.list
sudo apt-get clean all
sudo apt-get update //run it twice
sudo apt-get upgrade

Reference:
[http://allforlinux.com/2010/07/solving-e-sub-process-usrbindpkg-returned-an-error-code1/](http://allforlinux.com/2010/07/solving-e-sub-process-usrbindpkg-returned-an-error-code1/)

---

### Post by Catharsis on 2012-01-13
Aye, apt-get already told you what was wrong:
> /etc/default/grub: 35: Syntax error: EOF in backquote substitution
You're missing a closing quotation mark somewhere in '/etc/default/grub'. If you post it we can help you find the error if you want.

Then save & exit, run 'sudo update-grub' and then do your upgrade normally.

P.S. ptoche, did you survive? :)

---

### Post by amjjawad on 2012-01-13
> **ptoche said:**
> why downgrade? no idea, it sounded about right at the time.
I meant, you can choose the previous kernel on GRUB menu unless you have uninstalled the previous images :)

---

### Post by ptoche on 2012-01-13
@catharsis,

Either I or my ghost is alive!

I've had no problem since fixing the grub file.

thanks for the tips catharsis, well I couldn't find anything obviously wrong with the backquote, so it must have been some advanced backquoting feature, or perhaps the problem was inside the font file itself (ext. pf2), but I didn't look. And it's all gone now.

@amjjawad

I see what you mean, well I have reorganized my grub boot menu, so I don't have too many options in it, but I do have the "recovery" option and that does use the older kernel. I didn't know though. So either the "recovery" option always uses an older kernel or there has been one kernel upgrade since I installed my system about 3 months ago. I do remember some major upgrading at some point last month or so. While the "recovery" boot option specifically states the reference number of the kernel, the "default" boot option doesn't, so I'm inferring from this that kernel upgrades only affect the default boot option and not the recovery option, (unless of course you haven't fiddled with the boot options or you have recreated your "grub-on-the-fly" 40_custom file)...

This will clarify what I mean by fiddling with the grub boot menu options: 
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by HousieMousie2 on 2012-03-18
> **Catharsis said:**
> Aye, apt-get already told you what was wrong:

You're missing a closing quotation mark somewhere in '/etc/default/grub'. If you post it we can help you find the error if you want.

Then save & exit, run 'sudo update-grub' and then do your upgrade normally.

P.S. ptoche, did you survive? :)


Yet again, life intruded, another delay...

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

---

### Post by Catharsis on 2012-03-19
```
GRUB_CMDLINE_LINUX="
```
needs a closing quotation mark, i.e.
```
GRUB_CMDLINE_LINUX=""
```

---

### Post by HousieMousie2 on 2012-03-29
> **Catharsis said:**
> ```
GRUB_CMDLINE_LINUX="
```
needs a closing quotation mark, i.e.
```
GRUB_CMDLINE_LINUX=""
```

lol Thanks, Catharsis, worked like a charm.
Kind of strange, since I had not touched the GRUB manually nor with GRUB GUIs.

All's well that ends well... now if I can just get a kernel newer than 3.0.0-14 to boot on my other machine I would be a happy camper.

Thanks all.

Marking thread Solved!

---

