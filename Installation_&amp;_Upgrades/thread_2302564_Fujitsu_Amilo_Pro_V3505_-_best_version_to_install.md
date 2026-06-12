---
title: "Fujitsu Amilo Pro V3505 - best version to install?"
date: 2015-11-11
forum: Installation &amp; Upgrades
---

### Post by Painty on 2015-11-11
I've got the book - Ubuntu Unleashed which has a copy of 6.06 on DVD - I've installed it on the laptop - but I can't get internet configured - so I thought I'd download the latest version - burn to DVD and use the live version to then do a fresh install - thinking that maybe the networking stuff is a bit more automatic - 8 versions on! However the DVD won't load the live version which I assume may be because of the age of the laptop.

So - should I try a different iteration of Ubuntu? Or install differently? Or get advice on networking so I can at least get that laptop running?

---

### Post by grahammechanical on 2015-11-11
We do not expect Linux to suffer the same level of malicious attacks as Microsoft Windows does but I don't think it sensible to connect a machine with Ubuntu 6.04 to the internet. You most definitely should use a present day supported version of one of the Ubuntu family of Linux distributions.

Does that machine really only have 512 MB of RAM and only 128 MB of video memory?

[http://www.cnet.com/products/fujitsu-amilo-pro-v3505-15-4-core-2-duo-t5200-win-xp-pro-512-mb-ram-80-gb-hdd/specs/](http://www.cnet.com/products/fujitsu-amilo-pro-v3505-15-4-core-2-duo-t5200-win-xp-pro-512-mb-ram-80-gb-hdd/specs/)

I use Ubuntu and I do not like to recommend anything other than Ubuntu but I do not think that machine is capable of running Ubuntu with its Unity 3D user interface. There could be a couple of reasons why the newer versions of Ubuntu do not load a live session.

a) The need to use the nomodeset boot parameter option. See the heading the CD's Default Boot Options - section 6 F6

[http://www.cnet.com/products/fujitsu-amilo-pro-v3505-15-4-core-2-duo-t5200-win-xp-pro-512-mb-ram-80-gb-hdd/specs/](http://www.cnet.com/products/fujitsu-amilo-pro-v3505-15-4-core-2-duo-t5200-win-xp-pro-512-mb-ram-80-gb-hdd/specs/)

b) The need to use a non-pae kernel which Ubuntu no longer supplies but Lubuntu does. However, the Intel T5200 is a 64 bit CPU so I do not think this problem applies in your case.

[http://ark.intel.com/products/27252/Intel-Core2-Duo-Processor-T5200-2M-Cache-1_60-GHz-533-MHz-FSB](http://ark.intel.com/products/27252/Intel-Core2-Duo-Processor-T5200-2M-Cache-1_60-GHz-533-MHz-FSB)

I suggest that you examine Xubuntu or Lubuntu or Ubuntu Mint as alternatives to Ubuntu.

Regards.

---

### Post by mörgæs on 2015-11-12
Hi, welcome to the fora.

You don't have PAE problems with this processor.
When you have installed L/Xubuntu using wired internet access and applied all updates [this guide]("http://ubuntuforums.org/showthread.php?t=370108") should help you.

---

### Post by Bucky Ball on 2015-11-12
> **mörgæs said:**
> Hi, welcome to the fora.

You don't have PAE problems with this processor.
When you have installed L/Xubuntu using wired internet access and applied all updates [this guide]("http://ubuntuforums.org/showthread.php?t=370108") should help you.

^^^
This. You can try both Xubuntu and Lubuntu from the install disk prior to installing. See how they go. 14.04 LTS is long-term support until 2017 and 15.10 until next January. Both are directly upgradeable to the next LTS release 16.04 when the time comes. :)

---

