---
title: "Kernel Panic on install.  Any ideas?"
date: 2012-01-20
forum: Installation &amp; Upgrades
---

### Post by GhostOfTomJoad on 2012-01-20
So, here's the run-down.
I acquired an Intel Atom based mini-tower with a bad Windows install on it and was trying to upgrade it to Ubuntu 10.10 Netbook(it seems to work well with the Atom).  I build the live USB, plug it in, and fire it up.  

Splash screen: check
Select language: check
Keyboard layout: negative.  Kernel Panic: not syncing vfs.

I've tried several different flash drives and on every port.  I get the same crash at the same point in the install every time.  Has anyone had this issue and found a workaround?

Thanks in advance.

---

### Post by Buntumatic on 2012-01-20
Three things come to mind.

You sure it was Windows that was bad not the box?
Have you tried any other Linux on USB stick, like [SystemRescueCd]("http://www.sysresccd.org/Main_Page")?
Have you tried playing with BIOS settings, checked for BIOS upgrade?

---

### Post by snowpine on 2012-01-20
Good advice above.

Also keep in mind that support for 10.10 is about to end, so maybe you want to try the current 11.10 release? It might just magically work thanks to the 1 year of updates & improvements between 10.10 and 11.10. 

Netbook Remix is not required for the Atom family of processors; you can run any flavor or version of Ubuntu you like (personally I would probably choose Lubuntu or Xubuntu for Atom-based due to their lower system requirements). :)

---

### Post by GhostOfTomJoad on 2012-01-20
> **Buntumatic said:**
> Three things come to mind.

You sure it was Windows that was bad not the box?
Have you tried any other Linux on USB stick, like [SystemRescueCd]("http://www.sysresccd.org/Main_Page")?
Have you tried playing with BIOS settings, checked for BIOS upgrade?

I did check to make sure that the box was functional. Debian ran like a champ. I'd stick with that but I'm of the camp that prefers Unity.

Edit: which BIOS setting should I be looking for?

---

### Post by GhostOfTomJoad on 2012-01-20
> **snowpine said:**
> Good advice above.

Also keep in mind that support for 10.10 is about to end, so maybe you want to try the current 11.10 release? It might just magically work thanks to the 1 year of updates & improvements between 10.10 and 11.10. 

Netbook Remix is not required for the Atom family of processors; you can run any flavor or version of Ubuntu you like (personally I would probably choose Lubuntu or Xubuntu for Atom-based due to their lower system requirements). :)

I'll probably upgrade to Ocelot and import xfce eventually after support runs out. Good to know UNR isn't requisite for the Atom though.

---

### Post by snowpine on 2012-01-20
> **GhostOfTomJoad said:**
> Good to know UNR isn't requisite for the Atom though.

You will occasionally stumble onto outdated websites that reference "Ubuntu optimized for the Atom." This was a special Ubuntu version developed in 2008-09 and marketed as OEM to netbook manufacturers like Dell. It was kind of a marketing gimmick, and the project fizzled out once the "upstream" Linux kernel (and therefore any recent Linux distro) improved support for netbook hardware.

---

### Post by GhostOfTomJoad on 2012-01-20
> **snowpine said:**
> You will occasionally stumble onto outdated websites that reference "Ubuntu optimized for the Atom." This was a special Ubuntu version developed in 2008-09 and marketed as OEM to netbook manufacturers like Dell. It was kind of a marketing gimmick, and the project fizzled out once the "upstream" Linux kernel (and therefore any recent Linux distro) improved support for netbook hardware.


I read that somewhere.  I'm used to installing whatever the current version is at the time of install on desktops so I just assumed that information was still current.

---

### Post by snowpine on 2012-01-20
At the time of the first Asus EEE netbooks, there was a lot of excitement that Linux would finally hit the mainstream. (In fact, that was how I first heard of Linux.) But unfortunately, they came preinstalled with crummy distros like Xandros. Even Ubuntu at that time required a few "tweaks" to get essential features (like wifi and power managment) working. The public got the impression that Linux was a buggy OS with poor hardware support, and demanded netbooks with Windows XP pre-installed.

So I think Canonical came out with the Netbook Edition partly as a consumer-confidence-booster, to let users know they were responding to their concerns with a special product developed just for their hardware. Now that netbooks are commonplace, it's pretty obvious they do not require a special Remix distro.

---

### Post by GhostOfTomJoad on 2012-01-20
Just had a thought. Would changing from FAT32 to exFAT on the flash drive possibly do any good?

---

### Post by snowpine on 2012-01-20
FAT32 is fine. What method did you use to create the Live USB, and have you tested it on another computer?

Have you tried running in Live mode?

---

### Post by GhostOfTomJoad on 2012-01-20
> **snowpine said:**
> FAT32 is fine. What method did you use to create the Live USB, and have you tested it on another computer?

Have you tried running in Live mode?


I used Unetbootin and, when that install failed, I used YUMI.  It has been tested and confirmed working on my primary machine.  

Booting as live crashes as well.

---

### Post by snowpine on 2012-01-20
I've never tried YUMI; Unetbootin can be a little flaky in my experience.
Ubuntu made their own USB startup drive creator: **usb-creator** and it's rather nice, maybe that's worth a try?

[http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator](http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator)

Another next step in troubleshooting is to try a different distro, for example the current 11.10, especially if your hardware is recent.

---

### Post by GhostOfTomJoad on 2012-01-20
> **snowpine said:**
> I've never tried YUMI; Unetbootin can be a little flaky in my experience.
Ubuntu made their own USB startup drive creator: **usb-creator** and it's rather nice, maybe that's worth a try?

[http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator](http://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator)

Another next step in troubleshooting is to try a different distro, for example the current 11.10, especially if your hardware is recent.


I used startup creator from my machine at work that's running 11.10. I'll try that when I get home and report back.


Okay.  Tried the 11.10 install made using Startup Creator and got the Error "Not a Com:32 image."  I'm assuming that's a bad iso.

---

### Post by GhostOfTomJoad on 2012-01-21
Okay, got it working.  I used YUMI to create another Debian install.  After that was installed, I was able to use GRUB to boot the live Ubuntu drive.  

The problem, it turns out, was in a corrupted Windows bootloader rejecting the new install.  Once Debian was installed, the bootloader had been replaced and all was right with the world.

I'm still not sure why Debian would boot and not Ubuntu but it worked as an end-around.

---

