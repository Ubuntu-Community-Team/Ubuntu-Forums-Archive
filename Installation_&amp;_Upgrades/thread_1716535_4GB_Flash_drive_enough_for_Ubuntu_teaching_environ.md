---
title: "4GB Flash drive enough for Ubuntu teaching environment?"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by chrisgregg on 2011-03-28
This summer, I'm going to be teaching a programming class to a group of middle school students, and I don't have access to install software on the computers we'll be using.  At this point I don't even know if they'll be Macs or PCs, but I should be able to find out soon (and the class doesn't start until June, so I've got time to figure this out).

What I thought about doing was creating a set of flash drives with an Ubuntu installation on each one, and have the students run the computers off of the flash drives. I'd like them to be able to save their work, and I'd like to be able to set up a Python environment, a Java/Eclipse environment, and a GCC environment.  I also thought it would be relatively easy to set up a single drive and then clone it for the number of computers I'll have.

The course is a survey course in a number of different languages, and nothing will be particularly fancy (e.g., a few limited GUI apps, and no large data sets).

Would 4GB drives be enough to set something like this up?  Thanks!

---

### Post by galacticaboy on 2011-03-28
I would say yes, that should be plenty, but as a precaution I would go with something like an 8GB flash drive to be on the safe side, depends on how much you want them to save.

---

### Post by Hedgehog1 on 2011-03-28
+1 on galacticaboy's assessment. 4 gigs is workable, but (budget permitting) 8 gig USB sticks would allow room for this and future classes you will teach to grow.

***The Hedge***

:KS

---

### Post by chrisgregg on 2011-03-29
Thanks for the suggestions!  I agree, 8gb would be better.  I've been playing around with a 4gb stick, and after getting rid of things like open office and other bloat (for our purposes), I've still got over 700mb left for the students to use.  Not ideal, but I'm not sure the budget will support getting 16 8gb drives vs 16 4gb drives (which can be had for about $8 apiece now).

I'll keep searching, though, so we'll see.

---

### Post by leg on 2011-03-29
I have done this twice on 4gb flash drives. The first time I created this type of environment it was an installation for music which was basically ubuntu studio. After I created that I created a programming environment for C++, Java and specifically Android development. This works very nicely from a 4GB drive on the fairly modest PCs we have.

The method I followed was to create a live usb stick and then start customising it by installing the software I needed. I also adjusted the log on so that it booted straight into the system with the default user. Restrictions on our network meant that I had to install software at home (my assumption was blocked port numbers for Synaptic) but the Internet worked fine once I figured out how to set the browser up.

Have fun.

---

### Post by TechWiz2100 on 2011-03-29
Searching [Google]("http://www.google.com/search?q=8gb+flash+drive&tbs=shop%3A1&aq=f#q=8gb+flash+drive&hl=en&tbs=shop:1,p_ord:p&sa=X&ei=TPeRTYbxMO2C0QGYm_DMBw&ved=0CAsQuw0oAQ&bav=on.2,or.r_gc.r_pw.&fp=1affaf436805e436") for online products shows that 8GB flash drives can be as cheap as 8 dollars a piece as well or about $12 a piece from a more [reliable source]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007960%20600000479&IsNodeId=1&bop=And&Order=PRICE&PageSize=20") if you live in the states

---

### Post by leftaroundabout on 2011-03-29
I used to have Lucid on a 4GB flash for a while, which did work out quite nicely at the beginning, but then I had it stuffed faster than expected. And you don't have much space left for swap with such a solution. Really careful users (unlike me) would probably get along with it, but I wouldn't rely on all of the students managing it.

So, yeah - 8GB would definitely be better. I now do really a lot of stuff from one of these, together with optional external hard drives it works great.

---

### Post by KegHead on 2011-03-29
Hi!

I actually use 2gb usb stick drives w/no problems.

4gb is overkill imho.

KegHead

---

### Post by C.S.Cameron on 2011-03-29
A Live install is about 700MB leaving about 3GB for persistence.
A full install is over 2GB but is more customizable.

---

