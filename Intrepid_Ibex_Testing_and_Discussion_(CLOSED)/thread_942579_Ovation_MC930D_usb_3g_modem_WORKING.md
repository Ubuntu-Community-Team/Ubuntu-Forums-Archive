---
title: "Ovation MC930D usb 3g modem WORKING"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by gcday on 2008-10-09
Hurrah! I've managed to get my Ovation MC930D modem (used for O2 3g) working under Intrepid. 

Here are the steps.


1) If you plug in the modem, it does not work, intrepid does not detect it. As far as I can see this is because the device needs to be switched. 

2) Open a terminal (alt+ f2) 

3) type "sudo eject /dev/sr0"

4) Intrepid picks up it as novatel wireless modem.

5) I then selected the connection "o2 faster"

6) Surf away. 


Couple of oddities that I could do with clearing up - "o2 Faster" uses a different user name and address than what I understand it to be for my o2 modem. My settings should be:

    * Phone Number: *99***1#
    * Initialization String 2: AT+CGDCONT=1,"IP","mobile.o2.co.uk"
    * Username: o2web
    * Password: password

However I can find no way to manually change this - if I try and change the connection settings, it just reverts back to the default settings. Checking my account, I don't seem to roaming and the usage is being racked up against my account in the normal way.

---

### Post by gcday on 2008-10-10
Quick question related to this - how would I submit the correct network settings so that they can be checked and incorporated into the network manager as a 3g provider option?

---

