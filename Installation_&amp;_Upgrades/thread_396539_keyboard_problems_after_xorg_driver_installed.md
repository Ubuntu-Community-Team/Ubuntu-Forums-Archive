---
title: "keyboard problems after xorg driver installed"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by leopardsanderson on 2007-03-29
Hi there, quite new to linux... I installed ubuntu dapper 6.06 LTS and using it since three days and had been very happy with it!

The only problem that bothers me now is about my keyboard...
I have a laptop with ATI and so, when I installed ubuntu the screen resolution was 1024x768 instead of 1280x800. So I downloaded with synaptic "xorg-driver-fglrx" (7.0.???) and started the configuration process with:
```

 sudo dpkg-reconfigure xserver-xorg

```
The process goes well and finally I got 1280x800 (after configuring manually xorg.conf)
Now we come to the problem: during this configuration I have to set my keyboard...

Here are the settings made during the configuration in /etc/X11/xorg.conf
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"it"
	Option		"XkbVariant"	"nodeadkeys"
	Option		"XkbOptions"	"altwin:meta_win lv3:ralt_switch eurosign:e"
EndSection
```

Now: the problem! THe problem I have is simple: the special caracters like è ò ù @ wich are at the right, near the return button, aren't typed if I press the key. When I hit them nothing happens. Also other symbols like € wich are activated with right Alt or Ctrl+Alt don't work.

I tried then to change some fields in xorg.conf, as layout, options, model, but nothing really changes.

Last: question: I'm using gaim to chat with my msn friends and the "n" doesn't work! Here it works, I can't understand. Maybe the two problems aren't linked...

Bye bye!

Some useful info:
Laptop: Fujitsu-siemens amilo si1848 dual core with Ati mobility x1300
ubuntu 6.06 dapper. Language: english, keyboard layout: ita

---

### Post by openmtl on 2007-06-01
The Option "XkbVariant" "nodeadkeys" is what would **_stop _**certain keyboards creating those special characters. Thus I would try to blank out that option. Also check in GNOME Preferences -> Keyboard that the right keyboard layout is set. Recently with upgrades within 6.10 and from 6.10->7.04 on gb keyboards I've had some fun quirks with that nodeadkey option.  On a GB (UK) keyboard what happens if you have deadkeys set is that you have to hit certain keys twice to get the character (and the reverse on the deadkey keyboards looks like you lose access to the special characters as you have described).

---

