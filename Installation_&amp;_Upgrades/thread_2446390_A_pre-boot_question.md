---
title: "A pre-boot question"
date: 2020-06-29
forum: Installation &amp; Upgrades
---

### Post by pengyou2 on 2020-06-29
This is either an Ubuntu/Windows question or it is neither.  I have Windows 7 on a notebook.  I am going to put Ubuntu on it also and have a dual booting system.  There is a lot of documentation on the internet to do that.  I would like to do something a little different.  I would like my notebook to boot to an intermediate "system" that will install a VPN and firewall that would be accessible to both Windows and Linux and would also require password access.  Is this possible - for a mortal man?

---

### Post by crip720 on 2020-06-30
I don't think so.  You can have a VPN and firewall installed on your router, depending on make of router or buy a VPN router.  You can also have a VPN load on startup on Ubuntu and think Windows.  Most of the better ones run on both OSs.  Think the closest you could get to what you want, is an minimum OS that has firewall and VPN and run Ubuntu and/or Windows in a VM(virtualbox)

---

### Post by ActionParsnip on 2020-06-30
You could run the server OS in HyperV. The Windows OS you "boot to" in HyperV is a VM on your hardware so you can set the VPN up there and any OS you virtualise after that will use the VPN. Its probably easier (and quicker) to setup a Raspberry Pi (or similar) as a proxy then point all your systems to use that as a proxy.

---

