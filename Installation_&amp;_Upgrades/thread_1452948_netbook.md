---
title: "netbook"
date: 2010-04-12
forum: Installation &amp; Upgrades
---

### Post by jklopez on 2010-04-12
i was just wondering if i could install ubuntu on a augen oe-a736 netbook ,it has no dvd-drive or hdd ,i dont think it has a bios either ,i dont want to dual boot or anything just a full install of ubuntu ,is it possible via usb ,i installed ubuntu on laptops with a usb .the netbook is my 7yr old son's and the point is to play online flash games and stuff witch win ce 5.0 dose not support,thanx 4 any help...

---

### Post by drreed on 2010-04-13
> **jklopez said:**
> i was just wondering if i could install ubuntu on a augen oe-a736 netbook ,it has no dvd-drive or hdd ,i dont think it has a bios either ,i dont want to dual boot or anything just a full install of ubuntu ,is it possible via usb ,i installed ubuntu on laptops with a usb .the netbook is my 7yr old son's and the point is to play online flash games and stuff witch win ce 5.0 dose not support,thanx 4 any help...


Since nobody else jumped on this . . .my answer is go for it. You might want to try a network install with it, since you can't use a dvd then why not kick your skills up a notch?

Hehehe

The usb stick would be cool too. I have a spare so I think I'll try it tomorrow. I'd like to be able to just whip out my memory stick and boot any PC with Linux. Your son will think you're from "Mission Impossible"

---

### Post by EmmaMadeleineMcDonald on 2010-04-13
Netbook are a branch of subnotebooks, a rapidly evolving category of small, lightweight, and inexpensive laptop computers suited for general computing and accessing Web-based applications; they are often marketed as "companion devices", i.e., to augment a user's other computer access.

---

### Post by scu-ba-de-buntu on 2010-08-21
I know this is an old post, but it is the only other on besides my post on another thread ([here (#995)]("http://ubuntuforums.org/showthread.php?t=1349626")) that involves this netbook.

Note I am not sure yet of the status of this netbook and linux. It is either ported or almost ported. Ubuntu on the other hand is a distro of linux that to my understanding has not been ported to this machine. You should be able to make xbuntu or something run on it after the SoC porting is tackled. There exists various other distros which would be more suited to this notebook however.

What follows is information you should know about this netbook:

The Augen e-go you are referring to here is an ARM based computer. This means that the processor has a different architecture than has been adopted as the mainstream standard known as IA32 (Intel Architecture, 32-bit) which is commonly refereed to as simply "x86". It should be noted that the speed of this ARM processor is independent of the fact that is a different architecture. What this means to you is that when software is being compiled from source code, it is converted from human readable information to information that tells the machine specifically where to put data on a hardware level. In other words, software would have to be recompiled for this architecture (assuming no architecture specific functions calls were part of the code - read "porting"). For the most part linux works on ARM processors. This netbook is a SoC (System-on-Chip) which means that for linux to work on it, it requires porting. You can read more about the work on this [here]("http://ubuntuforums.org/showthread.php?t=1349626").


Cheers.

---

