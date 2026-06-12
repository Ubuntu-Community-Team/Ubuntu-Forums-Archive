---
title: "What is &quot;nohd&quot; boot parameter equivalent in grub of Ubuntu?"
date: 2011-11-13
forum: Installation &amp; Upgrades
---

### Post by indiAJoe on 2011-11-13
I have a machine whose hardisk crashed.So while booting up Ubuntu 11.10 normally, it will get stuck at the Hardware detection part.
I am able to boot the live cd Porteus (slax) by giving the boot cheatcode "nohd" in the lilo.
"nohd" is to ignore hardisk mounting while hardware detection.

I want to boot ubuntu on this machine. So what is the equivalent boot parameter I have to give in grub of the live CD, so that it will skip harddisk detection while booting?

Thanking you,
-indiAJoe  :confused:

---

### Post by dandnsmith on 2011-11-13
Have you tried it - I've never had a problem with lack of HDD when using Ubuntu LiveCDs (or any others I've tried - but not your slax)

---

### Post by indiAJoe on 2011-11-13
Machine is a laptop, so the hardisk is still inside. But it has got corrupted so badly that, Ubuntu booting gets stuck when it does hardware checking..
In lilo when I give 'nohd' option, it skips that harddisk recognition part and boots up remaining part.
But since ubuntu uses grub, I couldn't find the equivalent boot parameter. 
And yes, trying 'nohd' didn't work in grub.

---

### Post by dandnsmith on 2011-11-13
OK,
I'd expect at worst that the bootup using LiveCD would wait until it failed to read the HDD, and then continue.
A lot of laptops, these days, are so constructed that it is a simple matter to disconnect (for the inevitable HDD replacement).
Anyway, what did you hope to achieve by booting from a CD?

---

### Post by indiAJoe on 2011-11-13
I wanted to atleast run Ubuntu live on the machine.
When I deleted the entire damaged partition on the hardisk by booting with Porteus, it have now started booting up. So problem is partially solved.
But i would still like to know the boot parameter for switching off the hardware recognition while booting. Which i think is a very important thing when hardware crashes. 
PS: We waited a lot (many hours), Ubuntu never stopped trying to recognize harddisk and hence didn't continue with booting..

---

### Post by dandnsmith on 2011-11-14
OK - that clarifies the issues to 2 parts:
1. booting from LiveCD: my researches, albeit not with the latest versions, show that grub isn't used. Instead you use a direct system based on syslinux called isolinux. Any searches for a HDD are confined to the content of the initrd and vmlinux referenced on the CD (so you'd have to rebuild those and configure a newCD from scratch)
2. grub on the HDD installation - presumably grub 2 (so called even tho it calls itself version 1.99). This is going to depend on the state of the HDD - after all, if it's completely unusable, you wont even get grub starting. Next stage is the usability of the sectors where the second stage of the boot process are, followed by the usability of the partition where the linux stuff is.

I don't think all this is going to help you much, but, just in case...

---

### Post by indiAJoe on 2011-11-14
Oh, Ok.Thanks, I didn't know the live cd was not using grub.
But still wouldn't there be any boot parameter which i can give in the boot options which will ignore harddisk detection?
I saw it has some options like acpi=off, noapic etc in the menu. but didn't find anything specific for switching off harddisk detection.

---

### Post by MAFoElffen on 2011-11-14
> **indiAJoe said:**
> Oh, Ok.Thanks, I didn't know the live cd was not using grub.
But still wouldn't there be any boot parameter which i can give in the boot options which will ignore harddisk detection?
I saw it has some options like acpi=off, noapic etc in the menu. but didn't find anything specific for switching off harddisk detection.
I'm not sure if these work with Ubunutu's version of the kernel, but I've kept this reference with me:
>  
"hdx="  is recognized for all "x" from "a" to "h", such as "hdc".  

"idex=" is recognized for all "x" from "0" to "3", such as "ide1".   

[COLOR=Red]"hdx=noprobe"          : drive may be present, but do not probe for it  

"hdx=none"             : drive is NOT present, ignore cmos and do not probe  [/COLOR]

"hdx=nowerr"           : ignore the WRERR_STAT bit on this drive  

"hdx=cdrom"            : drive is present, and is a cdrom drive  

"hdx=cyl,head,sect"    : disk drive is present, with specified geometry

"hdx=autotune"         : driver will attempt to tune interface speed                                 to the fastest PIO mode supported,                                 if possible for this drive only.                                 Not fully supported by all chipset types,                                 and quite likely to cause trouble with                                 older/odd IDE drives.   

[COLOR=Red]"idex=noprobe"         : do not attempt to access/use this interface[/COLOR]  

"idex=base"            : probe for an interface at the addr specified,                                 where "base" is usually 0x1f0 or 0x170                                 and "ctl" is  assumed to be "base"+0x206  

"idex=base,ctl"        : specify both base and ctl  

"idex=base,ctl,irq"    : specify base, ctl, and irq number  

"idex=autotune"        : driver will attempt to tune interface speed                                 to the fastest PIO mode supported,                                 for all drives on this interface.                                 Not fully supported by all chipset types,                                 and quite likely to cause trouble with                                 older/odd IDE drives.  

"idex=noautotune"      : driver will NOT attempt to tune interface speed                                 This is the default for most chipsets,                                 except the cmd640.  

"idex=serialize"       : do not overlap operations on idex and ide(x^1)
Hope it helps.

One thought I had, was that you said it was "corrupted..." Wondering if that or mechanical.  People bring me drives that other's say are wasted... 

Me, I would boot on a rescue disk, such as the Ultimate Boot Disk > Low level format. > Fitness Test... Boot on a GParted LiveCD > Add a Partition Table. > Partition > Format.  All that would get rid of anything twisted, mark out anything not suitable and prep it for reuse.

Like I said- Just a thought.

---

### Post by indiAJoe on 2011-11-15
Oh, Nice . those boot parameters were precisely what i was looking for. 
Thankyou very much. I shall try them.

PS: The hardisk suffered physical damage. (It fell down from table!!)
Initially only a few sectors in it were corrupt. But as the hardisk spinned more and more, it became more worse. and finally became completely corrupt by end of the day. Luckly backed up important files before that.

---

