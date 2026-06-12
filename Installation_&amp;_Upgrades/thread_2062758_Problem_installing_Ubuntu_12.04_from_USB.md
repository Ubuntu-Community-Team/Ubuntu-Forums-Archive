---
title: "Problem installing Ubuntu 12.04 from USB"
date: 2012-09-25
forum: Installation &amp; Upgrades
---

### Post by Drew012 on 2012-09-25
Hello, I have a problem while installing and even running a live Ubuntu 12.04 off of my USB. The problem is I have created bootable ubuntu usb's and they work when I try them on my netbook. However, when I use it in the computer I am trying to run it on, it only runs to a certain point.
Note, I have used both the pendrivelinux universal live USB installer, the default disk creator on ubuntu, and Unetbootin to create these USB's. They all run fine on my small netbook. The iso file used was actually for my main machine not my netbook (its a 64 bit iso). When I try to boot with my main computer I get through the following when using the universal installer:

System powers on, goes through option page to get in to boot menu/BIOS/Etc.
Loads Installer boot menu from the live USB, everything looks good.
I can select any of the options from the list (Run ubuntu from usb, install on hard disk, test memory, etc).
When I go to "Run Ubuntu from this USB" it starts out loading the /casper files loads more initialization files AND THEN GETS STUCK:
on following line: ```
[     3.885689] device mapper: ioctl 4.22.0-ioctl (2011-10-19) initialised: dm-d  
```

When I run this on my netbook it continues through the initialisation files and eventually starts up ubuntu. What could be causing this problem? I currently cant boot in to my regular windows or linux partitions, and they are both really corrupt even if I could. How should I fix this problem if I cant even do a fresh install?

If you need any more information I will be able to post back within a few minutes. This problem is urgent as I barely have a functional computer for school! Thanks for all of the help!

---

### Post by oldfred on 2012-09-25
What is difference. Is your computer 64bit? It really should not even start if not 64bit. What video card/chip do you have. That is usually the biggest issue. Many systems then work with nomodeset. Some system require other boot options.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Also sometimes BIOS settings can make a difference. But that varies greatly by Vendor.

---

### Post by Drew012 on 2012-09-25
Weird...

For my netbook:
```
andrew@thunderdome:~$ uname -a
Linux thunderdome 3.2.0-23-generic-pae #36-Ubuntu SMP Tue Apr 10 22:19:09 UTC 2012 i686 i686 i386 GNU/Linux
```

This is the .iso file I used: ubuntu-12.04.1-desktop-amd64.iso
I used a bootable version of this .iso for both computers.

For my main computer I am trying to install it on:
AMD x6 core 64 bit processor

So why is the 64bit iso even working on my netbook? Could that be the cause of the problem in that the file is really 32 bit even though it says "...amd64.iso"?

---

### Post by Drew012 on 2012-09-25
EDIT: It is i686 so it make sense to be able to run the 64 bit file?

```
andrew@thunderdome:~$ sudo uname -m
[sudo] password for andrew: 
i686

```

---

### Post by oldfred on 2012-09-25
uname -a
i386 or i686 = 32-bit
x86_64 = 64-bit
[http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

---

### Post by Drew012 on 2012-09-25
Yes, I did have that mixed up but should the 64 bit processor be able to run the 32 bit .iso? (Since my processor definately is 64 bit it should be able to run either)

---

### Post by darkod on 2012-09-25
64bit CPU can run both 32bit and 64bit.
32bit CPU only 32bit.

If you use the 32bit ISO it will install the 32bit version even if the CPU is 64bit.

On the other hand, if you try to install a 64bit ISO on a 32bit CPU it should give you architecture error and refuse to install.

---

