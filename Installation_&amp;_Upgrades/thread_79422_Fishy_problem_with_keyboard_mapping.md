---
title: "Fishy problem with keyboard mapping"
date: 2005-10-20
forum: Installation &amp; Upgrades
---

### Post by ender on 2005-10-20
Hello guys.

I just upgraded to Breezy using Synaptic a few days ago and I noticed that I have a very strange problem with my keyboard mapping. It's missing the "left" and "right" arrow keys. It only happens in Gnome and no matter what I do to fix it the problem reappears the next time I log in. :confused: If anybody has any suggestions I'd be more than happy to try them out cause changing the keyboard mapping every time I log in has become quite a nuisance.

Ideas tried so far : 
1. Change mapping to US international using Gnome's preferences - works only for 1 session (the new mapping I add does not go away but it somehow becomes corrupt in the process)
2. Editing Xorg.conf - it seems to be ok; my keyboard does have exactly 104 keys (I counted them... just to make sure :p ) and it is a common PS2 keyboard without fancy hot-keys and stuff

Xorg.conf relevant part here :

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

```

---

### Post by ender on 2005-12-27
I don't know how I fixed my problem but I managed to do it :p. Not now, mind you, but a long time ago. Unfortunately I never could understand what I did different and why my keyboard mapping started to work properly. :???: That's why I never posted a solution here for other people to see.

Anyway, I've been having the same kind of problems again, this time with a clean install of Breezy from the shipped CDs. This time my 'space' and 'p' keys didn't work. While trying to fix the problem I actually managed to kill my 'b' and 'n' keys as well. :mad: Searching the forums, I found many people with similar problems and all sorts of solutions that didn't work for me. What I think solved my problem in the end was running the following command at every session start:
```
setxkbmap -layout 'us' -model pc104 
```
I'm not sure if this is truly my fix (and it's definitely not similar to anything I did the first time) but it seems to be working for now. 

Another thing that I have noticed is that new users that I create have correct keyboard mappings. So a stupid 'fix' would be to simply abandon the problematic account and switch to a new one. Stupid bug.. stupid solution. :rolleyes:

---

