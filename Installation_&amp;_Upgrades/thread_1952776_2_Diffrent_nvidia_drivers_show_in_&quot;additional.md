---
title: "2 Diffrent nvidia drivers show in &quot;additional drivers&quot; with should i choose"
date: 2012-04-04
forum: Installation &amp; Upgrades
---

### Post by nico23 on 2012-04-04
fresh kubuntu 12.04 install:

one says "...(corrent version) [recommended]"
and the other one "(version-current-updates)"

should i get the 2nd one for newer version? will this update automatically? what it the diffrence?

---

### Post by critin on 2012-04-05
> **nico23 said:**
> fresh kubuntu 12.04 install:

one says "...(corrent version) [recommended]"
and the other one "(version-current-updates)"

should i get the 2nd one for newer version? will this update automatically? what it the diffrence?

Probably depends on your card.  Is it working good now--without changing the driver?  "Recommended" should work-   Does it say it's not activated?  

Yes, they do update automatically, though the "recommended" has been the same version for mine forever.
 I usually have as good or better luck with the nouveau, but I have an old card and don't care to run 3D affects.

---

### Post by nico23 on 2012-04-05
first of all fullquotes suck and are forbidden on good forums, and direct replies with fullquotes such even more.

i said fresh install so you could guess pretty easy to guess that both are not activated. i am asking the question because i want to ask wich one i should choose. use your brain! dont post if you not actually can help. i also dont understand this word > nouveau

i not asked for a working driver i asked what driver its never. u did not andswer that question!
i was just confused with the german and english language used (i am german).

[IMG]http://img6.imagebanana.com/img/8ry305kh/snapshot1.png[/IMG]

current version = latest version? i guess not. so i just took the 2nd one and after thinking about it i am more sure that this one is more up-to-date and i want the "latest" driver through that machanism i know i can maybe can get an even more up-to-date one with manual install but this is fine for me.

now the others can come and start the hating on me for beeing unpolite ...

---

### Post by critin on 2012-04-05
> 
i said fresh install so you could guess pretty easy to guess that both are not activated. 

No I could not guess.  Apparently** a card** **was activated during the install** or you would not have been able to see the desktop.  The screen would have been dark.  Only you would know if the "recommended" or another was activated or not.  Only one is activated.

A nouveau driver is an open source driver and the choice to choose it is among "additional drivers" if there is no newer nvidia driver for the installed card.

I'm glad you got it figured out and it works for you.

---

### Post by nico23 on 2012-04-07
???
well as i understand the "Aditional drivers" tool in Ubuntu is to activate propriatary drivers for your card.

when you install ubuntu the open source driver is automatically activated. and its not in the aditional drivers! like you see in the screenshot. so both options are not activated thats the usual way you get after a install. in the past i had just one option there thats all. and there will never be a activated driver after a fresh install in this dialog in ubuntu, maybe in mint or something but not in ubuntu! if someone proves me wrong on this i am fine with this but i guess nobody will. so yes you could have gussed it.#

// lol now i know what [nouveau]("http://en.wikipedia.org/wiki/Nouveau_%28software%29") is, to me it sounds like a french word for new or something like that.

---

### Post by dino99 on 2012-04-07
both drivers does not makes difference right now:

- activate nvidia-current
 (its the default driver for the related release, aka Precise)

- nvidia-current-updates
as its name let you know, you will get "updates" that are not "by default" supposed to be used by Precise (like the "proposed" archive into sources.list)

As Precise is the latest ubuntu release, you will only see difference when QQ will be the dev release, or when nvidia will pushed a newer version. For example, 295.33 is the latest driver in Precise, and might be the latest, then only "security" fix will be accepted by default.

---

