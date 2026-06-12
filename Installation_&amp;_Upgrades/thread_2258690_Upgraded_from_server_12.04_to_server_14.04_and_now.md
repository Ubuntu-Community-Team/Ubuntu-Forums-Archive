---
title: "Upgraded from server 12.04 to server 14.04 and now i dont have any drivers."
date: 2014-12-29
forum: Installation &amp; Upgrades
---

### Post by rapid3642 on 2014-12-29
The title pretty much says it all. I upgraded from 12.04 to 14.04 and now i dont have any drivers. My mouse wont work, the gui doesnt allow me to login, i have to press ctrl+alt+f4 to login. I have no network access. does anyone have the same situation? The upgrade finished before restarting but after i restarted everything went down the drain.

---

### Post by nerdtron on 2014-12-29
In place upgrades are hit-or-miss. You don't even say the hardware you are using. 

Anyway I think a fresh install is always the best option to upgrade. You have backed up you data right?

---

### Post by rapid3642 on 2014-12-29
hardware is the following:
CPU: AMD 3+ 8150 eight core
Motherboard: ECS A990FXM-A
Video Card: Nvidia 640 GT
Ram: 8GB DDR3 1600 Kingston
HDD: 2TB seatgate barracuda
Power Supply: 1000w RMA

Yes data has been backed up but would take a very long time and we are talking a few days to get everything back to the way it was. so because of this i would like to fix it opposed to reinstalling.

---

### Post by MAFoElffen on 2014-12-29
So you are not running just Server edition.... Right? Since you are saying:
> 
My [COLOR=#ff0000]mouse[/COLOR] wont work, the [COLOR=#ff0000]gui doesnt allow me to login[/COLOR], i have to press ctrl+alt+f4 to login. I have no network access. does anyone have the same situation?

That implies you either just originally installed (a) Server Ed., then installed a desktop to it (b) did do-upgrade-release and gave it an option to change from server to desktop edition, somewhere since the original install (c) Intsalled an Desktop Edition and are running server services on that...

None of those really matter, but what does matter is what desktop you are using (Please supply answer to that).

What is curious is that you didn't see any error in the apport or install logs. A do-release-upgrade does keep logs... Those would indicate what went wrong.

This can be fixed without a reinstall. That is very nice, new equipment. (My hat off to you on that.) What I would try first is to do:
First, look at your source list and ensure there wasn't any pointers to PPA's. Remove those if there. Then:
```

sudo apt-get install -f

```
...Just in case there are any broken packages in that recent process. That would try to fix those broken packages and fix any unmet dependencies. if that takes care of your problems, good. If that was a problem with the upstart/init, that would explain all.

If not, then you could boot up in text mode (look at post 2 of my sticky, link in my sigline)
```

dpkg-reconfigure xserver-xorg

```
Go through the prompts to reconfigure X.
You will have to reinstall your nVidia driver after that...

Last would be to look at the network issue. Network, I look at the OSI model.
Does it have a link light? (cable plugged in and card work, physical)
Do you have a mac address? Please post
```

ifconfig -a

```
If the ports aren't coming up, then it may be a driver issue, if they are, but are not getting assigned IP's then a different problem...
Then post:
```

cat /etc/resolv.conf

```
That is built dynamically from various other things at bootup... problems there would point in oter directions...
And lastly post:
```

cat /etc/network/interfaces

```

---

### Post by rapid3642 on 2014-12-30
Thats correct. I am running a server edition of ubuntu and then i later installed the ubuntu-desktop gui overlay. Then much much later down the road i did the do-release upgrade. sorry for not being specific before.

Also thanks i tried building a decent server but only could afford desktop parts.

And i dont believe i checked the install logs, i didnt know one exisited, i only check the syslog. i'll google this and go through the report. Now as a side note when going through this upgrade there wasnt an error that i know of. nothing stopped the installation. However if i didnt even know that the installs had logs then im pretty sure there are a ton of things i missed lol. So thank you very much for pointing that out! after i do some googleing and looking through logs ill post back here. Your very kind and thank you for taking the time to reply to my post :-)

---

### Post by MAFoElffen on 2014-12-30
That's what I thought...

Did you do the testing I ask for? I need input/feedback of what the net devces are saying and the status of X...

---

