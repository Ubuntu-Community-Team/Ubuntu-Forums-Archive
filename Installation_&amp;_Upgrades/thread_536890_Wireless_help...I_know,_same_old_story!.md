---
title: "Wireless help...I know, same old story!"
date: 2007-08-28
forum: Installation &amp; Upgrades
---

### Post by soeiro on 2007-08-28
Hi guys,

I'm a complete newbie that just installed Ubuntu 7.04 in an Acer Aspire 5051. The problem i get (just like many of you) is that i just can't get my wireless to work. My wireless is a Broadcom 802.11g (that's the only information i have).
I tried almost everything that i found on the net and nothing works, anyway i'm just starting when it gets to write command lines.

Could you please help me, i'm starting to get frustrated about the new OS, and i really want to quit Windows.

Thanks in advance.

Soeiro

---

### Post by Steve1961 on 2007-08-28
> **soeiro said:**
> Hi guys,

I'm a complete newbie that just installed Ubuntu 7.04 in an Acer Aspire 5051. The problem i get (just like many of you) is that i just can't get my wireless to work. My wireless is a Broadcom 802.11g (that's the only information i have).
I tried almost everything that i found on the net and nothing works, anyway i'm just starting when it gets to write command lines.

Could you please help me, i'm starting to get frustrated about the new OS, and i really want to quit Windows.

Thanks in advance.

Soeiro

First things first, type the following in a terminal:

lspci -v

this should give you more information about your wireless card.  Then search the forum for a how to based on that information.  e.g.

[http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=197102&highlight=broadcom)

---

### Post by undertherift on 2007-08-28
With a broadcom chipset, you're most likely going to have to use bcm43xx-fwcutter.

If you google that, you should be able to find a good tutorial.
Here's a good post i think:
[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

---

