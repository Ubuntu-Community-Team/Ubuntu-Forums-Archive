---
title: "Middle-click issues"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by chrisamiller on 2009-04-02
After upgrading from Intrepid, clicking the right and left buttons together no longer registers as a middle-click. Several versions ago, I would have just added this line to my xorg.conf, under the mouse section

```
Option  "Emulate3Buttons" "False"
```

However, in recent versions, the mouse sections are no longer hosted in xorg.conf, with a message stating that "HAL is now used".

Can anyone tell me how to enable Emulate3Buttons, so that when I click the left and right buttons together, it emulates a middle click (and I can go back to pasting from muscle-memory)
-----------------------------------------------------

Naturally, right after I posted this, I found a workaround here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/54191/comments/12](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-mouse/+bug/54191/comments/12)

Briefly:

1) run "cat /proc/bus/input/devices", and find the line giving the name of your mouse.  In my case, this was:  

N: Name="Logitech Optical USB Mouse"

2) create a file:  /etc/hal/fdi/policy/mouse-3button.fdi

3) in that file, place the following:
```
<match key="info.product" string="Logitech Optical USB Mouse">
 <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
</match>
```

Replace "Logitech Optical USB Mouse" with your own identifier from step 1.  

4) Unplug/replug your mouse if it's USB.  PS/2 mice may require a restart.


Hope this helps someone else in the future.

---

