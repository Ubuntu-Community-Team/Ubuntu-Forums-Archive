---
title: "Usb Hard Drive"
date: 2007-04-01
forum: Installation &amp; Upgrades
---

### Post by jamissell on 2007-04-01
well if u have a 149gb USB WD external hard drive can i install ubuntu on it and still have all my stuff on my main comps internal HD with windows on it and be able to boot up on ether system

---

### Post by eentonig on 2007-04-01
Yes, 
I'm running ubuntu on my companies laptop and wasn't in the position to repartition the internal HD (no space available, not allowed to).

I advice to use the 'alternate install' CD.
One thing to pay attention to when installing, is to make sure that you select the correct HD to install files and grub on. 
Basically, during install. Install grub on
> root (hd1,0)
And after the install, when you reboot it will fail and you have to alter the grub menu.
> root (hd0,0)

Seems dumb, but it's necessary.

When I boot my laptop and I have the USB HD attached, I get the grub menu and the choice to boot Ubuntu or windows. If I boot without USB HD, it just boots into windows.


Look on the forum or search for 'external HD install', there's a very good howto I used to get it working.

---

### Post by jamissell on 2007-04-01
OK thanks so much this will be great

---

### Post by jamissell on 2007-04-01
well 1 more thing what is 'alternate install' CD.

---

### Post by jamissell on 2007-04-01
ok im a big noob at this how do i burn it or can i mount it on poweriso or somthing. is there any thing i need to do to get it to install right so i will work with both o/s.

---

