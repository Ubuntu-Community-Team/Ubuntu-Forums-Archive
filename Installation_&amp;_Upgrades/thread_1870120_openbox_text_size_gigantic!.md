---
title: "openbox text size gigantic!"
date: 2011-10-26
forum: Installation &amp; Upgrades
---

### Post by Naruthir on 2011-10-26
Hi,

  I had a notebook Ubuntu installation that I have upgraded to 11.10. I did not like the Unity layout one bit, so I wanted to try openbox, unfortunately I am having an odd problem. The text is HUGE, like 72 or larger. 

  I tried to look trough every configuration i could find, and no help at all, even Google failed me. So I was hoping someone could explain how to fix the weird theme size, and please notice that the text size in obconf is 6.  I do not understand one bit what is making the text size such out of proportion, considering it works just fine in gnome/unity. 

 Please notice it is all text that is huge, menus, terminals etc. :confused:

---

### Post by Naruthir on 2011-10-26
So how would I bug report this issue?

---

### Post by oldtimer7777 on 2011-10-26
> **Naruthir said:**
> So how would I bug report this issue?

If you install Lubuntu and try using Openbox in Lubuntu, does this problem still exist?

---

### Post by Naruthir on 2011-10-27
Yeah, in any case found the solution, DPI in openbox is screwed, so I had to change xorg.conf and put in 96x96 dpi. 

Adding following options under Device.
```
Option "UseEdidDpi" "False"
Option  "DPI" "96 x 96"
```

After reboot it worked just fine, kinda sad that it cannot handle 1080p by default.

---

