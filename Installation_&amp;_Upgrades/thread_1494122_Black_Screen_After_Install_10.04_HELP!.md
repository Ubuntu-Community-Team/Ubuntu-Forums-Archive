---
title: "Black Screen After Install 10.04 HELP!"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by steinaro on 2010-05-26
Concerning Ubuntu 10.04, I was having problems starting the live CD until someone told me to set the option NOMODESET when I started it. It worked, black screen gone! 

Excellent until... today when I installed it to the hard drive. Now I am having the problem again with the screen which goes black after the Grub selection screen during boot.

I searched the Internet and saw there are some different solutions out there, but I am not sure which is correct. I tried modifying the default grub file, but with no luck. 

By the way, I have an ATI FirePro video card which I bought last year.

Any simple solutions?

---

### Post by davidmohammed on 2010-05-26
can you confirm you are booting with nomodeset in your grub?...


press shift on boot to display grub - press e to edit and look to see if nomodeset is on the line.

if it isn't - add nomodeset before quiet splash.

---

### Post by steinaro on 2010-05-26
Thanks, it worked!

I tried to do that before but couldn't understand why I couldn't edit the line. It turns out the 'quiet splash' part extended to the next line and I couldn't figure out how to get to it.

Anyway, the solution was to add 'nomodeset' after 'quiet splash'.

---

### Post by darkod on 2010-05-26
I think it should prompt you for a found video driver now, and once it is installed you don't need to add nomodeset any more.
Otherwise, if it doesn't work without adding nomodeset, there is a way to make it permanent.

---

