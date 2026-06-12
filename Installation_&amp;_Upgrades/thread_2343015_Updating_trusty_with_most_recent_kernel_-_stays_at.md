---
title: "Updating trusty with most recent kernel - stays at 3.13.0-53"
date: 2016-11-12
forum: Installation &amp; Upgrades
---

### Post by miha-valencic on 2016-11-12
Hi!

I'm trying to upgrade a kernel on one of my linux boxes, but doing so with `apt-get update` and `apt-get upgrade` does not upgrade it. The other box is currently on 3.13.0-89, whereas the box in question is currently on 3.13.0-53.

While looking at [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) I can't even figure out what is the latest version, given that v3.13.11.11-trusty is 2 years old (based on the timestamp). But, I digress...

The [askubuntu post]("http://askubuntu.com/questions/598483/how-can-i-use-kernel-3-19-in-14-04-now") suggests to install vivid lts package, but given the post's date I guess I could also use Xenial.

My main questions is: is this a right way to go? I would like to minimize downtime and I mostly rely on apt-get updates to keep the system up-to-date, but I have failed to do so in this case. I suppose there might be some packages on the system which prevent the apt-get dist-upgrade to do it's own magic?

From what I understand, apt-get install linux-generic-lts-whatever will move the kernel version from v3.13 up. I still don't know who to make it current though.

To repeat: I'd like to upgrade 3.13.0-53 to a more recent version.

Thanks!

PS: the system has been rebooted and the latest (and only) kernel in /boot is 3.13.0-53-generic.

---

### Post by gifford on 2016-11-12
You have to enable the LTS Stack to get the updated kernel. I am running Trusty (14.04) and have the 4.4.0-47 kernel.
This guide explains it much better than I will be able to. 
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by jeremy31 on 2016-11-12
Is the problem computer dual boot with another Linux distro?  If I remember correctly the latest 3.13 kernel in Ubuntu is 3.13.0-100

Please post the result of ```
dpkg -l | grep linux-image
```

---

### Post by ajgreeny on 2016-11-12
In fact it is now 3.13.0-101, so things have moved on a lot from the 3.13.0-53 you currently have.

Do you have some really good reason to move to the new kernel series (xenial's or later)?
The 3.13.0-# series is supported until 2019 when the 14.04 Trusty group of OSs loses further support, so if it works with your hardware you can stick with it and lose nothing.

---

### Post by gifford on 2016-11-12
Again, to update your Kernel to the latest for Trusty 14.04, you have to activate the LTS Enablement Stack. It will provide the newer kernel derived from 16.04. The process is rather simple and is the correct way
to update 14.04 to newer kernels. And again, I running 14.04 and have the 4.4.0-47 kernel.

---

### Post by miha-valencic on 2016-11-12
gifford et al,

I suppose I could update the LTS stack and move to higher kernel versions. I might try that, once I understand why it won't upgrade from 3.13.0-53. I see that apt-cache tells me the highest is 3.13.0-98:
```

apt-cache search linux-image-3.13.0 | grep generic | sort | tail -1
linux-image-3.13.0-98-generic - Linux kernel image for version 3.13.0 on 64 bit x86 SMP

```

Request dpkg output:
```

# dpkg -l | grep linux-image
ii  linux-image-3.13.0-53-generic       3.13.0-53.89                         amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-23-generic        3.5.0-23.35~precise1                 amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-26-generic        3.5.0-26.42~precise1                 amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-27-generic        3.5.0-27.46~precise1                 amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-28-generic        3.5.0-28.48~precise1                 amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-30-generic        3.5.0-30.51~precise1                 amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-31-generic        3.5.0-31.52~precise1                 amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-32-generic        3.5.0-32.53~precise1                 amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-34-generic        3.5.0-34.55~precise1                 amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-37-generic        3.5.0-37.58~precise1                 amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-39-generic        3.5.0-39.60~precise1                 amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-41-generic        3.5.0-41.64~precise1                 amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-42-generic        3.5.0-42.65~precise1                 amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-43-generic        3.5.0-43.66~precise1                 amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-44-generic        3.5.0-44.67~precise1                 amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-45-generic        3.5.0-45.68~precise1                 amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-46-generic        3.5.0-46.70~precise1                 amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-51-generic        3.5.0-51.77~precise1                 amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-52-generic        3.5.0-52.79~precise1                 amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-54-generic        3.5.0-54.81~precise1                 amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic 3.13.0-53.89

``` 


I'm not sure why the "extra" version is installed, since this is a virtualized linux. And no, it is not dual boot. 

LSHW output:
```

#lshw
hostname
    description: Computer
    product: VMware Virtual Platform ()
    vendor: VMware, Inc.
    version: None
    serial: VMware-redacted
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: administrator_password=enabled boot=normal frontpanel_password=unknown keyboard_password=unknown power-on_password=disabled uuid=redacted
  *-core
       description: Motherboard
       product: 440BX Desktop Reference Platform
       vendor: Intel Corporation
       physical id: 0
       version: None
       serial: None
     *-firmware

```

Thanks!

---

### Post by deadflowr on 2016-11-12
***sudo apt-get upgrade*** will never install a newer kernel, since apt-get upgrade will not install any new packages.
To install a newer kernel you must run it with
```
sudo apt-get dist-upgrade
```

Zero need to upgrade the hardware stack as the 3.13 kernel has full support through 2019.

---

### Post by jeremy31 on 2016-11-12
The linux-image-extra file was added at some point in the past couple years and contains kernel modules for wifi, ethernet, and video among others 

Are you sure you have Ubuntu 14.04 installed or was this a recent upgrade from 12.04.?

---

### Post by miha-valencic on 2016-11-13
> **jeremy31 said:**
> The linux-image-extra file was added at some point in the past couple years and contains kernel modules for wifi, ethernet, and video among others 

Are you sure you have Ubuntu 14.04 installed or was this a recent upgrade from 12.04.?

[HR][/HR]I'm sure it is running 14.04, though I'm not sure it wasn't upgraded. How could I check that?
```


cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.5 LTS"

```

Given that `stat /var/log/installer/syslog` reports Change date as `2013-03-20` I suspect the server might be running 12.04 before that and that I've upgraded to 14.04 - though I would not bet on it.

---

### Post by miha-valencic on 2016-11-13
Also note the apt-cache policy output:
```

# apt-cache policy linux-image-3.13.0-53
linux-image-3.13.0-53-lowlatency:
  Installed: (none)
  Candidate: 3.13.0-53.89
  Version table:
     3.13.0-53.89 0
        500 http://si.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
linux-image-3.13.0-53-generic:
  Installed: 3.13.0-53.89
  Candidate: 3.13.0-53.89
  Version table:
 *** 3.13.0-53.89 0
        500 http://si.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status

```

Looking at my /etc/apt/sources.list, I'm now positive that the system was upgraded from 12.04. The sources.list contains:
```

deb http://si.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://si.archive.ubuntu.com/ubuntu/ trusty main restricted


deb http://si.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://si.archive.ubuntu.com/ubuntu/ trusty-updates main restricted


deb http://si.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://si.archive.ubuntu.com/ubuntu/ trusty universe
deb http://si.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://si.archive.ubuntu.com/ubuntu/ trusty-updates universe


deb http://si.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://si.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://si.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://si.archive.ubuntu.com/ubuntu/ trusty-updates multiverse


deb http://si.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://si.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

```

The sources.list on another server, which was upgraded to 3.13.0-98 looks to be the same.

---

### Post by jeremy31 on 2016-11-13
See if there is a result for ```
apt-cache policy linux-kernel-generic
```
 ```
apt-cache policy linux-generic-lts-trusty
```
```
apt-cache policy linux-generic-lts-xenial
```

Just looking for xenial because the lsb-release showed 14.04.5 and that would normally have the xenial kernel.  The original version may have been 12.04.2 as that would have used the 3.5 kernel

---

### Post by miha-valencic on 2016-11-13
Jeremy, thanks for taking the time to look into it. Here are the outputs:
```

# apt-cache policy linux-kernel-generic
N: Unable to locate package linux-kernel-generic
# apt-cache policy linux-generic-lts-trusty
linux-generic-lts-trusty:
  Installed: (none)
  Candidate: 3.13.0.101.109
  Version table:
     3.13.0.101.109 0
        500 http://si.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     3.13.0.24.28 0
        500 http://si.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
# apt-cache policy linux-generic-lts-xenial
linux-generic-lts-xenial:
  Installed: (none)
  Candidate: 4.4.0.47.34
  Version table:
     4.4.0.47.34 0
        500 http://si.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages

```

Thanks!

---

### Post by jeremy31 on 2016-11-13
```
apt rdepends linux-image-3.13.0-53
```

Might give us an idea of how it was installed

---

### Post by miha-valencic on 2016-11-13
rdepends:
```

# apt-cache rdepends linux-image-3.13.0-53
linux-image-3.13.0-53-generic
Reverse Depends:
  linux-image-3.13.0-53-generic:i386
  linux-signed-image-3.13.0-53-generic
  linux-image-extra-3.13.0-53-generic
linux-image-3.13.0-53-lowlatency
Reverse Depends:
  linux-image-3.13.0-53-lowlatency:i386

```

depends (if it might give some insight - note some conflicts, which I don't know whether make sense or not.
```

# apt-cache depends linux-image-3.13.0-53
linux-image-3.13.0-53-generic
  Depends: initramfs-tools
  Depends: module-init-tools
  PreDepends: dpkg
    dpkg:i386
  Suggests: fdutils
 |Suggests: <linux-doc-3.13.0>
  Suggests: linux-source-3.13.0
  Suggests: <linux-tools>
    linux-tools-generic
    linux-tools-generic-lts-saucy
    linux-tools-generic-lts-trusty
    linux-tools-generic-lts-utopic
    linux-tools-generic-lts-vivid
    linux-tools-generic-lts-wily
    linux-tools-generic-lts-xenial
    linux-tools-lowlatency
    linux-tools-lowlatency-lts-utopic
    linux-tools-lowlatency-lts-vivid
    linux-tools-lowlatency-lts-wily
    linux-tools-lowlatency-lts-xenial
    linux-tools-virtual
    linux-tools-virtual-lts-utopic
    linux-tools-virtual-lts-vivid
    linux-tools-virtual-lts-wily
    linux-tools-virtual-lts-xenial
  Suggests: linux-headers-3.13.0-53-generic
 |Recommends: grub-pc
    grub-pc:i386
 |Recommends: grub-efi-amd64
    grub-efi-amd64:i386
 |Recommends: grub-efi-ia32
    grub-efi-ia32:i386
 |Recommends: grub
  Recommends: lilo
  Conflicts: <hotplug>
  Conflicts: <hotplug:i386>
  Conflicts: linux-image-3.13.0-53-generic:i386

```

---

### Post by jeremy31 on 2016-11-13
Let's see if this command will cause any harm
```
sudo apt-get install --install-recommends --dry-run linux-generic-lts-trusty
```
The --dry-run keeps it from making any changes

---

### Post by miha-valencic on 2016-11-13
The command went smoothly, so I decided to install the package. After reboot:
```

$uname -r
3.13.0-101-generic

```

The question why it was not installed before still remains, though.

Thanks for all your help!

---

### Post by jeremy31 on 2016-11-13
The answer to why may have been in the terminal results from the dry run.

---

### Post by miha-valencic on 2016-11-13
> **jeremy31 said:**
> The answer to why may have been in the terminal results from the dry run.

Oh... bummer. There were no errors there; that's why I decided to run it without --dry-run flag.

Anyways, thank you very much for your time, I appreciate it.

Kind regards!

---

### Post by jeremy31 on 2016-11-13
Please use the thread tools menu at the top of the page to mark as solved.  I thought there might be something about the package conflicting with another

---

### Post by miha-valencic on 2016-11-13
> **jeremy31 said:**
> Please use the thread tools menu at the top of the page to mark as solved. 

Just did. Thanks for pointing that out and again, thanks to all of you for your help.

---

