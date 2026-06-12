---
title: "[SOLVED] Can't get 2finger scrolling or gsynaptic to work"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by qubit67 on 2008-10-25
I have     vert/horiz twofingerscrolling set to 1 in my  /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi, but it's not working. When I try to open gsynaptic, the 'SHMConfig' 'true' error pop's up.

 When I run        xinput list-props "SynPS/2 Synaptics TouchPad"
i get:
```

Device 'SynPS/2 Synaptics TouchPad':
	Device Enabled:		1
	Synaptics Edges:		1632, 5312, 1575, 4281
	Synaptics Finger:		25, 30, 256
	Synaptics Tap Time:		180
	Synaptics Tap Move:		220
	Synaptics Tap Durations:		180, 180, 100
	Synaptics Tap FastTap:		0
	Synaptics Middle Button Timeout:		75
	Synaptics Two-Finger Pressure:		257
	Synaptics Scrolling Distance:		100, 121
	Synaptics Edge Scrolling:		1, 0, 0
	Synaptics Two-Finger Scrolling:		0, 0
	Synaptics Edge Motion Pressure:		30, 160
	Synaptics Edge Motion Speed:		1, 400
	Synaptics Edge Motion Always:		0
	Synaptics Button Scrolling:		1, 1
	Synaptics Button Scrolling Repeat:		1, 1
	Synaptics Button Scrolling Time:		100
	Synaptics Off:		2
	Synaptics Guestmouse Off:		0
	Synaptics Locked Drags:		0
	Synaptics Locked Drags Timeout:		5000
	Synaptics Tap Action:		2, 3, 0, 0, 1, 2, 3
	Synaptics Click Action:		1, 1, 1
	Synaptics Circular Scrolling:		0
	Synaptics Circular Scrolling Trigger:		0
	Synaptics Circular Pad:		0
	Synaptics Palm Detection:		1
	Synaptics Palm Dimensions:		10, 200
	Synaptics Pressure Motion:		30, 160
	Synaptics Grab Event Device:		1

```

can anyone help?
oh btw, its a lenovo R61 14" 7732-15M

---

### Post by b3n87 on 2008-10-25
I didnt know you could get two finger scrolling, what website is that from?

---

### Post by qubit67 on 2008-10-25
[http://olalindberg.com/blog/2007/11/14/two-finger-touchpad-scrolling-in-ubuntu/](http://olalindberg.com/blog/2007/11/14/two-finger-touchpad-scrolling-in-ubuntu/)

[http://ubuntuforums.org/showthread.php?t=82850&highlight=osx+touchpad](http://ubuntuforums.org/showthread.php?t=82850&highlight=osx+touchpad)

[http://ubuntuforums.org/showthread.php?t=516798](http://ubuntuforums.org/showthread.php?t=516798)

[http://lucumr.pocoo.org/cogitations/2007/11/13/two-finger-scrolling-on-ubuntu/](http://lucumr.pocoo.org/cogitations/2007/11/13/two-finger-scrolling-on-ubuntu/)

off google, try it for more..

---

### Post by wgrant on 2008-10-25
Those instructions are outdated and won't work on Intrepid. See the top of [the HAL section of the X configuration documentation](https://wiki.ubuntu.com/X/Config#hal) for an example fdi file to do just this. See [the Synaptics touchpad documentation](https://help.ubuntu.com/community/SynapticsTouchpad) for other configuration possibilities (I've recently revamped the page).

---

### Post by qubit67 on 2008-10-25
cheers William, will give it a shot :)

---

### Post by qubit67 on 2008-10-25
Good O Will !!! your a :KS  :):):)  problem solved with your instructions above, and thank you for bringing my trouble shooting afternoon/night to an end... back to studying for uni exams.

---

### Post by wgrant on 2008-10-25
> **qubit67 said:**
> Good O Will !!! your a :KS  :):):)  problem solved with your instructions above, and thank you for bringing my trouble shooting afternoon/night to an end... back to studying for uni exams.

Great to hear! Hmmm, I should really be studying too, but we release in 6 days...

---

### Post by qubit67 on 2008-10-25
I know, you guys are doing such a great job, freaking everyone is using Ubuntu nowdays. I remember ordering version 1 cd over the net ~ 5 years ago. It took about 3 months to get shipped to me and I thought I wasn't going to get it, ah the good ol' days. Good luck for your papers and thanks again

---

