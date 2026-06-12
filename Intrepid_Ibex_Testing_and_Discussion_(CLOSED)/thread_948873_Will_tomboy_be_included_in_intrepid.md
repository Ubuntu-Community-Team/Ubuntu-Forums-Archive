---
title: "Will tomboy be included in intrepid?"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by zorkerz on 2008-10-15
Today to my horror updates to intrepid removed tomboy! This is easily my most used and valued application on ubuntu. It is one of the few applications that I use that is relatively unique to ubuntu that is as compared to mac or windows.

Does anyone know the reason for tomboy being removed?

It appears that mono 2.0 has been released, which is the platform that tomboy runs on. I believe some of the updates today were for mono. Could this be a temporary thing as mono is updated in ubuntu?

I asked a question about this on launchpad [https://answers.launchpad.net/ubuntu/+question/48106](https://answers.launchpad.net/ubuntu/+question/48106)

---

### Post by zorkerz on 2008-10-15
I just remembered that f-spot was also removed with the same update this makes me think it is very likely this is only a temporary situation.

---

### Post by FuturePilot on 2008-10-15
> **zorkerz said:**
> Today to my horror updates to intrepid removed tomboy! This is easily my most used and valued application on ubuntu. It is one of the few applications that I use that is relatively unique to ubuntu that is as compared to mac or windows.

Does anyone know the reason for tomboy being removed?

It appears that mono 2.0 has been released, which is the platform that tomboy runs on. I believe some of the updates today were for mono. Could this be a temporary thing as mono is updated in ubuntu?

I asked a question about this on launchpad [https://answers.launchpad.net/ubuntu/+question/48106](https://answers.launchpad.net/ubuntu/+question/48106)
Tomboy is still here for me. Maybe it was just an odd glitch in the upgrade?

---

### Post by zorkerz on 2008-10-15
Possibly but when I reinstalled tomboy i also needed to reinstall all of its old mono dependencies. 

Do you have all your update categories (security, recommended, pre-release,and unsupported backports) checked in system->administration->software sources?

It could just be a pre-release/proposed update or you may be using a mirror that has not synced with the main one yet.

---

### Post by jblackhall on 2008-10-15
It's probably temporary.  Partial Upgrade = the devil :)  Pay attention to what's being removed the next time you do your updates and you won't scare yourself like that again.

---

### Post by zorkerz on 2008-10-15
Your right jblackhall partial upgrades do some odd things also proposed updates can be a pain. I did notice it was removing tomboy i just can't resist my desire to update no matter the consequences. 
                                                         :~)

---

### Post by FuturePilot on 2008-10-15
> **zorkerz said:**
> Possibly but when I reinstalled tomboy i also needed to reinstall all of its old mono dependencies. 

Do you have all your update categories (security, recommended, pre-release,and unsupported backports) checked in system->administration->software sources?

It could just be a pre-release/proposed update or you may be using a mirror that has not synced with the main one yet.

I have all of those except Pre-Release. I usually avoid using Pre-Release unless I need to test a package in there because sometimes that repo can cause problems.

---

### Post by directhex on 2008-10-15
Mono 1.9.1+dfsg-4ubuntu1 was added to the archive today

It's possible it wasn't all in the archive at the same time when you ran your upgrade, ESPECIALLY if you run amd64 instead of i386 (the platform-independent mono components are built only on i386 systems, the amd64-only bits are built on their own)

---

### Post by zorkerz on 2008-10-15
Ya im running amd64 I had not thought about a delay in those packages. That makes much sense to me. Another partial upgrate at the moment. Ive been procrastinating my studying for a midterm all day. My main strategy is to try and update every few seconds and find things to talk abotu online.

---

### Post by directhex on 2008-10-15
Intrepid will definitely ship with Tomboy and F-Spot, as with previous releases. you were caught by a transient repository problem, something you need to get used to when running a development branch. As jblackhall says, don't let partial upgrades remove things until you check what it wants to remove

---

### Post by zorkerz on 2008-10-15
Im glad to here its a transitory thing. Im used to/can handle temporary issues like this I just let myself get scared someone had decided to remove tomboy. Again thanks for all the input.

---

### Post by Sef on 2008-10-15
Normal for testing for things to not work a few days.  It was frustrating, but glad Tomboy is back.

---

