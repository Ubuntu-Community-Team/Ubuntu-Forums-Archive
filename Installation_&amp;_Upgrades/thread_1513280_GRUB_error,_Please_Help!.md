---
title: "GRUB error, Please Help!"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by newb85 on 2010-06-19
I installed Grub 2 a few weeks ago, and since everything was running fine (after finagling a little so it would load WinXP) and I was tired of watching Grub chainload into Grub 2 on startup, I ran upgrad-from-grub-legacy.

Now when I start the machine, I see this

GRUB Loading stage1.5.


GRUB loading, please wait...
Error 15
_

And nothing more happens.
What does this mean?  Is there a way I can get my system back to operational (perhaps using a Live CD)?

---

### Post by confused57 on 2010-06-19
> **newb85 said:**
> I installed Grub 2 a few weeks ago, and since everything was running fine (after finagling a little so it would load WinXP) and I was tired of watching Grub chainload into Grub 2 on startup, I ran upgrad-from-grub-legacy.

Now when I start the machine, I see this

GRUB Loading stage1.5.


GRUB loading, please wait...
Error 15
_

And nothing more happens.
What does this mean?  Is there a way I can get my system back to operational (perhaps using a Live CD)?

Looks like legacy grub is still installed on the mbr, see #13 in this tutorial by drs305 for reinstalling grub with the live cd:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by SoFl W on 2010-06-19
[https://wiki.ubuntu.com/Grub2#Err15](https://wiki.ubuntu.com/Grub2#Err15)

---

### Post by darkod on 2010-06-19
Like already suggested, installing grub2 to the MBR should sort it out for you.

When you ran the upgrade-from-grub-legacy did you make sure you selected where to install grub2 when asked? To the MBR of the disk?

A common mistake people make when presented with a text based menu to select a device where to install grub/grub2, is that they use up/down to highlight their choice but then simply hit Enter. You need to hit Space to mark the choice, and usually a * sign will appear. Just hitting Enter doesn't select it, it just continues with the process with nothing selected in fact.

If that is what happened, then the upgrade didn't install grub2 to the MBR as you thought it would.

---

### Post by kansasnoob on 2010-06-19
> **newb85 said:**
> I installed Grub 2 a few weeks ago, and since everything was running fine (after finagling a little so it would load WinXP) and I was tired of watching Grub chainload into Grub 2 on startup, I ran upgrad-from-grub-legacy.

Now when I start the machine, I see this

GRUB Loading stage1.5.


GRUB loading, please wait...
Error 15
_

And nothing more happens.
What does this mean?  Is there a way I can get my system back to operational (perhaps using a Live CD)?

If you need detailed help please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by newb85 on 2010-06-19
> **confused57 said:**
> Looks like legacy grub is still installed on the mbr, see #13 in this tutorial by drs305 for reinstalling grub with the live cd:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Thanks a lot!  That worked like a charm.

---

