---
title: "Help Booting Backtrack 5 alongside Win7 &amp; Ubuntu"
date: 2012-02-14
forum: Installation &amp; Upgrades
---

### Post by Tomkay94 on 2012-02-14
Hey guys,

I have been using Ubuntu for just over a year now and I absolutely love it :) My question (I hope is under the right section) is with regards to using Grub 2.0 as a triple bootloader for Windows 7 (Primary Partition), Ubuntu 11.10 and Backtrack 5 R1.

I am very intrigued by Backtrack 5 and have always wanted to try it out. I've been looking up details about tutorials and such over the past few days in order to familiarize myself with its installation. 

Is it possible to get Backtrack 5 R1 32bit to have a displayed option in Grub with Ubuntu and Windows 7? I have read it is, and I have this tutorial which details how to do it:

[http://www.hackavision.com/2011/06/so-you-want-to-use-backtrack-5.html](http://www.hackavision.com/2011/06/so-you-want-to-use-backtrack-5.html)

If I use the steps provided in this installation, will Backtrack 5 have its own choice when Grub loads? Will it remove Windows 7? (Ive read of instances where this has happened). I appreciate anyone who can help me with this. 

Thanks guys,
Thomas

---

### Post by haqking on 2012-02-14
> **Tomkay94 said:**
> Hey guys,

I have been using Ubuntu for just over a year now and I absolutely love it :) My question (I hope is under the right section) is with regards to using Grub 2.0 as a triple bootloader for Windows 7 (Primary Partition), Ubuntu 11.10 and Backtrack 5 R1.

I am very intrigued by Backtrack 5 and have always wanted to try it out. I've been looking up details about tutorials and such over the past few days in order to familiarize myself with its installation. 

Is it possible to get Backtrack 5 R1 32bit to have a displayed option in Grub with Ubuntu and Windows 7? I have read it is, and I have this tutorial which details how to do it:

[http://www.hackavision.com/2011/06/so-you-want-to-use-backtrack-5.html](http://www.hackavision.com/2011/06/so-you-want-to-use-backtrack-5.html)

If I use the steps provided in this installation, will Backtrack 5 have its own choice when Grub loads? Will it remove Windows 7? (Ive read of instances where this has happened). I appreciate anyone who can help me with this. 

Thanks guys,
Thomas

You can put backtrack in the grub menu yes.

however if you dont know that already then you are better just using a Backtrack Live CD/DVD or running it in a VM.

It is a special sec auditing distro, it is not designed for typical everyday Linux use you know that right ?

Most things in BT are done using Root and most things a typical end user does should not be done as root.

BT in itself is nothing more than a UBuntu 10.04LTS with all the common Sec auditing tools collected and installed for you for easy access.

I suggest trying it out lots on the Live or in VM versions before potentially trashing your machine ;-)

Peace

---

### Post by Tomkay94 on 2012-02-14
Yea I read that it was a really specialized distro mainly used for security purposes. It sounded very secure (not that Ubuntu isn't secure  :P), I'll try the live CD out. It would be the same as an Ubuntu installation I assume? Boot into BIOS, Boot from CD, thats it right?

Thanks btw for the quick reply :)

---

### Post by haqking on 2012-02-14
> **Tomkay94 said:**
> Yea I read that it was a really specialized distro mainly used for security purposes. It sounded very secure (not that Ubuntu isn't secure  :P), I'll try the live CD out. It would be the same as an Ubuntu installation I assume? Boot into BIOS, Boot from CD, thats it right?

Thanks btw for the quick reply :)

I wouldnt say BT is secure as a OS in the way i think you mean it, it is not meant for typical desktop use.

It is meant as a Penetration testing/Security Auditing suite of tools fit for purpose, not for general desktop use by an end user wanting to surf the web and use most multimedia tools and such.

As for the security of Ubuntu/Linux in general it is equal in footing to most end user OS, read here for a basic understanding [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

As for same as Ubuntu installation, in BT5 things are alot simpler then previous versions, but remember like i said it is not meant to be for end user use.

Dont expect all hardware to work, dont expect too much guidance from the system itself and installation of packages do not come from the usual Ubuntu repos, they come from the BT/Offensive security team.

So you cant just go ahead and apt-get install <anything you like> ;-)

As for live CD then yes you just boot to it.

However i would recommend you read the BT wiki.

[http://www.backtrack-linux.org/wiki/index.php/Main_Page](http://www.backtrack-linux.org/wiki/index.php/Main_Page)

---

