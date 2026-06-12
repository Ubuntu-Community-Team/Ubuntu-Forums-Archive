---
title: "Cannot install Ubuntu with Windows 7 (partition)"
date: 2012-01-30
forum: Installation &amp; Upgrades
---

### Post by cao3ni2ma3 on 2012-01-30
Hello,

I already ran a search, so I apologize if this issue has come up before. I'm trying to install Ubuntu v. 11.10 on a laptop running Windows 7 Starter Edition with Wubi. Whenever I try to install it, I get the following error message:

> Permission denied. 

For more information, please see the log file: 

c:\users\alex\appdata\local\temp\wubi-11.10-rev245.log


I've asked a friend who uses Ubuntu and he said I may need to install from a USB, but I don't have one at the moment. I have an external hard drive, but he recommended against it. I don't have the CD and my computer doesn't have an optical drive anyway. What can I do?

---

### Post by carl4926 on 2012-01-30
You should make sure you know the difference between wubi and a proper install.

Don't rush in to this or you may regret it. It's likely too that the way the vendor installed windows is not at all friendly.

---

### Post by carl4926 on 2012-01-30
And of course, this file
c:\users\alex\appdata\local\temp\wubi-11.10-rev245.log 			 		

May have the reason for your problem with wubi

---

### Post by cao3ni2ma3 on 2012-01-30
> You should make sure you know the difference between wubi and a proper install.What is a "proper install"? From a CD? 
>  It's likely too that the way the vendor installed windows is not at all friendly.I don't understand what you mean.
> And of course, this file  
May have the reason for your problem with wubiAnd if I knew what the problem was, I wouldn't be asking here.

---

### Post by carl4926 on 2012-01-30
**Proper** = To the HD in Linux partitions (wubi is inside windows)

**Vendor Partitions: **They tend to create 4 Primary partitions which means you can't create any more unless you delete one.
Boot a live cd a post the result of
```
sudo fdisk -l
```

---

### Post by Karlchen on 2012-01-30
Hello, cao3ni2ma3.

Could it be you are encountering a wubi bug filed as bug #862003? Cf. [**Permission denied: 'E:\\wubildr**]("https://answers.launchpad.net/wubi/+question/183979") and [**Bug 862003**]("https://answers.launchpad.net/wubi/+bug/862003"), please.

On my Acer One D260, which came with Windows 7 Starter pre-installed, installing the older Ubuntu version 10.04 via Wubi succeeded without any hassle. Yet, that was an older Wubi version, not v245.

Kind regards,
Karl

---

### Post by cao3ni2ma3 on 2012-01-30
> **carl4926 said:**
> **Proper** = To the HD in Linux partitions (wubi is inside windows)

**Vendor Partitions: **They tend to create 4 Primary partitions which means you can't create any more unless you delete one.
Boot a live cd a post the result of
```
sudo fdisk -l
```I said in my initial post that I don't have a CD. 
> **Karlchen said:**
> Hello, cao3ni2ma3.

Could it be you are encountering a wubi bug filed as bug #862003? Cf. [**Permission denied: 'E:\\wubildr**]("https://answers.launchpad.net/wubi/+question/183979") and [**Bug 862003**]("https://answers.launchpad.net/wubi/+bug/862003"), plea[LIST]
[/LIST]se.

On my Acer One D260, which came with Windows 7 Starter pre-installed, installing the older Ubuntu version 10.04 via Wubi succeeded without any hassle. Yet, that was an older Wubi version, not v245.

Kind regards,
KarlThanks a lot, Karlchen. You were very close indeed. The error was [this one](https://answers.launchpad.net/wubi/+question/184711) (linked from the same page) and the log looks the same. I am going to try rebooting to see if the installation was in fact successful. 

One last thing: 
[QUOTE= bcbc]PPS you cannot install Wubi from USB[/QUOTE]Is this true?

---

### Post by leonardodag on 2012-01-30
you install wubi from inside Windows. If you install via a CD or a USB stick, it's a "normal" installation, where you need to partition your hard drive to intall ubuntu alongside windows. See [this]("http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/") for how to create a bootable USB stick (works like a CD).

---

