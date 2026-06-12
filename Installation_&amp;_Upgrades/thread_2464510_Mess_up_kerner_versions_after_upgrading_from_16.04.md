---
title: "Mess up kerner versions after upgrading from 16.04 to 18.04"
date: 2021-07-03
forum: Installation &amp; Upgrades
---

### Post by jimhce on 2021-07-03
Hi,

The upgrade to 18.04 was finished, but for some reason, the upgrading process failed to update kernel version, grub configure etc configure files, it now failed to boot and stopped at root as an emergency entry. The build OS kernel version is 4.15.0-140-generic, the current OS version is 4.13.0-36-generic. Because it did not start network, I could not run apt upgrade to fix it, but I am in the root, I can change any configure files. Where is the kernel boot file for kernel command line BOOT_IMAGE=/boot/vmlinuz-4.13.0-36.-generic root=UUID=efxxxxxxxxxxxxxxxxxx ro quiet splash?

Thank you.

---

### Post by TheFu on 2021-07-03
Not enough information to safely help. At least not for me.

Using a flash boot with the newer release ISO correctly installed on it (use any imaging tool), then you can boot from that USB device and enter "Rescue Mode".  This is probably the easy way to attempt fixes.  [https://www.tecmint.com/boot-ubuntu-in-rescue-mode/](https://www.tecmint.com/boot-ubuntu-in-rescue-mode/)  If that isn't working, then .... 

Best to run a Live Boot environment (like created above), install **boot-repair** (DO NOT run any repair!!!!!), have it gather information and post the generated URL here for some boot gurus to review.  Again - DO NOT run the "Repair" - that can break things worse than it is now. I know it will be tempting.  What we want from that tool is the boot-info URL, nothing more.

Perform upgrades only on fully patched versions of the OS. If there are any package issues at all, or held packages, the upgrade to a new release will almost certainly fail.

I prefer to ensure the old OS is running the HWE kernel.  This would be the kernel used by the base of a new install for the next release.  There are how-to guides on help.ubuntu.com or wiki.ubuntu.com for moving to the HWE kernel for desktops and servers. The steps are different, so ensure you follow the steps for YOUR release and server/desktop.  Swapping a new kernel is a big deal. Doing it as a separate step breaks down the issues into smaller chunks. That's my theory.  Expect any upgrade to fail and have sufficient backups and restore plans to recover.  Sometimes starting over from scratch (the prior state of the system) is the best option.

---

### Post by jimhce on 2021-07-04
Thanks TheFu for your response, there are reasons why I can only upgrade from the upgrade and release upgrade commands. 

Anyway, what is the kernel version for ubuntu 18.04.5 LTS? My laptop installed the 18.04.2, the version of the kernel is 4.18.0-17-generic, I upgraded to 18.04.5 LTS, the uname -r displayed kernel version 4.13.0-36-generic, but there is another 4.15.0-142 and 4.15.0-147 in /boot, that does not make sense.

Thank you.

---

### Post by Impavidus on 2021-07-04
4.15 is the standard kernel for 18.04, the oldest Ubuntu release still supported. 4.13 was (I think) the kernel of Ubuntu 17.10, also used by Ubuntu 16.04 with HWE from January to July 2018, when it reached end of life. The proper thing to do was to upgrade to the 4.15 kernel in July 2018 and to Ubuntu 18.04 some time between then and April 2021, when Ubuntu 16.04 reached end of life. 4.18 was the kernel from 18.10, used by 18.04 with HWE from January to July 2019, when that reached end of life. You shouldn't end up on that kernel now. In other words, your system is a mess.

You state you have reasons why you can't fresh install. The best thing to do would be to eliminate those reasons. But if you really wish, the problem might be solvable if we get the information from that boot info summary.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by TheFu on 2021-07-04
My 18.04 systems, upgraded from 16.04 earlier this year, have 
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu **18.04.5** LTS
Release:        18.04
Codename:       bionic

$ uname -r
**5.4.0-77-generic**
```

I'm running the HWE kernels.  These are the same as the original 20.04 kernel (where I don't run the HWE kernel, yet).

There was a webpage with the supported kernels and supported releases in a chart. It showed how each point release xx.yy.z mapped to which kernel and for how long each was supported.  Basically, the xx.yy.0 gets normal support for 5 yrs and the .1, .2, .3 ..... .5, .6 point releases have to move forward as each is released with the next, newer, kernel.  If we install 18.04.1, we've signed up to install 18.04.2, .3, .4, .5 and perhaps .6 with the new kernel each of those provides.  My memory could be wrong on all of this, since for me, *new is the enemy of stable* on my servers.  Used to be, Canonical supported each kernel separately for each point release. Imagine trying to support 6 kernels per release and having 4 LTS releases between normal and ESM support to backport everything.  That's a bunch of effort for possibly 24 different kernels. Knocking that down to just 2 kernels per LTS makes it much more manageable.

Alas, I can't find that webpage anymore. ;(  It really was a nice chart.

---

### Post by grahammechanical on 2021-07-04
Yes, it was a nice chart but it is now way out of date

[https://wiki.ubuntu.com/Kernel/Support](https://wiki.ubuntu.com/Kernel/Support)

Over the years what is called Ubuntu has become more compiicated. Once it was Desktop & Server. Now, added into the mix are kernels for IOT devices and Cloud images and I guess a lot more.

Regards

o

---

