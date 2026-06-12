---
title: "Wireless problems after upgrading to 8.10"
date: 2008-10-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Oziyak on 2008-10-08
Hey everyone.

I'm about to do a fresh install of 8.10 after upgrading form 8.04.  It seems that my wireless usb drive has stopped working and when I click on "Windows Wireless Drivers", select my drive then press "Configure Network", I get an error message saying "Could not find network configuration tool".

I'm just wondering if my windows wireless driver will still work if I do a fresh install of 8.10? or if that program that allows you to install a windows driver for a usb wireless device will only work on 8.04?

thanks

---

### Post by Oziyak on 2008-10-08
I actually need to correct this... it seems as if my packagemanager works... and that I can view my network wirelessly... but not surf the internet... and the connection icon at the top right of the screen shows no connection?

---

### Post by Oziyak on 2008-10-08
I've been toying with it.... what I did was check for some updates.... several installed over the "nonexisting" internet connection...

after that the wireless seemed to work.... as did my nagging nvidia graphics card driver problem.... I restarted... graphics work great

but now the wireless isn't working again.... 
maybe I have to reinstall the windows wireless driver program?
I'll post my findings.... if you know anything please post

---

### Post by Oziyak on 2008-10-16
anything....?

---

### Post by maestrobwh1 on 2008-10-16
My atheros chipset has become annoyingly flaky with 8.10... connects but hangs and seems to be connected, but anything involving the net seems to just crap out after a bit.  I get maybe 5 minutes before I have to "pump" the connection.  (Using sudo pump -i ath0 seems to get it working most of the time)

---

### Post by Oziyak on 2008-10-16
interesting... and thanks for the command...
I've just installed a newer version of the kernel and it seems to be staying online a little longer... hopefully for good :)

---

### Post by webdr on 2008-10-17
This has to be one of the most frustrating aspects of switching to ubuntu.
I've been on it since dapper, and the inconsistency of wireless networking stability is truly maddening.

I've stayed with 7.10 as my main workhorse because it seems to do the best, but even then, I have done testing with various wireless adapters, prism, atheros, and realtek chipsets and much to my dismay, I seem to get my best network performance and stability from that other OS (MSXP) I dearly hate to admit it, but it is true.

I've been lurking on the madwifi and ath5k devlists for over 18 months, and while they are very active developments, it feels very much like when you are watching a steam locomotive first taking off (lots of wheel spin, action and noise, but not a lot of traction and forward movement).

I am venting, but there really must be some resolution to these issues if we are to expect Ubuntu to continue making huge inroads to the desktop and laptop market.

---

