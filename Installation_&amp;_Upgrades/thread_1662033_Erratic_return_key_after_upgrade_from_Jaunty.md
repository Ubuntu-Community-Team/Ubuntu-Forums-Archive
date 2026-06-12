---
title: "Erratic return key after upgrade from Jaunty"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by hugoles on 2011-01-07
Hi all,
 
 I upgraded 2 consecutive times ----from Jaunty to Karmic and then right  away to Lucid--- and now I have an annoying problem with the return  (enter) key, it behaves erratically. It does not work as it should every  time I press it: I have to hit the key up to 5 times to make it work!  The most annoying thing is that this varies randomly, sometimes it works  with one hit. When it does not work, the cursor only blinks, so I guess  is not a problem of the keyboard. I upgraded to Maverick hoping to  solve the issue but it is still there. The enter key from the num pad  works just fine. Using xev I get:
 
 KeyPress event, serial 36, synthetic NO, window 0x4c00001,
     root 0x27a, subw 0x0, time 3237594, (439,190), root:(820,339),
     state 0x10, keycode 36 (keysym 0xff0d, Return), same_screen YES,
 "   XLookupString gives 1 bytes: (0d) "
 "   XmbLookupString gives 1 bytes: (0d) "
     XFilterEvent returns: False
 
 FocusOut event, serial 36, synthetic NO, window 0x4c00001,
     mode NotifyGrab, detail NotifyAncestor
 
 FocusIn event, serial 36, synthetic NO, window 0x4c00001,
     mode NotifyUngrab, detail NotifyAncestor
 
 KeymapNotify event, serial 36, synthetic NO, window 0x0,
     keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
            0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
 
 ---**and sometimes it gives:**
 
 FocusOut event, serial 36, synthetic NO, window 0x4c00001,
     mode NotifyGrab, detail NotifyAncestor
 
 FocusIn event, serial 36, synthetic NO, window 0x4c00001,
     mode NotifyUngrab, detail NotifyAncestor
 
 KeymapNotify event, serial 36, synthetic NO, window 0x0,
     keys:  2   0   0   0   16  0   0   0   0   0   0   0   0   0   0   0   
            0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
 
 KeyRelease event, serial 36, synthetic NO, window 0x4c00001,
     root 0x27a, subw 0x0, time 5656450, (-462,655), root:(287,770),
     state 0x10, keycode 36 (keysym 0xff0d, Return), same_screen YES,
 "   XLookupString gives 1 bytes: (0d) "
     XFilterEvent returns: False
 
 **The enter key on the num pad gives:**
 
 KeyPress event, serial 36, synthetic NO, window 0x4c00001,
     root 0x27a, subw 0x0, time 5779665, (-495,224), root:(612,597),
     state 0x10, keycode 104 (keysym 0xff8d, KP_Enter), same_screen YES,
 "   XLookupString gives 1 bytes: (0d) "
 "   XmbLookupString gives 1 bytes: (0d) "
     XFilterEvent returns: False
 
 KeyRelease event, serial 36, synthetic NO, window 0x4c00001,
     root 0x27a, subw 0x0, time 5779785, (-495,224), root:(612,597),
     state 0x10, keycode 104 (keysym 0xff8d, KP_Enter), same_screen YES,
 "   XLookupString gives 1 bytes: (0d) "
     XFilterEvent returns: False
 
 Does anybody have an idea what might be causing this problem? Any help is very appreciated!!

---

