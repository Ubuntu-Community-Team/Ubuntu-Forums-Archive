---
title: "Help! Mouse doesn't work properly since upgrade..."
date: 2005-04-15
forum: Installation &amp; Upgrades
---

### Post by Kokosnuss on 2005-04-15
Help! I'm becoming really desperate because my mouse doesn't work properly since I upgraded from Warty by reinstalling Ubuntu. In Warty, everthing went fine with exactly the same hardware.

The problem is that the mouse is "jumping" very often in unexpected situations (every ten seconds average). Some times even clicks are "generated" so that windows are opened or closed and other undesired actions... During this time, the whole Desktop is blocked and even music or movies stop playing. Unfortunately, I haven't got the knowledge to solve the problem myself. Some similar topics in this forum point to xorg.conf, but I don't really know what to edit there. Maybe my hardware is especially difficult, because I've got a Dell Inspiron 8100 with an internal and an external mouse (Logitech, two buttons, one wheel, nothing special) and a touchpad. As I said before, everything worked perfektly in Warty. My xorg.conf looks like this:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"auto"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option		"HorizScrollDelta"	"0"
EndSection
```
I already changed "protocol" to "auto" and tried "/dev/input/mouse0", but it didn't help.

I have the suspicion, that the problem sometimes also occurs when typing, so here's the "keyboard" section:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
	Option		"XkbOptions"	"nodeadkeys"
EndSection
```

Well, I'm hoping that anyone can help me, because working with Ubuntu isn't especially funny with this nasty little problem, but I'd love to stay faithful to this great OS...

Thanks in advance,
Felix

---

### Post by kassetra on 2005-04-16
[QUOTE=Kokosnuss]Help! I'm becoming really desperate because my mouse doesn't work properly since I upgraded from Warty by reinstalling Ubuntu. In Warty, everthing went fine with exactly the same hardware.

The problem is that the mouse is "jumping" very often in unexpected situations (every ten seconds average). Some times even clicks are "generated" so that windows are opened or closed and other undesired actions... During this time, the whole Desktop is blocked and even music or movies stop playing. [/QUOTE]

Question for you... are you using a KVM switch?

---

### Post by Kokosnuss on 2005-04-17
No, I don't use a KVM switch. It's all 100% normal hardware and it worked perfectly in warty. What can I do?

I've already been trying this:

-booting with another external mouse
-booting with no external mouse
-setting "noapic" and "nolapic" parameters in grub
-reinstalling the system

Unfortunately nothing did help...  :???: 

So what could I do else?

---

### Post by Kokosnuss on 2005-04-24
I'm wondering whether this might be a solution:

-downgrading to Warty (reinstall)
then
-updating to Hoary with Synaptic

Maybe there is only a configuration problem and Warty, where everything worked fine, can solve it.

What do you think?

---

### Post by Tehanu on 2005-05-01
Hi! 

I'm also having this problem. I'm currently running a Dell C600 Latitude, and, while my mouse(touchpad) doesn't generate clicks, it does jump all over the place, and is sluggish to response. I've tried manipuating the xorg.conf, like I did for Warty, but it doesn't help the problem...

If anyone knows how to fix this, I know that Kokosnuss and myself would great appreciate it.

Thanks guys. :)

---

### Post by Kokosnuss on 2005-05-15
Well, reinstalling Warty and then upgrading to Hoary doesn't help either:

In Warty, again, I had no problems with the mouse, but when I upgraded, the problems came back.

So what can I do? Working all the time with a jumping mouse really isn't too funny...

---

### Post by samba on 2005-08-25
Hi all,

I have the same problem on my Dell Inspiron 8100. This is very annoying, and is completely new, at least for me. Not only my mouse jumps every 10 seconds or so, but if the music is playing it jumps as well, and the keyboard freezes as well for a short time. So it seems that something in general freezes every 10 seconds or so.

It wasn't happening before, say 3 weeks ago. All I did since then, apart usual upgrades, is the following; I used a different external mouse for a few days. But now I'm back with the external USB mouse I've always been using, and it still jumps.

So it's either related to this change of mouse (which is unlikely), or to one of the recent upgrades. But I have no idea which package is problematic... I think I upgraded the kernel in one of the recent upgrades; I'm now using the 2.6.10-5-386.

Has anyone got any idea what package is creating this problem? Is it related to X? or the kernel? or ...? is this a known bug?

Thank you very much,

vince :-)

---

