---
title: "Network problem after dist upgrade"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by spock84 on 2007-10-22
On my desktop, networking just isn't working before I run "sudo /etc/init.d/./networking restart". Ubuntu doesn't recognize my RT2500 card (CNet CWP-854) at boot up.

Then it will work for a while, but then the network settings change from WEP (I've got an unencrypted wireless network and this setting always worked before) to WPA after a while, and nothing works, so I'll have to manually reset it each time. The card doesn't even support WPA does it? So that's certainly odd.

The latter problem happens on both my desktop and my laptop (iw3945 card) and both were upgraded through the update manager.

Anyone know what's going on? This never happened in any of the previous versions.

---

### Post by spock84 on 2007-10-23
bump

---

### Post by fazavon on 2007-10-23
try /etc/init.d/dbus restart

does it error? does it work?

//j

---

### Post by spock84 on 2007-10-23
That works just fine. Although it must be run with sudo to work, which I assume is correct.

---

### Post by fazavon on 2007-10-23
does your card work now?

What kind of card is it again?

lspci

---

### Post by spock84 on 2007-10-23
Well, the card WORKS, it's just not recognized at boot and in Network Settings it constantly changes back to WPA for some reason.. That happens less frequently on the laptop.

---

