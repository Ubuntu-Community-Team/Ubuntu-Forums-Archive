---
title: "Mint 17.1 Rebecca kernels"
date: 2015-05-23
forum: MINT
---

### Post by Cavsfan on 2015-05-23
This is probably going to sound dumb but I didn't realize that Mint doesn't install newer kernels via CLI update methods.
I installed Mint 17 and then upgraded it to 17.1 a long time ago and still had kernel 3.13.0-37-generic while I also have Ubuntu Trusty 14.04 and it has kernel 3.13.0-53-generic.
```
cavsfan@cavsfan-MS-7529:~$ ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
Mar 27 11:59

```

So, after some searching on Google I found out how to install the 3.13.0-53-generic kernel and am currently booting with it.

It is always a manual process of installing newer kernels with Mint?

Here is all I have:
```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep -e "linux-kernel" -e "linux-headers" -e "linux-image"
ii  linux-headers-3.13.0-37                       3.13.0-37.64                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic               3.13.0-37.64                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-53                       3.13.0-53.89                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic               3.13.0-53.89                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-37-generic                 3.13.0-37.64                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-53-generic                 3.13.0-53.89                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic           3.13.0-37.64                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic           3.13.0-53.89                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-kernel-generic                          3.13.0-37                                           all          The Linux kernel.

```

Regards

---

### Post by Cavsfan on 2015-05-23
I just now realized I didn't have **linux-generic linux-headers-generic linux-image-generic** installed so I installed them.

So now I have these packages installed:
```
cavsfan@cavsfan-MS-7529:~$ dpkg -l | grep -e "linux-kernel" -e "linux-headers" -e "linux-image"
ii  linux-headers-3.13.0-37                       3.13.0-37.64                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic               3.13.0-37.64                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-53                       3.13.0-53.89                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic               3.13.0-53.89                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                         3.13.0.53.60                                        amd64        Generic Linux kernel headers
ii  linux-image-3.13.0-37-generic                 3.13.0-37.64                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-53-generic                 3.13.0-53.89                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic           3.13.0-37.64                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic           3.13.0-53.89                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                           3.13.0.53.60                                        amd64        Generic Linux kernel image

```

So that will keep them up to date maybe?

---

### Post by buzzingrobot on 2015-05-23
You can use the Update Manager to add new kernels in Mint 17.1. I think you need to look in the "View" section of the menu.

---

### Post by ajgreeny on 2015-05-23
I think new kernels and new drivers for some items are not normally updated automatically by default in Mint, but as buzzingrobot says you can change that setting in the update manager, either for a one off upgrade or for ever, by enabling the updates of sections 4 & 5, as all updates are given "safety" scores and 4 & 5 are deemed to be potentially problem causing.

---

### Post by Cavsfan on 2015-05-24
> **buzzingrobot said:**
> You can use the Update Manager to add new kernels in Mint 17.1. I think you need to look in the "View" section of the menu.

I googled and found that and it's where I installed the kernel that Trusty is using - 3.13.0-53-generic. 
But I wonder if that was a bad decision based on the recommended check mark by the 3.13.0-37-generic I was using.

[ATTACH=CONFIG]262192[/ATTACH]

> **ajgreeny said:**
> I think new kernels and new drivers for some items are not normally updated automatically by default in Mint, but as buzzingrobot says you can change that setting in the update manager, either for a one off upgrade or for ever, by enabling the updates of sections 4 & 5, as all updates are given "safety" scores and 4 & 5 are deemed to be potentially problem causing.

I don't think I really want to enable 4 and 5 based on what it says. If I had left or if I restore the 3.13.0-37-generic kernel when another one comes along that is recommended does that kernel get installed through updates?

I placed a check mark by the bottom** Always select and trust security updates**. Not sure if I checked both or just the bottom one. If there is ever a security issue with the installed kernel does this provide an new updated kernel in updates. I only use CLI commands to update.

[ATTACH=CONFIG]262193[/ATTACH]

I now feel feel sort of naive about Mint and the way the kernels are updated. Ubuntu has many kernels passed down through updates and I was used to seeing that.

Thanks for the replies!

---

### Post by buzzingrobot on 2015-05-24
> **Cavsfan said:**
> I googled and found that and it's where I installed the kernel that Trusty is using - 3.13.0-53-generic. 
But I wonder if that was a bad decision based on the recommended check mark by the 3.13.0-37-generic I was using.


They're all Ubuntu kernels released for the 14.04 series, so it's pretty unlikely you'll see issues. When I use Mint, I routinely enable all 5 sections of its update scheme and install the latest available kernel.  I do that specifically to get a kernel + Nouveau driver combination that works with my Nvidia card, as well as allow a working proprietary drive to be installed.  Plus, they're all the same updates Ubuntu users routinely pull down.

---

### Post by Cavsfan on 2015-05-24
> **Cavsfan said:**
> I googled and found that and it's where I installed the kernel that Trusty is using - 3.13.0-53-generic. 
But I wonder if that was a bad decision based on the recommended check mark by the 3.13.0-37-generic I was using.

> **buzzingrobot said:**
> They're all Ubuntu kernels released for the 14.04 series, so it's pretty unlikely you'll see issues. When I use Mint, I routinely enable all 5 sections of its update scheme and install the latest available kernel.  I do that specifically to get a kernel + Nouveau driver combination that works with my Nvidia card, as well as allow a working proprietary drive to be installed.  Plus, they're all the same updates Ubuntu users routinely pull down.

Thanks a lot for that info! I'll do the same then. As you can see from my signature I have a fairly older nVidia card myself.
It can't quite handle the new drivers like in Windows 7 I don't dare update the driver as I always have to roll it back to what it is using now.

I am using the 304.125 legacy driver on all my Linux installs. I have Mint 17.1, Trusty and 2 developmental install of Wily 15.04.

---

### Post by buzzingrobot on 2015-05-24
My Nvidia issue is different: It's a newish 750ti which requires a newish kernel and new driver combination. If the 304 driver works for you, don't change it.

---

### Post by Cavsfan on 2015-05-25
> **buzzingrobot said:**
> My Nvidia issue is different: It's a newish 750ti which requires a newish kernel and new driver combination. If the 304 driver works for you, don't change it.

Thanks. I'll resolve this thread now as I know a little more about Mint and how kernels are updated than I did before.

---

