---
title: "[SOLVED] How to disable visual effects through cli?"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kagashe on 2008-10-27
I have installed Intrepid RC. Live CD could be run only in safe graphics mode. After installation I changed the driver from vesa to intel. I could get the GDM login screen but X lock up (infinite loop) is taking place after login.

I added openbox and I could login to openbox session with intel driver.

I suspect that X lock up may be due to visual effects enabled by default.

I would like to disable the visual effects without login to Gnome through Cli or by login to openbox session (which may be again through Cli only).

How to disable visual effects through cli?

kagashe

---

### Post by jerrylamos on 2008-10-27
My IBM Thinkpad R31 with Intel graphics freezes when desktop opens because of compiz code, the code that does visual effects.

To see if this helps,
boot in recovery mode
when selection menu appears choose
root prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume normal boot

If you want to try compiz again then do the same except install instead of remove.  You have to have internet running, so do
sudo dhclient
ifconfig
to see if the network is up.

Jerry

---

### Post by kagashe on 2008-10-28
Thanks. I can login to Gnome with intel driver after removing compiz.

kagashe

---

