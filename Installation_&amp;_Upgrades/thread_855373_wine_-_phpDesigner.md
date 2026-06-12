---
title: "wine - phpDesigner"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by ddragas on 2008-07-10
Hi 

has anybody successfully installed phpDesigner 2008 on ubuntu with wine ?
I'm getting exception error at start up (like on this [thread]("http://ohioloco.ubuntuforums.org/showthread.php?t=796701") ). I would like to use phpDesigner because I have payed license.

Can somebody please help me

I really want to replace my XP with Ubuntu 8.04

---

### Post by 3StrikesDesign on 2008-10-15
To get phpDesigner 2008 working correctly with Wine you need to run the following command as the user which you are logged in as.

wget [http://kegel.com/wine/winetricks](http://kegel.com/wine/winetricks) && sh winetricks msxml3

---

### Post by jollins69 on 2009-10-12
this helped me out. thankyou! :)

---

### Post by TxRx on 2010-04-09
I'd like to just confirm for anyone else who uses this in Windows that simply applying the above MS update in the manner above 'does' fix the phpdesigner (ver6.5) for me. 

Thank you ever so much, i've been using this on windows for years and so glad it's working on Ubuntu now!

TxRx

---

### Post by pazof on 2011-12-08
Confirmed - worked for me on Debian Squeeze 6.0.3a 64-bit, with phpDesigner 7.2.4. So many thanks, been trying for days to get it running...

---

