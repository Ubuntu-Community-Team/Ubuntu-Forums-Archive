---
title: "Projectors with Intrepid..."
date: 2008-10-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mariner09 on 2008-10-01
I have a Lenovo T61 and with Hardy, I could launch the Screen Resolution tool under Preferences and select 1024x768 and click on the mirror option and all would be well.  I tried this tonight with Intrepid and the mirror option would never stick.  I also tried 640x480, 800x600 as well as 1024x768.

Here's my video chipset:

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

And of course, the default xorg.conf:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Any recommendations would be appreciated...

---

### Post by nanog on 2008-10-01
Try switching to a resolution compatible with your projector -- say 1024x768 -- and using the CRT/LCD switch (kernel-based mirroring!). Also, please post a bug -- I can't because all my hardware is nvidia and not properly supported by the new xorg.

---

### Post by wilsong on 2008-10-01
What happens when you click Detect Displays? Have you rebooted recently. Just curious about little things, anything you have tried so far?

---

### Post by mariner09 on 2008-10-01
I clicked on the detect displays numerous times.

I rebooted twice with the projector connected.

I could change all my resolutions on the LCD, but nothing would go out the video port.

Nanog, what is this CRT/LCD switch?  I tried the Fn+F7 key combo which is the traditional hardware method for alternating output.

I tried 1024x768, 800x600 and 640x480...

---

### Post by wilsong on 2008-10-01
I have always used Fn-F8 for switching output. That's how all the Dell's are? (used to work at Dell for 2 years.. ) try Fn-F8?

---

### Post by nanog on 2008-10-01
Its different on every laptop -- its the switch that mirrors output to the vga port. If its supported by the kernel it should work regardless of xrandr/xorg. The key is to switch to a resolution that your projector supports. Since intel is open source your problems are fixable so please, please file a bug. (I may but another laptop with intel graphics if they fix the projector issue.)

---

### Post by wilsong on 2008-10-01
Instead of using a monitor do you have a regular CRT/LCD you can try to see if it will switch to an 800x600 or other res on an external LCD.  

I take it this projector has been working well with other devices? 

Ill keep trying to think of other ideas.. and post, keep trying!

---

### Post by mariner09 on 2008-10-01
I have a regular CRT in the garage I worked out my original xrandr script with gutsy.  Hardy made it so easy I was spoiled.  The projector worked on a Windows laptop and I never got to test it with my FC9 load as I wiped it in favor of II last night.  Oops...

The Lenovo Thinkpads rely on an open source project for their function keys.  With every release, more of them just work in Ubuntu, but the CRT/LCD switch is one of the last ones out there not working yet.

---

### Post by wilsong on 2008-10-01
I think maybe it could be just how early it is into Intrepid, sure its linux, but its so young.. ive pulled my hair out a few times since i upgraded, but i just keep trying to work through it.. i think as time goes by the stability will work itself out, if everyone just keeps participating and contributing their testing and questioning and troubleshooting in the forums and IRC.. try coming into the #ubuntu+1 channel and seeing if anyone has an idea.. or maybe upgrade when the beta is released in the next day or two and see if it helps?

---

### Post by mariner09 on 2008-10-08
I added a virtual statement to my xorg.conf and it boots so that's a good sign.  I had to try 3 different iterations before it would come up.  I'll try the projector again with that and we'll see what we get...

---

