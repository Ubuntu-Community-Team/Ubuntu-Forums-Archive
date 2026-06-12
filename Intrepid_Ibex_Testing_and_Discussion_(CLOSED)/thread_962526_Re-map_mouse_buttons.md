---
title: "Re-map mouse buttons"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by codedmin on 2008-10-29
Hy there, i have a mx revolution. I used btnx but not it don't work. God thing, all the buttons are working. But not like i want.

Is there any simple way to map buttons? Or better i only want that my search button do replace the middle button!

I can do that if i active the mouse keys in keyboard preferences, but with that active my numbers in keyboard stop working.

Any help?

Thanks

.Xmodmap
> keycode 122 = Pointer_Button2
pointer = 1 2 3 4 5 8 9 10 11 12 13 14 15 16 17 6 7


With mouse keys active, when press search button xev
> 
KeyRelease event, serial 40, synthetic NO, window 0x6000001,
    root 0x1a6, subw 0x0, time 88806862, (89,20), root:(794,43),
    state 0x210, keycode 225 (keysym 0xfeea, Pointer_Button2), same_screen YES,
    XKeysymToKeycode returns keycode: 122
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False




With mouse keys not active, when press search button xev
> 
KeyRelease event, serial 35, synthetic NO, window 0x6000001,
    root 0x1a6, subw 0x6000002, time 88676193, (46,56), root:(751,79),
    state 0x10, keycode 225 (keysym 0xfeea, Pointer_Button2), same_screen YES,
    XKeysymToKeycode returns keycode: 122
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False



Solved here [http://ubuntuforums.org/showpost.php?p=6057289&postcount=13](http://ubuntuforums.org/showpost.php?p=6057289&postcount=13)

---

