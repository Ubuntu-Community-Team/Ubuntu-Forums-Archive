---
title: "Blank Screen on Reboot"
date: 2011-12-20
forum: Installation &amp; Upgrades
---

### Post by NateN34 on 2011-12-20
Hi,

I have the following netbook: 

**Ubuntu 11.10 i386 Desktop**
Acer Aspire D257
**Intel GMA 3150**
Intel Atom N570 Dual Core
Intel NM10 Express Chipset

First off, the operating system works fine and will shutdown just fine and boot up just fine, after being off. Although the problem is, that if I try to restart the PC after being in Ubuntu, then it will go to a black screen. Ubuntu shuts down and closes everything fine, but when it goes to reboot after that, the screen goes black and I have to hard power of the PC...

I have no clue what the issue is, but here is what I tried:

* Updated GRUB with i915.modeset=1 in GRUB
* Bought and replaced the hard drive, so it's not a hardware issue
* Updated everything on the operating system, to the latest packages
* Reinstalled the operating system 10 times with 4 different flash drives.
* Compared checksums and the ISO is not corrupt.
* Downloaded the ISO 4 different times.

After all of that, it still REBOOTS to a black screen. Although ti will shutdown or bootup from a cold start, just fine...just does not like to reboot.

Want to know the worst part? -- On my first install, everything worked fine and it would restart just fine! Although every subsequent install after that goes to black screen, when it tries to reboot from Ubuntu.

Anyone know what the issue is? I really love this operating system and would love to use it, but this is a major issue.

Thanks in advance,
Nate

---

### Post by sudodus on 2011-12-20
The newest version 11.10 should have the best drivers for new hardware, but during the first months, there are bugs, so try other versions and other flavours for example

[KLX]ubuntu 10.04 LTS, 11.04, 11.10
You might like
Kubuntu with KDE desktop
Lubuntu with LXDE smallest footprint desktop
Xubuntu with XFCE small footprint desktop

I think you might find that one of these co-operates well with your hardware and you might like one desktop environment better than the others.

---

### Post by MAFoElffen on 2011-12-20
> **NateN34 said:**
> Hi,

I have the following netbook: 

**Ubuntu 11.10 i386 Desktop**
Acer Aspire D257
**Intel GMA 3150**
Intel Atom N570 Dual Core
Intel NM10 Express Chipset

First off, the operating system works fine and will shutdown just fine and boot up just fine, after being off. Although the problem is, that if I try to restart the PC after being in Ubuntu, then it will go to a black screen. Ubuntu shuts down and closes everything fine, but when it goes to reboot after that, the screen goes black and I have to hard power of the PC...

I have no clue what the issue is, but here is what I tried:

* Updated GRUB with i915.modeset=1 in GRUB
* Bought and replaced the hard drive, so it's not a hardware issue
* Updated everything on the operating system, to the latest packages
* Reinstalled the operating system 10 times with 4 different flash drives.
* Compared checksums and the ISO is not corrupt.
* Downloaded the ISO 4 different times.

After all of that, it still REBOOTS to a black screen. Although ti will shutdown or bootup from a cold start, just fine...just does not like to reboot.

Want to know the worst part? -- On my first install, everything worked fine and it would restart just fine! Although every subsequent install after that goes to black screen, when it tries to reboot from Ubuntu.

Anyone know what the issue is? I really love this operating system and would love to use it, but this is a major issue.

Thanks in advance,
Nate
(Also in reference to Post 2)
Please turn in a bug report to Launchpad. Refer the package to "Plymouth."

Being such, (IMHO) the other Ubuntu variants will have the same results.  They all use the same base, the same xserver-xorg-core, the same xserver-xorg-video-intel (your video driver) and the same Plymouth.

Where this problem seems to lie? Plymouth starts on XSession start and again in Xsession shutdown.  On shutdown, there is shutdown scripts, that is supposed to shutdown X cleanly, stop all services and bring down the filesystem.  Your system is not shutting down the Xsession cleanly with is borking the BIOS/and or Graphics framebuffer.

A good test > If Reboot = no graphics (no BIOS Meassages, etc) Powerdown > remove power cord > remove battery for 30 seconds.... Put battery back in > Put power cable back in > Powerup.

Anyways, it sounds like it's in the rc x directory scripts. Sometimes if you set GRUB_GFXMODE, in your /etc/default/grub file to a usuable mode, such as
```

GRUB_GFXMODE=[COLOR=Red]1024x758x16[/COLOR]

```and set the 
```

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash [COLOR=Red]vga=791[/COLOR]"

```Then run 
```

sudo update grub

```Then it will set the underlying console into a mode that is more friendly with Plymouth and straighten that out.

Background other-- Any release ISO is a snapshot on when it was released.  A lot of problems found on that release date where corrected and if you update and upgrade, a lot of those changes will be picked up.

---

### Post by NateN34 on 2011-12-20
Yeah, oh well, I am just going to leave it. On a netbook I only really use the startup and shutdown functions anyway..

I tried everything that you said, as well as nomodeset and some acpi settings, but it still does not work.

Funny thing is though, rebooting works great on 11.04, but that version is too old..

---

### Post by sudodus on 2011-12-21
> **NateN34 said:**
> ...
Funny thing is though, rebooting works great on 11.04, but that version is too old..
No 11.04 is not too old, but 11.10 is too new ;-)

---

