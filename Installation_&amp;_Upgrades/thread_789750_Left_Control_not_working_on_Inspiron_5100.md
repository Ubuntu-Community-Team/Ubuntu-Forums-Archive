---
title: "Left Control not working on Inspiron 5100?"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by satmandu on 2008-05-10
I have a new xubuntu install on a Dell Inspiron 5100, and for some reason the left control button isn't responding when I try to do things like control-c in programs such as firefox or xfce terminal.  Right control works just fine!

I ran xev, and it spits this out for the two keys:

KeyRelease event, serial 31, synthetic NO, window 0x2a00001,
    root 0x57, subw 0x0, time 88303652, (168,-14), root:(591,290),
    state 0x4, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 31, synthetic NO, window 0x2a00001,
    root 0x57, subw 0x0, time 88305455, (168,-14), root:(591,290),
    state 0x0, keycode 109 (keysym 0xffe4, Control_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False


So the left control key SEEMS to be working, but somewhere it is getting intercepted.  But I'm not sure where that might be happening.

Is there a default xubuntu key binding for that key I should be aware of?

Which keyboard model should I have picked for a US Inspiron 5100?

In the setup configuration, I left the default of "generic 105 key (intl) keyb".  I also see Dell Latitude keyboard options, but not Inspiron options.

This is quite irritating, as simple things like copy and paste don't work using the keyboard commands.

Interestingly enough, switching VTs using leftctl-alt-Fkeys seem to work though.

Any ideas?

---

