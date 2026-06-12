---
title: "Installation failure."
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by themarker0 on 2012-05-08
So I've tried to boot. It refuses to get to the installation regardless the method I use. For simplicities sake here is the same message I sent my UUG. 


So Installing the newest version of Ubuntu is stumbing me quite a bit. To first rule out CD drive and image corruption I did download a fresh copy of UNetbootin and it to no avail does nothing. I'm looking around for an image of 10.04 to see if it will install, not much hope. Ubuntu is currently installed on this machine but it does not boot, 10.10 broke it. Parts are as listed below.

Intel Core 2 Quad Q9550  @ 2.83GHz
4.00 GB Dual-Channel DDR3 @ 533MHz
ASUSTeK Computer INC. P5E3-WS-Pro
1024MB GeForce GTX 550 Ti (ASUStek Computer Inc)
977GB Seagate ST31000524AS ATA Device (SATA)
977GB Western Digital WDC WD10EALS-00Z8A0 ATA Device (SATA)
78GB Western Digital WDC WD800JD-22LSA0 ATA Device (SATA)	(Boot Drive and drive for *Nix
Optiarc DVD RW AD-7261S ATA Device
Scarlett 2i2 USB
Creative 1616


Anything there look like it could be a system breaker? Any Ideas? 

Thanks, Mark

---

### Post by darkod on 2012-05-08
Did you try to boot with the parameter nomodeset?

So, are you trying to repair the 10.10 (it's end of life already) or install the latest 12.04 LTS?

---

### Post by themarker0 on 2012-05-08
> **darkod said:**
> Did you try to boot with the parameter nomodeset?

So, are you trying to repair the 10.10 (it's end of life already) or install the latest 12.04 LTS?

Install the latest. 10.10 was a mistake install anyways. Somehow my 10.04 bugged into updating to it. 


Any booting into the old Ubuntu fails. I'm just looking to install the new one, but all attempts to start the Ubuntu program fails.

---

### Post by wilee-nilee on 2012-05-08
So here are instructions on using nomodeset from a live cd and install.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

You were asked about this but did not answer, at least directly. :)

---

### Post by themarker0 on 2012-05-09
> **wilee-nilee said:**
> So here are instructions on using nomodeset from a live cd and install.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

You were asked about this but did not answer, at least directly. :)

I can't get to that screen though. Which is my current issue. The live CD/USB doesn't even get to that.

---

### Post by wilee-nilee on 2012-05-09
> **themarker0 said:**
> I can't get to that screen though. Which is my current issue. The live CD/USB doesn't even get to that.

You can't get to the the first gui on the cd by holding down the shift  key just after powering on. This will also bring up grub if you have  installed Ubuntu. Use a cd unetbootin can get to the gui that has the f6 prompts but I don't know how, some other usb loaders for installing do.

If you get there hit f6 tick nomedset and try booting in.

A GeForce GTX 550 is a nvidia card some times this is needed to get in, or a install from a alternative cd a text install, to get the install done and load the drivers.

Check this link same card same install.

[http://askubuntu.com/questions/127305/how-to-install-ubuntu-12-04-on-a-computer-with-a-nvidia-geforce-gtx-550-ti](http://askubuntu.com/questions/127305/how-to-install-ubuntu-12-04-on-a-computer-with-a-nvidia-geforce-gtx-550-ti)

---

### Post by themarker0 on 2012-05-10
The alternate CD installed but now I run into the same problem as before... The proprietary Nvidia driver needs to be downloaded and installed before it will show anything. Anyway I can do this from the CLI?

---

### Post by darkod on 2012-05-10
Yes, you can install using command prompt.

But the system should offer you a grub2 boot menu if it's dual boot, or you need to hold Shift to display the menu when the computer is booting, just after the POST finishes. The boot menu comes BEFORE everything, so you have to be able to display it.

Then simply edit the ubuntu entry to add nomodeset and it should boot to the desktop allowing you to activate the driver much easier in a GUI.

---

