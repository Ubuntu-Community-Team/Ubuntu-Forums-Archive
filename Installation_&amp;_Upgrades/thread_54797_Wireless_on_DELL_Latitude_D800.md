---
title: "Wireless on DELL Latitude D800"
date: 2005-08-06
forum: Installation &amp; Upgrades
---

### Post by jrohde on 2005-08-06
Hi,

I've just installed my first Linux (Hoary) on a laptop, a DELL Latitude D800. Most went ok, but not - of course - the wireless configuration.

After a bit of messing with the setup up my access point (D-Link DI 614+) I had a successful install, but as far as I can see, it only installed IPV6. How come?

My laptop has a Intel PRO/Wireless 2100 3B (that's what HAL reports).

IWCONFIG reports:

eth1      unassociated  ESSID:"rohde"  Nickname:"ipw2100"
             Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
             Bit Rate=0 kb/s   Tx-Power:off
             Retry:on   RTS thr:off   Fragment thr:off
             Encryption key:1A2B-3C4D-5E   Security mode:open
             Power Management:off
             Link Quality:0  Signal level:0  Noise level:0
             Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
             Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Thanks,

Jakob

---

### Post by FLeiXiuS on 2005-08-06
Give me a more productive insight on what you have done.  

How did you setup your wireless.  Did you use ndiswrapper or did the drivers pre-exist?  Also give me a print out on 'ifconfig'.

---

