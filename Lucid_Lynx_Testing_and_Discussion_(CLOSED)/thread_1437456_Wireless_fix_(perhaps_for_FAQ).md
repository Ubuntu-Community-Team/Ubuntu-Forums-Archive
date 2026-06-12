---
title: "Wireless fix (perhaps for FAQ)"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Squatter on 2010-03-23
I never could get wireless to work on an old (Intel 2200 based wireless chip) laptop.  This applied to 9.04, 9.10 and now 10.04.  Windows and OSX laptops worked fine but Ubuntu would only work when connecting with an open router (ie no WPA, WPA2).

The same laptop worked fine when it was a Windows laptop.  Ubuntu would see all the local routers but be unable to login and always reported "bad password".

I tried everything from the default network manager to manual configuration of wpa_supplicant and finally wicd.  When 10.04 also failed to work correctly, I got serious.  Eventually, I got stuck into the wicd templates.  Templates are just another way of automating the wpa_supplicant way of doing things.

Eventually, I cracked it but only after determining that this issue seemed to be specific to my wireless router (an ASUS RT-N11).  The router allows TKIP or AES with WPA and WPA2 but not both.  So the commonly used (& recommended) wpa_supplicant template did not work.  It required a specific template which only supported whichever encryption method was configured in the router.  So (in my case) WPA required TKIP and WPA2 required AES.

My successful wpa_supplicant entries (or wicd templates) included :
For WPA with TKIP :
proto WPA[COLOR=Red] not WPA RSN[/COLOR]
key-mgmt WPA-PSK
pairwise TKIP[COLOR=Red] not CCMP TKIP[/COLOR]
group TKIP[COLOR=Red] not CCMP TKIP[/COLOR]

For WPA2 with AES :
proto RSN [COLOR=Red]not WPA RSN[/COLOR]
key-mgmt WPA-PSK
pairwise CCMP [COLOR=Red]not CCMP TKIP[/COLOR]
group CCMP [COLOR=Red]not CCMP TKIP[/COLOR]

This required creating 2 new templates for wicd (quite simple).

I have seen many reports of similar problems but no-one seems to have publically acknowledged solutions.  So if you have the problem, it may work for you.  It does suggest that the ASUS router or even the Intel ipw2200 Linux driver is not quite observing a protocol correctly.

I should add that I went back to a couple of HOWTOs and the solution is there but not obvious.  And for someone not wishing to get hands dirty with wpa_supplicant, this is a big problem.  At least with the wicd template change, one is back to a working gui wireless management interface which really ought to be the goal.

I would send this to the wicd forum but it is currently closed.  Maybe I will look at the default network manager to see how that should be fiddled to make it work.

---

### Post by psyke83 on 2010-03-23
You really, really, really need to file a bug, rather than post information here.

Also, why are you connecting without encryption? You're exposing yourself to security risk, especially for all non-secure transmissions.

(And let's not make this an issue of freedom, because it's not. Give friends the password to your router if you want to share the connection ;)).

---

### Post by Squatter on 2010-03-24
Firstly, I am not sure if it is a bug or user error.  Maybe someone could have provided the gem of information that I required.

Secondly, I merely tried no encryption as this type of "bug" has been reported elsewhere.  So I confirmed that no encyption presented no problem.  And in any case, the open wireless router was not connected to anything else when I tested it.  This scenario only existed for 5 minutes.

I run this laptop off ethernet as its battery means it is not too mobile anymore.  And its age, not worth a new battery.

I reported a bug once before and was politely told to RTFM.:rolleyes:

---

### Post by Squatter on 2010-03-31
The above fix worked until the next reboot and everything is back to not working again.  Maybe when Lucid Beta 2 is out, I will re-visit this issue again.

---

