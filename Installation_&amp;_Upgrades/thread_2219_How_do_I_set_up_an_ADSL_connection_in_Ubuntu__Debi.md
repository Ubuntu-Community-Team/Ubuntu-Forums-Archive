---
title: "How do I set up an ADSL connection in Ubuntu / Debian?"
date: 2004-10-26
forum: Installation &amp; Upgrades
---

### Post by HiddenWolf on 2004-10-26
While on this system I have had a working network connection under Gentoo, so far I haven't managed with Debian or Ubuntu.

Problem I run in to:
*Installer does not give the option to set up a pppoe connection, but dhcp assumes the connection is up due to the internal network
* I cannot run pppoeconf, because Root is disabled.

Thus
* I get timeout errors during boot, when syncing hardware clock
* I can't finish base.conf

---

### Post by HiddenWolf on 2004-10-26
Alright. I got into my desktop.

I've got sound, I've got X, I've got middle mouse button. I can print. Great

But still, I cannot get an internet connection.

I ran pppoeconf "sudo pppoeconf"

Got in, finally, but it hangs.
It was detecting eth0, hang at 100%. I went to cook dinner, came back, was still there.

Any suggestions on how to get my connection up?

---

### Post by FLeiXiuS on 2004-10-26
What NIC card do you have, and which modem?

---

### Post by HiddenWolf on 2004-10-26
It's an integrated VIA solution. VIA-rhine does the trick.

Somehow my ppoeconf worked after a reboot, IE I get an external IP-addres (217.xxx.xxx.xxx) on ifconfig ppp0.

Now my problem is that all networking is sent to eth0, and not to ppp0...

---

### Post by HiddenWolf on 2004-10-26
route add default ppp0 did the trick

---

### Post by anabelle on 2008-07-05
What do you mean by "route add default ppp0 did the trick "

Im having the saem problem and i need to solve it.

---

