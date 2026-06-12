---
title: "Logitech internet navigator loses internet keys in intrepid"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by wgandhi on 2008-11-08
Long time ubuntu user upgraded to intrepid. The multimedia keyboard is not working as well as before. The media keys work, volume keys work but "Community","iTouch","Shopping" etc do not work on intrepid (previously I was able to remap these to something useful).

The evtest /dev/input/event3 does show the key code being mapped upto 495.
Relevant output:
    Event code 256 (Btn0)
    Event code 257 (Btn1)
    Event code 258 (Btn2)
    Event code 259 (Btn3)
    Event code 260 (Btn4)
    Event code 261 (Btn5)

There are no new messages in dmesg.

The Xorg.0.log has these messages:
(WW) Logitech Logitech USB Keyboard: unable to handle keycode 260
(WW) Logitech Logitech USB Keyboard: unable to handle keycode 257
(WW) Logitech Logitech USB Keyboard: unable to handle keycode 256
(WW) Logitech Logitech USB Keyboard: unable to handle keycode 259
(WW) Logitech Logitech USB Keyboard: unable to handle keycode 258

Hal detects 2 keyboard devices at event2/3. However, the max keymap detected is only upto 255.

My guess is that there are not enough bits in the X keycode. Any help in mapping the keys to lower keycode will be appreciated. How do I get the scancode of the extra keys? It does not show up in the console.
-Wish

---

