---
title: "Keyboard and mouse no response at login screen after upgrade to 15.04"
date: 2015-04-28
forum: Installation &amp; Upgrades
---

### Post by ssj71 on 2015-04-28
Hi all:

This is a late 2014 15" Macbook Pro (haswell cpu).

I just upgraded and have been trying to figure this one out on my own, but I'm pretty stuck. Everything seemed to upgrade fine but when grub loads the 3.19 kernel it seems to disable usb or something. The keyboard and mouse do not respond at all. The login screen loads, blanks for a second then comes back but the pointer has dissappeared. The clock continues to run fine, the wifi connects, but I cannot type or use the mouse. I have tried a USB version of both a mouse and a keyboard and also tried booting off of a live 15.04 USB which doesn't load at all (I'm guessing similar since toggling the caps lock key does not turn on the light once the bootloader is done). I've tried booting with nomodeset and several other options but no avail. Recovery mode hangs up before I can select any options.

I can still boot with the 3.16 kernel but I really want 3.19 for the thunderbolt support added. I'm comfortable in a terminal and can post whatever logs that could help if you ask. I tried to look at them myself but don't really know what to look for. Hopefully we can find a solution.

Thanks.

---

### Post by ssj71 on 2015-04-29
I've been playing with the liveUSB more and was able to successfully boot the live and my install when I used the acpi=off boot option. Shutting down hung with a message reboot:System halted (is that actually hanging or just because I have quiet and splash off?). I don't want to use acpi=off though. I followed[ this guide for troubleshooting acpi]("https://wiki.ubuntu.com/DebuggingACPI") and it says "the issue is in the ACPI table parsing code itself, or perhaps the SMP code." and also "Such bugs should be reported against the linux package." Does that mean I should report the bug to the kernel devs? Also I'm not sure exactly what my bug is (or how to search duplicates) "[hardware x] acpi support breaks between 3.16 and 3.19"?

Thanks
_ssj71

---

