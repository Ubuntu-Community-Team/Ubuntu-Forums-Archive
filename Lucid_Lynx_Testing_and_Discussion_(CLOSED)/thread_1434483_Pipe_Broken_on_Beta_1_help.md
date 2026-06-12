---
title: "Pipe Broken on Beta 1 help"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sandeepb on 2010-03-20
Hi everyone,

I had burned the new Beta on a DVD yesterday night and booted with it, and the problem is when choosing either try it as a live cd or install, I get the boot splash but then it complains that the pipe is broken or something and then my display goes saying there is no signal, so it's dropping the connection. I want to install this new version and I can't till I can get to the installation.

My System specs are:

AMD Phenom II x4 940
Corsair Dominator 4GB Ram
750GB Hitachi Deskstar, 640 GB WD Caviar Black
ATI 5850

Help will be really appreciated.

---

### Post by kansasnoob on 2010-03-20
Have you tried "Check CD for defects"?

It takes a few minutes to run.

---

### Post by sandeepb on 2010-03-20
I thought it could be the disc so I used unetbootin to write it to a USB and boot from that and it stilled showed the error. 

It could be a corrupted iso. I will try downloading it again. After doing the check cd for defects option.

---

### Post by sandeepb on 2010-03-20
OK I gave it a shot inside a VM, and I managed to install it and everything, works perfectly fine, what's wrong with it on my original hardware then?

---

### Post by fedexnman on 2010-03-20
yeah im having problems too , when i try to install it goes thru the motions and after awhile it shows an error saying   cd/dvd drive is dirty or the cd/dvd needs to be burned slower, or my hardrive is unhealthy, i used disc utility to check my hardrive and ran the selftest and it said it was ok, and i also burned the iso slower and i get the same problems, beta? i guess ?

---

### Post by sandeepb on 2010-03-20
lol the alpha's meant to be more bugged up, at least I got to use it, well apart from not having 3d Effects and resolution due to the ATI drivers not working yet.

---

### Post by fedexnman on 2010-03-20
reinstalled karmic sucess..., man this beta 1 broke my whole system,note to self. i need to install betas on a seperate hardrive, instead of partitions

---

### Post by sandeepb on 2010-03-20
Found out what my problem is.

For some weird reason this update of Lucid doesn't seem to detect a HDMI output, I had to go to DVI, after installing Driver for ATI (taken from the lucid ati bug tracker) gave me no HDMI output and a mucked up screen on DVI.

guess it's back to windows for time being.

---

