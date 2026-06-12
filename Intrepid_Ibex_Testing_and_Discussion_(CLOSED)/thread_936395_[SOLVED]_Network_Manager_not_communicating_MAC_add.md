---
title: "[SOLVED] Network Manager not communicating MAC address with router."
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by FuturePilot on 2008-10-02
I use MAC address filtering on my router. The problem is it seems that Network Manager isn't communicating my wireless MAC address to the router making it impossible to connect. However it seems that I got it working after I manually added my wireless card's MAC address in Network Manager as you can see in the screenshot. Originally that field was blank. I'm wondering if anyone else is having this problem and if there's a bug report or if perhaps I should create a bug report on this.

---

### Post by hugmenot on 2008-10-02
Two things:

1. It&#8217;s impossible that "your router does not communicate the MAC address" because your MAC address is what makes WLAN work in the first place. Otherwise you would not receive any packets.

2. You are wrong about the meaning of this field. See the attachment. The field is to specify with which network card you want this connection to work

In conclusion, don&#8217;t file anything, please.

---

### Post by wilsong on 2008-10-02
> **FuturePilot said:**
> I use MAC address filtering on my router. The problem is it seems that Network Manager isn't communicating my wireless MAC address to the router making it impossible to connect. However it seems that I got it working after I manually added my wireless card's MAC address in Network Manager as you can see in the screenshot. Originally that field was blank. I'm wondering if anyone else is having this problem and if there's a bug report or if perhaps I should create a bug report on this.

Did you have multiple network adapters, maybe thats why it worked once you but your MAC Address of the device you wanted to use into this field?

---

### Post by FuturePilot on 2008-10-03
> **hugmenot said:**
> Two things:

1. It&#8217;s impossible that "your router does not communicate the MAC address" because your MAC address is what makes WLAN work in the first place. Otherwise you would not receive any packets.

2. You are wrong about the meaning of this field. See the attachment. The field is to specify with which network card you want this connection to work

In conclusion, don&#8217;t file anything, please.
Ok thanks for the explanation.

> **wilsong said:**
> Did you have multiple network adapters, maybe thats why it worked once you but your MAC Address of the device you wanted to use into this field?
I only have a wireless card and an ethernet port.

But shouldn't Network Manager be picking up the MAC address automatically? It's still odd that I was only able to connect after I put my MAC address in there.

Edit:
Ok it seems I have other problems connecting that are not related to a MAC address issue. So I'm just going to mark this as solved.

---

