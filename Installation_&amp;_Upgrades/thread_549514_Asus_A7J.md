---
title: "Asus A7J"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by Almonde on 2007-09-12
Installing Ubuntu om my laptop is not going so great.
Have the A7J, it's an CoreDuo 2Ghz, 1.5gb internal mem, 100GB HD, X1600 ATI 256mb, 17" WS

The standard Ubuntu won't even load the GUI.
The alternate one hangs on the same point over and over again.
75% in at the WVDIAL.

any hints or tips?

---

### Post by Almonde on 2007-09-13
I know ATI vidcard is the issue here.
Just trieing to figure out how to go
about it, already tried the alternate install.
Noticed another posting with the option
of a certain driver. Will check that out
as well.

Any A7J owners' input also appreciated ;)

---

### Post by Almonde on 2007-09-15
Freespire 2.0 not working either :(

---

### Post by Comrade_Weng on 2007-09-16
I had this very same problem with my A7J. The trick is to install Ubuntu 6.06 Dapper  and then upgrade to first Edgy then to Feisty. The reason for not only installing Edgy is that for some reason networking does not work with the A7J under Edgy when installed from a CD, but it does when upgraded from Dapper.

Not had any success in getting the tv tuner to work yet nor the webcam, but I have just about managed to get compiz working, despite the issues with fglrx, glx and ati cards. For some reason I am unable to activate automatic login and I also must enter my password twice on the login menu. Not sure what I've done there.

---

### Post by Comrade_Weng on 2007-09-16
Forgot to mention that once into Feisty you can enable the restricted fglrx driver and all is good.

---

### Post by Comrade_Weng on 2007-09-16
I've just managed to get the tv tuner working using kaffeine and the guide for installation found here

[http://mcentral.de/wiki/index.php/AverMedia_Cardbus_Hybrid_TV_FM_E506R#Installation](http://mcentral.de/wiki/index.php/AverMedia_Cardbus_Hybrid_TV_FM_E506R#Installation)

---

### Post by Almonde on 2007-09-17
thanks alot for the feedback, I will give it a go :)

---

### Post by Almonde on 2007-11-18
I got Gusty running now.
Installed without a hitch.

Right now though, my wireless and my normal network card
are not activated and/or used....

Any sollutions?

---

### Post by Comrade_Weng on 2007-11-18
I first upgraded to gutsy from feisty with no problems, i then decided to do a clean install of gutsy and everything worked first time. Just make sure your restricted hardware is ticked to use the wireless card.

Did you use a live cd or a text based install cd? I used to live and my wireless worked using that. 

Not really got any solutions im afraid since i never had any wireless problems. Best looking around the forums for a solution. 

I did have problems getting the tv tuner to work under gutsy, but have got that sorted now. Follow the installation procedure here: [http://mcentral.de/wiki/index.php/Em2880#Installation](http://mcentral.de/wiki/index.php/Em2880#Installation)

Still no joy with the webcam though, although i havnt tried much and am not really sure what to search for on the forums.

---

