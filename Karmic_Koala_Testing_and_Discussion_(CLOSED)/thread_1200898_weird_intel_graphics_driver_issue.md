---
title: "weird intel graphics driver issue"
date: 2009-06-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2009-06-30
If I load alpha 2 live cd without changing anything it seems the intel graphics driver doesn't load properly, I cannot enable desktop effects.

However, if all I do is to remove splash and quiet from the boot options screen it loads properly and desktop effects are enabled automatically at loggin, I can even change it to extra effects without issue.

How can we trouble shoot this to maybe figure out whats going on here?

or is this something to toss up to it being alpha and that the xserver is still being worked on?

can I contribute in some way so someone else doesn't have this problem?

lspci graphics line:> 00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)


---

### Post by buzzmandt on 2009-06-30
sorry, wanted to add too that this is the live cd, so no updates since its release have been applied.  might be helpful info.

EDIT, just checked and there are buku lots of updates, one is intel, xorg, etc and that might just take care of it.  might wait for alpha 3 to continue with this thread. I'll try any suggestions but not ready to commit such an early alpha to my HD.

---

