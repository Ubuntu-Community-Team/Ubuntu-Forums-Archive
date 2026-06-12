---
title: "Kernel 3.7.6 and nVidia driver"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by Nick Payne on 2013-02-07
Running 12.10 amd64 with nVidia 313.09 driver. I just installed the 3.7.6 kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"). On reboot, my second monitor was blank and my primary monitor was running a lower resolution than its native resolution. I ran nvidia-settings and it told me that the nVidia driver was not installed!

Rebooted into the 3.7.5 kernel and I have both monitors back at their native resolutions and nvidia-settings shows me what I would expect. When I search syslog for the period covering the boot with 3.7.6, there is no reference to nvidia at all. When I boot back into 3.7.5, syslog shows:
```
Feb  7 16:19:05 nick-mint kernel: [   22.852693] nvidia: module license 'NVIDIA' taints kernel.
Feb  7 16:19:05 nick-mint kernel: [   22.852696] Disabling lock debugging due to kernel taint
Feb  7 16:19:05 nick-mint kernel: [   22.860855] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Feb  7 16:19:05 nick-mint kernel: [   22.860965] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  313.09  Tue Dec  4 21:22:17 PST 2012

```

---

### Post by carl4926 on 2013-02-07
A kernel upgrade would require you re-build the nvidia module from the nvidia blob

---

### Post by Nick Payne on 2013-02-07
That normally happens as part of the install - it did with 3.7.5, 3.7.4, etc. I didn't have to do anything post-install to get the nVidia driver to work with those kernels.

---

### Post by carl4926 on 2013-02-07
It wasn't clear to me exactly what mods you are running and how on top of 12.10
But if I build a kernel on any of my nvidia machines I have to rebuild the nvidia blob

---

### Post by Nick Payne on 2013-02-07
My understanding is that if the nvidia driver was installed from an ubuntu package (this one was, it's from the xorg-edgers ppa), then it should be updated automatically after each kernel upgrade. And up to this latest kernel, that is what happened on kernel upgrades.

---

### Post by carl4926 on 2013-02-07
I don't use PPA's
But you'd have to check.

I'd kind of assume anyone that's build their kernel from source would be on top this. I say this completely without prejudice.

My ubuntu installs are standard, but in other systems where I use custom or factory kernel builds, I manage nvidia manually with each upgrade.

---

### Post by Nick Payne on 2013-02-07
I'm not building the kernel from source. I downloaded the kernel deb files from kernel.ubuntu.com. Anyway, it seems the problem is elsewhere. Looking at the terminal log for the kernel install, I found this:
```
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.7.6-030706-generic /boot/vmlinuz-3.7.6-030706-generic
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms_packages.py", line 22, in <module>
    import apport
ImportError: No module named apport
Error! Bad return status for module build on kernel: 3.7.6-030706-generic (x86_64)
Consult /var/lib/dkms/nvidia-current/313.09/build/make.log for more information.
```
and fossicking around, I noticed that python3-apport was installed but python-apport was not. I uninstalled the 3.7.6 kernel, installed python-apport, then installed the kernel again. Still got errors, but slightly different:
```
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.7.6-030706-generic /boot/vmlinuz-3.7.6-030706-generic
Error! Bad return status for module build on kernel: 3.7.6-030706-generic (x86_64)
Consult /var/lib/dkms/nvidia-current/313.09/build/make.log for more information.

```
and the nvidia make.log contains
```
DKMS make.log for nvidia-current-313.09 for kernel 3.7.6-030706-generic (x86_64)
Thu Feb  7 19:24:34 EST 2013
If you are using a Linux 2.4 kernel, please make sure
you either have configured kernel sources matching your
kernel or the correct set of kernel headers installed
on your system.

If you are using a Linux 2.6 kernel, please make sure
you have configured kernel sources matching your kernel
installed on your system. If you specified a separate
output directory using either the "KBUILD_OUTPUT" or
the "O" KBUILD parameter, make sure to specify this
directory with the SYSOUT environment variable or with
the equivalent nvidia-installer command line option.

Depending on where and how the kernel sources (or the
kernel headers) were installed, you may need to specify
their location with the SYSSRC environment variable or
the equivalent nvidia-installer command line option.

*** Unable to determine the target kernel version. ***

make: *** [select_makefile] Error 1
```
At this point I gave up and rolled back to the 3.7.5 kernel. But it does look as though, apart from the last error shown, that the latest version of dkms has a missing dependency on python-apport.

---

### Post by cotmv on 2013-02-12
I had the same problem with 3.7.6 and 3.7.7 on mint with both nvidia 313.18 and 313.09. I added a symlink and now all is well.

```
ln -s /usr/src/linux/include/generated/uapi/linux/version.h /usr/src/linux/include/linux/version.h
```
good luck

---

### Post by rozwell69 on 2013-02-16
> **cotmv said:**
> I had the same problem with 3.7.6 and 3.7.7 on mint with both nvidia 313.18 and 313.09. I added a symlink and now all is well.

```
ln -s /usr/src/linux/include/generated/uapi/linux/version.h /usr/src/linux/include/linux/version.h
```
good luck

Damn, I wish you mention that it is required to reinstall kernel packages after creating this symlink.. I was reinstalling the nvidia-current and kernel packages alternately and wasted a few hours looking for solution which was under my nose from the very beggining.

Here is a full solution for kernel 3.7.8, so everyone will know exactly what to do:
[LIST=1]
[*] Download kernel packages
[*] Install them. For example:
```
$ sudo dpkg -i /tmp/kernel_v3.7.8/*.deb
```
[*] Create a symlink: ```
$ sudo ln -s /usr/src/linux-headers-3.7.8-030708-generic/include/generated/uapi/linux/version.h /usr/src/linux-headers-3.7.8-030708-generic/include/linux/version.h
```
[*] Reinstall packages (repeat step 2)
[/LIST]

---

