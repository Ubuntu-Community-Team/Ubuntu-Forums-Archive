---
title: "simplest method to RAID mirror boot drive?"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by bsmith1051 on 2007-06-22
What is the simplest way to get a new from-scratch Ubuntu 7.04 system running on mirrored hard-drives?  I don't care if it's hw or sw-based, but I want to use the matched pair of SATA2 drives I already own.

In the past I've used the Fake RAID on my motherboard (under Windows) but that sounds like a complete pita to implement under Linux, and is not as robust as the native Linux sw RAID ("dmraid").

Even setting-up 'dmraid' sounds complicated, e.g. install temp copy of Ubuntu, install/config dmraid, reinstall Ubuntu and manually tweak lots of partition and bootloader settings.
[http://ubuntuforums.org/showthread.php?t=464758](http://ubuntuforums.org/showthread.php?t=464758)

The simplest thing -- ideally -- would be a completely 'transparent' hw solution like my old Arco Duplidisk (but which only supports PATA drives),
[http://www.arcoide.com/disk_pci.php](http://www.arcoide.com/disk_pci.php)
They have new SATA versions but they only support SATA1 and they cost $300!

The next simplest thing would be for the Ubuntu install to offer a 'dmraid' install option but I haven't been able to find any reference to such a thing.  Is there a '1-button' install option for the Linux sw RAID?

Or, can someone recommend a less expensive hw solution that supports both Ubuntu and SATA2, and can be installed without needing to monkey with the install process?  Thank you for any suggestions!

---

### Post by bsmith1051 on 2007-06-22
FYI
I found this article about native support in Ubuntu/Linux for 3Ware hw controllers,
[http://www.3ware.com/KB/article.aspx?id=14546](http://www.3ware.com/KB/article.aspx?id=14546)
Basically it says that the current kernels will recognize most of their controllers, e.g. the $200 model 9650SE (2-port).  Does this mean that I could install Ubuntu in 1 step on this card, and without needing to tweak any settings?

---

### Post by bsmith1051 on 2007-06-23
I think I've found a solution which almost no one mentions:  the existing script on the Alternate Install CD!  This allows you to implement the built-in sw RAID with almost no extra work.

I haven't tried it yet but basically it sounds like this:
1. boot the "Alternate" CD
2. choose "Manual" partitioning
3. partition both drives with matching sets of partitions of Type="Physical disk for RAID" 
4. select "Configure software RAID" and create "md" (multidisc) partitions for each pair; select Type=RAID1
5. continue the installation as usual !

Here's where I finally found these instruction,
[http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)

Update: **THIS WORKED PERFECTLY!**

Update #2: 10/21/07, updated the URL

---

### Post by netvampire on 2007-07-22
The guide you provided works perfectly. Thanks. Its clear and easy to understand.

---

### Post by McSwordfish on 2007-10-20
> **bsmith1051 said:**
> I think I've found a solution which almost no one mentions:  the existing script on the Alternate Install CD!  This allows you to implement the built-in sw RAID with almost no extra work.

I haven't tried it yet but basically it sounds like this:
1. boot the "Alternate" CD
2. choose "Manual" partitioning
3. partition both drives with matching sets of partitions of Type="Physical disk for RAID" 
4. select "Configure software RAID" and create "md" (multidisc) partitions for each pair; select Type=RAID1
5. continue the installation as usual !

Here's where I finally found these instruction,
[http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)

Update: **THIS WORKED PERFECTLY!**

Firstly, will this work in a dual boot with windows?

Secondly.
"404 Not Found."
Do you have an alternative link for this page? Or would you be willing to email it to me (mcswordfish@gmail.com)

Cheers muchly.

---

### Post by bsmith1051 on 2007-10-21
A little experimenting with the old URL got me to the new URL,
[http://users.piuha.net/martti/comp/ubuntu/en/raid.html](http://users.piuha.net/martti/comp/ubuntu/en/raid.html)

I'll update the original post now, too.

P.S.  No, I don't think this will work on a dual-boot, not unless you can find a native EXT2/3 driver for Windows!

---

