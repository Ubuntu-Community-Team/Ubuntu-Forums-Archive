---
title: "Linux Mint 16 Cinnanon, Atheros wifi"
date: 2014-04-29
forum: MINT
---

### Post by eagleBZ on 2014-04-29
Hi, for almost every day about a week or so ago i was going over to a friend's house (they asked me to wipe the windows OS's off of both of their PC (they have 2  desktops) and install Linux on them.) I did this to both of their PC's already early last week, had no problem getting their living room PC (it indicated it was online during the Linux install checklist) online, it worked "right out of the box" kind of, but their bedroom PC, after I wiped that HDD, installed Linux, its Linux install checklist (when the DVD I made from the Linux Mint Cinnanon ISO before installing it on their PC's booted up to install, that is) indicated it was not online, I proceeded to install linux anyway, Ok, so all last week I kept trying to get their bedroom PC online, and so last time I was over their house I got this data from their bedroom PC:

--command I used: nm-tool
says (user name) network is disconnected

next I did
--lshw -C network
it gave me this output:
(it says I have to log in as a super user - but how do I do that? (I'm brand new to linux) 
(terminal output)
--*-network
--Descr wireless interface
--physical ID 1
--bus info usb@2:5
--logical name wlan0
--serial 00:26:f2:51::26:74
--capabilities ethernet physical wireless
--config broadcast = yes, 
--driver = ath9k
--htc version = 3.11.0-12 generic
--firmware = 1.3 
--link no
--multicast = yes
--wireless = IEEE 802.11 bgn

this is all the data I got from their PC in the bedroom. they have a Netgear USB dongle (it even comes with a little stand where the dongle plugs into via its USB into this stand itself, while the stand + dongle setup has its own cable that, itself, also plugs into a USB port on that PC) It wouldn't connect to online either with this whole unit plugged into the computer or when I tried unplugging the dongle out of its stand and plugging the dongle only into a USB port on this PC.

How can I get this PC online?

Thanks in advance.

---

### Post by Bashing-om on 2014-04-29
eagleBZ; Hi ! Welcome to the forum.

Often times getting wireless up is a process of a different color. Easier done if one has access to a wired connection.

Does the box in the living room have a wired internet connection ? Take that box to the wired connection and run terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

``` and maybe, just maybe - the wireless driver will also be updated and become functional.

I have seen threads here where getting the "driver = ath9k" functional can be a bit trying - but I have seen it done.

[INDENT][INDENT]hey, it could happen
[/INDENT][/INDENT]

---

### Post by eagleBZ on 2014-04-30
> **Bashing-om said:**
> eagleBZ; Hi ! Welcome to the forum.

Often times getting wireless up is a process of a different color. Easier done if one has access to a wired connection.

Does the box in the living room have a wired internet connection ? Take that box to the wired connection and run terminal commands:
```

sudo apt-get update
sudo apt-get upgrade

``` and maybe, just maybe - the wireless driver will also be updated and become functional.

I have seen threads here where getting the "driver = ath9k" functional can be a bit trying - but I have seen it done.
[INDENT][INDENT]hey, it could happen
[/INDENT]
[/INDENT]


I feel kind of dumb to ask this question, but do you mean I have to disconnect their bedroom computer (tower only), carry it to their living room PC tower, connect their two towers together, and somehow run these commands to try to update the bedroom PC's wireless drivers or what?

---

### Post by Bashing-om on 2014-04-30
eagleBZ; Nope,

There is nothing 'dumb' about asking for deeper explanation. We all have to learn somewhere, and here is a better source of information.

IF that living-room box is hard wired (cable modem) to the internet, disconnect that box completely, and put in place - all wired up - the box from the bed room.
Such that now the box that has the WIFI problem is on that wired connection. At this point with out the WIFI dongle attached.
run the terminal codes:
```

sudo apt-get update
sudo apt-get upgrade

```
Now attach the WIFI dongle and see if from the network manager that you can enable wireless. It is possible that the hard wire will need to be disconnected to get WIFI to activate, after all updates/upgrades are completed and the internet connection closed out in the desk top.
NOW IF the living room box is routed to a router, and you have a spare ethernet cable, why just hook that broke system up also to that router, will not even have to do anything with the "good" box.

All we want is is a hard wired connection to the internet so the broke system has access to ubunt's repository of packages in order to update.

1 answered question is worth a thousand uh oh's

---

### Post by howefield on 2014-04-30
Thread moved to the "*Other OS/Distro Support*" forum.

---

