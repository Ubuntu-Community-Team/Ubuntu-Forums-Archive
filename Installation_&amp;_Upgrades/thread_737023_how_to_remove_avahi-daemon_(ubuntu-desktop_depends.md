---
title: "how to remove avahi-daemon (ubuntu-desktop depends on it)"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by gruadp on 2008-03-27
I have a server with a static-ip and avahi-daemon freaks me out, cause I dont know what it really does (man-page tells me about apple zeroconfig-protocoll, which I dont need) and it messed up my nsswitch.conf and caused host-lookupproblems on local domains.

but when I want to remove it:

# apt-get remove avahi-daemon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  avahi-daemon libnss-mdns ubuntu-desktop

ubuntu-desktop sound serious and I dont want to have it removed, but I dont want to have this avahi-monster hanging around under my bed any more 
:twisted:

thnx
peter

---

### Post by TenPlus1 on 2008-03-27
You don't reall yhave to remove it, simply goto System -> Administration -> Services and untick Multicast DNS service discovery .. and this disables Avahi-daemon...

---

### Post by kakao on 2008-05-15
> **TenPlus1 said:**
> You don't reall yhave to remove it, simply goto System -> Administration -> Services and untick Multicast DNS service discovery .. and this disables Avahi-daemon...

But what does it do? Does Gnomes Network Settings "Roaming" have something to do with it?

Thanks

---

