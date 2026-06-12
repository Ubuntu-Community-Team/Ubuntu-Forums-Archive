---
title: "install display not completely on the screen... cant install"
date: 2005-12-02
forum: Installation &amp; Upgrades
---

### Post by lleb on 2005-12-02
I had this problem with Debian back when 3.0 first came out, or maybe right before.

when i start the installer about 1-2in is BELOW the bottom of my screen with my laptop.  Edubuntu seems to be suffering the same problem.  Now Debian does not have this problem and has not since before Sarge went stable.

This is really a shame as i have no way of properly installing and thus testing the Edubuntu distro that I am very interested in.

any way to fix this, and no there is nothing i can do to adjust the way the laptop displays its output.  no hooking a monitor up to it does not fix anything.  have tried and no luv.

---

### Post by bwog on 2005-12-02
Does it stay that way when you press enter (which starts the default installation)?

---

### Post by lleb on 2005-12-02
[QUOTE=bwog]Does it stay that way when you press enter (which starts the default installation)?[/QUOTE]

thats when it happens.  so i can not read all of the options for partitions and what not.  the initial screens are fine, i can even read all, or so i think, the data on the F1 and F3 page.

---

### Post by dcstar on 2005-12-02
[QUOTE=lleb]I had this problem with Debian back when 3.0 first came out, or maybe right before.

when i start the installer about 1-2in is BELOW the bottom of my screen with my laptop.  Edubuntu seems to be suffering the same problem.  Now Debian does not have this problem and has not since before Sarge went stable.

This is really a shame as i have no way of properly installing and thus testing the Edubuntu distro that I am very interested in.

any way to fix this, and no there is nothing i can do to adjust the way the laptop displays its output.  no hooking a monitor up to it does not fix anything.  have tried and no luv.[/QUOTE]
A monitor usually has adjustments for screen size to allow for this sort of thing, a laptop is another matter.......

---

### Post by TeeSeeJay on 2005-12-03
I've had this same problem with linux distros on some laptops. I think it has to do with probing for supported modes, the hardware responds with some "virtual" modes that it supports (like a 800x600 native display that supports a 1024x768 "virtual desktop" -- like that.) Since this is text mode we're talking about, though, it's got something to do with the number of supported lines and junk. This problem probably happens after it moves to framebuffer mode, right?

On my laptop I was able to turn off "stretch mode" in the bios, which confined the text mode to a much smaller box centered on the screen, but at least it was present. See if you can find a similar setting on yours.

---

### Post by lleb on 2005-12-03
Ill look tomorrow as ill be at my LUG install fest in the afternoon.  Maybe someone there can help me out with it too.

---

### Post by bwog on 2005-12-03
Please post the solution if you find it. 

(Isnt there a boot option for framebuffer? From the Wiki: 

Note: Some video chipsets have buggy VGA BIOS implementations; they may render text consoles incorrectly, especially when connected to flat-screen displays (including laptop LCDs). Depending on your localization, you may be able to work around this at the LiveCD boot prompt by typing "live debian-installer/framebuffer=false".)

---

### Post by Topsiho on 2005-12-03
I have got the same problem, or a problem like this one, when istalling Ubuntu (Warty, Hedgehog, Breezy, Dapper, and Debian 3.1) on my Promedion (really a Clevo) 2700T notebook. The whole screen is lowered somewhat, so that the bottom lines (about, let's say, 6 lines) are dropped below the physical screen. The two lower ones appear in a small format at the top of the screen.

I know of no way to avoid this, and the installing of Ubuntu on other computers goes nicely without this problem.

It makes answering whether you want to continue with the configuring of partitions a hit or miss affair, which is potentially dangerous of course.

Installing other distro's like Fedora or Mandrake on the 2700T did not give this problem, but there the installing is in a nice(r) graphical screen ....

Topsiho

---

