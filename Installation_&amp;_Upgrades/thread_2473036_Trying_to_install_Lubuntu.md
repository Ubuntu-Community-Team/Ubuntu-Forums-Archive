---
title: "Trying to install Lubuntu"
date: 2022-03-21
forum: Installation &amp; Upgrades
---

### Post by linuxdetected on 2022-03-21
Hello everyone so I have this old laptop with 500MB it suffered from a hard drive failure.


I have replaced the hard drive and is trying to install Lubuntu however I'm getting the blank white cursor forever flashing this is me booting from Disk as this laptop refusing to detect USB.

---

### Post by tea for one on 2022-03-21
Please supply full specification of old laptop.
Make, model, 32 or 64-bit, graphics, RAM and HDD size, wireless card etc.

---

### Post by linuxdetected on 2022-03-21
Sony vivo PCG-8R1M 32BIT I think and it has 500MB of ram and 80GB HDD and has a wireless network connection module.

No operating system is installed as the HDD was recently replaced by me.

---

### Post by uninvolved on 2022-03-21
Lubuntu requires 64 bit for a supported version. Your best bet is to find a 32 bit distro aimed at running on older hardware. Many recommend the 32 bit Debian as a suitable alternative.

---

### Post by guiverc on 2022-03-21
[FONT=fixedsys]If your machine is the wrong architecture for a Lubuntu (*or other Ubuntu ISO*) you'll get either of two outcomes

- a message "[COLOR=#000000]*This kernel requires an x86-64 CPU, but only detected an i686 CPU*"

- black screen with underline-cursor (*it may or may not blink - depending on your boxes firmware*).

Your boxes firmware dictates which you'll see.  

As already stated by @Uninvolved (*a Lubuntu member like myself*), if your box is 32-bit only (or *i386* in Debian & Ubuntu terminology which doesn't use Linux's i386/i486/i586/i686 distinctions - though i686 has been required for some time by Ubuntu), what message you got maybe the expected result IF you've booted the wrong ISO for your architecture. 

A quick scan online and your box appears to be Pentium M, which meant the last supported release of Lubuntu it would boot is [Lubuntu 18.04 LTS which is now EOL]("https://lubuntu.me/bionic-eol/").  Further note:  some older pentium M laptops ran better using the GA kernel (*having issues with the 5.4 kernel*) so older Lubuntu 18.04 media (18.04 or 18.04.1) installation media is best.

FYI: I still use pentium M devices; one has Lubuntu 18.04 LTS on it, for the others it's Debian GNU/Linux.  The oldest supported release of Lubuntu however is Lubuntu 20.04 LTS so you won't get Lubuntu support if you choose Lubuntu.
[/COLOR][/FONT]

---

### Post by linuxdetected on 2022-03-22
Hello thanks for the response however I have tried installing lububtu 18.04 and debain 11.2.0 i386 all files are 32BIT and my laptop is still scanning the disk but the forever white cursor is flashing.

---

### Post by him610 on 2022-03-23
Debian 32bit download - [https://www.debian.org/distrib/]("https://www.debian.org/distrib/")
Raspberry Pi OS 32bit download - [https://www.raspberrypi.com/software/operating-systems/](https://www.raspberrypi.com/software/operating-systems/)
look for this one...
```

Raspberry Pi OS Lite
Release date: January 28th 2022
System: 32-bit
Kernel version: 5.10
Debian version: 11 (bullseye)
Size: 482MB
Show SHA256 file integrity hash:
Release notes

```

I have the RaspberryPi 32bit OS on a Atom N270 powered netbook with 1.5G RAM. If you only have 500MB RAM, you may need to consider a lighter version of Linux, of which I am unfamiliar; however, there are some folks here that are.
Good luck.

---

### Post by breakdaze on 2022-03-24
I can also recommend Slackware for an old 32bit PC. You just need 64Kb RAM, but 1Gb is suggested.

---

