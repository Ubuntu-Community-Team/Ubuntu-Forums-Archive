---
title: "Want to dual-boot &amp; Cannot resize my disk"
date: 2020-10-07
forum: Installation &amp; Upgrades
---

### Post by mgonzalez506 on 2020-10-07
Hello I have my Vaio with ubuntu and now I need to install windows 7.

I cannot resize my disk using GParted because it wont let me move space. 

I just have one partition /dev/sda1 with all space in my computer (596.17 GB)

How can I make space for my windows 7 partition?

Thanks in advance

---

### Post by CelticWarrior on 2020-10-07
Welcome.

First of all, you don't need to install Windows 7. You may want - very different - but you shouldn't or at least you shouldn't use it connected to the internet. Windows 7 is an obsolete OS many years past its due date, consequently without security updates for a very long time. If you must use Windows install Windows 10.

Partitions can't be managed while mounted and partitions can't be unmounted in a running system. Ergo you need to do that in a live session.

---

### Post by SeijiSensei on 2020-10-08
If you have a Win 7 or Win 10 installation image, I suggest installing VirtualBox, creating a virtual machine, and installing Windows to a VM. (Make sure to install the "Extension Pack" as well.) You can install VB from the Ubuntu repositories, but I prefer to use the Oracle repository described in these instructions: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

If you want Windows to play games, then you'll probably need to install it to the bare hardware. For anything else, you should find using a virtual machine a fine alternative.  Plus it lets you have both operating systems running on the same desktop at the same time.

---

### Post by TheFu on 2020-10-08
For some reason, I thought that Windows always had to be installed first, before any other OS, or booting wouldn't work. Windows isn't known for  playing nice with other OSes.

I haven't dual booted in about a decade. Windows runs either inside a virtual machine (KVM) or directly on Windows-only hardware.  For almost everything I need Windows for, a VM is the best solution.  But we all have different needs.
 
For clarity, win7 support ended January 2020, so 9 months ago.  Provided win7 isn't on a network, running it is fine. It is a fun OS to hack in a security lab.

---

### Post by Shibblet on 2020-10-08
> **CelticWarrior said:**
> Welcome.

First of all, you don't need to install Windows 7. You may want - very different - but you shouldn't or at least you shouldn't use it connected to the internet. Windows 7 is an obsolete OS many years past its due date, consequently without security updates for a very long time. If you must use Windows install Windows 10.

Partitions can't be managed while mounted and partitions can't be unmounted in a running system. Ergo you need to do that in a live session.

> **SeijiSensei said:**
> If you have a Win 7 or Win 10 installation image, I suggest installing VirtualBox, creating a virtual machine, and installing Windows to a VM. (Make sure to install the "Extension Pack" as well.) You can install VB from the Ubuntu repositories, but I prefer to use the Oracle repository described in these instructions: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

If you want Windows to play games, then you'll probably need to install it to the bare hardware. For anything else, you should find using a virtual machine a fine alternative.  Plus it lets you have both operating systems running on the same desktop at the same time.

> **TheFu said:**
> For some reason, I thought that Windows always had to be installed first, before any other OS, or booting wouldn't work. Windows isn't known for  playing nice with other OSes.

I haven't dual booted in about a decade. Windows runs either inside a virtual machine (KVM) or directly on Windows-only hardware.  For almost everything I need Windows for, a VM is the best solution.  But we all have different needs.
 
For clarity, win7 support ended January 2020, so 9 months ago.  Provided win7 isn't on a network, running it is fine. It is a fun OS to hack in a security lab.

These are all great alternatives to his problem.  But what he really wants to do is get back some of his HD space, and install Windows 7.

I am assuming you cannot resize this space, because it is also your boot drive.  Try booting a Live Session off of an Ubuntu USB stick, and running GParted from there.

---

### Post by mgonzalez506 on 2020-10-08
Thank you all I will try all the options this weekend and see what happen :)

Have a great day you all!

---

