---
title: "Help install ubuntu to AOpen machine"
date: 2017-08-08
forum: Installation &amp; Upgrades
---

### Post by bpkpq4 on 2017-08-08
Okay, my last machine burned out and I've been towerless for a year or so (trying to save up money for a new machine, but life finds a way of making other things more important).

My level of expertise is pretty stinking low, so please bear with me.
---
Recently picked up an old XP machine for free due to how bad an idea it is to try to run an XP machine online these days.

I decided to try to install Ubuntu and see what I could get out of it, but the standard installation instructions have me rather stuck.

First solution I tried was the boot to USB option (machine seems to have a CD drive, not a DVD and I'm not sure if it can burn or only read), since I have a ready supply of USB sticks with sufficient memory.

Computer doesn't seem to recognize the flash drives. I went into the BIOS and set it to only boot to USB ZIP and then to only USB FDD (there were only two options labeled as USB). Neither worked (my bootable flash drive was created via Rufus according to canonical instruction). The computer didn't seem to recognize the disk as a bootable drive.

A little bit of research: my motherboard reads as AOpen Mx46-533V. A google search for "boot to usb" for that motherboard turns up a manufacturer website with a driver download that mentions allowing boot to usb in broken english. Research also suggests that updating my BIOS with a driver is a great way to brick the whole machine if I don't know what I'm doing (and I certainly don't).
---
Exploring alternative options, I heard my father suggest WUBI, since the machine boots to XP just fine. The thought then being I could install Ubuntu 12 inside windows, then upgrade to a more recent version of Ubuntu from there.

It might not surprise you to hear that WUBI keeps failing. The error log seems to indicate that it's failing to acquire the necessary packages due to a 404 error from a website. I suspect canonical has abandoned WUBI for so long that it no longer maintains the download links that WUBI is trying to use.
---
I toyed with the idea of a Network install, since I have a Windows 10 laptop (my wife's computer, so that's why I'm not installing to that machine instead) that is perfectly functioning, but what little I could understand of that process didn't give me much hope that I would find more success from that route.
---
I wish I could give better info about the kind of help I need, but honestly I'm getting so little information from my google searches that I'm not even sure what kinds of information I need to give you folks or what kind of questions I should be asking my search engines.

Anyone have a clue which way I should go? My only consolation in all this is that the machine was free to me, so nothing is lost if I end up pitching the whole thing. Still, hate to waste a perfectly functioning machine if I can avoid it.

Cheers. 
Ben

---

### Post by mörgæs on 2017-08-09
Hi, welcome to the fora.

> **bpkpq4 said:**
> A little bit of research: my motherboard reads as AOpen Mx46-533V. A google search for "boot to usb" for that motherboard turns up a manufacturer website with a driver download that mentions allowing boot to usb in broken english. Research also suggests that updating my BIOS with a driver is a great way to brick the whole machine if I don't know what I'm doing (and I certainly don't).


Have you seen warnings that the BIOS update is dangerous for this particular motherboard?

---

### Post by bpkpq4 on 2017-08-09
> **mörgæs said:**
> Hi, welcome to the fora.



Have you seen warnings that the BIOS update is dangerous for this particular motherboard?

No, not specifically, but it seemed to be a general warning I kept finding.

I want to thank everyone reading this for taking the time, but as I explored the sticky thread about WUBI, it took me to the wiki where I found that I could manually download the desktop CD iso, put it in the same folder as wubi.exe, and wubi would be able to install that way.

It seems to be installing now. We can probably close this thread.

---

### Post by yancek on 2017-08-09
If you read the Ubuntu WUBI documentation then you know that is has not been supported for years and only runs inside your windows install so if you remove or have a problem booting your windows xp you will not be able to access Ubuntu either.  The Wubi installer puts an entry in the windows boot file (boot.ini with xp).  I would expect  some serious problems if you are using a current Ubuntu as it is going to be much too heavy to run well.  If things don't go well with this install, you might post back and get some advice for Ubuntu variants on an older machine or just Linux on older machines.  Good luck.

---

### Post by mörgæs on 2017-08-09
If you haven't seen warnings for the motherboard in question I suggest that you go ahead and update. After that a clean install of Lubuntu, wiping Windows and Wubi in the process. 

I have updated BIOS on many different computers, never with any bad results. I more or less do it by default when I get old hardware in for repair unless I see a specific warning.

---

