---
title: "FTP to DHCP Node?"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by tim042849 on 2012-05-20
We have ubuntu 10.04, ubuntu 12.04 here. I'm just curious if it is possible to make
an FTP connection to a computer that is connected via DHCP. In the past, I have used
static IPs only, but to make a long story short, I have had a lot of problems with static IPS 
with later versions of ubuntu on both wired and wireless connections.

The possible first step is to see if one can configure a local network so that the same DHCP
addresses are assigned to the same computers (MAC addresses). Is this possible?
Any thoughts?
thanks
tim

---

### Post by steeldriver on 2012-05-20
yes modern routers will allow you to do it - it's called 'address reservation' or 'DHCP reservation'

you may also be able to use <hostname>.local (via mDNS / zeroconf)

---

### Post by tim042849 on 2012-05-20
> **steeldriver said:**
> yes modern routers will allow you to do it - it's called 'address reservation' or 'DHCP reservation'
Oh good! That will be handy. I will research that. Thank you.
> **steeldriver said:**
> you may also be able to use <hostname>.local (via mDNS / zeroconf) Hmm! Not  sure that I understand the last. My question is not a great priority,
so links to further resources would suffice.
Thanks again.
tim

---

