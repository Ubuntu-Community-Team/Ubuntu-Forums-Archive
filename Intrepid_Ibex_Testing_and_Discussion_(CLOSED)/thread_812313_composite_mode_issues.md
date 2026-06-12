---
title: "composite mode issues"
date: 2008-05-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2008-05-29
This isn't just related to intrepid but ubuntu as a whole really. I'm sure I could fix this issue if I spent 3 weeks banging my head against a wall but I've done that too many times.

Since the goal of this project has always been to make a linux distro for the average man I'd like to look at a problem through average man's eyes.

I bought a Hi-grade laptop recently and looked forward to finally moving off my ubuntu hating Acer. Unfortunately things arn't much better, this laptop has never been able to run desktop effects and the average user doesn't want to spend eternity downloading drivers, reading forum posts and screaming at error messages!

my card is reported as 01:00.0 VGA compatible controller: VIA Technologies, Inc. Chrome9 HC IGP (rev 01)

It is claimed to be compatable and there are drivers out there, but I've had no luck with it. Graphics is so important, if the graphics and sound don't work properly nobody will ever be interested in adopting linux. Is there no way to simplify the process of identifying your graphics card and ensuring it is operating in the correct mode?

---

### Post by ronacc on 2008-05-30
I feel for you , my one experience with VIA graphis (back in the EDGY days) was so bad that I swore off VIA forever. That was on a destop so I could plugin an Nvidia card and cure it . With a laptop you are stuck.

---

### Post by macroshaft on 2008-05-30
I keep hearing time and time again people saying that ubuntu looks good but they can't play their favourite games on it. I know I can point them at glest or with a lot of effort ID software's games can be installed but that's just a headache.

Imagine, would those people swear by their windows boxes or consoles if when they bought them they had to enable a special graphics mode, but before they could do that they had to figure out what was stopping it from loading and probably install some driver and compile it from source?

I do understand that the task is enormous but it's alienating a huge portion of the market, we simply don't have the games library, and there's simply no point in acquiring it until our computers work out of the box.

It's not as if it's a select few models, it's almost every damn card, and all the big players too! There's no excuse for nvidia and ati to not have decent drivers, somehow they need to be given a wakeup call!

---

### Post by quickshade on 2008-05-30
not sure, but in most cases I would stick to the main 3 video card producers. I mean Via.....really??? You wanted to get off the ubuntu hater acer, but you didn't do any research (going off topic from the average user) in buying it.

---

### Post by plun on 2008-05-30
Well, VIA joined "the open source bandwagon" but we will see if they
are doing a ATI....  (not the latest GPU)

[http://www.phoronix.com/scan.php?page=article&item=via_oss&num=1](http://www.phoronix.com/scan.php?page=article&item=via_oss&num=1)

:)

---

### Post by aamukahvi on 2008-05-30
> **plun said:**
> Well, VIA joined "the open source bandwagon" but we will see if they
are doing a ATI....  (not the latest GPU)
Didn't AMD release R600 documentation?

---

### Post by plun on 2008-05-30
> **aamukahvi said:**
> Didn't AMD release R600 documentation?

Nope, as I understands it

[http://www.phoronix.com/scan.php?page=article&item=ati_r500_3d&num=1](http://www.phoronix.com/scan.php?page=article&item=ati_r500_3d&num=1)

> Next up: open-source R600 3D support...


ATI/AMD is probably aware of "hardware thieves" ......  :)

---

### Post by macroshaft on 2008-05-30
Quickshade, my Acer was stolen and at the time, due to reasons I need not go into here, I was only able to buy from 1 supplier who had stopped stocking the only decent model they did. It was a case of buying a bad laptop or a worse one. Any computer is better than none!

---

### Post by aamukahvi on 2008-05-31
> **plun said:**
> Nope, as I understands it

[http://www.phoronix.com/scan.php?page=article&item=ati_r500_3d&num=1](http://www.phoronix.com/scan.php?page=article&item=ati_r500_3d&num=1)

ATI/AMD is probably aware of "hardware thieves" ......  :)

Ok, looked it up... Not as much as for R500:
[http://www.x.org/docs/AMD/](http://www.x.org/docs/AMD/)

---

### Post by quickshade on 2008-05-31
> **macroshaft said:**
> Quickshade, my Acer was stolen and at the time, due to reasons I need not go into here, I was only able to buy from 1 supplier who had stopped stocking the only decent model they did. It was a case of buying a bad laptop or a worse one. Any computer is better than none!
Did not know it was stolen and you could only choose one other laptop, that explains a lot. Anyways I do agree that this needs to be improved, but so much work needs to be done so it will most likely take years before you can just start up linux and use effects.

---

### Post by macroshaft on 2008-05-31
Agreed, it's a huge mountain to climb but it does need doing. Perhaps this renewed Ubuntu collaberative release schedule spirit may help ease that burden a little.

As far as laptops go I havn't done any research, no point since all I had to choose from was a selection of Hi-grades and Acer's, but I was thinking since Dell are bundling Ubuntu these days is it a safe bet to assume a Dell laptop would work reasonably well?

---

### Post by gnuslov on 2008-05-31
I've had luck with the new beta chrome9 drivers [from via]("http://linux.via.com.tw/") with my everex gbook.  Most desktop effects work decently, though sometimes a bit slowly.  This integrated graphics card just isn't very powerful to start with, and it's slowed down even more by beta drivers.  

Hopefully via's new open source push is sincere and will be followed through on, what with via being a big player in ultra mobile devices now and linux being the best option for those kind of computers.

But still, i'd have to say, knowing then what I know now, I'd have stayed away from this via powered device which needed me to install new graphics drivers (and then fight to get them to work properly), to fiddle way too much with the alsa-drivers for it, and which won't allow me to control the fan speed and on which suspend is broken.

---

### Post by macroshaft on 2008-05-31
Has anyone ever tried to design a site to attempt to list as much linux ready hardware as possible, a guide people could refer to before making a purchase and submit their experiences afterwards?

I was going to make some sort of list for my own use so that I could advise others confidently of how likely their computers are to convert smoothly to ubuntu.

P.S. How did you install those via drivers? I got an archive with rpm files in, did you run those through alien? Also it asks me to upgrade to an older kernal than the one I'm running. Ok to skip that step??

---

### Post by macroshaft on 2008-05-31
Ok, I got the correct version and installed, restarted X and my screen went plain white then slowly faded to black.

Any ideas?

---

### Post by ronacc on 2008-05-31
> **macroshaft said:**
> Has anyone ever tried to design a site to attempt to list as much linux ready hardware as possible, a guide people could refer to before making a purchase and submit their experiences afterwards?

I was going to make some sort of list for my own use so that I could advise others confidently of how likely their computers are to convert smoothly to ubuntu.

P.S. How did you install those via drivers? I got an archive with rpm files in, did you run those through alien? Also it asks me to upgrade to an older kernal than the one I'm running. Ok to skip that step??

google  "hardware compatability" and you will get a bunch of lists .

---

### Post by Amaranth on 2008-06-03
Until Via starts playing ball (either with good binary drivers or good specifications) there is no chance to use Compiz on your hardware.

At this point if they do release specs it'll probably be a year or two before things are stable enough for me to be comfortable allowing Compiz to run by default on Via hardware.

---

### Post by gnuslov on 2008-06-03
> **macroshaft said:**
> Ok, I got the correct version and installed, restarted X and my screen went plain white then slowly faded to black.

Any ideas?

And there's where it gets "fun". There's a file called viax.conf inside the tarball you get from via (in some cases, the installer will edit your xorg.conf with this stuff already in it, just commented out) .  I tried a handfull of things until I solved the same problem you're having.  Eventually I noticed a line that said "Option "PanelID"     	"19"	#1440x900,  Dual,  Non-Dithering" and I exclaimed "Hey, my panel is 1440x900", tried it, and it worked for me. YMMV, as well as your config options.

You might find more help [here]("http://www.tkarena.com/forums/linux-arena/") than you will on these forums. (most salient item from over there is that for some people Option "LCDPort" "DFP_HIGHLOW" worked)

> **Amaranth said:**
> Until Via starts playing ball (either with good binary drivers or good specifications) there is no chance to use Compiz on your hardware.

Well, I wouldn't say *no* chance.  Just not a *good* chance and a chance that what chance there is will be buggy, slow, and crash prone, though I've so far only really experienced the slow part.

---

### Post by macroshaft on 2008-06-04
What does YMMV mean?

---

### Post by MALEADt on 2008-06-04
> **macroshaft said:**
> What does YMMV mean?

[http://www.acronymfinder.com/af-query.asp?acronym=YMMV](http://www.acronymfinder.com/af-query.asp?acronym=YMMV)

---

