---
title: "Problem before installing"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by DreamerHxC on 2006-11-22
Hello everybody:
I have tried to install Ubuntu booting from Live CD and double click "Install" but I don't even get to here. Live CD desktop gets freezed just before show himself up. I can restart X (ctl+alt+backspace) to go back to the logon screen and when I log with user "ubuntu" (the only user) it happens the same: freezed.
I tried to install on text mode with the alternative CD, but when I install it and I log with my user, it's the same than with live cd: freezed again. ¿Any idea?
My PC:
HDA NTFS Windows XP
HDB Ubuntu Linux 6.10 Edgy Eft
And another USB HD
AMD Athlon XP 2000+ with NForce2 motherboard and ATI 9550 graphic card.

Thank you all for your help.

---

### Post by ReaderRat on 2006-11-22
> AMD Athlon XP 2000+ with NForce2 motherboard and **ATI 9550 graphic card.**
ATI Video - Install the drivers - Edgy - Radeon 9550
          **[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Installing_the_driver](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#Installing_the_driver)**

---

### Post by DreamerHxC on 2006-11-23
Thank you but. Im gonna try.

---

### Post by DreamerHxC on 2006-11-23
ok I do everything when when I do "fglrxinfo" I get:

```
fglrxinfo
Xlib: extension "XFree86-DRI" missing on display ":0.0".
display: 0.0 screen:0
OpenGL vendor string: Mesa Project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)
```


insted of what guide says:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.6011 (8.28.8)
```

And it's still happing the same with desktop

---

### Post by DreamerHxC on 2006-11-23
great! I rebooted and it's working but will I have to install original ATI drivers or something like that? Will I have any problems with graphic card?
EDITED: I selected another screen resolution and configured my mouse, rebooted and I'ts not working again :(

---

### Post by DreamerHxC on 2006-11-23
Ok, I do what the wiki says but when I reboot, it's freezed again and I have to do what the wiki says again...
And I have noticed that when I do what the wiki says for installing the driver and I reboot, before showing the logon screen, I can hear a sound, but the next time I reboot, I don't hear the sound.

---

### Post by ReaderRat on 2006-11-24
Sound Solutions - Comprehensive Guide
       **[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)**

---

### Post by DreamerHxC on 2006-11-24
But is it the solution for the sound? Because when I can login in graphic mode the sounds works great

---

### Post by ReaderRat on 2006-11-24
If your video is okay now, it might be best to post a new thread about the sound problem.

---

### Post by ReaderRat on 2006-11-24
You may try: GoTo "Tags" (at the top of the page), click on it, and type in "sound" (without the quotes)....you may find a solution there.
Also, if your video problem is "fixed", check "Tags" first, then post your sound problem in a new thread, if you don't find a solution in Tags.

---

