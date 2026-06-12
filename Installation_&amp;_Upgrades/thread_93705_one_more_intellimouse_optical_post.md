---
title: "one more intellimouse optical post"
date: 2005-11-22
forum: Installation &amp; Upgrades
---

### Post by TheAnonymousx on 2005-11-22
So I'm using two mice on two different linux systems. The first moues that I'm using is the microsoft intellimouse optical, and as everyone else has tried, I'm trying to get the back and forth buttons to work. I have installed imwheel and edited the file, and run the command, but nothing changed. So, for those of you that GOT the back and forth buttons working on your intellimouse, what are the steps you took, or what does your imwheel file look like (I can't even FIND the Xfree86-config4 fiile I'm supposed to edit first).
The second mouse is a logitech mx1000 laser mouse, but I'll cross that bridge when I come to it (different system).
Thankx for the help guys.

---

### Post by Maverick911 on 2005-11-22
The file you want to edit is /etc/X11/xorg.conf. I would suggest backing it up first. I messed it up a couple of times and couldn't start X.
```
cd /etc/X11
```
Make a backup:
```
cp xorg.conf xorg.conf.bak
```
Edit the file:
```
sudo gedit xorg.conf
```
I've got a wireless Intellimouse 2.0. I got the forward/back buttons to work in Firefox by just editing the "InputDevice section to look like this:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"		"9"
	Option		"Emulate3Buttons"	"false"
	Option		"ZAxisMapping"		"4 5"
EndSection
```
I changed "Protocol" from IBMPS/2 to ExplorerPS/2
I added "Buttons" "9"
I chaged "Emulate3Buttons" from true to false.

This worked for Firefox. I only needed imwheel if I wanted the forward/back buttons to work in Konquerer and Nautilas.

Hope this helps.

---

### Post by TheAnonymousx on 2005-11-28
Kewl, I made the changes but can't restart X now since, well I'm using the machine. I'll restart over lunch and see how things go.
Thankx

---

