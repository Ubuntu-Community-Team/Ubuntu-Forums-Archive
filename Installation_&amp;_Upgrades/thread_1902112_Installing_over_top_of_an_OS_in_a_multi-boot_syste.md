---
title: "Installing over top of an OS in a multi-boot system"
date: 2011-12-30
forum: Installation &amp; Upgrades
---

### Post by jaws222 on 2011-12-30
I currently have 4 operating systems on an hard drive and need to reinstall over one of them while keeping the other 3.  Do I simply choose the partition (OS) that I want to install over?  Is there more to it?

---

### Post by 2F4U on 2011-12-30
No, thats it. You choose the partition of the old system for the new installation. You may have to manually edit the grub menu (if you are using grub). Take care to choose the right partition.

---

### Post by grahammechanical on 2011-12-30
The new installation will put a new updated Grub menu in place (I am assuming Ubuntu). If you have another version of Ubuntu that you want as your main or first on the list OS, then you need to load that Ubuntu and run

```
sudo update-grub
```

I would advise installing this utility on your main Ubuntu:

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

I have four Ubuntu OSes and sometimes I overwrite one of them with another Ubuntu OS just to try them out. But I use Grub Customizer in my main Ubuntu to keep my boot menu in order. Grub customizer is very good.

Regards.

---

### Post by jaws222 on 2011-12-30
> **grahammechanical said:**
> The new installation will put a new updated Grub menu in place (I am assuming Ubuntu). If you have another version of Ubuntu that you want as your main or first on the list OS, then you need to load that Ubuntu and run

```
sudo update-grub
```

I would advise installing this utility on your main Ubuntu:

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

I have four Ubuntu OSes and sometimes I overwrite one of them with another Ubuntu OS just to try them out. But I use Grub Customizer in my main Ubuntu to keep my boot menu in order. Grub customizer is very good.

Regards.

Thanks guys.  I'm currently running Pear OS, Kubuntu, and Crunchbang Statler (Debian).  The 4th was an Opensuse that I need to install over.  It was totally hosed during an update.  Opensuse just not my cup of tea so I want to try another.  All of them are Grub2 so I'd assume to make the new install go to the MBR. I've used sudo update-grub before and am familiar.  I was thinking of trying either CentOS or Chakra, but heard the installations were not too friendly when multi-booting.  So far Ubuntu rules.  Thanks again.

---

