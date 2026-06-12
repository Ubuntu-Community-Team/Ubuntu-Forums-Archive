---
title: "Bootable USB stick sometimes recognized..."
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by jwhendy on 2009-11-20
Hi,


I went through a hell of a time getting a workable 'actual' installation onto a USB stick... not a live version but a real, functioning installation.

Since then I've optimized a kernel for my computer. My issue:

- When I need to boot into Windows (on hard drive) for something, I'll reboot or shutdown afterwards.
- At the HP 6910p boot screen, I press F9
- I select 'USB Hard Drive'
- I get a lilo boot screen
- I select my custom kernel
- It starts booting and then says something to the effect of VFS: unable to sync, please use correct "root=" option; unrecognized device (8,11).
- I reboot and go through the exact same steps and get same result. My somewhat working fix:

- Boot into install cd, mount USB stick, chroot into USB stick and do:
--- lilo -v -M /dev/sdb
--- lilo -v -b /dev/sdb
--- reboot
- Then I press F9 and select USB Hard Drive and try to boot into the 'vanilla' (bloated) version of my kernel (Zenwalk 6.2 kernel with USB options built in instead of compiled as modules) and get the kernel panic again
- Then I reboot and do the EXACT same thing (vanilla kernel again) and it will work
- From XFCE, I do:
--- su root
--- lilo -v -M /dev/sdb
--- lilo -v
--- reboot
- Then I try to boot into my optimized kernel and get a kernel panic
- Then I reboot and do the EXACT same thing and it works

PLEASE help me avoid 6 reboots and running commands from an install CD! My dmesg when booting works is [HERE]("http://sites.google.com/site/jwhendytank/optimizedDmesg.txt").

Any thoughts? The computer obviously recognizes the USB stick when I press the power button since I can get to the lilo screen, right? There is something else not picking up the USB stick later on in boot. What in the world!??


Sincere, sincere thanks,
John

---

