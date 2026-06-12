---
title: "ATI video driver 10.10 question"
date: 2010-10-19
forum: Installation &amp; Upgrades
---

### Post by lindsay7 on 2010-10-19
My laptop has the ATI Radeon Express 200 graphics card installed and it worked fine until Ubuntu 10.10.  Why would this not be supported with the latest version 10.10?

Does this mean that my laptop is at its end for Ubuntu from here on out?

---

### Post by ronparent on 2010-10-19
Which drivers are you using. ATI no longer supports a proprietary driver for the Express 200 series. The non-proprietary drivers in 10.10 should still work.

---

### Post by lindsay7 on 2010-10-19
I do not know what driver is being used on 10.4.  When I try to install 10.10 or even run the live cd for 10.10 it locks up with a black screen after I hit the try without installing button.

---

### Post by ronparent on 2010-10-20
In booting to the live cd, try hitting f6 for some boot options. Select the one pertaining to display (I forget the wording). Will it boot then?

I chickened out when I went to win7 and updated all my video cards so my graphics wouldn't be degraded (neither ATI nor nvidia was supporting older chip sets). That is not likely possible with a laptop. If you had upgraded you might have to purge the old drivers. I find it hard to believe that the non-proprietary drivers won't work. 

We need more help though, I purged all my old display hardware when I upgraded my computers for Win 7 and can no longer check it out.

---

### Post by lindsay7 on 2010-10-20
Thanks for your help.  You gave me a hint and for others reading this, what I did is hit enter during the startup of the live cd and get the boot window with the options to press the f6 keys I found the command to select nomodeset and started the install process with that.  After you select nomodeset hit the esc key and install.  It installed 10.10 and everything worked,  I installed Ubuntu Tweak and then found the source center button to install x-updates. now everything works great.

I install from the Super Ubuntu cd which has Tweak and a lot of other stuff includeded, It makes set up a lot easier.

---

### Post by ronparent on 2010-10-20
Great to hear you have it working. Have fun.

---

