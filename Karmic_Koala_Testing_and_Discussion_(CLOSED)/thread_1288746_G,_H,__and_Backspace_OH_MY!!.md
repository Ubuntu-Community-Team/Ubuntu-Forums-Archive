---
title: "G, H,  and Backspace OH MY!!"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by thegodsquirrel on 2009-10-11
After the last couple updates the G H and backspace have gone out.  I dont think it is a hardware issue, as they are working with a different keyboard layout, but I would like to find out why they stopped working on the old layout.

---

### Post by emarkay on 2009-10-11
Now that's bizarre - after a reboot they are still gone?  
Have you inverted and "thumped" yopur KB to see if it's something intermittently coincidental?

---

### Post by thegodsquirrel on 2009-10-11
It is a laptop KB so have taken the keys off and cleaned but they dont seem to work expecially after sitting on suspend or after a reboot?  Hopefully switching the layout will keep the problem at bay.

---

### Post by tgalati4 on 2009-10-11
Run xev in a terminal and post the output of the effected keys.


For g, it should look something like:

KeyPress event, serial 32, synthetic NO, window 0x3a00001,
    root 0x84, subw 0x0, time 14098713, (73,109), root:(76,598),
    state 0x0, keycode 42 (keysym 0x67, g), same_screen YES,
    XLookupString gives 1 bytes: (67) "g"
    XmbLookupString gives 1 bytes: (67) "g"
    XFilterEvent returns: False

MotionNotify event, serial 32, synthetic NO, window 0x3a00001,
    root 0x84, subw 0x0, time 14098783, (74,109), root:(77,598),
    state 0x0, is_hint 0, same_screen YES

KeyRelease event, serial 35, synthetic NO, window 0x3a00001,
    root 0x84, subw 0x0, time 14098809, (74,109), root:(77,598),
    state 0x0, keycode 42 (keysym 0x67, g), same_screen YES,
    XLookupString gives 1 bytes: (67) "g"
    XFilterEvent returns: False

One event for press, one event for release

In the meantime, dust off your thesaurus and choose words that don't have G or H.

Oh, and don't make any mistakes.

---

### Post by thegodsquirrel on 2009-10-11
KeyRelease event, serial 36, synthetic NO, window 0x4c00001,
    root 0x1a7, subw 0x0, time 3918872, (789,479), root:(794,502),
    state 0x0, keycode 42 (keysym 0x67, g), same_screen YES,
    XLookupString gives 1 bytes: (67) "g"
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4c00001,
    root 0x1a7, subw 0x0, time 3984710, (793,225), root:(798,446),
    state 0x0, keycode 43 (keysym 0x68, h), same_screen YES,
    XLookupString gives 1 bytes: (68) "h"
    XFilterEvent returns: False
KeyRelease event, serial 36, synthetic NO, window 0x4c00001,
    root 0x1a7, subw 0x0, time 4028881, (948,175), root:(953,396),
    state 0x0, keycode 22 (keysym 0xff08, BackSpace), same_screen YES,
    XLookupString gives 1 bytes: (08) "
    XFilterEvent returns: False

---

### Post by tgalati4 on 2009-10-11
So, xorq is catcking the release events for the 3 keys, but not the press events!

I've never seen that.

And, no clue as to what is wronq..

---

### Post by thegodsquirrel on 2009-10-16
> **tgalati4 said:**
> So, xorq is catcking the release events for the 3 keys, but not the press events!

I've never seen that.

And, no clue as to what is wronq..

It is strange that it only happens right after I bring out of suspend and once it warms up they work fine, I think it may be hardware.

---

