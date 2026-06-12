---
title: "NX7100GS XServer Failure"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by Blue_T0oth on 2007-08-26
duel booting xp and 7.04 on the same drive and grub and xp r working fine but my vid drivers r messed up on ubuntu, just finished installing and the live cd worked just fine ne advice?

---

### Post by Pumalite on 2007-08-26
Get IN first with: sudo dpkg-reconfigure xserver-xorg. Say yes to most defaults, choose 'vesa' as your driver. Then: startx
Later you can install appropriate driver.

---

### Post by WeeWillyWacko on 2007-08-27
I have an identical problem. Booted and installed from the live cd no-prob. Initial startup X fails to start with no screen errors. logging in and running dpkg-reconfigure xserver-org gives error "xserver-org is not installed and no info is available"... I can do the installation of the xserver-org, but shouldn't the installation have done that?  ](*,)  This is on an ECS Mbd with on-board Nividia graphics. -- oh nevermind! I was typing xserver-org instead of xserver-xorg... :-P

Bill

---

