---
title: "Network problem upgrading Edgy -&gt; Feisty"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by jfofnian on 2007-10-26
Hi,

I've just upgraded my Ubuntu Edgy to Feisty (I know, I'm a version behind!), using the automatic upgrade.  Sadly, since the installation completed, I can't get my (wired) network connection to work.  It was fine before the update, and I can still connect through my Windows partition, so I'm thinking the problem must be with Feisty.  I'd really appreciate advice, and if this isn't a standard problem, then I'm happy to provide any information you might need.  Would simply upgrading again to Gutsy (by CD) be likely to solve this issue?

Thanks in advance.

---

### Post by nab on 2007-10-26
Hi,

I had in feisty the problem and solved it following this HOWTO: [Wireless Security - WPA1, WPA2, LEAP, etc.]("http://ubuntuforums.org/showthread.php?t=202834")

On the first start everything worked fine. On second start everything broke down.
It seems that the manual configuration in /etc/network/interfaces and nm-applet broke my system, because after removing all edits from /etc/network/interfaces my wlan works fine again.

Hopr this helps,
Niko

---

