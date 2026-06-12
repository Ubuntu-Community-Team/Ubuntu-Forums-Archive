---
title: "Howto install fonts ? (Gimp/Flubber)"
date: 2005-09-25
forum: Installation &amp; Upgrades
---

### Post by cotcot on 2005-09-25
I want to have some more fonts available in Gimp, OO, ....
One of the fonts I want is 'flubber'. I have it with the Gimp install on my XP-computer but not on my Ubuntu computer. 
Where can I find it and how can I install it ? 
How can I install freetype-1.1.tar.gz and sharefonts-0.10.tar.gz ?

Thanks

---

### Post by Xian on 2005-09-25
There are generally two locations on your system where fonts are stored:

- /usr/share/fonts [global use]
- /home/your_name/.fonts [user specific use]

Have you tried placing the fonts in either of these paths?

---

### Post by cotcot on 2005-09-26
OK , I have found the font in /usr/X11R6/lib/X11/fonts and could install the freefont with the instructions of README.
I have found flubber in a fonts-ttf-decoratives rpm, converted it with "alien" and installed it with "dpkg".

So everything is OK

---

