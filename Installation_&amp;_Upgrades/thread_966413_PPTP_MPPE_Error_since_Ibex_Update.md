---
title: "PPTP MPPE Error since Ibex Update"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by Johannes Hoppe on 2008-11-01
Hi,

I updated one of my Ubuntumashines last night. Today I tried to Connect to my University-Network via VPN.

But but since Ibex it's imposseble for me setting up the following configurations:
```
[main]
Description=ZEIK
Connection-Type=pptp
PPTP-Server=vpn.uni-potsdam.de
Use-Peer-DNS=yes
Encrypt-MPPE=yes
Encrypt-MPPE-128=yes
Encrypt-MPPE-Stateful=yes
Compress-MPPC=no
Compress-Deflate=no
Compress-BSD=no
PPP-Lock=yes
Auth-Peer=no
Refuse-EAP=no
Refuse-CHAP=no
Refuse-MSCHAP=no
MTU=1500
MRU=1500
LCP-Echo-Failure=10
LCP-Echo-Interval=10
PPP-Custom-Options=
Peer-DNS-Over-Tunnel=no
X-NM-Routes=
Use-Routes=no
```

Neighter it's possible to set this features via the GUI nor via the Importfunktion of the new GUI of the Network-Manager. It's also impossible to export a PPTP-Config.

I was lucky to update not me primary PC.
Does someone has an idee?

---

### Post by david on 2008-11-03
I have the same problem, unfortunately I did upgrade my main box and now I really need the VPN going. 

I found the MPPE controls in the gui under "advanced" but any changes there don't get saved. Press OK and they are just gone. 

This is a real showstopper for me. :(
/david

---

### Post by ke3ju on 2008-12-04
> **david said:**
> I have the same problem, unfortunately I did upgrade my main box and now I really need the VPN going. 

I found the MPPE controls in the gui under "advanced" but any changes there don't get saved. Press OK and they are just gone. 

This is a real showstopper for me. :(
/david

Has anyone found a fix for this yet?

I'm glad I made a Ghost backup of my Hardy install, because this garbage isn't going to fly.

Cheers,
Ed

---

