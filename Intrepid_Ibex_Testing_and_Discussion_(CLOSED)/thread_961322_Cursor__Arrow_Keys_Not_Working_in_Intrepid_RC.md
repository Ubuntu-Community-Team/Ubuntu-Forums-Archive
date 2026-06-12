---
title: "Cursor / Arrow Keys Not Working in Intrepid RC"
date: 2008-10-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Jæd on 2008-10-28
Hi,

I've upgraded to Intrepid RC and I've found my cursor (arrow) keys no-longer work. I'm using a UK keyboard. Output from xev using the left arrow key is:

KeyRelease event, serial 33, synthetic NO, window 0x5800001,
    root 0x52, subw 0x0, time 1132514736, (169,171), root:(179,238),
    state 0x80, keycode 113 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

Setting different keyboards in the keyboard preferences panel don't seem to solve the problem...!

Let me know as this is really annoying...! 

Thanks...!

---

### Post by Jæd on 2008-10-28
Solved this by looking at : [https://bugs.launchpad.net/ubuntu/intrepid/+source/xorg-server/+bug/255008](https://bugs.launchpad.net/ubuntu/intrepid/+source/xorg-server/+bug/255008)

"so the workaround is to use the gnome keyboard capplet and change the model as "generic - evdev", until a permanent solution is in place."

Did this and solved the problem...

---

### Post by midnightflash on 2008-10-28
Seems to be the following bug:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/255008](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/255008)

There are soltuions in that report.

---

