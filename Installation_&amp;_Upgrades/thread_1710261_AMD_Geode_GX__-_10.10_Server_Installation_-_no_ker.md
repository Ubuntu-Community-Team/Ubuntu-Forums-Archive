---
title: "AMD Geode GX  - 10.10 Server Installation - no kernel installed"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by vbrachos on 2011-03-19
I would like someone **expert to help me with the following problem:**
**Hardware**: Wyse x150se Thin Client (AMD Geode GX, 256mb DDR, 512MB Hard Disk)

**I would like to install the ubuntu 10.10 server onto the above thin client.** I installed it (not swap file used, in order to fit in the small HardDisk)

**BUT**, I got the following message message and the installation could complete(I completed) without the kernel!!!

"no installation kernel was found in the defined APT sources 
you may try to continue without kernel, and manually install your own kernel later
This is only recommended for experts, otherwise you will end up with a machine that doesn't boot. Continue without Installing Kernel?" I said **YES**

**ATTENTION: **
1) I found that the linux kernel does not support teh AMD Geode GX, as a result a patch should be added during the kernel compilation. :shock:
2) I tried 8 different linux live USB(ARCHOS, DamnSL, Puppy, Ubuntu, Slax, Knoppix, android ...) distr and most of them prompt me with "Kernel Panics" or not supported vendor.

**I would like:**
1. To install a linux distribution onto that computer (i586)
2. Or could you help me how to install after the incomplete 10.10 ubuntu installation the kernel with the AMD Geode GX support (change some files probably)

---

### Post by Simba7 on 2011-04-07
I don't know if suggesting a specific distro besides Ubuntu is allowed here, but...

Did you try Gentoo or Debian? I compiled Gentoo on a K6-233 and it runs rather well, even though it took a couple weeks to compile.

I was going to put 11.04b1 on it, but noticed they dropped support back in 10.10. I did notice they still have i586 on quite a few packages in the recent versions, which they really should change to i686 to avoid confusing their users.

---

### Post by vbrachos on 2011-04-08
Thank,you very much for the reply. I installed successfully the tiny core linux. I found it lightweight and the only one i have found which support geode. For the hisfody, i am going to build a cluster of these funless thin clients.

---

