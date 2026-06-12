---
title: "Fresh install over disc with preloaded Win 7"
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by poignantprick on 2012-04-22
Before I send my laptop in for a busted hard drive I wanted to seek some insight from here. This is my third post. I try my best to seek out answers without asking for help. So I googled, and searched here for answers FIRST. This has been after almost 2 months of issues.

The question is whether there are any known issues with doing a fresh install of Ubuntu over a drive preloaded with Win 7. :confused:

I had Ubuntu running perfectly alongside Win 7, but I wasn't even using Win7. Windows crashed and since I never saved a disc image I was unable to recover. Ubuntu started having troubles and within a short time I could not get it to run. SO I did a fresh install. I get Ubuntu installed and then it all goes sour within a short time. I have tried MANY things, and several distributions. I do not know much about hardware, and am very new to owning my own computer. 
Most errors I have seen throughout my struggles have all pointed to issues with the hard drive. I ran some SMART tool thingy and the results were frightening. 

Please help me if you can. I am running a live session.

Aspire 5552g-7641
amd phenom 2 x4 n970
amd radeon hd 6650m
4 gb ddr3 Mem

---

### Post by Herman on 2012-04-22
A HDD should be able to be erased and re-written many, many times without any problems, probably in the (EDITED: hundreds of thousand, if not millions of times).

EDIT: A few people are reluctant to make a normal Ubuntu install in flash memory because they are worried about their flash memory wearing out. [Flash memory has a life expectancy of between 10000 and 100000 erase cycles]("http://en.wikipedia.org/wiki/Flash_memory"), or even as much as 1000000, so therefore I assume hard drives can be wiped and re-written even more times than that.

Basically speaking, hard drives store data by microscopic patterns of magnetic fields, something along the lines of cassette tape.
All magnets eventually lose their magnetic properties, that's why we need a new magnetic compass after a while.
Exposure to other magnets, and exposure to excess heat among other things can accellerate the loss of ability of a material to retain its magnetic properties.

Sectors where the magnetic properties on a hard disk are getting relatively weak are called 'bad blocks', and are able to be 'swapped out' by the disk's firmware, or by the file system, something in a rough sort of way like you can change tires on a car.. (There is a generous supply of spares in extra reserved tracks on the disk).

If you have large speakers, (which contain powerful magnets), make sure they're not too close to your PC tower.
Also check you hard drives are getting adequate cooling, (air ducts not blocked).

Apart from that it comes down to quality control at the hard drive factory.
You can buy cheap or expensive hard drives and if you pay more, you hope you get what you pay for. Some HDDs come with a guarantee for a certain time limit. (Worth checking).

---

### Post by poignantprick on 2012-04-22
> **Herman said:**
> 
If you have large speakers, (which contain powerful magnets), make sure they're not too close to your PC tower.
Also check you hard drives are getting adequate cooling, (air ducts not blocked).

Apart from that it comes down to quality control at the hard drive factory.
You can buy cheap or expensive hard drives and if you pay more, you hope you get what you pay for. Some HDDs come with a guarantee for a certain time limit. (Worth checking).

Thank you for the reply. I have not set it near any speakers. I even got scared one time when I set my phone on it. When I set it on my lap I always check to make sure the vent is unobstructed.

My computer is still within manufacturer warranty. It has been less than a year. Maybe I will go that route. At this point I cannot imagine this is a software issue. If warranty does not cover it I know drives are getting cheap.

---

### Post by Herman on 2012-04-23
The warranty should cover it.

There's no rational argument that I'm aware of which would cause the manufacturers to refuse to honor your warranty on the grounds that the machine has had Ubuntu installed in it, but note the word 'rational' (as opposed to 'legal'). You would probably need to read the fine print in the warranty to see if there's any problem with installing an operating system other than the one the machine was sold with. I doubt if there will be any clause regarding the subject, but you could check. 

The default file system for Ubuntu is ext4, which features delayed allocation and persistent pre-allocation and doesn't require defragmenting, so it should be easier on the hard disk than the file system the machine shipped with. You can read about ext4 here, [Ext4]("http://en.wikipedia.org/wiki/Ext4") - Wikipedia to start with and if you're interested there's lots more to read about it.

---

### Post by MonkeyPaw on 2012-04-23
Unfortunately, sometimes hard drives fail. My last laptop also had a hard drive that failed after less than a year. I'm sure if you sent it in, they will check it out. I think in my laptop's case, it had a failed motherboard, too.

Otherwise, you should be totally fine to do a clean install when you get your machine back. I would recommend booting into windows first and making your recovery DVDs. It will take a few minutes, but at least it gives you the ability to restore to factory settings in the event you ever want to sell your laptop down the road.

---

### Post by jadtech on 2012-04-23
yup hard drives can be an issue last year  I got a new lap top worked great for 5 days the hd just quit no reason , tried to boot one day and it wouldnt boot it wouldnt recover and it would lock up trying to reinstall windows..

took it back to best buy geek squad looked it over  a bit and tried to get it going told me they were letting me pick out a new lap top the HD had went bad it was an HP they wouldnt let me even get another HP they were pulling them all beause it was there 4 sold with the same HD issue ..

---

### Post by poignantprick on 2012-04-23
Thank you everyone. 

I am going to mark as *solved*.

---

