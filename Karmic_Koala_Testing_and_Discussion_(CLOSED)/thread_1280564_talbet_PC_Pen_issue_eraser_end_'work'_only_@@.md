---
title: "talbet PC Pen issue: eraser end 'work' only @@"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wildbat on 2009-10-02
hi, I have a Fujitsu T4220 tablet pc.

the eraser end can move the cursor and left-click(for some reason) but nothing work at the the normal pen tips.

tried: wacom-utility
[http://www.gtk-apps.org/content/show.php?content=104309&forumpage=0](http://www.gtk-apps.org/content/show.php?content=104309&forumpage=0),
but no luck ( it detect no graphic tablet device :<) 

anyone have a clue how to fix that ?

---

### Post by Roswellgrey on 2009-10-02
Chances are its a serial digitizer, and as such the utility you mentioned won't work :(

What's the output of :

xinput --list

This should show whether the stylus is being detected OK ( or not.. )

---

### Post by astrand on 2009-10-13
I'm having the exact same problem with KArmic on my T4215

xinput --list 
indicates that the wacom eraser is detected, but not the stylus.

Any updates on this issue?

Thanks,
A.

---

### Post by Favux on 2009-10-13
Hi astrand,

Could you attach the output of "xinput --list"?

---

### Post by astrand on 2009-10-13
The xinput --list output is attached.
Thanks,
a.

---

### Post by Favux on 2009-10-13
Hi astrand,

That definitely isn't right.  Your eraser line is:
```
"PnP Device (FUJ02e5) eraser"	id=8	[XExtensionKeyboard]
```
and your stylus line should look something like:
```
"PnP Device (FUJ02e5)"	id=?	[XExtensionKeyboard]
```
To rule out a hardware problem, i.e. broken stylus tip, is it working in another OS, say windows?

Let's hope it's something simple with the serial section of the  .fdi.  Please attach a copy of your '10-linuxwacom.fdi' at "/usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi"

Are you using Karmic beta?

---

### Post by astrand on 2009-10-13
It's definitely not a HW problem.  

Pen and eraser both work in vista.

10-linuxwacom.fdi is attached. 

This is a fresh install of Karmic Beta, not an upgrade.

cheers,
Allan

---

### Post by Favux on 2009-10-14
Hi astrand,

The .fdi looks OK to me.  So it may not be something simple.  :(
It sure looks like the stylus should show up.  We could try playing with it a little.  After all the eraser is showing up.

Other possibilities are kind of endless.  Upstream .fdi problem.  Like in the 10-Tabletpc.fdi?  Or maybe the the udev 40-wacom.rules accidently dropped the symlink for your serial tablet?  Or maybe a regression in linuxwacom, where your product id accidently got dropped?

We could check out the Vendor and Product ID's with lsusb and/or lshal>lshal.txt.

I'd search launchpad for a bug(s) report.  You may need to file one.

---

### Post by Favux on 2009-10-15
Oh, and you should check Xorg.0.log to see what's happening with xorg when the .fdi tries to configure the stylus.

---

### Post by astrand on 2009-10-29
Just and update...
A recent upgrade to my karmic beta install has now completely broken stylus and eraser function....

cheers,
Allan

---

