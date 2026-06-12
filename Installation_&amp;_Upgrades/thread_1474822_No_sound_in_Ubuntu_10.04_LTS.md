---
title: "No sound in Ubuntu 10.04 LTS"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by blackfox-bt on 2010-05-06
I have upgrade my Ubuntu 9.10 to Ubuntu 10.04 LTS and, i dont know why, sounds doesn't work properly. Amarok is currently the only program that could plays sounds, Desktop sounds doesn't work, Totem doesn't work, Rhythmbox doesn't work, Wine sounds doesn't work!.

The alsa mixer is well-configured (Amarok works!), I have installed the PulseAudio * programs and all seem to be fine.

The history is that I have upgrade my system on 4-may-2010, before upgrade I have not had problems.

The login screen sound works too, is something wrong with my sound configuration?, how can I load the default configuration?, what is the difference between Amarok an other sound software?.

---

### Post by blackfox-bt on 2010-05-06
MY alsa-information :
[http://www.alsa-project.org/db/?f=fd0a004fd1d391f043175a22b9e3ee72a9e561a4](http://www.alsa-project.org/db/?f=fd0a004fd1d391f043175a22b9e3ee72a9e561a4)

---

### Post by blackfox-bt on 2010-05-06
yes, it was a problem with my configuration, I don't know why and I don't know where.

I solve this problem deleting the .pulse folder in my home

:~$rm -r .pulse

---

### Post by KPDXHAM on 2010-05-19
First of all, I've used Ubuntu for around 8 months now and 9.10 was working fine for me, but I've just installed a fresh copy of 10.04 LTS on a new HDD and the sound was not working! :-s
After reading some ideas on another thread in this forum, the "DUH" light came ON for me... :idea:
I went to System, Preferences, Sound and found that my Output Volume had the "MUTE" checked! :???:
I have no idea how this happened. :-k 
I'm just thankful I didn't have to spend time trying to figure out what was wrong. :grin:

---

### Post by vontero on 2010-06-17
thanks blackfox .. i have the same problem . and i fix it using your help

---

### Post by vishaluc on 2010-07-27
I faced this problem when i changed the 'Connector' option in the 'Output' tab in sound preferences to 'Analog Headphones'. After i changed the 'Connector' option back to 'Analog Output' everything seems fine. Try it.

---

### Post by Indyviews on 2010-08-25
I upgraded from 9.10 to 10.04LTS this evening and had the same problem. I just want to say a **very big thank you to KPDXHAM**...you solved my problem!

---

### Post by Beardybaldy on 2010-09-01
> **vishaluc said:**
> I faced this problem when i changed the 'Connector' option in the 'Output' tab in sound preferences to 'Analog Headphones'. After i changed the 'Connector' option back to 'Analog Output' everything seems fine. Try it.



Worked perfectly for me!

---

### Post by e3k on 2010-10-07
if this should not help. then try to go to system#preferences#sound and choose the output tab and then set the connector to speakers:KS this worked for me.

---

### Post by milanes on 2011-06-21
> **blackfox-bt said:**
> yes, it was a problem with my configuration, I don't know why and I don't know where.

I solve this problem deleting the .pulse folder in my home

:~$rm -r .pulse


Thank you very much!!
This is just amazing. I deleted it, rebooted the System and got my pidgin and skype sounds back.

---

### Post by aeiou25 on 2011-08-07
> **KPDXHAM said:**
> First of all, I've used Ubuntu for around 8 months now and 9.10 was working fine for me, but I've just installed a fresh copy of 10.04 LTS on a new HDD and the sound was not working! :-s
After reading some ideas on another thread in this forum, the "DUH" light came ON for me... :idea:
I went to System, Preferences, Sound and found that my Output Volume had the "MUTE" checked! :???:
I have no idea how this happened. :-k 
I'm just thankful I didn't have to spend time trying to figure out what was wrong. :grin:


Thank You, KPDXHAM !
i can't sleep because my ubuntu can't play mp3 ..........

---

### Post by Dynamo Nath on 2011-09-27
Hi,

As you can tell I'm new to this whole Ubuntu thing and was wondering if someone could tell me why this works please? I now have sound on my NB200 but am interested in learning rather than blindly following instructions on the net. Thanks :)

---

