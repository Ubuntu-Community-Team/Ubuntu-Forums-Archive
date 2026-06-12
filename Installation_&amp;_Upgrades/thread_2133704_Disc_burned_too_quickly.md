---
title: "Disc burned too quickly?"
date: 2013-04-08
forum: Installation &amp; Upgrades
---

### Post by cajunlibra on 2013-04-08
Hello,

I have an older computer that's pretty outdated. I had Ubuntu 9.10 installed on it but in an attempt to upgrade it, the OS is now no longer usable. I found a 9.10 live CD which I can run  but installation has become a problem.

When I tried using a newer CD, I get an error that the CD was created too fast so it can't be read. This is very strange to me but what can I do.

If I am able to install 9.10 on this computer, how can I upgrade the system to newer versions? It is dual booted with an older version of XP SP1. It has has issues upgrading.  When I had 9.10 working properly, it went very smoothly and was very fast. I'd like to have this as an extra computer.

Also, the BIOS apparently does not support USB boot and I'd have to pay some company $30 to get a software upgrade for it.

Any help is appreciated.

---

### Post by ppjdee on 2013-04-09
When burning .iso I always burn at the slowest speed to a DVD, to avoid any burn issues.

---

### Post by fantab on 2013-04-09
Ubuntu version 9.10 has been long dead. See [Here]("https://wiki.ubuntu.com/Releases"). The [latest Ubuntu]("http://www.ubuntu.com/download/desktop") versions are 12.10 and 12.04 LTS [Long Term Support until 2017]. If you can wait then 13.04 will be released shortly. I would recommend 12.04.

If you can give us some details of your machine, like CPU, RAM, Graphics we will be able to guide you in the right direction. 
If you have low specs machine consider [Lubuntu]("http://lubuntu.net/") or [Xubuntu]("http://xubuntu.org/getxubuntu/"). If you have less than 700 MB RAM then [Lubuntu Alternate Install]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO") is your best bet. If that doesn't help then try [Lubuntu Minimal Install]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall").

When burning .iso burn at lower speeds and not at Maximum speeds.

---

### Post by cajunlibra on 2013-04-15
Well, to start. I'm not an idiot. I'm well aware that 9.10 is dead. I'm running 12.10 on my laptop. 9.10 is the only "official" CD that I have from Canonical back when they sent CDs for free. I burned multiple CDs at the slowest rate and none of them are recognized properly by the old computer. My laptop can read them just fine. I keep getting the message that the disc was burned too quickly.

I found information on a net boot install but I can't find vmlinuz. 
I did find initrd.gz at [http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-i386/current/images/netboot/ubuntu-installer/i386/](http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-i386/current/images/netboot/ubuntu-installer/i386/)

The directions for GRUB install at [https://help.ubuntu.com/12.10/installation-guide/i386/ch05s01.html](https://help.ubuntu.com/12.10/installation-guide/i386/ch05s01.html) state that I need both files. Where is that file located? I downloaded linux, is it the same kernel file?

---

