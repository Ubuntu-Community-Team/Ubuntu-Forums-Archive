---
title: "ATI - Gnome, I've more problem than usual :D"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by 3n1gm4 on 2008-03-07
Hi all.

I upgraded to 7.10 then I installed envy to install ATI drivers (i've an ATI 9600 Radeon), this caused (after i restarted X) a change of screen resolution BUT there is no direct rendering.

I menaged a bit, google, this forum and so on, maybe I did something wrong... Now I've an other problem too!

- All graphics things are SLOW, when i move a window i see all the pixel moving almost one by one...

- If i run glxgears the screen get orange and all I see is the mouse (i can move it)... It lasts a bit, then X restarts by itself.

- If I login using the Failsafe Gnome Session all things are faster, i cannot launch glxgears/glxinfo


I think that's there are more than one thing that doesn't work... How and what can I resolve? Do you need more information?
Thank you for any reply :)

---

### Post by uberlube on 2008-03-07
Try going into the restricted driver manager and disableing the ati driver. Then se envy to uninstall the driver, then reinstall. If the problem persists, go to the ATI website and try to find the specific driver for your card and install that. Then if the problem still persists, I suggest going into the RDM again and disabling the driver, this time leaving it off. Also at this point consider getting an nvidia :lolflag:

---

### Post by 3n1gm4 on 2008-03-08
Wow. Now I've a decent screen resolution, 2D apps run at "normal speed", but there is no direct rerendering and:


```
enigma@enibuntu:~$ fglrxinfo 
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)

```

To get  direct rendering enabled i should have ATI as vendor here, right? I Can' do that, i searched (google, and in this forum) but i didn't find out how to change this :\

PS: Of course the next video card will be nvidia, and not only for this problem!

---

