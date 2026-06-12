---
title: "Karmic Alpha 4 GDM broke"
date: 2009-08-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Digital Hick on 2009-08-14
I would really appreciate some help.

I have a Compaq CQ60.
I tried to run the liveCD of Ubuntu 9.10 Alpha 4 (32-bit).

The CD spins up and it gets past the splash but then crashes when GDM tries to start.  The screen will flash about five times and then it dumps me at a CLI.  :( It says to check the Xorg.0.log.  In there is says something like this.

```

WW        GeForce 8200M G  ignored

EE        open /dev/fb0:  No such file or directory
No devices detected
Fatal Server Error
No Screens found

```

The liveCD works on my desktop but not my laptop.  So I know the disk isn't corrupted.  I have 9.04 installed on my laptop and it runs fine.  Knock on wood.  What is going on with gdm?  The menu option brings up this tiny little thing when I get it working on my desktop.  What happened to the old one?

I know they are changing the boot loader and moving away from hal, but this makes any kind of experimenting rather hard.

Thanks in advance for any help.

---

### Post by Digital Hick on 2009-08-14
Shameless bump:)

---

### Post by amano on 2009-08-14
Most of us will not have a possibility to check because they have a different laptop. 

Would you mind filing a bug on launchpad?

---

### Post by bubba_169 on 2009-08-14
Already filed I think. I have the same laptop and am having the same problem and this bug seems to describe it pretty well. I think its to do with the graphics drivers for nvidia.

Launchpad url: [https://bugs.launchpad.net/bugs/404577]("https://bugs.launchpad.net/bugs/404577")

---

