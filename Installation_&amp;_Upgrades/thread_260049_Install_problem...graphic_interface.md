---
title: "Install problem...graphic interface"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by mstrat on 2006-09-18
During the initial boot from the CD, I cannot get Ubuntu to load.  I get the message:

Failed to start the X Server (your graphical interface) It is likely that it is not set up correctly.  Would you like to view the X-Server to diagnose the problem?

Then I can do nothing but shut down.  I put Ubuntu on another laptop computer without any problems, and am using it 100% on that computer (It fits my uses perfectly), so I think it is something other than my error.  I am attempting to install it on a Toshiba Satellite notebook with Intel Centrino Duo Core processor and a 17" widescreen display...is that a problem?  

Any suggestions?

---

### Post by taurus on 2006-09-18
Do you even get a prompt when X fails?  Try pressing <Ctrl><Atl>F2 to get to another console.  Log in and at the prompt, reconfigure your X again with

```

sudo dpkg-reconfigure xserver-xorg

```

p.s.  What graphic card do you have in your machine?

---

### Post by mstrat on 2006-09-18
I got Ubuntu to install, in a safe mode...it is not running at a good resolution though.  I have run the reconfigure and had many problems, played with it and got it back up and running again.  I think I can live with the resolution I have now gotten it to run at, though any suggestions for :

Intel Graphics Card, Graphics Media Accelerator GMA 950?

Thanks for all the help...

---

### Post by mstrat on 2006-09-18
I downloaded the Linux driver from Intel, now I'm in need of figuring out how to use it.

---

