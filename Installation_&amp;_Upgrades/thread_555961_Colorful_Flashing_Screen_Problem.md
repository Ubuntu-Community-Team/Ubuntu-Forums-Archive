---
title: "Colorful Flashing Screen Problem"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by joshthejest on 2007-09-20
I have had ubuntu installed on this machine in the past (feisty).  I installed feisty again this time and when I get to the login screen all I see are brilliant flashes of light of all sorts of colors... hot pink lime green... starts off slow and then speeds up.  Any ideas?

I should also note that when I switch to 16 bit I don't get this, but something else... the screen is mostly black and just displays bits and pieces of different colors...  It is a different arrangement every time I use ctrl+alt+backspace

I also tried installing freebsd with gdm, but... I got something similar.

---

### Post by Pumalite on 2007-09-20
Do md5sum on your isos, burn at 4x, clean the lens in your burner or replace it.

---

### Post by joshthejest on 2007-09-20
... it is already installed though...
Is there a solution that might fix the problem I'm having with my display?

Same thing happens with regular dvd fedora core installation... black screen with colors everywhere... This recently worked on this machine.... atleast I could get to the graphical install on it.... before.

---

### Post by Pumalite on 2007-09-20
Check you CD's in another computer to see if it is bad CD's or problem with display. At this moment I suspect your burner.

---

### Post by joshthejest on 2007-09-20
Command line works fine btw

---

### Post by Pumalite on 2007-09-20
Then:
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx
.

---

### Post by Gremlinzzz on 2007-09-20
when I get to the login screen all I see are brilliant flashes of light of all sorts of colors... hot pink lime green... starts off slow and then speeds up. Any ideas?
Sounds familiar think ill talk too Dr. Timothy Leary,
:guitar:

---

### Post by joshthejest on 2007-09-20
Changing the video to vesa worked... was there something wrong with the nvidia driver that I had used in the past?

---

### Post by Pumalite on 2007-09-20
Tell me the exact name of your video card and I'll tell you what to install and how if you need to.

---

### Post by joshthejest on 2007-09-20
It is an Nvidia Geforce 6200... if you need more information than that I can open the case and read it off.. just would rather not...

---

### Post by Pumalite on 2007-09-20
Now that you are IN the system, you might want to try this at the Terminal:
sudo apt-get install nvidia-glx
Let's see how it goes.
(you might need 'Legacy Driver', I'm not sure). We can always fix it and try something else.

---

### Post by joshthejest on 2007-09-21
I installed nvidia-glx and nothing bad happened...

---

### Post by Pumalite on 2007-09-21
Cheers.

---

### Post by joshthejest on 2007-09-21
Thank you for your help.

---

### Post by Pumalite on 2007-09-21
You are welcome. Good luck.

---

