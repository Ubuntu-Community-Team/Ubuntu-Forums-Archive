---
title: "No x.org after Ubuntu Studio install :("
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by Chuklz on 2007-07-23
Well, after using Ubuntu and linux in general for a couple months now, I wanted to try Ubuntu Studio for the audio programs.  

After installing, I got up to the progress bar and then when the log in window was supposed to pop up, I get an Xserver error message.  The video chipset I am running is an ATI Xpress 200m on my Turion64 laptop.
I read about the binary drivers or something of that sort but i have no clue what to do.

Any help is greatly appreciated!

---

### Post by Pumalite on 2007-07-23
What kind of CD you used to install your first Ubuntu? Live CD or Alternate CD. Because you seem to be having graphical interface problems. How much memory do you have?

---

### Post by Chuklz on 2007-07-23
it was the alternate cd and there is no other choice to download

i have a gig of ram and 128 dedicated video ram

---

### Post by Svictor on 2007-07-23
Chuklz: 
> I get an Xserver error message is about as informative as "it does not work". Please be more precise: what is the message? Usually, it says what is wrong...
You probably don't need to deal with the binary drivers, since ubuntu was working before.
The alternate CD is just a text-interface instead of the regular live CD. It installs the same things in the same way.

---

### Post by Pumalite on 2007-07-23
You can try: sudo dpkg-reconfigure xserver-xorg. Most defaults are OK. Choose 'vesa' as your drive, then startx. Post back if you continue to have problems.

---

