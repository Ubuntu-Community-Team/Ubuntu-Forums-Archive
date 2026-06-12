---
title: "install with no ethernet card?"
date: 2006-07-16
forum: Installation &amp; Upgrades
---

### Post by logants on 2006-07-16
I want to install Ubuntu, I have no ethernet card I have a wireless-g usb network adapter (WUSB54G) instead. how do I install this way? I have tried and it always fails when it tries to detect the ethernet, is there a way around this? any help is greatly appreciated, Thank you.

---

### Post by halitech on 2006-07-18
check here: [WUSB54G]("http://www.ubuntuforums.org/showthread.php?t=135983&highlight=WUSB54G")

and look at posts 8 and 9, seems you aren't alone with that brand USB wireless. hope this helps.

---

### Post by mejohnsn on 2006-07-19
> **logants said:**
> I want to install Ubuntu, I have no ethernet card I have a wireless-g usb network adapter (WUSB54G) instead. how do I install this way? I have tried and it always fails when it tries to detect the ethernet, is there a way around this? any help is greatly appreciated, Thank you.

I have a similar situation. But I have a different wireless card, and I am still waiting for an answer to my question about partitioning before I do a full install from the liveCD.

In the meantime, I run Ubuntu off the liveCD only. And I have no ethernet card. I use a Wireless card instead. When I use the older card, which _is_ recognized by Ubuntu, it shows up as 'wlan0', NOT as 'eth0' or 'eth1'. When I use the newer card, which is not recognized, it shows up as 'eth1' and does not work.

So in the former case, I launch System>Administration>Network, choose 'wlan0' as my default gateway, find the ESSID in the drop down menu, enter the key, click OK and everything works.

You can verify this with "ping -c 3 www.yahoo.com".

You should try doing the same thing, and then install from that point (there is an install menu option somewhere), as long as Ubuntu recognizes your card.

If Ubuntu does not recognize your card, it will try to classify it (during boot time) as 'eth1', but 'eth1' will not work. I don't have any further advice for you in that case, except to buy a card that Ubuntu does recognize (they are pretty cheap now).

Good luck!

---

