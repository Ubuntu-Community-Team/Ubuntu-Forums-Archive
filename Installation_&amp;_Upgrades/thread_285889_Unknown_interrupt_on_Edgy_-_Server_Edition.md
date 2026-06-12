---
title: "Unknown interrupt on Edgy - Server Edition"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by secici on 2006-10-27
I experienced a loop of reboots after I installed Edgy - Server Edition to an ASUS M5N notebook. Kernel is 2.6.17-10-Server

*Unknown Interrupt or fault at EIP 00000060 c0100295 00000294*

This error can be found by doing a search like:

[http://www.google.com.tr/search?hs=52Q&hl=tr&client=firefox-a&rls=org.mozilla%3Atr%3Aofficial_s&q=2.6.17+%22Unknown+interrupt%22&btnG=Ara&meta=](http://www.google.com.tr/search?hs=52Q&hl=tr&client=firefox-a&rls=org.mozilla%3Atr%3Aofficial_s&q=2.6.17+%22Unknown+interrupt%22&btnG=Ara&meta=)

acpi=off doesn't help this time...

What could be done?

Thanks.

---

### Post by alan-robinson on 2006-10-29
I'm seeing the same problem, this time on a VIA EPIA-M system.  Again, acpi=off didn't help.

I've got a feeling it's something to do with the server build of the kernel, so I'm just downloading the alternate CD to try that.  The install CD boots fine, and it uses the same kernel version, so clearly some versions of that kernel can boot on my hardware.

For me, the problem happens very early on in boot - pretty much immediately after grub.  

I'm just waiting for the alternate CD to finish downloading, but I thought I'd mention it in case you wanted to give that a try.  I'm hoping that fixes it, if not does anyone else have any suggestions?

---

### Post by alan-robinson on 2006-10-29
I've confirmed that this problem seems to only happen with the linux-server kernel (installed by the Server CD image by default).

I downloaded the i386 alternate CD, which installs the linux-i386 kernel by default.  This booted fine on my hardware.

I'm not sure if it's possible to get the Server CD to install the i386 kernel or not - if so, that would be an even easier workaround.

I hope this helps you, and anyone else seeing this problem, to at least work around it and make some progress.

---

### Post by marsian_bulldog on 2006-10-30
Great thanks!
I have used a lot of time with this, becourse i assumed that alternate and desktop edition had the same issue with VIA EPIA MII-10000.

I will give alternate a try, and i hope it can be installed base-config only.

One other good thing, i now know that my board is not defective :-)

Thanks again

---

### Post by David Mulligan on 2006-11-03
I had this problem on my Dell D600 laptop as well.  My goal is to install Ubuntu on a 2G USB stick.  Guess I will try the alternative install.

---

