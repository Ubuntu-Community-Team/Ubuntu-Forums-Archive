---
title: "Pre-Install Question: What X?"
date: 2005-09-24
forum: Installation &amp; Upgrades
---

### Post by longtex on 2005-09-24
I have a PartnerTech POS Terminal. The touchscreen driver needs XFree86.

Is Ubuntu's X the XFree86 or X.org?

---

### Post by Xian on 2005-09-24
It's Xorg. Debian's Sarge is XFree86.....

---

### Post by longtex on 2005-09-24
Dang. I may have to go to SuSE 9.1 for this thing...

Thanks for the quick answer!

---

### Post by papangul on 2005-09-25
Maybe there is some other better way to deal with it , I mean reinstall the driver or altering some config file! That will be cooler than changing the OS itself.
Btw, a driver can ask for X, how can it ask for Xfree86 particularly, has anybody got any idea?

---

### Post by longtex on 2005-09-25
[QUOTE=papangul]Maybe there is some other better way to deal with it , I mean reinstall the driver or altering some config file! That will be cooler than changing the OS itself.
Btw, a driver can ask for X, how can it ask for Xfree86 particularly, has anybody got any idea?[/QUOTE]

I dunno - the driver is source code, from Partner Tech, and the installation instructions include XFree86...-devel. If you try to compile it without installing the XFree86-devel stuff, you get a zillion errors; if you try to install the XFree86-devel first, you get a zillion conflicts with what appears to be Xorg stuff... 

I'd be REAL happy to leave the OS intact, but it's a SuSE 9.2. PartnerTech says their driver  works fine with SuSE 9.1, which is, of course, XFree86; it also works with various other distros they've tried, all of which are XFee86. 

I suppose I could get a copy of SuSE 9.1, but I happen to have a Ubuntu 5.04 DVD about ten feet away, and I thought maybe it was still XFree86... but it's not.

Now, if there IS a way to make it work with Xorg instead... <happy_camper_mode=ON>

---

### Post by papangul on 2005-09-26
SUSE has switched to Xorg also!

---

### Post by longtex on 2005-09-26
[QUOTE=papangul]SUSE has switched to Xorg also![/QUOTE]

Yah, I know this. SuSE 9.1 is XFree86, SuSE 9.2 and 9.3 are Xorg.

The manufacturer says his driver works on SuSE 9.1, but I don't have one; may buy one just for this purpose unless another way can be found.

---

