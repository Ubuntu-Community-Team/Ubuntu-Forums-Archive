---
title: "Laptop Install Problems"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by Diki on 2008-04-16
I am trying to install Ubuntu on my laptop and have run into a bit of a snag.
I've tried this on Ubuntu 8.04/7.10 and both produce the same result. Everything starts to boot up normally (into the Live session) and then it gets to this:

```
* Starting deferred execution     [OK]
* Starting periodic command scheduler crond     [OK]
* Checking battery state..     [OK]
* Running local boot scripts (/etc/rc.local)     [OK]
```

The screen flashes a couple times and it stops there. I am able to type in text but nothing happens when I do.
I tried 6.06 once and it screwed up and bitched about X Server not starting. I'm assuming that 7.10/8.04 are freezing up in the same place.

This is my laptop: [http://ca.lge.com/en/products/model/detail/r405expressdualseries_r405a.cb01a9.jhtml](http://ca.lge.com/en/products/model/detail/r405expressdualseries_r405a.cb01a9.jhtml)

I'm not really sure what to do; any help will be appreciated.

---

### Post by kaginken on 2008-04-16
I've seen this before - in my case, it actually WAS booting up - I could hear it, and the hard drive light was active.  Is this the case with your computer?  Listen for the Ubuntu theme sound and try logging in.  I also believe that I did finally boot up (like 15 minutes later) and I was able to log in and fix it.  I'd have to dig around to see what the fix was, but try just waiting a very long time, see if it does actually start.

Hope this helps!
:guitar:

---

### Post by Ben Miller-Jacobson on 2008-04-16
When it goes to that blank screen, press ctrl-alt-f1. hopefully you will see normal boot up text and it will work. I don't know why this works, but it helps on my dad's old laptop.

Good luck.

---Ben Miller-Jacobson

---

### Post by Diki on 2008-04-16
> **kaginken said:**
> I've seen this before - in my case, it actually WAS booting up - I could hear it, and the hard drive light was active.  Is this the case with your computer?  Listen for the Ubuntu theme sound and try logging in.  I also believe that I did finally boot up (like 15 minutes later) and I was able to log in and fix it.  I'd have to dig around to see what the fix was, but try just waiting a very long time, see if it does actually start.

Hope this helps!
:guitar:

I have tried waiting; nothing happens.

[quote=Ben Miller]When it goes to that blank screen, press ctrl-alt-f1. hopefully you will see normal boot up text and it will work. I don't know why this works, but it helps on my dad's old laptop.

Good luck.[/quote]

That opened up a command prompt.

---

### Post by Partyboi2 on 2008-04-16
when you see 
> * Running local boot scripts (/etc/rc.local)     [OK]
Press ctrl+Alt+F2 to get to a terminal, then reconfigure the xserver
```
sudo dpkg-reconfigure xserver-xorg
``` choosing vesa for the driver. Once you have finished answering all the questions type
```
startx
```hopefully this will give you a working desktop where you can work on getting the correct driver installed.

---

### Post by Diki on 2008-04-16
> **Partyboi2 said:**
> when you see 

Press ctrl+Alt+F2 to get to a terminal, then reconfigure the xserver
```
sudo dpkg-reconfigure xserver-xorg
``` choosing vesa for the driver. Once you have finished answering all the questions type
```
startx
```hopefully this will give you a working desktop where you can work on getting the correct driver installed.

Tried that and got this:

[b]Fatal server error:
no screens found

waiting for X server to begin accepting connections
giving up.
xinit: Connection reset by peer (errno 104): unable to connect to X server
xinit: No such process (errno 3): Server error.[/b]

---

### Post by Partyboi2 on 2008-04-16
What happens when you try installing in safe graphics mode(2nd option ubuntu main menu)?

---

### Post by Diki on 2008-04-16
> **Partyboi2 said:**
> What happens when you try installing in safe graphics mode(2nd option ubuntu main menu)?

The same thing.

---

### Post by Partyboi2 on 2008-04-16
Have you tried installing with the[ alternate cd]("http://releases.ubuntu.com/7.10/")?

---

### Post by Diki on 2008-04-16
> **Partyboi2 said:**
> Have you tried installing with the[ alternate cd]("http://releases.ubuntu.com/7.10/")?

If that is the text-based installer: yes. It installed but would not boot into the OS (it either got stuck in the same place or during the boot screen with the orange bar scrolling left/right; I cannot remember which).

---

### Post by Partyboi2 on 2008-04-16
You could try installing the proprietary driver for the card. I would suggest reinstalling ubuntu using the alternate cd (text installer) then boot into recovery mode (you might need to press esc when grub is loading to get this option, I can't remember at the moment) once you have got to the prompt in recovery mode download the driver
```
wget https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/64bit/ati-driver-installer-8-3-x86.x86_64.run
``` after you have downloaded the driver start the installer
```
sh ati-driver-installer-8-3-x86.x86_64.run
```follow it through the install, then after it has installed choose your resolution
```
aticonfig --resolution=0,[COLOR=Black]1280x800[/COLOR]
``` then type ```
startx
```

---

### Post by Diki on 2008-04-16
I tried to download it and just got **Resolving [blah]... failed: Name or service not known.**.
I downloaded the driver and uploaded it elsewhere to ensure that I was typing it in correctly and nothing changed.

---

