---
title: "NM: VPN (PPTP) - Add Button disabled"
date: 2008-09-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Sophont on 2008-09-21
I just tried (with the live 64 bit * CD) Alpha 6 hoping that I can now use VPN again (a requirement before I can upgrade).

Most stuff seems to be at least OK. But even after I installed the PPTP package (all on live CD session) the Add buton on the NM 7.0 Tab for VPN is still disabled.

Bug #259168 ("Network Manager unable to connect to PPTP VPN") suggests that VPN via NM can be configured (then giving trouble afterwards).

What have I missed?
Or does it only (half-) work with svn version that didn't make it into Alpha 6 yet (the beug report was pre-6)?

Does anybody have PPTP VPN working via Intrepid NM?

It's still working on my Hardy installation (though suffering a bit due to the fact that I have to fix the MTU with a script after every connect because the MTU fields in NM are fake). How come it's regressed in the shiny NM 7?

p.s.
* I also tried the 32bit version - but that failed to boot. But it's the 32biut version of Hardy that I have installed on my computer and which has been working mostly fine since almost 3 years ago (about 1 year since I started using PPTP VPN with it)

---

### Post by leech on 2008-09-21
You have to install the network-manager vpn packages.  Namely network-manager-pptp.

Leech

---

### Post by Sophont on 2008-09-21
Second paragraph in my post says: "... after I installed the PPTP package ...".

Thanks - but I knew that and I did that.
I also mentioned that I have it running already and for quite a while on Hardy (and gutsy before that IIRC).

The VPN Tab is there right away. But even after installing the PPTP Package the Add button remains disabled.

---

### Post by jfernyhough on 2008-09-21
Try adding the NM 0.7 PPA to your sources.list

```
## NM 0.7
deb http://ppa.launchpad.net/network-manager/ubuntu/ intrepid main
# deb-src http://ppa.launchpad.net/network-manager/ubuntu/ intrepid main
```

This should update the pptp packages.

---

### Post by Sophont on 2008-09-23
> **jfernyhough said:**
> Try adding the NM 0.7 PPA to your sources.list
This should update the pptp packages.

Thanks - I'll try that. Though I thought that Alpha 6 would have included this version if that works.

---

