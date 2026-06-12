---
title: "[SOLVED] Hardware problem and suggestions"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by clueless on 2008-08-14
Hi guys,

I have a problem building a new pc and I don't know where else to ask...
Anyway, I had trouble with my old pc not starting up any more and I decided to build a new one.
I ordered some new pieces which are:
a new case (Asus TA-881)
a hard disk (Western Digital Caviar, 400 GB)
a Gainward Bliss 8500 GT Silent video card
an Athlon 64 X2 4800+ cpu
and an Asus M2N-XE motherboard

So I got them, added my previous 2 hard disk drives (2 Maxtor 80 GB) which contain my /home folder with all emails and some other folders, all very important, since somewhere in there lies my thesis on which I'm working and should be ready by the end of September.

And I had a 450 Watt generic PSU.

I mixed up all these ingrediends and got a nice looking PC that just wouldn't boot up. I started taking out stuff but the thing just refused to boot. I got a "no signal" screen and 3 beeps from my motherboard. 

I went to a pc store in my neighbourhood and they told me that the graphics card is no good. So bought another one, a GeForce 8600. Got back home tried it but still nothing.

Went back to the store and they told me that it's most likely the PSU. I had used my old 450 Watt generic PSU. The guy there (the same guy that told me that since I'm using LINUX I should use the REAL nVidia drivers, from the nVidia repository, because the Ubuntu drivers do not work well with nVidia cards) told me that it ought to be the PSU and tried to sell me one for 80 euros! I didn't take it, instead I bought a 500 Watt (branded CMB)  and went home to try it but no luck.

So I have a brand new computer, with brand new components that will just not start up. Could it be the PSU? It most certainly is not the video card, because I cannot believe that I just bought 2 brand new faulty cards. And I don't think it's the motherboard either, since I tried both cards on an older Asus motherboard using the two PSU units and had the same luck.

Any ideas? Should I just go ahead and spend 80 euro to buy a branded PSU?

---

### Post by sdowney717 on 2008-08-14
[http://pcsupport.about.com/od/nonworkingcomponent/ht/beepcodestb.htm](http://pcsupport.about.com/od/nonworkingcomponent/ht/beepcodestb.htm)

I googled beep codes.

what type of bios, the codes differ.

For AMI bios it is this
3 Beeps - Base memory read/write test error

   1. Reseat the memory.
   2. Replace the system memory with new or known-good memory modules.

---

### Post by clueless on 2008-08-14
Hey, thanks!
I hadn't thought about trying to decode the beep messages! I just assumed they meant that something went wrong.

I searched on the Asus website but I couldn't find what bios my motherboard is using, I saw somewhere that it's Award, but this I know for sure: my memory modules are brand new, never used, 2 x Kingston KVR800D2N5/1G modules.

If I remember correctly I am getting 1 long and 2 short beeps, which would mean graphics card error according to the award bios beep code. 

So I'm back to the begining: was I so unlucky to buy to brand new faulty graphics cards, two faulty motherboards or is it something else? And could this something else be the PSU unit?

---

### Post by oldsoundguy on 2008-08-14
take everything out .. including all but the video card, memory & cpu .. no drives and see if it will even POST. (you may have to remove the graphics card and see if it will post to the on board video.)

(a really good investment is a universal POST card you can get on eBay for 5 bucks.  It will sit in there and you can watch the numbers .. when something locks up .. it will show just WHAT is giving you trouble.

YEP those beeps indicate a graphics card problem.  Make sure the card is seated properly and if you have to use a jumper system to disable any on board graphics, do so. (and if the card requires a power jumper, make sure it is plugged in!)

---

### Post by clueless on 2008-08-15
I did try that: I took everything out leaving only motherboard, 2 memory modules and the graphics card and still nothing. I tried without the graphics card and the beeps were different. The computer of course would not boot up, since this motherboard has no integrated graphics.

I doubt however any of the components is faulty, since they are all brand new and I am having the same exact problems on two different motherboards with two different graphics card. This is why I was thinking that it might be the PSU or something to do with jumper settings. But I cannot find any information regarding jumper settings on my motherboards!

---

### Post by worx101 on 2008-08-15
Have you at least tried removing the memory? just to see?

Especially since they seem to be the only thing from your previous PC that you are still using?

(just because they are new does not mean they will not give out on your quickly)

---

### Post by clueless on 2008-08-15
Yes I have tried using only one of them but no luck. And they are not new from my old PC, I bought them brand new with all the other components.

I am starting to believe that it may be the PSU. It is new, but maybe it's because it's a generic one. Maybe the voltage is not sufficient, I don't know what to think. My PSU's values are:


```

+ 3.3V  + 24 A
+ 5V    + 36 A
+ 12V   + 23 A
- 5 V   + 0.5 A
+ 5V SB + 2.0 A

Total power 500 W

```

Should I spend more to get a new PSU? Any suggestions?

---

### Post by mips on 2008-08-15
First your MB use AMIBIOS as per the manual.
[http://www.bioscentral.com/beepcodes/amibeep.htm](http://www.bioscentral.com/beepcodes/amibeep.htm)

First question, while installing & swapping out stuff did you disconnect the power cable or switch off at the back of the power supply? Reason I ask is that if you did not the board still has power applied to it and this can damage things if you poke around.

I would disconnect ALL components & cables and only connect:
1. 24pin ATX power connector
2. 4-pin ATX power connector
3. Case power switch
4. CPU
5. 1x ram stick

Makes sure the RAM is properly seated. Sometimes you think they are seated but they are not. I encountered this with a friends MB recently. For about 2 years he thought he had a faulty dimm socket but he simply failed to seat the ram properly which required a bit of force on my side. Incorrect seating resulting in beep codes and no post.

Connect the power cable and see what beep codes you get.

Disconnect the power cable.

Install GFX card and make sure it is properly seated. Connect monitor.

Connect power cable and try again.

I would leave all the jumpers in their default positions.

It's not impossible for the PSU to be faulty but I doubt it. You can always try and swap it out with a another one if you have one in another case or just lying around.

---

### Post by clueless on 2008-08-15
I did all this with same results. :(

And I have always been careful to completely unplug the power before adding or removing hardware on the motherboard. Also checked many times if something was not inserted correctly. I have built other PCs without any problems before, so I am fairely confident that I haven't missed something there.

But it's the first time I have built a PC with a recent graphics card. That is why I am thinking that it could be the PSU. I mean, before I always bought the cheapest PSU I could find. But maybe the new graphics card needs something more. I was reading around on the internet about my card's power requirements and about PSU's in general and came to the conclusion that 400 Watt, 500 Watt or 600 Watt doesn't make all the difference. It should have to do with the voltage and checking my PSU's the both have a +12V of 23A (the 450 Watt PSU) and 24A (the 500 Watt PSU) while the GeForce 8600GT needs 20A. I don't understand too much of this but seeing the numbers pretty close and my current PSUs very cheap, I am convincing myself more and more that it's the PSU's fault.

I ordered a Corsair VX450W with a 12V rail of 33A and I am hoping for the best. I will let you know how this worked out.

---

### Post by oldsoundguy on 2008-08-15
Don't think it is the PSU .. But it could be.  My dual core 64 AMD runs off an Enerxax 485 without a hitch.  And I am running a dual DVI Nvida card on it along with a boatload of stuff AND a full box.
Plus the processors run at 100% 24/7/365 as it processes stuff for BOINC

It IS beginning to sound like either a bad memory stick or the WRONG memory stick.  Especially if you do NOT even get a post screen.

You DO need to plug "beep codes" into Google and find out what the machine is telling you for the bios that is on board 
(Also, your manual should be open and on your desk any time you go mucking around inside a computer.  I have built a lot of computers of varying types over the years, and the first thing is to RTFM! as every board is different and every iteration of every manufacturer is different.)

---

### Post by clueless on 2008-08-15
The memory modules look ok and the beeps indicate that the problem is coming from the graphics card.

I searched the enermax page and regarding your PSU, it has two 12V rails, 32A each, while my PSU has one 12V rail with only 12V.

I think - and hope - that it will work with the new PSU I ordered!

---

### Post by mips on 2008-08-15
> **oldsoundguy said:**
>  or the WRONG memory stick.  Especially if you do NOT even get a post screen.

It's definately not the wrong memory as Kingston list it as compatible with that specific MB.

---

### Post by clueless on 2008-08-15
> **mips said:**
> It's definately not the wrong memory as Kingston list it as compatible with that specific MB.

Yes the specific model of Kingston memory modules is mentioned, among others, in the Motherboard's manual as recommended.

---

### Post by tommcd on 2008-08-15
> **clueless said:**
> 
But it's the first time I have built a PC with a recent graphics card. That is why I am thinking that it could be the PSU. 


Sorry if this sounds like a stupid question, but does the graphics card have an input for a PCI-express power connector on the back of it? And if so, did you plug in the correct power adapter from the PSU into it?

---

### Post by clueless on 2008-08-16
> **tommcd said:**
> Sorry if this sounds like a stupid question, but does the graphics card have an input for a PCI-express power connector on the back of it? And if so, did you plug in the correct power adapter from the PSU into it?

No it doesn't have a power connector. I searched very thoroughly on the card and the specifications!

---

### Post by clueless on 2008-08-21
Ok, solved!
I just received my Corsair VX450W and everything works great.
So, lesson learned: it's not all about the Watts. Cheap PSUs may have a 500W or 600W output but not the necessary amperes on the +12V rail to power a recent graphics card. That is why a cheap PSU will cost 15 euro and a decent one 60 euro.
I learned this the hard way!

---

### Post by mips on 2008-08-21
> **clueless said:**
> Ok, solved!
I just received my Corsair VX450W and everything works great.
So, lesson learned: it's not all about the Watts. Cheap PSUs may have a 500W or 600W output but not the necessary amperes on the +12V rail to power a recent graphics card. That is why a cheap PSU will cost 15 euro and a decent one 60 euro.
I learned this the hard way!

Glad to hear you got your problem sorted out. You should ask for a refund on that cheapo PSU.

Enjoy your new computer!

---

### Post by lswest on 2008-08-21
Yeah, I spent ages checking specifications for my new PSU when ordering the parts for my PC, I think I ended up spending about 40 euros on it.  No idea how many PSUs I checked though, some of them seem like good deals until you compare the amperes (seems like a dirty trick to me, but I guess it would be fine for low-end PCs).

Glad you got it sorted out though,
Lswest

---

### Post by clueless on 2008-08-21
Well, lesson learned! As for the refund... I don't think I am entitled to one, the specifications were there, I just didn't know how to interpret them. And I threw the box away so I don't think I could even exchange it for something else... Well, no matter, at least my computer works again.

---

