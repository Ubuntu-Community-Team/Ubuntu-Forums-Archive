---
title: "Old System"
date: 2006-02-22
forum: Installation &amp; Upgrades
---

### Post by bradhawk08 on 2006-02-22
So I just got an old dinosaur from the attic.  It is a Compaq Presario 4640.  It has a P2 266Mhz with i believe either 16 or 32MB of RAM and a 4GB HD. I ran the installation on it and it ran completely through.  Now it is doing the same thing that my other computer is doing that i tried to load Ubuntu on.  There is no graphical interface.  The difference is is that this computer doesn't tell me there is an error loading the X Window System it just goes into a terminal. I know that the memory is low, but if i upgrade that should the system work with graphical interface and all?

---

### Post by T31 on 2006-02-22
mmm I dont know but maybe you could try to install something lighter than gdm+gnome if the issue is the mem, try doing this in a console

sudo aptitude install icewm xdm rox-filer

;)

update: use icewm-experimental if you want fonts with antialiasing and some graphics eye-candy extras here you have a [screenshot]("http://photos1.blogger.com/blogger/1987/995/1600/icewmdapperf4.png") from my desktop

and if you wanna go still lighter icewm, windows manager   dfm, icons on desktop     xfe, file manager

---

