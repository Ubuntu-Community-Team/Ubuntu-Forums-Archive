---
title: "[SOLVED] Can't boot xppro"
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by McTek on 2008-02-05
Just downloaded the latest upgrade and xppro does not appear in grub menu.
This has happened before I just edited menu.lst and pasted in this:

> title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+

and windows would boot OK. This time it didn't work. I get an ERROR #1
What do I need to do to correct this.

---

### Post by mikewhatever on 2008-02-05
Shouldn't the chainloader be +1? Here's mine
> 
root            (hd0,0)
savedefault
makeactive
chainloader     +1


I not sure what version you upgraded to, or have you, perhaps, just updated, but to make sure this Windows entry does not get overwritten again, place it outside of '### END DEBIAN AUTOMAGIC KERNELS LIST'. The very bottom of the page would be a good place.

---

### Post by McTek on 2008-02-05
Thank you sir, sometimes you can stubble over the dumbest things.

---

