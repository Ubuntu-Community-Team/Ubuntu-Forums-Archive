---
title: "What to do with HWE after upgrade"
date: 2023-08-30
forum: Installation &amp; Upgrades
---

### Post by oldgraf on 2023-08-30
Hello, in a laptop was long time with Desktop version of 18.04. Was installed HWE-18.04. Next i upgraded to 20.04. And HWE for 18.04 is still there. Do i need to remove it? My current kernel is 5.4.0-159-generic

---

### Post by grahammechanical on 2023-08-30
You do not need to remove the 18.04 HWE. Software Updater should remove it. I am using Ubuntu 20.04.6 LTS and it is running Linux kernel 5.15.0-82. So, your kernel is still an old kernel. Ubuntu 20.04 has had 6 point releases since 20.04 was first released. The 20.04 HWE has been updated a few times since then. Either way, Ubuntu 20.04 reaches end of standard support in April 2025. We can get an extra 5 years support (until 2030) by adding Extended Security Maintenance (ESM).

It is free for the user with up to five machines. Read about it.

[https://ubuntu.com/blog/ubuntu-pro-beta-release](https://ubuntu.com/blog/ubuntu-pro-beta-release)

[https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)

Register for personal. That is the option for the home user.


[https://ubuntu.com/pro](https://ubuntu.com/pro)

You want a free personal token.

[https://ubuntu.com/pro/dashboard](https://ubuntu.com/pro/dashboard)

There is documentation  in that web page. Or, upgrade to Ubuntu 22.04 LTS before 20.04 reaches end of support life.

[https://ubuntu.com/pro/tutorial](https://ubuntu.com/pro/tutorial)

Regards

---

### Post by oldgraf on 2023-08-30
Thanks but this is not accepted answer...
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.6 LTS
Release:    20.04
Codename:    focal

Nothing is removed from updates
uname -a
Linux 5.4.0-159-generic #176-Ubuntu SMP Mon Aug 14 12:04:20 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux

apt policy linux*hwe-18.04 | grep Installed | grep -v none
Installed: 5.4.0.159.154

---

### Post by TheFu on 2023-08-30
It is was me, I'd use synaptic to find all the installed kernels, pick a kernel line that works for me and remove all the others.  Then I'd remove the headers and modules for those "gone" kernels too.  I don't have much choice, since I keep a separate /boot partition and it isn't sized to allow too many kernels to exist. It is necessary to remove older kernels before the /boot/ partition is full and I'm stuck in an odd failure/upgrade status.
Here's the contents of a 20.04 system:

```
$ ls -F /boot/
config-5.15.0-78-generic  initrd.img@                   lost+found/                   vmlinuz-5.15.0-78-generic
config-5.15.0-79-generic  initrd.img-5.15.0-78-generic  System.map-5.15.0-78-generic  vmlinuz-5.15.0-79-generic
efi/                      initrd.img-5.15.0-79-generic  System.map-5.15.0-79-generic  vmlinuz.old@
grub/                     initrd.img.old@               vmlinuz@

$ df -Th /boot/
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/nvme0n1p2 ext4  574M  281M  252M  53% **/boot**
```

IME, apt wants to keep 2 kernel versions for each kernel line, not 2 kernel versions overall.  I have the linux-generic-hwe-20.04 package, and the header/module packages to match, installed.
```
$ dpkg -l |grep hwe
ii  linux-generic-hwe-20.04               5.15.0.79.86~20.04.39                                                amd64        Complete Generic Linux kernel and headers
ii  linux-headers-generic-hwe-20.04       5.15.0.79.86~20.04.39                                                amd64        Generic Linux kernel headers
ii  linux-hwe-5.15-headers-5.15.0-78      5.15.0-78.85~20.04.1                                                 all          Header files related to Linux kernel version 5.15.0
ii  linux-hwe-5.15-headers-5.15.0-79      5.15.0-79.86~20.04.2                                                 all          Header files related to Linux kernel version 5.15.0
ii  linux-image-generic-hwe-20.04         5.15.0.79.86~20.04.39                                                amd64        Generic Linux kernel image

```
Hope this helps.  There's a page that explains how to do an HWE install for each supported release under help.ubuntu.com or wiki.ubuntu.com somewhere. Any web-search tool should find it.

---

### Post by MAFoElffen on 2023-08-30
Please post the results of this within CODE Tags:
```

apt list linux-generic-hwe-* --installed

```

---

### Post by oldgraf on 2023-08-30
```
apt list linux-generic-hwe-* --installed
Listing... Done
linux-generic-hwe-18.04/focal-security,now 5.4.0.159.154 amd64 [installed]
```

---

### Post by TheFu on 2023-08-30
Odd.  I didn't do any upgrades from 18.04 --> 20.04.  For me, it was time for a fresh install.
I'd install the linux-generic-20.04 kernel+headers+modules (which shouldn't do much), then reboot into the 20.04 kernel.
Next, I'd remove the linux-generic-hwe-18.04 kernel+headers+modules.
Next, I'd consider whether moving to the 20.04 HWE kernel is something I wanted or not.  For me, because I have Ryzen 5xxx APUs, I needed a kernel with at least 5.10 or later to get GPU support. That was a key reason why I moved to 20.04 HWE.  YMMV.   Of course, if you are happy with the 5.4.x kernel, you don't need to do much, but that little cleanup to clearly use the 20.04 version could be important if you don't have ESM on the system.  There may be a bunch of kernel updates to the 5.4.x kernels that has been missed due to 18.04 standard support having ended last April (May/June). I lose track.

---

### Post by MAFoElffen on 2023-08-31
Your posted ouptut uncovered something that did not get upgraded in the release upgrade... The Hardware Enablement Stack (HWE).

Here is how the package name nomenclature works for the HWE package:
```

linux-generic-hwe-XX.XX

```
With "XX.XX" being the LTS release number for the LTS RElease it was derived from. For example
```

linux-generic-hwe-20.04 
 |_ 20.04
 |_ 20.10
 |_ 21.04
 |_ 21.10
linux-generic-hwe-22.04
 |_ 22.04
 |_ 22.10
 |_ 23.04
 |_ 23.10

```
So for 20.04 LTS, you need to install that package to correct that oversight
```

sudo apt install linux-generic-hwe-20.04

```

---

### Post by oldgraf on 2023-08-31
And this is my question. I installed hwe-18.04 where I was on 18.04. After upgrade to 20.04 I see this is still there. I don not need hwe-20.04 yet. 5.4 is ok for me. What to do - install some generic kernel and remove hwe-18.04 or ?

---

### Post by TheFu on 2023-08-31
> **oldgraf said:**
> And this is my question. I installed hwe-18.04 where I was on 18.04. After upgrade to 20.04 I see this is still there. I don not need hwe-20.04 yet. 5.4 is ok for me. What to do - install some generic kernel and remove hwe-18.04 or ?

Yes. See post #7.

---

