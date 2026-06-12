---
title: "Can't boot anything except unity (idepadFLEX)"
date: 2014-08-15
forum: Installation &amp; Upgrades
---

### Post by Crimson1988 on 2014-08-15
hello

I have Lenovo idepadFLEX 14'' touchscreen laptop. I would like to try different flavors like KDE, Cinamon (let it be LinuxMINT or whatever). but if I try to boot lets say a KDE or XFCE ubuntu based distro I get stuck at blackscreen and nothing seems to work. only DE that boots with no problems is Unity. anyone knows whats the matter with that? 

when I'm saying "boot" I mean fresh install from flash drive :)


thank you

---

### Post by TheFu on 2014-08-15
So ... trying different DEs does NOT necessitate having a different OS installation. The DE is just a GUI, like any other program.  There is a how-to-geek article about this. [http://www.howtogeek.com/193129/how-to-install-and-use-another-desktop-environment-on-linux/](http://www.howtogeek.com/193129/how-to-install-and-use-another-desktop-environment-on-linux/)

However, some settings between the different DEs are stored in the same files (under $HOME) and may conflict, so it is best to use a different userid (which provides a different $HOME) as you try different DEs. Does this all make sense?

Now that I think about this more, it is probably easier to jsut change the HOME directory in the /etc/passwd file and create a new directory under /home/ for each DE. Maybe not for people unfamiliar with how that works - changing the passwd file AND selecting a different desktop, then remembering to do that every time in the future isn't as easy as just creating a new userid (which will get a new HOME directory automatically).

---

### Post by Crimson1988 on 2014-08-15
yes it makes sense


but I have a slightly different situation. the thing is that I'm trying to make a fresh install of kubuntu, or mint KDE or XFCE and after I select "install" or "try linux" I get a black screen. it feels like my laptop's screen is not supported by DE or something like that (like missing touchscreen driver or smth) the only system that boots is ubuntu with unity

---

### Post by TheFu on 2014-08-15
Ah - the dreaded black screen ... You are not alone: [https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen)

---

