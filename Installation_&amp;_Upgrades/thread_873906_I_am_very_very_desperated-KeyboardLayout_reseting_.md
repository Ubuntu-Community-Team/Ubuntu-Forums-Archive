---
title: "I am very very desperated-KeyboardLayout reseting to default"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2008-07-29
I have really used lots of times but can not find  a solution
no matter what I do my keyboard always setback to default us i am using danish keyboard.

---

### Post by pytheas22 on 2008-07-29
Did you try setting it using the utility at System>Preferences>Keyboard (not sure what it's called in your language; I can provide a screenshot if you need it)?

If that still doesn't work, try editing your xorg.conf file:

```
sudo gedit /etc/X11/xorg.conf
```

and find the section for your keyboard.  Change the "Xkblayout" line to Danish.  I am not sure what the name is for the Danish layout; below is my keyboard configured for United States: 

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	**Option		"XkbLayout"	"us"**
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection
```

You would want to change "us" to whatever you need (probably "dn" or "dm," but those are just guesses), then log out of your session and back in and hopefully you will have the keyboard layout you want.

---

