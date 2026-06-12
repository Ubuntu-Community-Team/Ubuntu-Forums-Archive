---
title: "clean install"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by DarinB on 2009-12-18
I have a friend that is a computer illiterate. I mean a complete non computer user the kind that with an intrepid on her pc she deleted her network manager from her top panel and her windows list from her bottom one and swears she did nothing......sheesh!
Well on to my question. 
pentium 4 about a gig and a half of ram with an intel 01 graphics on the motherboard. 
i was thinking of putting jaunty on it since that is what i use and i can set it up like mine so i can help her on the phone easier.
question 1. can i copy my ppa's and keys on to a thumb and put them in for her?
or do i have to go hunt for them from scratch I would just love to simply or some how just throw my system on to her hdd.

---

### Post by DarinB on 2009-12-18
never did this but clone it to her hdd? is that something that actually is possible?

---

### Post by letsflyakite on 2009-12-18
not sure if this is what your after but you might want to check out a package called PartImage, which can take your whole hda into an image file, then you can restore into your friend's hda, so she will have an exactly same system as yours.

---

### Post by raymondh on 2009-12-18
aptonCD to transfer apps and dependencies.  I have used it to transfer Jaunty to jaunty.  

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by raymondh on 2009-12-18
> **letsflyakite said:**
> not sure if this is what your after but you might want to check out a package called PartImage, which can take your whole hda into an image file, then you can restore into your friend's hda, so she will have an exactly same system as yours.

The challenge will be the hardware differences between both systems.

---

### Post by Cheesemill on 2009-12-18
> **raymondh said:**
> The challenge will be the hardware differences between both systems.

No it wont. Ubuntu detects the hardware on every boot and loads the correct drivers (unlike Windows which would fail miserably). I've moved an install between different machines countless times with no problems.

The only thing you have to do is disable the Graphics drivers first if going from ATI to nVidia or vice versa (you can enable the correct driver afterwards).

---

### Post by raymondh on 2009-12-18
> **Cheesemill said:**
> No it wont. Ubuntu detects the hardware on every boot and loads the correct drivers (unlike Windows which would fail miserably). I've moved an install between different machines countless times with no problems.

The only thing you have to do is disable the Graphics drivers first if going from ATI to nVidia or vice versa (you can enable the correct driver afterwards).

You may be right, cheesemill.  But I had challenges with the wifi (finally resorting to ndiswrapper) and the touchpad moving a cloned install from a dell laptop to an HP netbook.  maybe I was just unlucky :)

Regards,

---

### Post by Cheesemill on 2009-12-19
You could also use [Remastersys]("http://geekconnection.org/remastersys/remastersystool.html") to create an installable .iso from your current setup.

---

### Post by DarinB on 2009-12-19
I made the .iso of my system, but it is 1.2 GB, do I need a dvd r and how do I know what kind -r +r, how do I find out what type I have I have never burned a dvd before.

---

