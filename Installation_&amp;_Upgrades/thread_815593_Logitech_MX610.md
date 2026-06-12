---
title: "Logitech MX610"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by melenor on 2008-06-01
I have a Logitech MX610 mouse and i have found several guides and i am unsure which to follow or which will do what i need
	I want all the buttons to work include the horizantel scroll, and it would be nice to get the IM amd e-mail buttons to work and light up
	Also this would be nice if it could work, if it could take 2 mouse button presses and make it into a keyboard combination like ( left click + right click = Ctrl+Alt+Delete)
	P.S. these are many different guides i found about the Logitech MX610 and i have no idea which one to follow.
		[https://help.ubuntu.com/community/Logitech_MX610](https://help.ubuntu.com/community/Logitech_MX610)
		[http://ubuntuforums.org/showthread.php?t=332256](http://ubuntuforums.org/showthread.php?t=332256)
		[http://ubuntuforums.org/showthread.php?t=65471](http://ubuntuforums.org/showthread.php?t=65471)
		[http://ubuntuforums.org/showthread.php?t=168538](http://ubuntuforums.org/showthread.php?t=168538)
		[http://ubuntuforums.org/showthread.php?t=327131](http://ubuntuforums.org/showthread.php?t=327131)
		[http://www.stuvel.eu/archive/64/tilt-wheel-logitech-mx610](http://www.stuvel.eu/archive/64/tilt-wheel-logitech-mx610)
		[http://ubuntuforums.org/showthread.php?t=455656&highlight=logitech+MX610](http://ubuntuforums.org/showthread.php?t=455656&highlight=logitech+MX610)

	Also in Fedora 9 the horizantel scroll worked automatically.

---

### Post by iaculallad on 2008-06-01
I suggest you use this guide [first]("http://ubuntuforums.org/showthread.php?t=332256") and see how it would work in your Logitech MX610 mouse device.

Probably, you also have to try those other guides you listed on your post and see if it could be configured to your likings.

---

### Post by melenor on 2008-06-01
I noticed that on the first line it says all buttons except horizantal scrolling, but yet it worked automatically in fedora, wouldn't it be easy to see how fedora does it and then just do the same thing for ubuntu?

---

### Post by iaculallad on 2008-06-01
I've done a research on your mouse and it seems that Horizontal Scrolling would not work. Let's wait for other member's responses just in case they had stumbled or came across this problem.

---

### Post by melenor on 2008-06-04
I got the horizontal scroll work,following this guide [http://www.stuvel.eu/archive/64/tilt-wheel-logitech-mx610](http://www.stuvel.eu/archive/64/tilt-wheel-logitech-mx610),  but only in firefox and a side effect is now the back and forward buttons only work in firefox. I was wondering if there was anyway to combine these 2 xorgs to allow all the buttons to work?

The ubuntu one
        Section "InputDevice" 
                Identifier      "MX610_2"
                Driver          "evdev"
                Option          "Name"  "Logitech USB Receiver"         # see 'cat /proc/bus/input/devices'
                Option          "Phys"  "*/input0"                      # this is the mouse part
                Option          "WHEELRelativeAxisButtons" "4 5"        # vertical wheel
                Option          "HWHEELRelativeAxisButtons" "7 6"       # horizontal wheel
        EndSection

The one from the guide
        Section "InputDevice"
                Identifier  "MX610"
                Driver      "evdev"
                Option      "CorePointer"
                Option      "Device"    "/dev/input/event9"
                Option      "ZAxisMapping" "4 5 7 6"
                Option      "Buttons"   "9"
                Option      "Resolution" "800"
        EndSection

thanks.

---

### Post by melenor on 2008-06-08
Since i am getting no help right now, i decided to play around slightly with the commands does anyone know where i can go to get some more information and what each line does, thanks.

---

