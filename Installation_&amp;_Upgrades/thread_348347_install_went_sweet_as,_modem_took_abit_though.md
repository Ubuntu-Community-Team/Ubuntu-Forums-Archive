---
title: "install went sweet as, modem took abit though"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by hoggboy on 2007-01-28
First time linux user here. system Toshiba Tecra 9000 laptop. Put Dapper 6.06 in went through the process all fine. Install as dual boot with win2k. Some problem with modem / softmodem, so heres what i did.

1) Installed sl-modem-daemon_2.9.10+2.9.9d+e-pre2-5build1_i386.deb  ,via package manager.

it would then dialup but disconect without connecting so did,

2) #open root terminal 

     "/sbin/ifconfig eth0 down"

#then

wvdial



connects sweet as n o problem but gnome dialer dont work so go through wvdial.

Hope it helps anyone having probelms on laptops.
Am updating as i type this so hpoefully new ppp dialer works

Easy as install, far easier than any windoze:D

---

