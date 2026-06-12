---
title: "planning to install ubuntu 8.10 beta A question"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by xnostradamusx on 2008-10-20
when 8.10 is finally released do i need to download the final release or i can still use the 8.10 beta i downloaded and 
change only some few files there?

---

### Post by renzokuken on 2008-10-20
you could install the beta and use it for now, and as soon as the final version of 8.10 is released your Update Manager will take care of ubgrading the beta to the final version

---

### Post by xnostradamusx on 2008-10-20
ahh thanks for the fast reply... so regarding bugs which is notified by devs while using the ubuntu 8.10 beta if my update manager update it to the final release if it was solved in the final release will it be the same with my beta. will there be any difference regrding from update from beta to final release or just downloading the final release itself?

---

### Post by renzokuken on 2008-10-20
there shouldnt be any difference between a fresh install of the final version, and a beta updated to the latest version.

all the update process is doing is replacing the buggy/outdated packages in the beta, with the (hopefully) secure and stable version of the packages that made it into the final release

---

### Post by xnostradamusx on 2008-10-20
ok ill download the beta now cause i cant wait till the release

hope when the day of release came my ubuntu beta will update itself and replicate as if its the same as the one been release which is the stable one

---

### Post by forumache on 2008-10-20
> **xnostradamusx said:**
> ok ill download the beta now cause i cant wait till the release

hope when the day of release came my ubuntu beta will update itself and replicate as if its the same as the one been release which is the stable one

It will update itself everyday (should you accept the notification) coming closer and closer to the final release. It is a smooth process generally.
Usually on the day of the release you get no updates, as all the updates were already applied during the previous days, you already have the final release a little bit earlier than other people ;)

---

### Post by xnostradamusx on 2008-10-20
i see so theres no problem then but last question does 8.10 support atheros wireless card in that release? cause i have 8.04 but i only manage to use it using some guides to make it work

---

### Post by forumache on 2008-10-20
I have 2 Atheros wireless cards (one on desktop, the other one on laptop) and both worked since Ubuntu 6.06.

You need to know your particular model. I think on the laptop I have something like AR5212...

There are 2 opensource drivers for Atheros, one of them is ath5k the other ath9k. Both my cards are supported by ath5k, no problems whatsoever. You need to check if your model is supported.

Better yet: boot the livecd. If it will detect your card and offer a list of access points, then it is supported out of the box, you are lucky. If not, it will work with some efforts, or not at all.

It's easy to test. Boot the beta live cd now!

---

### Post by xnostradamusx on 2008-10-20
i was using ubuntu 8.04 and my wireless card is atheros ar5006x it isnt supported by ubuntu but to make it work i have to use ndiscardwrapper
thats why i hope this coming release this card is already supported so i dont have to do all the tasks again to make my wireless work again.

---

### Post by forumache on 2008-10-20
I quote myself: "It's easy to test. Boot the beta live cd now!" :)

---

### Post by xnostradamusx on 2008-10-22
ok i already tried the ubuntu 8.10 now too many problems

first in my laptop still atheros wireless still isnt supported i checked the hardware for proprietary hardware it says no proprietary is in use then i saw my atheros wireless with a check when i click on that it says active and is in use and is supported by ubuntu funny thing is when i go to network to check for wireless there is no option to detect or connect to my wireless ap.

second try on my desktop i am trying the live cd but when it comes in the orange screen it will only turn in black then it wont load at all. i tried it in vmware with the same destop but it loads properly hmm a bug?

i tried mandriva 2009 one it runs and installs out of the box even my wireless no problem why does ubuntu dont absorb some backbone from mandriva's superb hardware detection so many people will be happy to migrate from windows to linux without facing too much headaches

---

### Post by forumache on 2008-10-22
> **xnostradamusx said:**
> ok i already tried the ubuntu 8.10 now too many problems

first in my laptop still atheros wireless still isnt supported i checked the hardware for proprietary hardware it says no proprietary is in use then i saw my atheros wireless with a check when i click on that it says active and is in use and is supported by ubuntu funny thing is when i go to network to check for wireless there is no option to detect or connect to my wireless ap.


It seems to be supported if it appeared there. Are you sure that you *left* click on the Network Manager applet in the upper right part of the screen (before the clock). It should display a list of AP it detected. Maybe your wireless ap is hidden?

---

### Post by inportb on 2008-10-22
Do you want to update the disc image itself? Try jigdo if you have the alternative installer.

---

### Post by xnostradamusx on 2008-10-22
> **forumache said:**
> It seems to be supported if it appeared there. Are you sure that you *left* click on the Network Manager applet in the upper right part of the screen (before the clock). It should display a list of AP it detected. Maybe your wireless ap is hidden?

my friend i know how to connect to wireless in 8.04 theres no difference on 8.10 it seems it sees the atheros wireless when u go to hardware but if i right click or left click there is no wlan0 or wireless which u can use. hmm if this would be the same release i think my wireless will still not work even wihh the final release

> **inportb said:**
> Do you want to update the disc image itself? Try jigdo if you have the alternative installer.

i dont have any idea regarding that i only got the ubuntu 8.10 beta

---

