---
title: "The Brigthness keys on Samsung Q210 dont' work... again"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rufuse on 2009-04-01
Recently, i installed ubuntu 9.04 and i was happy about fixed brightness regulation(fn+down, fn+up). But now it broken again and i don't have a clue why. :(
I hope it is right board to post it. Here's my xev output(looks ok to me):
```
KeyPress event, serial 35, synthetic NO, window 0x7c00001,but 
    root 0x13c, subw 0x0, time 881654, (-667,300), root:(4,351),
    state 0x0, keycode 233 (keysym 0x1008ff02, XF86MonBrightnessUp), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: [/B]
    XFilterEvent returns: False

KeyPress event, serial 35, synthetic NO, window 0x7c00001,
    root 0x13c, subw 0x0, time 959034, (-182,278), root:(489,329),
    state 0x0, keycode 232 (keysym 0x1008ff03, XF86MonBrightnessDown), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
acpi_listen don't produce any output to these keys.
I've tried setting these keys to 'nvclock -S +10' and 'nvclock -S -10' manually(system -> preferences -> keyboard shortcuts), but it simply doesn't work.

---

### Post by rufuse on 2009-04-02
bump

---

### Post by Barry Carroll on 2009-04-16
Did it break after you switched from the nv driver to the binary nvidia one perhaps?

---

