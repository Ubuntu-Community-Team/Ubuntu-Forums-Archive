---
title: "Lucid 64-bit doesn't boot on Lenovo X201"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by allaboutsam on 2010-08-19
I'm trying to do a clean install of Lucid (10.04.1) 64-bit on a Lenovo X201, Ubuntu only (no dual-boot), using the alternate install disk for an encrypted LVM.

I followed the default options at all points during installation, except that I opted not to configure the network because the computer is not currently connected to a network. The install (said that it) completed correctly.

When I turn on the computer, it correctly runs the BIOS. Then I get a blank screen with a flashing cursor in the upper lefthand corner. The hard drive accesses a couple of times. After a few seconds, the screen goes off (the cursor doesn't just vanish; the screen actually goes off), and it just sits there indefinitely without booting.

No grub, no nothing.

Any ideas what the problem could be?

I should note that I've tried this with the boot order in the BIOS set several different ways, including HD first and only, with no effect.

---

### Post by mörgæs on 2010-08-20
If the machine is stable enough, please run 

```
hwinfo --gfx
```

and post the results.

You could also try a live boot with a 32 bit version and see if it works better.

---

### Post by allaboutsam on 2010-08-21
Thanks for the suggestion, but "stable enough"? It won't boot at all. There is no command line to type commands in.

I suspect that my problem may be related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554569]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/554569")
and/or this one:
[https://bugs.launchpad.net/ubuntu/+bug/531027]("https://bugs.launchpad.net/ubuntu/+bug/531027")

I am continuing to troubleshoot and will post more information when I get it. But I could still use suggestions, if anyone has them!

allaboutsam

---

### Post by mörgæs on 2010-08-21
Sorry, I was mixing your thread and another. 

This one is maybe better:
[http://ubuntuforums.org/showthread.php?t=1464101](http://ubuntuforums.org/showthread.php?t=1464101)

---

### Post by allaboutsam on 2010-08-23
Temporary solution [here]("http://ubuntuforums.org/showthread.php?t=1558725").

---

### Post by GhostCoder on 2010-10-04
> **allaboutsam said:**
> I'm trying to do a clean install of Lucid (10.04.1) 64-bit on a Lenovo X201, Ubuntu only (no dual-boot), using the alternate install disk for an encrypted LVM.


I have this exactly same problem with 10.04.1 32-bit.

---

### Post by GhostCoder on 2010-10-04
> **GhostCoder said:**
> I have this exactly same problem with 10.04.1 32-bit.


I now tried with 32-bit 10.10-rc-alternate and everything (encrypted LVM, graphics, WLAN, bluetooth, suspend..) seemed to work fine out-of-the-box :) Cool!

---

