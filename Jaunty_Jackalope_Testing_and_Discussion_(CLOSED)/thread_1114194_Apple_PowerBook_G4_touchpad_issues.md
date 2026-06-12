---
title: "Apple PowerBook G4 touchpad issues"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by bodzasfanta on 2009-04-02
I've just installed the Jaunty beta on my PowerBook G4 from [the Live CD]("http://cdimage.ubuntu.com/ports/releases/9.04/beta/").

Everything works perfectly except the touchpad. It's absolutely non usable... I guess that's beacuse of this Apple touchpads are not Synaptic standards. 

Are there any solution for this problem?

Here is my xorg.conf (if it helps):

```
Section "Device"
	Identifier	"Configured Video Device"
	BusID		"PCI:0:16:0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

*I guess my videocard (Nvidia FX GO5200) also doesn't work well.*

And sorry for my english

---

### Post by ditsch on 2009-04-02
What do you mean with unusable? Touchpads should be configured with HAL anyway, not in xorg.conf. Right and middle click have to be activated in /etc/default/mouseemu manually.

---

### Post by bodzasfanta on 2009-04-03
No it's not the mouse, it's the touchpad.

I mean it doesn't work as I want... It works, but it's unusable. Jerky, imprecise, not enough sensitive...

---

