---
title: "How not to install GRUB ?"
date: 2006-12-23
forum: Installation &amp; Upgrades
---

### Post by albell on 2006-12-23
Hello,

I have Fedora Core 6 installed and want to add Ubuntu 6.10 (on the same HD). Fedora has installed GRUB in the MBR therefore when installing Ubuntu I would like to skip the GRUB installation and simply add the Ubuntu entries manually (in the GRUB that was previously installed by Fedora) once the ubuntu installation is completed. Is this possible? I cannot find a way to tell Ubuntu not to install GRUB !!!

Regards,
Alexaner.

---

### Post by confused57 on 2006-12-23
> **albell said:**
> Hello,

I have Fedora Core 6 installed and want to add Ubuntu 6.10 (on the same HD). Fedora has installed GRUB in the MBR therefore when installing Ubuntu I would like to skip the GRUB installation and simply add the Ubuntu entries manually (in the GRUB that was previously installed by Fedora) once the ubuntu installation is completed. Is this possible? I cannot find a way to tell Ubuntu not to install GRUB !!!

Regards,
Alexaner.

If you're using the Ubuntu Desktop live cd, it automatically installs grub to the mbr, I've never installed with the live cd, but it's my understanding it doesn't give you the option of where to install grub(or not to install grub)...the alternate cd gives you the option of where to install grub.

What you might want to consider is to go ahead and let Ubuntu install grub to the mbr, then you can use the live cd to reinstall the Fedora grub to the mbr and use the live cd to install grub to your Ubuntu root partition...you can add an entry to your Fedora grub to boot Ubuntu by chainloading.

Here's how to install grub, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Using the above method, to reinstall your Fedora grub, you'd select the root partition for Fedora, then setup on hd0...for installing Ubuntu grub to root partition, select setup on (hd0,2), or whatever your Ubuntu root partition is.

OR:  Download the Ubuntu alternate cd, opt to install grub to your Ubuntu root partition...here's how to install using the alternate cd:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

To chainload Ubuntu, you'd need an entry similar to this added to your Fedora grub:

title   Ubuntu
rootnoverify (hd0,2)
chainloader +1

---

### Post by albell on 2006-12-31
Hello,

Many thanks. Using the alternate cd allowed me the skip the GRUB installation.

---

