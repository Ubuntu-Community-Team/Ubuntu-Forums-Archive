---
title: "ubuntu studio"
date: 2007-05-27
forum: Installation &amp; Upgrades
---

### Post by firedancer on 2007-05-27
Hi, 

i own a 
intel desktop D845GEVBV2
Intel(R) Celeron(R) CPU 2.40GHz 
 HD IDE WD 40 gig
ATI 7000
1 g ram 
 ESS Technology ES1969 Solo-1 Audiodrive
alesis multimix 12 usb

Q: I record through alesis 12 usb and play back through the es1969 (can't record with it), after the rec the second track it starts getting harder to record tracks (problems running smooth)

 I've already got the the low latency kernel, can i enhance the recording 'speed' a little more 

just 'upgraded' to ub-studio went smooth, looks nice most ofthe stuff work, but it can be better if i do something, 

another thing, there is something i came across in one of the threads to speed it up even more ('realtime' ?) 

can anyone tell me something about that 




   
thnx in advance:KS

---

### Post by ticopelp on 2007-05-27
40 gigs doesn't seem like much for video editing, personally, but, assuming your ATI card works, everything else should be all right.

---

### Post by firedancer on 2007-05-28
can't record from the ess1969  cause it sucks ,

have to record through usb alesis , 


what is the best upgrade for my equipment, a soundcard or 1 gig ram 

any suggetions or tweak and fix the usb a little , cause that's what i notice it needs 


first track records , second track having problems ,after third one no motivation (the track  is wack)

a little more speed ,is enough 

is there a way 

would be glad to know one

---

### Post by firedancer on 2007-05-29
intel desktop D845GE
2.66 Ghz
40 G hd ide
ati 7000
1 Gb ram
  
** soundcards 
ess 1689 (nothing special)
alesis 12 mulitrack usb
lexicon omega usb    

i heard/searched and found the realtime kernel , but can i get it in the repo

should i install and see if latency problem resolves (or that i can work better)

should i buy another more compatible soundcard like maudio delta 

thnx in advance :KS

---

### Post by firedancer on 2007-05-30
[QUOTE=firedancer;2746191]intel desktop D845GE
2.66 Ghz
40 G hd ide
ati 7000
1 Gb ram
  
** soundcards 
ess 1689 (nothing special)
alesis 12 mulitrack usb
lexicon omega usb    

i heard/searched and found the realtime kernel , but can i get it in the repo

should i install and see if latency problem resolves (or that i can work better)

should i buy another more compatible soundcard like maudio delta 

thnx in advance :KS

is this of any help to me ?
sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - memlock 250000 >> /etc/security/limits.conf'
 sudo su -c 'echo @audio - nice -10 >> /etc/security/limits.conf'

---

### Post by RAdams on 2007-05-30
Celerons are terrible at multi-tasking and processor intensive tasks. That will be your weakest link, to be honest.

---

### Post by firedancer on 2007-05-31
so what processor  is recommended for recording, i run ubuntu studio 'upgrade'  :(

---

### Post by firedancer on 2007-05-31
other motherboard too ? , 

i think i'm gonna have a recording 'obstacle'  


processor, soundcard , ..................

i'm already broke , aah $ 7 still in my wallet 

well i'm trying to stay optimistic not realistic

---

### Post by tgalati4 on 2007-05-31
Try Dynebolic 2.4.2.  It's a live CD and it should run fast on your machine.  It's designed to run on older hardware.  I can do multitrack recording on a PII, 300 MHz machine using an M-Audio card.  This is a cheap way to get more CPU cycles without having to upgrade.

---

### Post by firedancer on 2007-05-31
i have dynebolic docked , my stuff man , i'm a rasta like JA(H)romi >>developer , did some stuff already like it , just need an maudio card , because the usb recorders aren't so good for realtime the other card's not capable of anything but distorted sound 

where i'm from though they don't sell good soundcards , and the most trusted internet company to buy stuff from doesn't sell m-audio

but i'll get one i can't wait , cause right now i have a lot of inspiration but not the tools , but patience is a virtue

first time though strangely i recorded through the usb alesis , but after that time it wasn't able to detect it as a 'soundcard' for real or i was high from the excitement dunno 


my wish is to put together a linuxstudio for recording which i can help other's with (low charge) to get their music going, i already have someone a devout christian friend of mine wants to record some religious songs, some other young guys, rock gitarist friend of mine with band  and my own reggae/posrap/worldmusic/culturalmusic, 

i helped some scouts once then i had  xp and pirated cubase (which after going online ](*,)  stopped working ofcourse)

one day ,  one day :KS

---

### Post by tgalati4 on 2007-05-31
I've used my dynebolic system to record binaural recordings of some church concerts.  You can find them at 

wingsoffaith.org/media.php

Search on binaural.  These are surround-sound recordings that you listen to with headphones.  The rest of the music is mixboard recordings dumped to a Denon CD recorder.  Then I extract with Audacity and process to mp3.

Good luck with your venture.

---

### Post by firedancer on 2007-05-31
listened to some , but then i was suddenly unable to get in the media section


not bad at all , good for the soul and spirit  

i'll try next time again , i'll show my friend and let him listen to some of the music you guys make





keep up the go(o)d works :KS

---

### Post by RAdams on 2007-06-01
> **firedancer said:**
> other motherboard too ? , 

i think i'm gonna have a recording 'obstacle'  


processor, soundcard , ..................

i'm already broke , aah $ 7 still in my wallet 

well i'm trying to stay optimistic not realistic

I don't know what the policy is on these boards about ads, so I won't get too specific here, but I did just spec out a new amd 64 bit processor, 1gb ram, and new motherboard for someone... at under $200... with shipping...

Anyway, I feel you on the budget thing. But if you ever scrape a couple hundred together (not easy, I know) then drop me a line at [email]nospamronald.adams@gmail.com[/email]. Remove the "nospam" from that address.

---

### Post by firedancer on 2007-06-01
i'm gonna try , my dad is my best friend , so when he can he helps me out, he actually helped me with my present pc , and we make music and made  an album ( cd)  together once , 

so i'll drop you a line when i'm ready  RAdams 

i just have to be sure it comes my way , haha:D

---

### Post by tgalati4 on 2007-06-01
Music streaming from my server is wonky, depending on how sunny your island is.  You can always download the file and play it locally--that's what the download button on the right is for.

I got most of my equipment through donations.  If I had extra machines set up, I would donate them to others that want to create music.  I have bits and pieces so I put together a wish list and you would be amazed at the amount of equipment that is tossed in the States.   

Low-cost computing is leading this revolution in expression.

Cool Runnin's

---

### Post by RAdams on 2007-06-01
> **tgalati4 said:**
> I have bits and pieces so I put together a wish list and you would be amazed at the amount of equipment that is tossed in the States.   

Low-cost computing is leading this revolution in expression.

Cool Runnin's

Amen.

---

