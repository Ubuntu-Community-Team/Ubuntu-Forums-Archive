---
title: "Unable to install"
date: 2013-01-23
forum: Installation &amp; Upgrades
---

### Post by bearcatrp on 2013-01-23
Tried to install Ubuntu 12.1 LTS on my ASUS laptop. Basically nuked my drive. Seems something is preventing it from booting in the MBR. Laptop is about 3 months old with an i5, USB 3 etc.. and win7 home premium 64. Is there something in these new laptops that stop installation or booting? I know win8 systems had issues but didn't think win7 systems had issues. Have installed ubuntu many times in the past but this is the first time I have had issues. I still had a ubuntu 10.4 LTS disk to try. At least I get the dual boot screen but as soon as I select ubuntu, go right back to non system disk or an issue in the MBR. Suggestions?

---

### Post by TheFu on 2013-01-23
> **bearcatrp said:**
> Tried to install Ubuntu 12.1 LTS on my ASUS laptop. Basically nuked my drive. Seems something is preventing it from booting in the MBR. Laptop is about 3 months old with an i5, USB 3 etc.. and win7 home premium 64. Is there something in these new laptops that stop installation or booting? I know win8 systems had issues but didn't think win7 systems had issues. Have installed ubuntu many times in the past but this is the first time I have had issues. I still had a ubuntu 10.4 LTS disk to try. At least I get the dual boot screen but as soon as I select ubuntu, go right back to non system disk or an issue in the MBR. Suggestions?

First, Ubuntu releases their distro 2 times a year - April and October.  The zeros ARE significant. The 12.10 (Oct) and 12.04 (Apr) need those zeros to denote the release month. It can be confusing if you don't list them. 

Newer computers are changing the way that everything boots.  Ubuntu 10.10 or 10.04 do not understand these new things as well (if at all) as the current releases:
* UEFI
* SecureBoot
* GPT partitioning (instead of MBR)
* 4K sector hard disks instead of 512b sectors.

I suggest that you read up on these and understand any choices you make during installs that can impact the outcome. There may be BIOS settings that you need to change to make it installable too.

Because all this hardware is so very new, it is difficult for distro developers to test every configuration.  I suspect it will be at least another year before this all settles down.  You'll **want a 12.04 or later distro to install.**

Thanks for blazing a trail for the rest of us!

In the meantime, there is a bootinfo script that will help you understand exactly what your machine has. [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) has more.

---

### Post by bearcatrp on 2013-01-23
Just downloaded and tried 12.04 win installer. Get the same mbr error message. The boot manager seems to be the culprit. Will do some reading to see what I can figure out. Thanks.

---

