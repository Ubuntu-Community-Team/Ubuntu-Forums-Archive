---
title: "Mouse wheel scrolling issue"
date: 2009-03-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Noremacam on 2009-03-12
After switching to Jaunty(clean install) my mouse wheel refuses to scroll up. However, I tested the mouse on another computer and it works fine. I also noticed that zooming in compiz(Super + mouse up/down) works just fine(meaning it is only selectively ignoring my mousewheel up based on context). I also noticed that I can use mousewheel up to bring other windows into focus, but actually scrolling up doesn't work. It doesn't work in firefox, pidgin, rhythmbox, etc. I've made sure my system is up to date packagewise, and everything else, but I still have the problem. xorg.conf looks awfully barren(nothing about a mouse, just my nvidia related stuff). I have no idea where to look to fix it.

I have a Logitech mx310, if that makes any difference...

Anyone know of a fix?

---

### Post by combatwombat_nz on 2009-03-29
Same problem here. Jaunty beta.
I use a trackpad on Asus Z9000. There is a scrollwheel below the pad, that worked in Hardy+Intrepid, now doesn't.

Output of  xinput -list
"Virtual core pointer"    id=0    [XPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 0
"Virtual core keyboard"    id=1    [XKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"AT Raw Set 2 keyboard"    id=2    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Video Bus"    id=3    [XExtensionKeyboard]
    Num_keys is 248
    Min_keycode is 8
    Max_keycode is 255
"Macintosh mouse button emulation"    id=4    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
"AlpsPS/2 ALPS GlidePoint"    id=5    [XExtensionPointer]
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is 1023
        Resolution is 1
    Axis 1 :
        Min_value is 0
        Max_value is 767
        Resolution is 1
"PS/2 Mouse"    id=6    [XExtensionPointer]
    Num_buttons is 32
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is -1
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is -1
        Max_value is -1
        Resolution is 1

The funny thing is that now the right side of the trackpad scrolls, but this is very uncomfortable.
Possible related bugs:
[https://bugs.launchpad.net/ubuntu/+source/xfree86-driver-synaptics/+bug/320632](https://bugs.launchpad.net/ubuntu/+source/xfree86-driver-synaptics/+bug/320632)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/315882)

---

