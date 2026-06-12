---
title: "Why would you not install the boot loader?"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by Thrasonic on 2008-02-06
Hey all,

When you go through the Live Install CD or DVD to install Kubuntu 7.10 and you get to the end where you've made all your choices and it's time to click the "Install" button there's a button labeled "Advanced".  If you click it you can join the "Popularity Contest" as well as choose if  you want the boot loader installed.  Why would you not install the boot loader?

---

### Post by bwtranch on 2008-02-06
You have to install some kind of bootloader whether it's GRUB or LILO .

---

### Post by louieb on 2008-02-06
The default is to install the IPL (initial program load) for GRUB to the MBR. If I have another Linux distro already installed I will want to use it GRUB boot loader. In that case I use the advanced button to install the IPL to the boot sector of the / (root) partition.  Then I can chainload the 2nd distro just like I would if it were XP.  

I could also just modify the first distributions GRUB menu  to boot the 2nd distributions kernel directly and not install its GRUB - but chainloading is a lot easier.     

More about dual booting in the **dual boot** link in my signature.

---

### Post by andrew.46 on 2008-02-20
Hi Thrasonic,

 Fair question:

> **Thrasonic said:**
>   Why would you not install the boot loader?

although you have missed one aspect of that particular screen which is an option to describe *where* you wish to install grub to. The default is (hd0,0) which is the MBR and will overwrite any bootloader already there. So you have a few choices:

[LIST=1]
[*]Install Grub to the MBR (hd0,0) as is the default
[*]Install Grub to a different location, perhaps to the partition where you are installing to if this installation is *not* going to hda1
[*]Don't install grub at all and use a different bootloader (such as lilo) that you will then setup later
[/LIST]

Most will not use this option at all I suspect or even be aware that it exists.

     Andrew

---

