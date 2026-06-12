---
title: "can't get breezy running with my dell 2405fpw"
date: 2005-11-15
forum: Installation &amp; Upgrades
---

### Post by yellowband on 2005-11-15
hi eveybody

as the title says, i can't seem to get up and running with with either ubuntu 5.10 live or ubuntu 5.04 on my hard drive, now that i'm using a dell 2405fpw.  When i boot from the live cd, all goes well until gname is about to load, then the screen goes black and says "d-sub, unable to display this mode", and i'm stuck from there. I'm assuming this may be a resolution thing, but how do i get going? and how do i fix this so it doesn't keep happening?

thanks

---

### Post by yellowband on 2005-11-15
no ideas?

should i get in contact with the developers or something?

---

### Post by tmanops05 on 2005-11-16
<<Cricket Sound>> Chirp Chirp

---

### Post by krackato on 2006-06-03
I'm having the exact same problem with Ubuntu 6.06.

---

### Post by radinator on 2006-06-03
I got it working with my 2405FPW without a problem relating to the monitor.

I did have a problem with my NVIDIA graphics card, which I had to search this forum to find the answer to.  I suspect the problem is your graphics card setup and your monitor are not compatable in their settings currently.

Perhaps a search on how to reinstall (using the console) your graphics driver?

Ray

---

### Post by MetalMusicAddict on 2006-06-03
I have a nVidia 6800 OC working very well with my 2405FPW. Im glad to help with any problems.

krackato. If your having the same problem as the OP my guess is that you need to install the proprietary driver. **nvidia-glx** It doesnt come in a base install or live CD.

---

### Post by tseliot on 2006-06-03
you should use the alternat-install disk of Ubuntu and install it.

Then (after the installation) the xserver should crash.

You can use this quick fix:

1) Boot in Recovery mode (you can select it from the GRUB menu almost as soon as you turn your computer.

In this way the xserver won't be started.

2) Reconfigure the Xserver:

```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver when it asks you. If you don't know the answer to the other questions just press ENTER to use the default answer.

3) Restart your computer:
```
reboot
```

Boot as usual and you should be able to see the graphical interface (the desktop enviroment).

If that doesn't work, repeat the process I described above but this time set the driver to "vga".


P.S. After you're able to use the Desktop Environment I suggest you to install the right drivers for your graphic card in order to make the most of it.

---

