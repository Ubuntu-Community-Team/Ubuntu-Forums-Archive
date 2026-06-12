---
title: "Ubuntu Installation took over windows 8.1 side. No windows on Boot Menu"
date: 2014-09-19
forum: Installation &amp; Upgrades
---

### Post by natan-kibret on 2014-09-19
Hello all,

I tried to install Ubuntu on my Lenovo y50 which comes with Windows 8.1 pre-installed and I succeeded. However, now I am not able to access my Windows side. I have went through the boot repair solution posted here: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) , I now see the Ubuntu boot menu, but Windows is not there. I only see Ubuntu, more ubuntu and system preferences which takes you to the boot configuration (F2). After using Boot  repair, I received an error and a link to write down. Here is the link: [http://paste.ubuntu.com/8378040/](http://paste.ubuntu.com/8378040/)

If it is relevant, My computer has 1 TB HDD and 8GB of SSD where I think the windows boot loader was installed, but now it is shown as Ubuntu in my boot configuration menu (F2).

When I go to disk utility, (disks) I see that only 42.8 GB of my 1 TB has been "used" and there is 49.2 GBs of unreadable material.

I would appreciate any help on the matter.

---

### Post by oldfred on 2014-09-19
Did you make the DVD restore set that your vendor does not now provide separately, but suggests you do it yourself. Or did you make a full backup of Windows?

You overwrote the entire hard drive with Ubuntu. There is no Windows nor recovery partitions.

Generally systems with small SSD, use that as boot cache for Windows. It is not where Windows boot loader is other than the cache to speed booting. 

Not sure if Lenovo offers replacement DVD sets for you or not. Some vendors do for a nominal shipping charge. 
Your product key for Windows is built into the UEFI, but is only good for your specific Vendor/model OEM type install. 
If you have to then you may need to purchase a full new copy of Windows.

---

