---
title: "Restricted driver installation problems"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by maarten12 on 2008-01-09
Hello, I wanted to install Restricted drivers on Ubuntu 7.10 (with custom stripped 2.6.22-14-generic kernel but it's called the same so I can select the restricted drivers) but when I click it, it installs it and says I need to restart. I do that and then it says it's not in use! I don't know how this is possible as it worked on my old stock kernel and it used to work on this custom one. I didn't have any errors on installation so that couldn't be it. I now use catalyst 7.11 which doesn't work at all for compiz or displaying moving pictures. (I need 7.11 for widescreen resolution and 7.12 doesn't support that) 

Laptop information:
Acer Aspire 9500 series
Ati Mobility Radeon X700.

Thanks in advance

---

### Post by Pumalite on 2008-01-09
'Ati Mobility Radeon X700.'
This is your problem. The ATI driver doesn't work, You get better resolution with 'vesa'. Unfortunately ATI support of Linux is very poor.
You might want to try ENVY, but results are unpredictable.

---

### Post by oldsoundguy on 2008-01-09
Echo Pumalite. 
The ATI drivers leave a lot to be desired.  (they ARE working on it post the AMD buy out, but trash is trash and they have a LOT of work to do before their software and drivers are ready for Linux!) Sufficiently so that I have replaced the ATI cards in my three Gutsy boxes with nVidia cards.  THOSE WORK and work well!
AND Envy is the easiest way to install the card drivers and software post system load.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Pumalite on 2008-01-09
That's right, I have nothing but Nvidia cards, and I'd never buy ATI unless they change radically.

---

### Post by maarten12 on 2008-01-09
Uh, yea but how do I change videocard in a LAPTOP?

---

### Post by oldsoundguy on 2008-01-09
appears you are going to have to live with the cards you were dealt at present.  That is until l ATI pulls it's head out.

You could try and use Envy and see if it works for you. (it did NOT work for me on ATI, but YMMV)

---

### Post by Pumalite on 2008-01-09
Next time choose a laptop with at least Intel in it. In the meantime, use Envy. Good luck.

---

