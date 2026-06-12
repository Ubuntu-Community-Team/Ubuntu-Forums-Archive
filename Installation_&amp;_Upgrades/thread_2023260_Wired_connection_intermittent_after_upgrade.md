---
title: "Wired connection intermittent after upgrade"
date: 2012-07-12
forum: Installation &amp; Upgrades
---

### Post by ArbiterOfTruth on 2012-07-12
Hello all. I upgraded from 11.10 to 12.04 & now my wired internet keeps disconnecting & reconnecting.

I am dual booted with Win7 Ultimate & I do not get that problem in Windows. I decided to give the upgrade a try & everything went as normal just like my previous upgrades. When the upgrade was finished, I booted into Ubuntu & everything ran smoothly, for about two minutes. Then the internet disconnected (Wired Network disconnected - you are now offline). It stayed like that for about 3 seconds then reconnected (Wired Connection 1 - Connection Established). It stayed reconnected for 43 seconds, then disconnects for 3 seconds & the whole thing starts over until I go back to Windows.

I am hoping somebody else got this problem & solved it. I will also take the OP's advice & run a new version live first to test it out in the future.

Thanks in advance,

---

### Post by dino99 on 2012-07-12
Long times ago i switch to wicd because of such issue. But you should not get this problem now, it has been fixed. Meaning your system is borked.

Solutions:
- rename : .local , .gconf , .config , .gnome2 folders, then logout/in, they will be cleanly recreated
- or do a fresh install

---

### Post by jmfal on 2012-07-12
Either your system is borked or your ethernet cable is.

---

### Post by ArbiterOfTruth on 2012-07-18
Thanks for the replies. If that were the case, why does it not happen in Windows?

---

### Post by marke525 on 2013-02-11
I had the same problem.  It has to do with the Network manager.  Here is the solution that worked for me

do this in a terminal window:

gksudo gedit /etc/NetworkManager/NetworkManager.conf  

then:

change the line: 
dns=dnsmasq
to:
#dns=dnsmasq#

then:
 
sudo restart network-manager

---

