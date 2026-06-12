---
title: "BusyBox during LiveCD bootup"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by DaltonAdair on 2008-08-06
I'm trying to install 8.04 on a fresh machine, squeaky clean.

Here is the machine I am working with:

Intel Atom processor @ 1.6GHz,
1GB of DDR2 @ 667MHz (4-4-4-12)
80GB WesternDigital SATA2 HDD
Creative 24x CD-RW 
Intel 945 chipset

The CD launches to the menu where I can pick Try it, Install, Memtest, all that good stuff. Memtest runs fine, no errors detected.

When I pick either the Install or Try it options, it begins to load up and then crashes into BusyBox with the following error:

```
udevd-event(1397]: run_programs: '/sbin/modprobe' abnormal exit
```

followed by the typical arrangment of BusyBox mysticism. :(

Anyone have any ideas? Is this a hardware issue? I understand the Atom is a pretty new processor but it is x86 so I am at a loss as to what is going on.

I am pretty sure the CD isn't defective either because I have used it several times on other machines, and this is one I had shipped to me. Didn't burn it myself. 

One last thing, doing "Check CD for Defects" gives the same final result as well...

---

### Post by DaltonAdair on 2008-08-07
*shameless bump*

I would really appreciate if anyone could offer advice.

---

### Post by DaltonAdair on 2008-08-07
*second shameless bump*

Come on guys, help me out and I will give you each one free internet. Please?

---

### Post by ikha0s on 2008-08-07
I have the same problem. I downloaded ubuntu-8.04.1-desktop-i386.iso. I double checked the image's MD5 checksum. And also I checked the MD5 checksums of all files on the CD (using included md5sum.txt) before the burn (I unpacked the iso) and after. 
Still it shows up damn BusyBox terminal whatever I choose in the boot menu. But it seems that I still able to install it through wubi, but that is not the solution, I need clean install.
And the wierdest thing is that no matter that the CD image and all included files DOES pass the MD5 check, when I run "Check CD integrity" from boot menu it shows up that I have 19 corrupted files (first it shows up BusyBox and when I type exit it performs the actual check).

If anyone has a solution to this wierd problem, please share.

2.2GHz AMD64 3200+
Two DDR2 (one - 1024MB, another - 256MB, operating on same frequences)
320GB Seagate SATA Drive
80GB Seagate IDE Drive
DVD+RW IDE Nec DVD-ROM
nVidia chipset

P.S. Sorry for my bad english.

---

### Post by aphroneo on 2008-08-07
You dropped off #ubuntu about two minutes too fast :)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/239602](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/239602)

nickrud

---

### Post by DaltonAdair on 2008-08-07
Makes sense, since I was using an 8.04 distribution and not a 8.04.1.

I will edit this reply if the solution works for me. As for the guy above, I dunno if this will help him out or not, but you should give it a shot too bud.:guitar:

---

### Post by esha7 on 2008-08-09
I also got the same problem..
my ubuntu only works on my laptop..
somebody plz help me...

---

### Post by DaltonAdair on 2008-08-09
Download the latest version from the link posted above and you should be ready to go.

---

### Post by esha7 on 2008-08-09
i`ve download the image.
but still got the same problem..

---

