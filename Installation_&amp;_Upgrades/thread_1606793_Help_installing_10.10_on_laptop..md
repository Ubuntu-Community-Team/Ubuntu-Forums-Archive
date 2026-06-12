---
title: "Help installing 10.10 on laptop."
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by jonwymore on 2010-10-26
I am trying to do a fresh install of 10.10 but when boot up off a flash drive or cd the screen is set to a resolution so that i cant see the all of the dialog boxes to click the buttons. Also the screen is split into two parts showing a mirror image of the install box. My laptop is an HP pavillion dv6000. This has happened in the past when installing 10.04 but i was able to click through blindly till i got it installed. Is there a way to change the resolution on the install screen through command line?

---

### Post by tommcd on 2010-10-27
You could try installing Ubuntu from the alternate install CD. This is a text based install CD that should bypass any graphics problems that you are having with the live CD.

And welcome to the Ubuntu forums!

---

### Post by garvinrick4 on 2010-10-27
> **jonwymore said:**
> I am trying to do a fresh install of 10.10 but when boot up off a flash drive or cd the screen is set to a resolution so that i cant see the all of the dialog boxes to click the buttons. Also the screen is split into two parts showing a mirror image of the install box. My laptop is an HP pavillion dv6000. This has happened in the past when installing 10.04 but i was able to click through blindly till i got it installed. Is there a way to change the resolution on the install screen through command line? Can you get into try Ubuntu and go to System drop down menu to Admin and to Additional drivers.
If does not help can you get to a terminal and if have to use Ctrl/Alt/f1 to terminal and Cntl/alt/f7 to get back to GUI. and so people can see your cards.
While in terminal copy and paste and run in this thread if possible.
```
lspci
```

---

