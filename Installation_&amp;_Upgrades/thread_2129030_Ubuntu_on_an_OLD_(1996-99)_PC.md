---
title: "Ubuntu on an OLD (1996-99?) PC"
date: 2013-03-25
forum: Installation &amp; Upgrades
---

### Post by Alaska Skier on 2013-03-25
hi guys, have tried ubuntu and i like it! i have had an old compaq for a while, how old? old enough that the case is the same cream gray that all electronics were in the 1990s, id estimate it to be a 1997 or 98, it originally had  win98 on it and was upgraded to win2000 which i used to play some games when i was say around 7 or 8, anyways i am  quite a bit older now and soon to be off to college and wanted to get ubuntu on it as it was a lighter OS and would run faster and take up less space, all i need to know is what distro and version or what updates i need to do for it to work on this PC, as for the PC, it about as fast as a revision A raspberry pi,

here are the specs:

cpu: x86 Family 5 Model 8 Stepping 12 Authentic AMD ~531 Mhz
Total Physical Memory (ram?): 196,144 KB (196.4 MB?)
HDD: C: 13 GB
       D: 4.67 GB


not much eh? shows that we sure have come a far way from this, all ready tried several ubuntu installs but i know im probably doing something wrong or using the wrong port or version. hope you guys can help, and please no answers like "why don't you get a new computer?", i just had the thing laying around and figured i would see if i could still use the thing rather than part it out.

---

### Post by tux-gamer on 2013-03-25
try using old version of ubuntu with lxde desktop.
perhaps 4.10 or 5.10 

btw, what do you want to do with this pc? use it as router? proxy server? office stuff?

---

### Post by mörgæs on 2013-03-25
Please don't recommend anyone to use old (=unsupported) versions. It will cause a major security problem.

The computer is a [K6]("http://en.wikipedia.org/wiki/AMD_K6-2"), which is not supported by Ubuntu any more. I would send it to recycling and get another used one in stead, sorry.

---

### Post by Alaska Skier on 2013-03-25
hey thanks all, im not worried about security as i would like to run xmbc and surf the web maybe, im familliar with the ldxe interface as its what the new Wheezy Raspbian runs on, id prefer something a little newer though, something i could get firefox on easly as i remember ldxe only really liking iceweasel, a ported version of firefox for the raspberry

---

### Post by Topsiho on 2013-03-25
I support  mörgæs when he says that you shouldn't use an old and unsupported version of Ubuntu. And Alaska Skier is wrong when he says that he is not concerned about security. He should be, if he wants to connect to internet. Unsecure computers have made the internet a jungle, and Linux users should not participate in this.

I think that the 200 MB of RAM is not enough even to run Lubuntu. Especially not for running Firefox. Sorry for this. Of course AS could try and upgrade the RAM to somewhat more, say to at least 512 MB or even 1 GB of RAM, if the motherboard can cope with so much RAM.

Even then the K6 processor is very slow, but as trying (X)(L)Ubuntu does not cost much or nothing, AS could of course try whether he is happy with it or not.

I sympathise with trying to reuse very old hardware :), but one needs to be realistic.

AS, look at Distrowatch and see if you can find a lighter distro that can run on your computer. If you run it without a GUI (in a terminal) you can use this to learn the real thing: using the command line. That should keep you busy for some time.

Topsiho

---

### Post by pradyot on 2013-03-25
Try out Lubuntu or puppy linux!

---

### Post by deadflowr on 2013-03-25
+1 for [puppy]("http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm").

Or try [crunchbang]("http://crunchbang.org/"), or even something like [bodhi linux]("http://www.bodhilinux.com/").

For fun, though you could try running Ubuntu on that machine, it's possible it'll run albeit run slow as molasses in the winter.

---

### Post by mörgæs on 2013-03-25
Please everybody: Don't give advice unless you know *exactly* what you are talking about. 

As I mentioned the K6 is unsupported. After 10.04 the entire Buntu family requires a CPU with CMOV instructions, which the K6 does not have. It's not a question of speed, it's a question of support. There might be a workaround, but it's simply not worth the effort.

Can Alaska Skier trust that people suggesting Puppy and Chunchbang have tested that the OS works without CMOV?

---

### Post by snowpine on 2013-03-25
Recycle it.

I know times are tough and money is tight for a lot of people. Try: Freecycle, Craigslist, Goodwill, friends, family, neighbors, local businesses, etc. and you should be able to find a decent computer free or low cost. :)

---

### Post by Alaska Skier on 2013-03-25
thanks to all guys, any possibility of getting xmbc running it in its native win 2000? i have a feeling that linux is going to be impossible on this machine, how bout an old hp pavillion circa 2003-05 with a celeron processor?, dont know the specs but im guessing bout 2 g's of ram and a 1.2Ghz processor

---

### Post by Alaska Skier on 2013-03-25
money is not really an issue as i have old computers lying all round the place, pick them up from all over the place, school tech coordinators gotta dispose of them somehow, just trying to find a use for this one but i guess it really is time for it to go, it will not go without a fight though as it definitely has some use for old software that i have and its similar to a first car, ya know, first computer:P

---

### Post by mörgæs on 2013-03-25
Windows 2000 is also unsupported. Though you might shed a tear there's no use for the old fella, sorry.

However the HP sounds like a good candidate for Lubuntu.

---

### Post by Alaska Skier on 2013-03-25
it origionally had xp and ran flight simulator 2002 good, i have 2 of those, one used to be the family computer but got taken out by a trojan,my mom wants to get her stuff off of it before i do anything to it, the other is the same configuration i believe, but is clean and just needs a power supply as the other one needed one when a power surge took it out

---

### Post by Alaska Skier on 2013-03-25
And about the compaq, i might just have it as a benchmark for worlds slowest computer based on a power to weight ratio (around 50 lbs), so 10Mhz per pound of computer, LOL

---

### Post by tux-gamer on 2013-03-25
@mogaes
i'am sory, i just try to help.
i wil not do that again.


@Alaska Skier
It's make me remember, i have a friend that have much older komputer,tch Pentium 75Mhz with 16MB Ram, and my friend want to try linux, so i installed Mandrake 8.0 on it with icewm, and he happy with it.
So just go to distrowach.com and search about minimalist distro in there.
but for New Firefox, you need more of ram.
for XBMC, perhaps you could try much better cpu, perhaps thoose celeron you mentioned before.

edit:
i saw nice thread in here [http://ubuntuforums.org/showthread.php?t=2129326](http://ubuntuforums.org/showthread.php?t=2129326) , Ubuntu 12.10 for Old computer.

---

### Post by Adam_GUI on 2013-03-25
The OP just barely meets the hardware requirements for Debian Stable with desktop.
For a machine from 96-99, that sounds about the right speed if you want hardware that old to do anything worthwhile.  

You exceed the minimum requirements for Damn Small Linux or Puppy Linux.

---

### Post by Alaska Skier on 2013-03-27
i have decided to recycle the old sucker as i looked up the K6 processor and a CPU upgrade would be impossible as the K6 uses a different socket than all ney AMD or intel processors, final verdict: the compaq is only good for its tank of a case, all innards are good for scrap metal. solution: turn HP Pavillion into network media center that i can acess from my laptop thanks for all the help guys. :)

---

### Post by tux-gamer on 2013-03-28
> **Alaska Skier said:**
> i have decided to recycle the old sucker as i looked up the K6 processor and a CPU upgrade would be impossible as the K6 uses a different socket than all ney AMD or intel processors, final verdict: the compaq is only good for its tank of a case, all innards are good for scrap metal. solution: turn HP Pavillion into network media center that i can acess from my laptop thanks for all the help guys. :)

You're welcome.
btw, for network media center, i have one, i use Router 3G TPLink MR3220 + HDD Ext, you can read in here [https://forum.openwrt.org/viewtopic.php?id=29910](https://forum.openwrt.org/viewtopic.php?id=29910) 
ps: the last post is my post

---

