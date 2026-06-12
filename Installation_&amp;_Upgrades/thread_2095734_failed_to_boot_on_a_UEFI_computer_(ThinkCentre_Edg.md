---
title: "failed to boot on a UEFI computer (ThinkCentre Edge 92)"
date: 2012-12-17
forum: Installation &amp; Upgrades
---

### Post by freemant on 2012-12-17
Hi,

I've installed Ubuntu 12.10 desktop x86-64 into a ThinkCentre Edge 92 PC. The install process went through just fine but it failed to boot. The computer says:

    Error 1962: No operating system found

The boot info can be found in:

    [http://paste.ubuntu.com/1444646/](http://paste.ubuntu.com/1444646/)

The firmware has been configured to boot in UEFI mode and QuickBoot has been disabled. The ubuntu live USB boots just fine.

Please help me on how I can troubleshoot this thing. For example, is it possible to invoke the UEFI shell or check any boot log?

Thanks!

---

### Post by oldfred on 2012-12-17
It looks like Boot-Repair made fixes.

Did you go back into UEFI menu and choose to boot the ubuntu entry? And does Windows boot from UEFI menu directly? If so the new entry Boot-Repair added should work. 

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
These style entries will not work.
'Windows ...) (on /dev/sdXY)'

UEFI
BootOrder: 0001,0005,0006,000B,0007,000C,0000,0004
Boot0001* ubuntu

---

### Post by freemant on 2012-12-18
Thanks for the reply. The problem is, there is no boot menu at all. The first thing appears on the screen is that error message.

---

### Post by freemant on 2012-12-18
It is likely due to this issue: [http://mjg59.dreamwidth.org/20187.html?thread=774619](http://mjg59.dreamwidth.org/20187.html?thread=774619)

---

### Post by freemant on 2012-12-18
sorry, that error ("no operating system found") was caused by the enable status of compatibility mode (CSM). After disabling that, the grub menu is displayed and I can boot into Windows. But choosing the ubuntu entry will boot into busybox. So, the problem is still not solved yet.

---

### Post by freemant on 2012-12-18
Sorry, actually I screwed up that ubuntu partition. So, now it is working fine.

---

### Post by oldfred on 2012-12-18
Whatever it takes to get it working. Glad you resolved it. :)

---

