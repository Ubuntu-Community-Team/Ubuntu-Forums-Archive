---
title: "Two tweaks: RNDIS timeout and Intel GMA965 graphics"
date: 2009-02-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kaykay on 2009-02-22
Hi, All,

I thought I'd share two tweaks that took me a bit of time to really nail down, to the degree that a simple search isn't going to lead most people to a solution.

The first is poor graphics performance on my laptop with an Intel GMA graphics controller. Some posts say to install xorg-edgers packages, some say that it's a driver problem.. what fixed it for me was what's contained in page 3 of [this post.]("http://ubuntuforums.org/showthread.php?t=1023419&highlight=intel+graphics&page=3") Open /etc/X11/xorg.conf and add: Option "AccelMethod" "UXA"

Things are much snappier now. A reboot is usually a good idea, to get everything back on the right page.

The other problem is one I've had to hand-install for years, and Intrepid was the first to fix it out-of-the-box. When using a windows mobile device with internet sharing (RNDIS for the tech world), one has to edit the PPP options file to stop pppd from dropping the connection every 10-30 seconds. Intrepid fixed it, and Jaunty broke it again. Open /etc/ppp/options and comment out (with a # mark) the lines starting with "lcp-echo-interval" and "lcp-echo-failure". That should fix it, though you may need to reboot. This is still hands-down better than what I used to have to do, messing about with kinternet and building modem connections and so on.

I hope I've saved somebody out there some time..!

Best,
K.

---

### Post by Triggerhapp on 2009-02-22
On note of the first, I know why it isnt enabled by default yet ;) its causing alot of instability for certain chipsets.

Hope it all stabalises well, personally :)

---

### Post by Mindless Automata on 2009-02-22
UXA seems to cause my laptop to completely freeze.  Could be another problem, but it hasn't happened since I disabled it.

---

### Post by kaykay on 2009-02-23
I do notice some graphical glitches, with UXA enabled, though no crashes on my end.. So user beware! Heed these good persons' warnings :)

---

