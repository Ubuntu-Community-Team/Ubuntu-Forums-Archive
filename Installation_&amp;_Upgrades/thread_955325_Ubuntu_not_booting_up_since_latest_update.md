---
title: "Ubuntu not booting up since latest update"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by bodmcn on 2008-10-22
Hi,

I'm hoping someone can help me out here.  Since the latest updates, my PC no longer boots into Ubuntu 8.04.1 - 2.6.24-19.

Initially the screen just went blank after the Ubuntu progress bar initialisation.  Now I get to the graphical login screen, but the keyboard does not work - not even the Num Lock.  The mouse works fine though.

If I press Ctrl-Alt-F1 during the Ubuntu progress bar, I get to a Desktop login, but the keyboard still doesn't function.  Once, the keyboard started working after I had an NTP stopped message.  I tried to do this again, but the keyboard stays very dead - apart from the Ctrl-Alt-Del, which reboots.

I'm very confused and would really like my PC back.  Would anyone have any ideas?

Thanks in advance,

---

### Post by bodmcn on 2008-10-22
Hi,

After playing around with the Num Lock key - it appears that the issue is with the wpa_supplicant process.  It appears to be killing the keyboard.

If I remove the wireless card, then the system boots up.

Any ideas on where to go from here?

Thanks in advance,

---

