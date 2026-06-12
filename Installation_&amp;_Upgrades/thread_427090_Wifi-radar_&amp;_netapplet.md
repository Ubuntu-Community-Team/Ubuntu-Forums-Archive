---
title: "Wifi-radar &amp; netapplet"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by patrickfromspain on 2007-04-29
Hi there!

I open this post just to share my experience with netapplet and wifi-radar instead of network-manager..

At the moment, I don't like Network-manager: I have to entry the passwork after every boot; last time I tried the pam-keryring stuff, there was a bug  that forced me to disable autologin.. and, even more, pam-keyring stuff is just a dirty fix.. which I don't like, and that has been broken a few times after updates (if my information are correct)

My solution? I uninstalled network-manager and installed both wifi-radar and netapplet. It's not perfect, since I've had to disconnect from the wifi-radar network to use  wired network in netapplet, and when changing back to wifi, I have to connect wireless in netapplet and then connect with wifi-radar. Anyway, it seems more work than it is, and it is quite straight forward (4 clicks, maybe 10 sec?)

I quite like this solution, as my lappy boots and connects to my home network inmediately. Also, I managed to connect to a WPA-PSK (TKIP) network using only wifi-radar (no fiddling with wpa-supplicant or such things..)

By the way, I'm using ndiswrapper drivers.

Just try it.. may be you like it better than NM.

PD: if you have a ralink card, has anybody tried blacklisting all the ralink kernel modules and using ndiswrapper? Also a dirty hack, but who knows.. maybe WPA and NM will work then.

EDIT: sorry, wrong forum. Can somebody move this to networking & wireless? Thanx!

---

