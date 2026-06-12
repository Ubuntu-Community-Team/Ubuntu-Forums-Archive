---
title: "Sudden Mouse problem Lucid Lynx Kernel 2.31"
date: 2010-02-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by SaikoRonin on 2010-02-16
I have never had a problem using my usb mouse on ubuntu before, suddenly the mouse pointer stopped moving,  I tried unplugging and replugging it in, then I restarted the computer and still nothing,  Then I ran lsusb and it shows its not showing up anymore.

I then tried restarting the computer with an old ps/2 mouse attached and I cant move the pointer but it can click.  

Incidentally I also noticed that the login screen now takes quite some time to show up after i hear the "splash sound" that usually is heard when the login screen appears.

Really odd... What should be my next move?  

Running Lucid Lynx Kernerl 2.31 
I updated to this and had no problems since it was released.

---

### Post by SaikoRonin on 2010-02-16
I have been looking for solutions and I thought it may have something to do with xorg.conf 

I tried sudo dpkg-reconfigure xserver-xorg followed by a reboot, and still nothing,

This strikes me as a usb problem since the usb mouse has the laser working but it does not show up in lsusb, However the fact that the wired mouse isnt working is completely stumping me...

any help guys?  I'd submit an error report but I want to try working it out first.

---

### Post by overdrank on 2010-02-16
Moved to Lucid Lynx Testing and Discussion :)

---

### Post by todak on 2010-02-16
If everything else works, then the next step would be to check your hardware, i.e., try another mouse. ;)

---

### Post by SaikoRonin on 2010-02-17
Well thats why i tried the wired mouse, to eliminate the possibility of the usb mouse being bad or it being a usb problem.

However I ended up reinstalling my swap portion of my hard drive and that solved the issues.  So it was obviously not the mouse.

---

### Post by Yes_It's_Me on 2010-02-17
I've also been experiencing the same issue with my wireless mouse. But my wired one works fine. It only happens sometimes. Today it's been working without any problems though.

---

### Post by SaikoRonin on 2010-02-19
My mouse stopped working again, and now my printer and my zune won't connect either.  I tried reinstalling swap again like before but it did nothing this time.  So that must not have been a fix

---

### Post by SaikoRonin on 2010-02-23
I have traced it to this error,  Connect-Debounce failed, port 7 disabled.

any ideas on how to fix this?

---

### Post by SaikoRonin on 2010-02-24
This is not a lucid problem,  Lock this thread please,  the problem presists after downgrading to Jaunty Jackalope

---

