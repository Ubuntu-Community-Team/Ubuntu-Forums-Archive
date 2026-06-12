---
title: "Upgrade woes - wireless connection not working"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by dkolars on 2011-01-06
Thought I'd upgrade from 9.10 to 10.10...  have both laptop and desktop, did laptop first as it's not my main system, only for travel.  Reading about upgrade, saw that I should upgrade to 10.04 first, and then to 10.10.  Si, I did upgrade to 10.04 thru the software center via wireless connection to my router. 
After upgrade, could not log in... I'd enter my password, it would flash up a screen that said "Ubuntu 10.04", and then pop up the log-in screen again... and again... and again...etc.  

So, installed 10.04 via CD, ended up formatting HDD.  Then, installed 10.10 over that, partitioned drive, etc.  All seemed ok, until I attempted to set up the wireless connection...  it says "Wireless network disabled", and so I went to the Network Connections screen... it wants SSID, BSSID, Device MAC addy, Cloned MAC addy, etc.  I entered the name of my router for the SSID, entered the 00:19:0e:...etc. for the BSSID, and Applied it...  nobody home.

The network card is recognized (Atheros AR5001 WNA), and it worked fine with 9.10 for the past year.

Hunted on the web for hints/clues/answers, and as usual, find that 90% of the stuff on the web about Ubuntu is from 2005, 2006, 2007, etc.  and is NO help!!!  

What do I do to get the card working?  When I installed 9.10 (clean install on newly formatted HDD), I ~think~ all I had to do was enter the IP addy of the router and it started working.  Been so long ago I don't remember the steps.

So, until this is solved, I'm sure not gonna attempt the upgrade on my desktop, and even then I think I'll clone my HDD before I do!!

TIA  dk

---

### Post by dkolars on 2011-01-07
Found a thread from October that addressed the problem exactly - [http://ubuntuforums.org/showthread.php?t=1604665](http://ubuntuforums.org/showthread.php?t=1604665)

Did all of this, and the wireless was attempting to connect.  It did actually exist for a bit.  Then, it disappeared, and once again, under Wireless Networks it says "Wireless is disabled".

When I 1st got Ubuntu, 9.04, it, too, would not deal with the Atheros card, so I got a USB wireless card and it worked perfectly.  Perhaps that is the solution here.  I've already wasted the better part of 8 hours dealing with this!  

And, discovering other things in 10.10 that I don't like!  I'm sure that there are probably ways to correct them, but why does it have to be so complex.  I click on Restart, and have to then confirm that.  Would love to turn that off... etc. etc. etc.

More as it becomes available...

---

### Post by dkolars on 2011-01-07
Lots of digging:

[http://ubuntuforums.org/showthread.php?t=1623460](http://ubuntuforums.org/showthread.php?t=1623460)

[http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html](http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html)

[http://ubuntuforums.org/showthread.php?t=1610829](http://ubuntuforums.org/showthread.php?t=1610829)

Seems as tho' ALL of these solutions worked... kinda.... sorta... not really.

I can do the above tweaks, and after rebooting, I have the choice of "Create new wireless network", or "Connect to hidden wireless network".

In 9.10, if I was in range of a wireless network, it would be listed, and I could connect (unless it was a secure network, of course)...  Here at home, why does the laptop not see my router?  Why is the word "hidden" in there?

I created a new wireless network, using the name of my router, and when I click on connect, initially, it tried to connect.  NOW, it stops instantly, and goes back to "Wireless is disabled".

So, I deleted all the wireless networks, rebooted, and created a new one.  NOW, it needs my PW again, as the Login Ring was not unlocked when I logged into the system.  Wha???  So, I click on "connect", and my network icon disappeared.  Plugging in my RJ45 did not bring it back, but the connection shows up in the Network Tools.  Cannot ping.  Reboot... now I need to Enter Password to unlock my login keyring...  And, "wireless is disabled"...

Enter WAN addy into BSSID, same result... attempt to connect, and "wireless is disabled"...  When I created the connection, Ubuntu set the Mode to "Ad-hoc" instead of "Infrastructure".  I changed it back to "Infrastructure", and now it tries to connect???

1)  After 2 min, the icon (segment of an arc of rings) is still active, looking like it's trying to connect -- then it pops up the "Authentication requred by wireless network" window and has all the info (WPA & WPA2 Personal + PW), and then tries to connect again.
2)  When I click on "desktop" (the name of my router), I have to input my PW for the router, AND again for the Keyring.
3)  The icon for "desktop" in the connection pop-up window has a lock, as it should
4)  After a few tries, it quits and tells me I'm offline, but leaves "desktop" there and I can click on it and try again... 

Something is working better, as now the router sees the notebook... but no connection from the Ubuntu side...

Ubuntu sucks when it comes to networking, imho...  It says I've never used my eth0, and it's connected right now!!

Still attempting to connect...

---

### Post by dkolars on 2011-01-07
Lots of digging:

[http://ubuntuforums.org/showthread.php?t=1623460](http://ubuntuforums.org/showthread.php?t=1623460)

[http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html](http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html)

[http://ubuntuforums.org/showthread.php?t=1610829](http://ubuntuforums.org/showthread.php?t=1610829)

Seems as tho' ALL of these solutions worked... kinda.... sorta... not really.

I can do the above tweaks, and after rebooting, I have the choice of "Create new wireless network", or "Connect to hidden wireless network".

In 9.10, if I was in range of a wireless network, it would be listed, and I could connect (unless it was a secure network, of course)...  Here at home, why does the laptop not see my router?  Why is the word "hidden" in there?

I created a new wireless network, using the name of my router, and when I click on connect, initially, it tried to connect.  NOW, it stops instantly, and goes back to "Wireless is disabled".

So, I deleted all the wireless networks, rebooted, and created a new one.  NOW, it needs my PW again, as the Login Ring was not unlocked when I logged into the system.  Wha???  So, I click on "connect", and my network icon disappeared.  Plugging in my RJ45 did not bring it back, but the connection shows up in the Network Tools.  Cannot ping.  Reboot... now I need to Enter Password to unlock my login keyring...  And, "wireless is disabled"...

Enter WAN addy into BSSID, same result... attempt to connect, and "wireless is disabled"...  When I created the connection, Ubuntu set the Mode to "Ad-hoc" instead of "Infrastructure".  I changed it back to "Infrastructure", and now it tries to connect???

1)  After 2 min, the icon (segment of an arc of rings) is still active, looking like it's trying to connect -- then it pops up the "Authentication requred by wireless network" window and has all the info (WPA & WPA2 Personal + PW), and then tries to connect again.
2)  When I click on "desktop" (the name of my router), I have to input my PW for the router, AND again for the Keyring.
3)  The icon for "desktop" in the connection pop-up window has a lock, as it should
4)  After a few tries, it quits and tells me I'm offline, but leaves "desktop" there and I can click on it and try again... 

Something is working better, as now the router sees the notebook... but no connection from the Ubuntu side...

Ubuntu sucks when it comes to networking, imho...  It says I've never used my eth0, and it's connected right now!!

Still attempting to connect...

---

### Post by dkolars on 2011-01-07
Lots of digging:

[http://ubuntuforums.org/showthread.php?t=1623460](http://ubuntuforums.org/showthread.php?t=1623460)

[http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html](http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html)

[http://ubuntuforums.org/showthread.php?t=1610829](http://ubuntuforums.org/showthread.php?t=1610829)

Seems as tho' ALL of these solutions worked... kinda.... sorta... not really.

I can do the above tweaks, and after rebooting, I have the choice of "Create new wireless network", or "Connect to hidden wireless network".

In 9.10, if I was in range of a wireless network, it would be listed, and I could connect (unless it was a secure network, of course)...  Here at home, why does the laptop not see my router?  Why is the word "hidden" in there?

I created a new wireless network, using the name of my router, and when I click on connect, initially, it tried to connect.  NOW, it stops instantly, and goes back to "Wireless is disabled".

So, I deleted all the wireless networks, rebooted, and created a new one.  NOW, it needs my PW again, as the Login Ring was not unlocked when I logged into the system.  Wha???  So, I click on "connect", and my network icon disappeared.  Plugging in my RJ45 did not bring it back, but the connection shows up in the Network Tools.  Cannot ping.  Reboot... now I need to Enter Password to unlock my login keyring...  And, "wireless is disabled"...

Enter WAN addy into BSSID, same result... attempt to connect, and "wireless is disabled"...  When I created the connection, Ubuntu set the Mode to "Ad-hoc" instead of "Infrastructure".  I changed it back to "Infrastructure", and now it tries to connect???

1)  After 2 min, the icon (segment of an arc of rings) is still active, looking like it's trying to connect -- then it pops up the "Authentication requred by wireless network" window and has all the info (WPA & WPA2 Personal + PW), and then tries to connect again.
2)  When I click on "desktop" (the name of my router), I have to input my PW for the router, AND again for the Keyring.
3)  The icon for "desktop" in the connection pop-up window has a lock, as it should
4)  After a few tries, it quits and tells me I'm offline, but leaves "desktop" there and I can click on it and try again... 

Something is working better, as now the router sees the notebook... but no connection from the Ubuntu side...

Ubuntu sucks when it comes to networking, imho...  It says I've never used my eth0, and it's connected right now!!

Still attempting to connect...

---

### Post by dkolars on 2011-01-07
Lots of digging:

[http://ubuntuforums.org/showthread.php?t=1623460](http://ubuntuforums.org/showthread.php?t=1623460)

[http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html](http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html)

[http://ubuntuforums.org/showthread.php?t=1610829](http://ubuntuforums.org/showthread.php?t=1610829)

Seems as tho' ALL of these solutions worked... kinda.... sorta... not really.

I can do the above tweaks, and after rebooting, I have the choice of "Create new wireless network", or "Connect to hidden wireless network".

In 9.10, if I was in range of a wireless network, it would be listed, and I could connect (unless it was a secure network, of course)...  Here at home, why does the laptop not see my router?  Why is the word "hidden" in there?

I created a new wireless network, using the name of my router, and when I click on connect, initially, it tried to connect.  NOW, it stops instantly, and goes back to "Wireless is disabled".

So, I deleted all the wireless networks, rebooted, and created a new one.  NOW, it needs my PW again, as the Login Ring was not unlocked when I logged into the system.  Wha???  So, I click on "connect", and my network icon disappeared.  Plugging in my RJ45 did not bring it back, but the connection shows up in the Network Tools.  Cannot ping.  Reboot... now I need to Enter Password to unlock my login keyring...  And, "wireless is disabled"...

Enter WAN addy into BSSID, same result... attempt to connect, and "wireless is disabled"...  When I created the connection, Ubuntu set the Mode to "Ad-hoc" instead of "Infrastructure".  I changed it back to "Infrastructure", and now it tries to connect???

1)  After 2 min, the icon (segment of an arc of rings) is still active, looking like it's trying to connect -- then it pops up the "Authentication requred by wireless network" window and has all the info (WPA & WPA2 Personal + PW), and then tries to connect again.
2)  When I click on "desktop" (the name of my router), I have to input my PW for the router, AND again for the Keyring.
3)  The icon for "desktop" in the connection pop-up window has a lock, as it should
4)  After a few tries, it quits and tells me I'm offline, but leaves "desktop" there and I can click on it and try again... 

Something is working better, as now the router sees the notebook... but no connection from the Ubuntu side...

Ubuntu sucks when it comes to networking, imho...  It says I've never used my eth0, and it's connected right now!!

Still attempting to connect...

---

### Post by dkolars on 2011-01-07
Lots of digging:

[http://ubuntuforums.org/showthread.php?t=1623460](http://ubuntuforums.org/showthread.php?t=1623460)

[http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html](http://pkadetiloye.blogspot.com/2010/11/ubuntu-wireless-disabled-siocsifflags.html)

[http://ubuntuforums.org/showthread.php?t=1610829](http://ubuntuforums.org/showthread.php?t=1610829)

Seems as tho' ALL of these solutions worked... kinda.... sorta... not really.

I can do the above tweaks, and after rebooting, I have the choice of "Create new wireless network", or "Connect to hidden wireless network".

In 9.10, if I was in range of a wireless network, it would be listed, and I could connect (unless it was a secure network, of course)...  Here at home, why does the laptop not see my router?  Why is the word "hidden" in there?

I created a new wireless network, using the name of my router, and when I click on connect, initially, it tried to connect.  NOW, it stops instantly, and goes back to "Wireless is disabled".

So, I deleted all the wireless networks, rebooted, and created a new one.  NOW, it needs my PW again, as the Login Ring was not unlocked when I logged into the system.  Wha???  So, I click on "connect", and my network icon disappeared.  Plugging in my RJ45 did not bring it back, but the connection shows up in the Network Tools.  Cannot ping.  Reboot... now I need to Enter Password to unlock my login keyring...  And, "wireless is disabled"...

Enter WAN addy into BSSID, same result... attempt to connect, and "wireless is disabled"...  When I created the connection, Ubuntu set the Mode to "Ad-hoc" instead of "Infrastructure".  I changed it back to "Infrastructure", and now it tries to connect???

1)  After 2 min, the icon (segment of an arc of rings) is still active, looking like it's trying to connect -- then it pops up the "Authentication requred by wireless network" window and has all the info (WPA & WPA2 Personal + PW), and then tries to connect again.
2)  When I click on "desktop" (the name of my router), I have to input my PW for the router, AND again for the Keyring.
3)  The icon for "desktop" in the connection pop-up window has a lock, as it should
4)  After a few tries, it quits and tells me I'm offline, but leaves "desktop" there and I can click on it and try again... 

Something is working better, as now the router sees the notebook... but no connection from the Ubuntu side...

Ubuntu sucks when it comes to networking, imho...  It says I've never used my eth0, and it's connected right now!!

Still attempting to connect...

---

### Post by dkolars on 2011-01-09
Well, it's on-line, but I'm not sure how?

I tried Wicd...  that connected once, then never functioned properly on the system again... I uninstalled it, re-installed it, got ALL kind of cryptic messages that it couldn't load, etc.

So, got rid of it, and went back to Network Manager.

It tried to connect, and just couldn't, BUT it never disabled the card.

I messed with the router settings -- why I would have to after having the laptop work with 9.10???  But, gotta try everything...  When I switched the Wireless Mode from "11b + 11g"  to "11g only", the wireless connected instantly, shows the available networks (mine and the neighbors!), and doesn't ask me to connect to a hidden wireless network.  

So, it's fixed, apparently by changing a router setting... a setting that worked just fine before... Why would the OS software upgrade affect the way the wireless card and router interacted?   Dunno, but it's working, and I can get on with my life!

dk

---

