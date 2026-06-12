---
title: "no DPMS with fglrx and jaunty beta x86-64"
date: 2009-04-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jwbaker on 2009-04-07
Does anyone have working DPMS with Jaunty 64-bit and fglrx?  On my machine with two Radeon 4550 cards, the monitor never turns off and "xset dpms force off" just gets me a blank screen with the monitor still on.

I have this in Xorg.0.log:

(II) Loading extension DPMS
(**) fglrx(0): Option "DPMS"
(II) fglrx(0): DPMS capabilities: Off
(**) fglrx(0): DPMS enabled

Which would seem to indicate that "off" is a supported DPMS mode.  By the way I'm using a Samsung 244T which cooperated fine with DPMS when I was using nvidia or intel graphics.

Any tips would be appreciated.

---

### Post by cmorrow on 2009-04-17
I get the exact same behavior, using a Radeon 4850 and a Radeon 3850 in Kubuntu 9.04 x86_64.

I have tried numerous combinations of DPMS Standby, off, etc. settings in my xorg.conf as well as in the KDE system settings.  xset dpms commands result in blanking my lcd panels but never turn off the backlight.

I upgraded to the (just released today) Catalyst 9.4 driver and notice no change.

The only way I can get DPMS to activate is using vbetool (sudo vbetool dpms off / sudo vbetool dpms on).

---

### Post by daponz on 2009-04-19
hi,

Same behavior here with catalyst 9.4 on radeon 4850 : the screen goes off but backlight stays on :/
Tried different xset settings with no luck, the only way to turn the backlight off is to use vbetool.

Looking for fix.

---

