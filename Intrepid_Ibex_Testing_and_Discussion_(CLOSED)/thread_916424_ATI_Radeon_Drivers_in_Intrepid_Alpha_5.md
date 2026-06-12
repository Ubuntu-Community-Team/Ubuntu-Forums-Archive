---
title: "ATI Radeon Drivers in Intrepid Alpha 5"
date: 2008-09-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by winrowc on 2008-09-10
Hi Ive been using Intrepid Alpha 5 for the past few days and Ive been loving it, but I messed up my xorg.conf file and stupidly didn't back it up properly.
Now it only displays in 800x600 and I want to fix it. Ive installed envy, but the ati drivers couldnt be enabled because it says the xorg.conf file is invalid. Then I fixed that but I feel its still an xorg.conf problem.


So two things:
First: how do you enable restricted drivers like this from the terminal? I want to see if I can do that in case it is just an Alpha problem. In "Hardware Drivers" it says that I can enable it, but when I give it Authorization, nothing happens, it stays not in use.

Second: Is there another command for reconfiguring the settings other than dpkg-reconfigure xserver-xorg? I did that and all I configured was the keyboard layout and it just took me back to the terminal. There was nothing regarding monitors or anything like that, which would make my xorg.conf file more normal.

---

### Post by Oldsoldier2003 on 2008-09-11
Moved from General Help.

---

### Post by inportb on 2008-09-11
Envy won't help you, as fglrx does not work with the current Xorg. If you use a blank xorg.conf, Xorg should default to the radeon driver, which works well enough for most purposes.

---

### Post by winrowc on 2008-09-13
Okay so now its working acceptably, but Im not able to use my other screen, so I'd really like to use some sort of driver that can at least do that and let me enable desktop effects. I went into Hardware Drivers and there's an ATi driver there and it allows me to authenticate so that it will Install and Turn on, but it doesn't do anything once I do that. It just stays not enabled. Any tips?

---

### Post by olskar on 2008-09-13
Time for a sticky about this? Lots of posts about problems with fglrx

---

### Post by MALEADt on 2008-09-13
> **winrowc said:**
> Okay so now its working acceptably, but Im not able to use my other screen, so I'd really like to use some sort of driver that can at least do that and let me enable desktop effects. I went into Hardware Drivers and there's an ATi driver there and it allows me to authenticate so that it will Install and Turn on, but it doesn't do anything once I do that. It just stays not enabled. Any tips?

The ATI driver will not work on intrepid, as they do not support the Xorg server which is being used at the moment. Maybe later on (some predict it to be december) ATI will release a driver which'll support the new Xorg server.
For the moment, you'll need Hardy, or pick the Open Source drivers (radeon & radeonhd), and they **really have** 3D support :) right now i'm using Compiz in combination with a ATI x1650, using the radeon driver.
Also dual head is supported by the open source drivers, but you'll have to modify your xorg.conf for that I think (check [this sample config](http://forums.fedoraforum.org/showthread.php?t=159763) out).

Remember to start with a "blank" Xorg.config, X will automatically probe your card and load the correct driver (which'll be radeon).

---

### Post by nlvivar on 2008-10-09
What do you mean by a "'blank' Xorg.config", and how can I make my blank?

I just upgraded from Hardy to Intrepid, and my ATI Radeon Mobile driver wasn't working.

Could you give a step by step on how to install the opensource drivers as you recommended, MALEADt?

Thanks.

---

### Post by BwackNinja on 2008-10-09
Opensource drivers come with ubuntu. Open your xorg.conf and set driver to "ati" and accelmethod to "exa".

---

