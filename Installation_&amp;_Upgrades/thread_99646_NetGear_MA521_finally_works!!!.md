---
title: "NetGear MA521 finally works!!!"
date: 2005-12-06
forum: Installation &amp; Upgrades
---

### Post by risknet on 2005-12-06
Hello all,

After several days of trying to install this MA521 on my Ubuntu 5.10 in HP Pavilion ze4610us laptop, this netgear MA521 finally works.

I tried installing this wifi network card based on a lot of information from google search, but nothing worked in my case..... but, finally this last solution worked.

Here is what I did.

1. Get Ndiswrapper and Ndiswrapper-utils using Synaptic Pakcage Manager
2. Download RTL8180L driver (Windows XP) from Realtek website
3. Install this driver using .INF file in Ndiswrapper
4. Make sure MA521 hardware is detected in Ndiswrapper (/sbin/ndiswrapper -l)

* * * (5) this was something I did wrongly initially * * *
5. Get the correct key if you use WEB key in your access point
    ( 5 text digits or 10 hex digits for 64 bits encryption !!!  Don't get confused! )
* in console window, run these commands in the following order as root

6. /sbin/iwconfig   => to see if your wlan0 presents.  if you see wlan0, continue...
7. /sbin/iwconfig wlan0 channel 6   => use your channel number here
8. /sbin/iwconfig wlan0 essid YOUR-WIFI-NAME   => your ssid name.  no double quotation marks.
9. /sbin/iwconfig wlan0 key YOUR-KEY   => if you use web key in your access point
10. **[B]/sbin/iwconfig wlan0 key open**[/B]   => you will see your link light lit up after #10
11. /sbin/ifup wlan0  => this will start up your wlan0.

I didn't think of using "/sbin/iwconfig wlan0 key open," and this was the main reason why I couldn't make my MA521 work.

I hope that this would help other friends in this Ubuntu forum.

= risknet =

---

### Post by Monchanger on 2006-10-28
Thanks for the help.  I managed to get mine done in less than half an hour using this.  I'd like to add a couple notes:

* Ndiswrapper did not appear in Synaptic for me.  It was already installed.  I am running a (mostly) up-to-date Dapper (as of today, 10/28/2006) with a stock 2.6.15-27-386 kernel.  It's *possible* that I've tried configuring this card before, so your results may vary.

* I got my driver off of the Netgear website, so what you have on your CD *should* be fine.

* If you are trying to connect to an unprotected network, use "any" for the ESSID in step 8 and then use "off" for the key in step 9.

Hope you had an even easier time than I did.

Monchanger

---

### Post by helium89 on 2006-11-08
Thanks for the help. Recently I had to reinstall Windows and the reinstall left me without some necessary wireless drivers and forced me to install Linux. Though I have to reset my router before I can finish the set-up (I forgot my password and connection information), getting the driver installed and the card recognized is further than I got last time I tried Linux. Hopefully this is a sign that Linux and I will get along well this time. One thing I did notice is that ndiswrapper wasn't in the package manager. Is it installed by default in Ubuntu?

---

### Post by berralac on 2008-02-15
well, I just installed xubuntu yesterday and have been fussing with this card since.  I do have a concern though, after it finally started to connect, is there a way to increase the link quality or to ensure that it is connecting to my router?

thanks

---

