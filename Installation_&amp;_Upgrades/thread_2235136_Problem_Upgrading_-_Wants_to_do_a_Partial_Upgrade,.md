---
title: "Problem Upgrading - Wants to do a Partial Upgrade, Is this safe for my xbmc install?"
date: 2014-07-19
forum: Installation &amp; Upgrades
---

### Post by Chanester on 2014-07-19
[COLOR=#333333][FONT=UbuntuRegular]Running software update gives me this: [IMG]http://i.stack.imgur.com/be9pV.png[/IMG]
Clicking partial upgrade gives me: [IMG]http://i.stack.imgur.com/sAgg2.png[/IMG]
It seems that it wants to remove (at least some portion of) xbmc. Is this safe to do without effecting my xmbc install? I'm quite happy with the way that it works, but am tiring of ubuntu nagging me periodically that it cannot do this update.
My xbmc is 12.2 "Frodo" and my os is 12.04.


[/FONT][/COLOR]

---

### Post by grahammechanical on 2014-07-19
Those of us who run the Ubuntu development branch are often offered a partial upgrade. We never take up the offer. We just click continue. I took up the offer just once. It broke the desktop. And that is the risk that you run.

Look at the reasons that the utility is giving you. Do any of them apply? Do you have the Proposed repositories enabled? Have you installed XBMC through a PPA? Is XBMC a beta version? If this is XBMC installed on to Ubuntu, then you can re-install it. If this is stand alone XBMC then you need to back up your data because you may need to re-install. 

Regards.

---

### Post by Chanester on 2014-07-19
I believe I installed it from the Software Centre, certainly it shows up as installed in there when I browse to it in SC.

---

### Post by Chanester on 2014-07-26
[COLOR=#333333][FONT=UbuntuRegular]The problem was caused because the system was using the [nathan rennie-waldock PPA]("https://launchpad.net/~nathan-renniewaldock/+archive/ubuntu/xbmc-stable") for xmbc instead of the [team xbmc]("https://launchpad.net/~team-xbmc/+archive/ubuntu/ppa") one which is now the official one.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I backed up the .xbmc folder in /home and let the update run.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]After performing this partial update caused xbmc to be removed. I changed by PPA for xbmc to the official one and tried to reinstall to 13.1 (Gotham). However the xbmc-bin has been left kicking (note it was in the upgrade section, not remove in the original question) around so I first had to sudo apt-get remve xbmc-bin. Once done I could reinstall xbmc from the official PPA. My user data was preserved.1[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]1 Note - I store my db into a mysql database, so YMMV. Additionally, this database had been upgraded to Gotham via another xbmc on the network. I'm not 100% sure this all would have worked without that being done prior.[/FONT][/COLOR]

---

