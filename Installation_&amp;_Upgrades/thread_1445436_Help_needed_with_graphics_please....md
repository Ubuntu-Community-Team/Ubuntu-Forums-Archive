---
title: "Help needed with graphics please..."
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by Lodmot on 2010-04-02
Okay. I just installed Ubuntu and the official ATI graphics drivers for Linux, and... well..... it looks damn sexy on my 42'' Toshiba TV! Only one problem... After about 10 minutes of using Ubuntu, my screen loses the signal. It just... drops out. Even if I'm actively doing something on the computer. The only way to get it back is to shut down and restart. I have an ATI Radeon 2600 HD PCI Graphics card, and my TV is connected to the card through HDMI. I've searched high and low for a solution to this problem, and I've found nothing... Any suggestions? Thankies. :B

Oh, and I should mention, this problem isn't just in Ubuntu. It's happened in other Linux distributions also.

---

### Post by Shazaam on 2010-04-02
Some basics...
Does your tv have a sleep/power saving mode?
Power Manager and Screensaver set up correctly in Ubuntu?
Temperature ok with the ATI card?

---

### Post by Lodmot on 2010-04-02
Well, it isn't the TV, because when I lose the signal, the screen shows a message saying "No Signal". So the problem is on the computer's end of it. I've checked the power settings, and didn't see anything out of the ordinary. And I'm not so sure about the temperature. But what I do know is, I've tried installing Ubuntu on another computer system, and it didn't have this problem. I also know that in Windows and on Leopard, this problem is non-existant. The graphics drivers definitely aren't the problem here, because it displays the desktop in full 1080 HD resolution...

---

### Post by Mark Phelps on 2010-04-02
> **Lodmot said:**
> The graphics drivers definitely aren't the problem here, because it displays the desktop in full 1080 HD resolution...

What?  

Since this Ubuntu install is, according to your testing, the ONLY install in which this problem occurs, that most probably means it IS a driver problem -- with this Ubuntu install.

I'm running one of the older, legacy ATI cards and using the open source drivers -- and I'm getting full 1080 resolution, too.  So, the fact you're getting that is no indication as to whether or not you're using the ATI restricted driver.

To find out, open a terminal an enter "fglrxinfo".  That will tell you if the ATI driver is installed, and if so, what version it is.

---

### Post by Lodmot on 2010-04-02
In my first post, I mention that it also happens in other linux distributions.

> 
Oh, and I should mention, this problem isn't just in Ubuntu. It's happened in other Linux distributions also.


If that's not what you meant, I also have tried re-installing Ubuntu about 3 times. It didn't fix the problem.

---

### Post by Lodmot on 2010-04-02
Okay. I believe I've found the problem. The fan in my graphics card was not spinning. Now it is, but it sounds like it's grinding against something. Freakin thing is a piece of crap.... >3<

---

