---
title: "Should i upgrade?"
date: 2007-07-10
forum: Installation &amp; Upgrades
---

### Post by sent17inel on 2007-07-10
I have an E machine C2160... I'm thinking about upgrading my computer in the next week. I currently have Ubuntu Fiesty on my computer. I want to upgrade to a gig of ram. Two 512 mb sdram dimm's. Along with a Nvidia Ge force FX 5200 256MB DDR PCI Graphics Card and a second hard drive (not sure which size yet). I know this computer is getting on in years.. but I don't really have enough to buy a new one... I don't have much money right now... but does anyone consider this wise? My hearts kinda already set on upgrading this computer. Do you think i would notice any significant increase in performance? Also does anyone suspect any hardware issues? And if you do think its not a bad idea for me to upgrade how much more of a lifespan do you think i will be able to get out of this computer after the upgrades are complete?

Also i forgot to say... currently I only have 256mb of ram and the integrated sd pro savage video card.....

---

### Post by Vajra Vrtti on 2007-07-11
The question you have to answer about the upgrade is: **why?**
I mean, what do you need/want your computer to do that it can't do, or can't do well, now?
That will determine the required upgrade.

> Do you think i would notice any significant increase in performance?Again, doing what?

> Nvidia Ge force FX 5200 256MB DDR **PCI** Graphics CardIsn't it AGP?

---

### Post by sent17inel on 2007-07-11
Im pretty sure its pci but regardless im going to get some kind of nvidia pci with 256 mb... that was more of an example. and umm i just want it to be faster.. video wise and just regular performance wise....

---

### Post by rillip on 2007-07-11
upgrading the ram and video card won't do anything if you don't need them

Next time you've got a typical run going on, open a terminal and run [code]top[.code]

You'll see something like this

top - 03:27:10 up 12:46,  1 user,  load average: 0.41, 0.44, 0.43
Tasks:  84 total,   5 running,  78 sleeping,   0 stopped,   1 zombie
Cpu(s):  3.1% us,  1.5% sy,  0.0% ni, 95.4% id,  0.0% wa,  0.0% hi,  0.0% si
Mem:    515004k total,   509296k used,     5708k free,    11116k buffers
Swap:  1124540k total,    18412k used,  1106128k free,   288232k cached

See how I haven't used up all my ram, but I have used 184 mb of swap?  Upgrading my ram will, at this point, give me a slight performance boost.  The bigger the used swap, the bigger performance boost, because (to simplify), swap is slower than RAM, and is only used when there's not enough RAM.

If you're not seeing a signifigant ammount, then a RAM upgrade won't do anything. As for the video card, it's pretty much unimportant unless you're playing games/doing 3d rendering.  If a program calls for more RAM than your card has, upgrade.  If not, it won't do much.

---

### Post by Vajra Vrtti on 2007-07-11
It's my feeling that 512MB RAM would be adequate, unless you have an application that can benefit from more RAM.

> how much more of a lifespan do you think i will be able to get out of this computer after the upgrades are complete?
It may be five years or five days. That depends on several factors: the quality of the hardware, how many hours it has been turned on, and in what conditions (temperature). There is always that risk in an upgrade and,  if it fails, you may have spent money in items that won't fit in a new machine.

---

### Post by sent17inel on 2007-07-11
I dont know... I want to upgrade so i can use alot of different 3d rendering effects. And im positive im unable to do so with my current card. Despite that though i also want my computer to load faster... when it turns on... will i notice a significant increase in the time it takes to turn on? 

also here is the input for the top command... i had to take a screenshot..

[http://i148.photobucket.com/albums/s32/sent17inel/Screenshot-danieldaniel-desktop.png](http://i148.photobucket.com/albums/s32/sent17inel/Screenshot-danieldaniel-desktop.png)

---

### Post by sent17inel on 2007-07-11
Also i would like to say that this is my computer running just firefox and gdesklets when i usually try to run Cedega to play Counter Strike 1.6 which is were my crappy video card comes into play.....

---

### Post by sent17inel on 2007-07-11
I was playing counter strike right now and my video card sucks!! thats for sure.. So part of why i want a new video card is so i can play games on here.. including counter strike source.... which i wont even bother trying because i know how bad the game play would be.... also i want to someday be able to have beryl and all that other cool Eye candy... which i why i think i will need a gig of ram... but i guess my main question is ... even with the ram and new video card do u think my computer will be able to handle it....? Playing counter strike source... or running berly... I'd be happy to provide you with more information if there is something i forgot to say... or something you need to know to make a more informed answer.... Plz and thank you!

---

### Post by Vajra Vrtti on 2007-07-11
> I want to upgrade so i can use a lot of different 3d rendering effects. And im positive im unable to do so with my current card. 
> when i usually try to run Cedega to play Counter Strike 1.6 which is were my crappy video card comes into play.....
The video card will make a big difference. As I could see, the GeForce FX 5200 can be PCI or AGP. 
The AGP version is the better choice if you machine has an AGP 8x port.
> Despite that though i also want my computer to load faster... when it turns on... will i notice a significant increase in the time it takes to turn on?
I don't believe so. The results of the top command show that you are not using all memory available. That is almost 5 hours after booting, which means that the boot process probably didn't required swap. So, more RAM should not make the machine boot faster.
> also i want to someday be able to have beryl and all that other cool Eye candy... which i why i think i will need a gig of ram...
You don't need much RAM for Beryl. The new video card and 512MB will be more than it needs.
> but i guess my main question is ... even with the ram and new video card do u think my computer will be able to handle it....? Playing counter strike source... or running berly...
I'm pretty confident about Beryl but I don't play Counter Strike and I have never had a GeForce 5200, so I can't be sure. Maybe someone else can answer that? ):P

Besides, what processor do you have?

---

### Post by sent17inel on 2007-07-11
Lol gosh im learning alot about myself... i beat around the bush alot.... My processor is an AMD athlon Xp 2100 and im pretty sure thats a couple years old... this is pretty much my biggest fear..... is my processor good enough?

---

### Post by sent17inel on 2007-07-11
This page [http://www.pcstats.com/articleview.cfm?articleid=998&page=2](http://www.pcstats.com/articleview.cfm?articleid=998&page=2) is telling me that My processor is similar to a Pentium 4... at least performance wise its close....! i think.... am i reading that right? and what does this mean? How will beryl run with the aforementioned video card and ram upgrade....?

---

### Post by sent17inel on 2007-07-11
i found this website that has some info on my processor [http://www.pcstats.com/articleview.cfm?articleid=998&page=2](http://www.pcstats.com/articleview.cfm?articleid=998&page=2) its coparing it to a Pentium 4 processor so what does this mean?

---

### Post by sent17inel on 2007-07-11
Answered my own question... [http://reddit.com/info/16hnf/comments/c16isa](http://reddit.com/info/16hnf/comments/c16isa) theres a comment towards the bottom about a guy with the same processor as me who says hes running beryl fine!! just out of curiosity and to be on the safe side what do you think the validity of his comment is?

---

### Post by Vajra Vrtti on 2007-07-11
In the [Counter-Strike site]("http://www.counter-strike.net/") we find these requirements:
**Minimum: **1.2 GHz Processor, 256MB RAM, DirectX 7 level graphics card
**Recommended:** 2.4 GHz Processor, 512MB RAM, DirectX 9 level graphics card
The GeForce FX 5200 card supports DirectX 9, so it is in the recommended range.
The AMD AthlonXP 2100+ is 1.73 GHz, about half way between the minimum and the recommended.
512MB RAM is enough to be in the recommended range but, to check that, reboot you machine, load Counter-Strike and run the top command as before (with the game still running). The sum of MEM and SWAP USED values is a good estimate of how much RAM you need to avoid swapping.

I don't expect problems running Beryl with that configuration.

---

### Post by sent17inel on 2007-07-11
I just tried to do that and nmy computer started going really slow when i opened up a terminal and then i waited like 6 minutes and then it froze... and i dont really want to try it again... can we just guestamate? honestly i dont have a problem buying a gig of ram.

---

### Post by Vajra Vrtti on 2007-07-11
> honestly i dont have a problem buying a gig of ram.If that's not a problem, 1GB is certainly better than 512MB.

---

### Post by sent17inel on 2007-07-11
K. thanks for all your help.

---

### Post by Vajra Vrtti on 2007-07-11
Good luck with the upgrade.

---

### Post by sent17inel on 2007-07-11
Thanks.!

---

