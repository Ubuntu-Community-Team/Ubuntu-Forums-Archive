---
title: "Can i run a GeForce4 MX 420 on Hardy"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by DarinB on 2008-02-28
Can i get my Geforce4 MX 420 running on hardy.
i can't upgrade my video card with out upgrading my Power Supply and the compatible on is pricey.
so i barely got my card running on feisty any ideas on hardy?????????

---

### Post by Pumalite on 2008-02-28
Maybe this helps:
[https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/173410](https://bugs.launchpad.net/ubuntu/+source/displayconfig-gtk/+bug/173410)

---

### Post by DarinB on 2008-02-28
Thank you very much i must confess though i ddin't really understand what it is talking about regarding the display config empty.
I have this old dell dimension 8200 box that runs great on feisty a few occasional issues with the geforce4 420 i was thinking of going to the LTS when it comes out, but i am worried that it will be a disaster.
maybe i should just keep what i have and get a bigger hard drive for my music and leave it at that. until i can afford a new box. what is your opinion???

---

### Post by Pumalite on 2008-02-28
When I have an OS that runs well and I like; I stick to it.

---

### Post by DarinB on 2008-02-28
i am still only 8 months into Ubuntu. Does it self destruct (so to speak) once it is no longer supported..
i.e. security updates and kernel updates????????????????????????????
Can i keep feisty until 9.04 or what ever????????

---

### Post by DarinB on 2008-02-28
wait, but you are a hardy user, so how did you find the conversion??
i am apprehensive about it and would love to just keep things ae they are right now i am really happy with it. REALLY HAPPY i have a few issues with my hp scanner but other wise it s all good even great.
so how does this new os thing work??????

---

### Post by Pumalite on 2008-02-28
I have Feisty, Gutsy and Hardy Heron. All work fine. I prefer a clean install.

---

### Post by DarinB on 2008-02-28
i am trying to understand this OS releases is it better for a user like me to wait and go to a longterm release like the one that will come after hardy???
what will happen when the support ends for feisty will my system then be at risk??????
i wish to avoid the upgrade treadmill OR should i really be on it?????????

---

### Post by overdrank on 2008-02-29
> **DarinB said:**
> i am trying to understand this OS releases is it better for a user like me to wait and go to a longterm release like the one that will come after hardy???
what will happen when the support ends for feisty will my system then be at risk??????
i wish to avoid the upgrade treadmill OR should i really be on it?????????

Hi and Hardy is the next LTS, and if you like to stay on the bleeding edge then you can upgrade every release. I have Feisty on my main system but I am test Hardy on another. So I agree that a clean install is better.As for you original issue it took a little work to get my graphics going on Hardy and alot of reconfigures. :)
Edit and yes When the support runs out you system will be at security risk.

---

### Post by Sendervictorius on 2008-02-29
I have an GeForce MX 440 card. It runs on Hardy fine. gnome-system-monitor has problems when maximised. (I think this is a bug with the new cairo graphs. Hopefully fixed before Hardy is released).

I have noticed that performance is noticeably better after installing the nvidia-glx drivers from synaptic.

---

### Post by DarinB on 2008-02-29
hey sendervictorius 
how are you running your geforece mx 440? i run my geforece4 mx 420 by simply using the common kernel nvidia driver and nothing else if something creeps in via updates i lose my Hz down to 60Hz ( kills my eyes i keep mine at 85 Hz).
what do you think will it work with hardy with less hassles?????

---

### Post by Sendervictorius on 2008-03-03
I didn't have any troubles. Hardy discovered my monitor correctly (1650x1050 22" LCD). It runs at 60Hz, but it is an LCD, so flicker is not a problem.

I would recommend you download and burn a boot image, then boot off the live CD and give Hardy a go - before thinking of installing it. Try before buying! You should be able to spot any problems if there are any. Although Hardy is still an Alpha release, from what I've seen it is pretty stable. However, I wouldn't install it permanently until the official Hardy release in April.

I understand Hardy has revamped and automated and improved the Xorg discovery process. It looks pretty smooth. When you do boot from the Live CD, it may be worth checking your /val/logs/Xorg.0.log file - to see if and how Xorg has discovered your video card and monitor hardware.

---

### Post by DarinB on 2008-03-03
great ideas thanks
i did try the 7.10 cd and it works, but i will check the x org log file
thanks

---

### Post by DarinB on 2008-03-03
i have a stupid question how do navigate to the /val/logs/Xorg.0.log?????

---

