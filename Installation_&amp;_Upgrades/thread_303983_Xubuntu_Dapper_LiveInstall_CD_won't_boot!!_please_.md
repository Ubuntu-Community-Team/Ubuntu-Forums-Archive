---
title: "Xubuntu Dapper Live/Install CD won't boot!! please help!"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by jclmusic on 2006-11-21
i ran ubuntu dapper on this same computer before, but i recently put in a new motherboard and cpu, and i had installed xfce on top of ubuntu before, and prefered it, so i decided to install xubuntu.

when i try to boot up the xubuntu dapper live cd, it stops where gdm would usually start up and i just get a "_" (like in a terminal) at the top of the screen, and no response from the keyboard.

---

### Post by renzokuken on 2006-11-21
sounds like a possible grafix problem.

List the full spec of your PC.

And have u tried the alternate install CD?

---

### Post by jclmusic on 2006-11-21
PSU: HIPRO HP-A1365F3
Motherboard: Intel Celeron with HP Pheonix BIOS
CPU: Intel Celeron 900MHz
15Gb IDE hard drive
Fujistu CDRW
Intel 10/100 enet card
Nvidia 180-P002-0000-B01 graphics card

and no, i haven't. do i need to? i tried reconfiguring xorg, but i couldn't get gdm to shut down to do it :-?

---

### Post by renzokuken on 2006-11-21
i would give the alternate  install cd a go if i was you (see [http://releases.ubuntu.com](http://releases.ubuntu.com) for the download)

the alternate CD is not a LiveCD but a semi graphic/text based install CD, its pretty easy, but may work better than the desktop CD

if you want to restart X (and GDM) after reconfiguring your xorg.conf, just press Ctrl + Alt + Backspace


EDIT. when GDM comes up and freezes, are you able to get to another console by pressing Ctrl+Alt+F1/2/3/4/5 etc?

if you can just do ```
 sudo nano /etc/X11/xorg.conf
```

edit your file and go back to your GDM screen, and press the Ctrl+Alt+Backspace to start your X server again

it might be worth selecting the "vesa" driver and seeing what happens

---

### Post by jclmusic on 2006-11-21
> **renzokuken said:**
> i would give the alternate  install cd a go if i was you (see [http://releases.ubuntu.com](http://releases.ubuntu.com) for the download)

the alternate CD is not a LiveCD but a semi graphic/text based install CD, its pretty easy, but may work better than the desktop CD

ok downloading now. is there not a xubuntu one? so i have to use the ubuntu one and replace gnome with xfce manually like before?

> 
EDIT. when GDM comes up and freezes, are you able to get to another console by pressing Ctrl+Alt+F1/2/3/4/5 etc?

nope, no response at all. can't even reboot, so have to use the power button.

---

### Post by renzokuken on 2006-11-21
ok, well give the Alternate CD install a go, and probably best to select the Vesa video driver for now.

the link i gave is obviously for the Ubuntu installation (gnome) but once installed u can easily do

```
sudo apt-get install xubuntu-desktop
``` to get XFCE

let us know how it goes

---

### Post by jclmusic on 2006-11-21
yeah, that's what i did before. no biggie was just curious. i'll let u know how it goes.

---

### Post by jclmusic on 2006-11-21
won't boot either :(

---

### Post by jclmusic on 2006-11-21
i discovered it's the hardware. i've just booted up the live cd on another computer, and it works fine. i think i'll swap the hard drives round to install it, and then have a go at configuring xserver etc to work.

think that'd work?

---

### Post by renzokuken on 2006-11-22
Worth a try yeah, although if it's not a hardrive problem then it might not solve it. 

may sound stupid but have u checked that ALL connections are correctly fitted and not loose in the computer from when u changed ur motherboard.

Occasionally, cables come slightly loose when u've been poking round inside and they just reqire pushing in properly again.

---

### Post by jclmusic on 2006-11-22
i installed it, and it works fine, in fact i'm talking 2 u from it now :)

the problem is, when i put the hard drive back in the other computer, nothing happens. i switch it on, and i don't even get a bios screen. fans and everything is all running, but nothing comes up on screen. 1 step forward, 2 steps back :( !

---

### Post by jclmusic on 2006-11-22
i put the my other hard drive with windows xp installed on it in the other computer and had the same problem, so it must be a hardware issue. :-k

---

### Post by jclmusic on 2006-11-30
i managed to install it on the right computer!!!
for anyone else who might be reading this, i did so using the network install cd.

the thing is, when i start up my new installation, the same thing happens! no x. just a blank screen with a "_" at the top that doesn't respond to any keyboard input. 

how do i get to a terminal from here or anywhere before where i can configure x? would switching drivers get it to work?

---

