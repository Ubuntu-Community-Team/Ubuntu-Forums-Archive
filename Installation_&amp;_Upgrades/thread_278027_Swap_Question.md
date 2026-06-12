---
title: "Swap Question"
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by StreetSmart on 2006-10-15
Hey, I have a Lenovo Thinkpad R60 with 2 gigs of ram. I know that usually your supposed to have double the ram size for swap. And when I had my crappy old desktop with 256 megs of ram.. i followed that.

My question is, do I even need a swap partition at all since I have so much ram. Odds are I'm not going to use up all the ram. I'm a student in Information Systems Security, so we do java programming. Compiling these programs is most likely the most amount of stress my system will ever get. Also, if I do need a swap partition how big should I make it, and what one of the two partition layouts would work best.

[windows][linux ext3][swap]

or

[windows][swap][linux ext3]

Thanks for the help!

EDIT: I think i should add that I will be installing Ubuntu alternate and choosing the server install.

---

### Post by Kateikyoushi on 2006-10-15
The partition layout basically does not matter.
I currently have 256MB swap in Ubuntu and never used more than 60% of it, with gentoo  never had a swap file, all this on a 512MB ram notebook.
But as usual YMMV.

I think you can live without 512MB  disk space and create a swap partition just in case, if you see it is really not neceserry then you can delete it later and resize the / partition.

---

### Post by NeoLithium on 2006-10-15
That's about right. With 2 GIGS of installed RAM, even with compiling, shouldn't necessarily need more than a 512MB swap; although if you find that you need more, resizing it later on is just as easy.

---

### Post by StreetSmart on 2006-10-15
You guys both said that if i find i need more swap i could alwayes resize the partition. How exactly would I know if I need more swap or not?

---

### Post by NeoLithium on 2006-10-15
Well, if you ever run monitoring applications that you can see your RAM/SWAP use, you can visually see if it's getting high.  Although like stated, with 2GIGS, I can't see much of a problem with having only 512MB, unless you plan on running NORAD on your box ;)

---

### Post by John.Michael.Kane on 2006-10-15
In case you should want to resize for more swap. you could use the live/cd with it's gparted program.


Though with the amount of mem you have. I would be hard press to see that run low.

---

### Post by JayTee on 2006-10-15
I have 2GB of RAM in my system and even when I have 9 or 10 programs running and my CPU utilization is high my swap usage is usually 0% or only about 1% max. My swap partition is 5.79 GB so I never worry about swap space anyway but if you have 2GB of RAM I doubt if not having more than 512MB of swap is going to be an issue.

---

### Post by StreetSmart on 2006-10-15
Awesome. I've got some homework to do, but after that I'll be installing ubuntu alternate! Thanks for the help guys.

---

