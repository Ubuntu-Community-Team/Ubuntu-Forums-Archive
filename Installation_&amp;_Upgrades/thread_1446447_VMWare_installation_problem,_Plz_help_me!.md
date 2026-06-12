---
title: "VMWare installation problem, Plz help me!"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by nhatoigiau on 2010-04-04
I'm trying to install Vmware on my Ubuntu 9.10, filename "VMware-Workstation-6.5.2-156735.i386.bundle". After installation , an error occured :

[IMG]http://i89.photobucket.com/albums/k221/im92cu/Screenshot1.png[/IMG]

then I run this command

```
sudo aptitude install build-essential linux-kernel-headers linux-kernel-devel
```and I get this

```
0 packages upgraded, 7 newly installed, 61 to remove and 2 not upgraded.
```For sure, I reinstall VMWare 

```
gksudo bash /media/THANHLONG/Documents/VMware-Workstation-6.5.2-156735.i386.bundle
Extracting VMware Installer...done.

```But an error is still there .

I run some commands :

```
root@thanhlong-laptop:~# uname -a
Linux thanhlong-laptop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux
root@thanhlong-laptop:~# rpm -q kernel-devel
package kernel-devel is not installed
root@thanhlong-laptop:~# apt-get install linux-headers-2.6.31-20-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.31-20-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```

This is log file:
```
Apr 04 14:24:29.470: app| Log for VMware Workstation pid=9355 version=6.5.2 build=build-156735 option=Release
Apr 04 14:24:29.470: app| Host codepage=UTF-8 encoding=UTF-8
Apr 04 14:24:29.470: app| Logging to /tmp/vmware-root/setup-9355.log
Apr 04 14:24:30.814: app| Extracting the sources of the vmmon module.
Apr 04 14:24:30.830: app| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.31-20-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.1
```
Please help me!

---

### Post by Psumi on 2010-04-04
Use virtualbox?

---

### Post by nhatoigiau on 2010-04-04
A friend told me that VMware 6.5 cant compile new kernel module, so that VMware cant work, he suggested me to use VMware 7.1 . I want to install VMware because I have 2 Virtual Machines running on Windows, I think if I install VMware on UBUNTU, it can load 2 VM I configured .

---

### Post by Psumi on 2010-04-04
> **nhatoigiau said:**
> A friend told me that VMware 6.5 cant compile new kernel module, so that VMware cant work, he suggested me to use VMware 7.1 . I want to install VMware because I have 2 Virtual Machines running on Windows, I think if I install VMware on UBUNTU, it can load 2 VM I configured .

VirtualBox can have infinite VMs in itself.

---

### Post by nhatoigiau on 2010-04-04
VMware workstation 7.0.1 is installed on my laptop. problem solved ! Thank psumi for your attention ! =)

---

### Post by Psumi on 2010-04-04
> **nhatoigiau said:**
> VMware workstation 7.0.1 is installed on my laptop. problem solved ! Thank psumi for your attention ! =)

VirtualBox is open source/free.

---

