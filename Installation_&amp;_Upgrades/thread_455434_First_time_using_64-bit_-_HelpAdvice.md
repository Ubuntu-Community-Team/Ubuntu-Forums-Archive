---
title: "First time using 64-bit - Help/Advice"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by aqualad on 2007-05-26
So I just built a computer:

Asus M2N32-SLIDeluxe Mobo (wireless edition) - possible known bugs?
AMD 64 X2 5200+
GeForce 8600GTS (Dual DVI output)
160GB Sata HDD
2GB SLI ready RAM

I'm having problems all over the place though.  I did get it to install but when it was booting the screen went black all the way until the login screen, but now after I've installed the drivers it just stays black after saying "Kernel Alive!"  This may be a bug, because there's another thread in this forum with two other people having the same problem.

Now, I can get Ubuntu on the computer, but I have a few questions not regarding the display problem:

Should I be using the 64-bit version?  
  If I do, will the person this computer is for (not very linux savvy) going to have problems whenever there are updates or new programs installed? (e.g. flash or any codecs/plugins)

Also, is there anything special I need to do during the install to make it work better?

Any help is appreciated. Good luck trying to answer these sporadic questions

---

### Post by trak87 on 2007-05-26
Many may disagree, but I'd stay with the 32bit version for now.

---

### Post by beermad on 2007-05-26
> **aqualad said:**
> So I just built a computer:

Should I be using the 64-bit version?  
  If I do, will the person this computer is for (not very linux savvy) going to have problems whenever there are updates or new programs installed? (e.g. flash or any codecs/plugins)


I haven't found any problems with codecs on 64-bit, but you *won't* be able to use Flash, as there isn't a 64-bit version. Personally I don't see that as a problem, as I hold to the maxim that whenever you've got nothing to say, Flash is the technology to say it.. But I believe it's supposed to be possible to get it to work if you uninstall the 64-bit copy of Firefox (or presumably other browsers) and install the 32-bit version instead.

Updates are no problem, because APT will be configured to pull in 64-bit updates rather than 32-bit ones.

---

### Post by rsambuca on 2007-05-26
I'd go with 64-bit.  Both Flash and java are easy to get working now with the great how-to's on this forum.  It takes less than ten minutes to get it up and running - and you only have to do it once.

---

### Post by aqualad on 2007-05-26
I'm gonna shoot for 64-bit again and hope for the best (32-bit actually mucked up my display worse than 64-bit)

Thanks for the input, if the codecs and flash are the only big issue then I can probably fix 'em up really quick with some how-to's, especially if it's a one time only deal.

---

