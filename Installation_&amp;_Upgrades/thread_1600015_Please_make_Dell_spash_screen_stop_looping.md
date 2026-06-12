---
title: "Please make Dell spash screen stop looping"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by spankler on 2010-10-18
Why, after a successful (I thought) dual boot installation w/ a  side-by-side lynx and meerkat install and XP does my system refuse to  boot? It just gets to the Dell screen, giving boot options (none of  which are making any difference) and keeps looping it. Last night, after  re-installing the grub (lost after the XP install) everything was  working fine. I powered down and this morning tried to restart  and...this. I really don't want to have to reinstall everything and  reconfigure and reinstall apps--what can I do? And more importantly, WTF  did this happen to begin with? Please help!

---

### Post by psusi on 2010-10-18
So if you reinstall grub, you can boot Ubuntu fine, then when you boot into Windows, it appears to work,  but then after you reboot again, it's broken?

It sounds like you have some brain dead program running on Windows that is overwriting grub.  Some crippleware tries to hide a marker in the grub area so it knows you have already used it past the expiration date so you can't reinstall it.

---

