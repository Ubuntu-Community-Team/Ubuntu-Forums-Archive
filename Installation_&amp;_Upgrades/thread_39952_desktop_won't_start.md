---
title: "desktop won't start"
date: 2005-06-07
forum: Installation &amp; Upgrades
---

### Post by inmate on 2005-06-07
hello all,

i've just install ubutu 5.04 from cd on my ibm thinkpad 600 laptop.
the installation went super-smooth, but on booting the first time, the speakers start make a funny clicking sound as soon as it loads the drivers. 
(soundcard is a Crystal 4237B chip, btw).

the real problem however, comes when i try to login - i enter my username and password and then the desktop doesnt load.
the mouse is there but nothing else. just a light brown background colour.

although the mouse moves, the buttons do nothing - nor anything from the keyboard. 
i have to pull the plug to boot againl.

any ideas?

much thanks...

---

### Post by inmate on 2005-06-07
ummm, okay scrap that - it seems to work now just fine.

not to sure what that was, but i think it had something to do with the sound driver.
anyways, this time when i booted there was no clicking noise and when i logged on a pretty little sound played as the desktop loaded.

okay - i must say, i am *very* impressed!

i had previously installed gentoo on here and that was a huge battle - just to get the mouse working, and sound. 
but with ubuntu...it all just works!

nice one, ta!

---

### Post by zAo on 2005-06-07
[QUOTE=inmate]ummm, okay scrap that - it seems to work now just fine.

not to sure what that was, but i think it had something to do with the sound driver.
anyways, this time when i booted there was no clicking noise and when i logged on a pretty little sound played as the desktop loaded.

okay - i must say, i am *very* impressed!

i had previously installed gentoo on here and that was a huge battle - just to get the mouse working, and sound. 
but with ubuntu...it all just works!

nice one, ta![/QUOTE]]
It works now, but what does dmesg say? Make the solution perminent and post it.

Have phun with Ubuntu!

---

### Post by inmate on 2005-06-07
mmm, its seems i spoke too soon!

this problem is intermittant. sometimes when ubuntu boots, the speakers make the strange klicking sounds, and then hangs on login.
othertimes it boots fine and all is well in the world.

i will poke inside dmesg to see what is up and post it into this forum.

hold that thought...

---

### Post by inmate on 2005-06-08
okay, the problem is sorted.

(this should all be under hardware, sorry)

problem rundown: (google, take note)
installing ubuntu 5.04 (hoary) on an IBM Thinkpad 600x - ALSA Sound does not work correctly. 
 > When the login manager appears, the speakers make a funny clicking sound. 
 > When user logs in, the desktop hangs while it is loading (presumably because it should play a pretty sound)

problem solution:
add a kernel parameter to "/boot/grub/menu.lst" , specifically 
pci=noacpi 
(while you're there, you might as well add: acpi=off apm=on)

then "it just works" :D

---

