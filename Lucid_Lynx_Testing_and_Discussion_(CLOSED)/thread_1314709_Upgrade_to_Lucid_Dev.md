---
title: "Upgrade to Lucid Dev"
date: 2009-11-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rednus on 2009-11-04
Is it a bit wierd or am I bit too ambitious? My "update-manager -d" doesn't do anything.. I am running 9.10 64 bit. Or is it something I am doing wrong? 

Cheers

---

### Post by graaant on 2009-11-04
You're a little too ambitious.
For the moment, you need to edit your /etc/apt/sources.list and replace karmic with lucid.

---

### Post by sertse on 2009-11-04
That said, toolchain is going to updated sometime tomorrow I think, so you might as well wait a day so you can do it  "officially"

---

### Post by rednus on 2009-11-04
> **graaant said:**
> You're a little too ambitious.
For the moment, you need to edit your /etc/apt/sources.list and replace karmic with lucid.


Thought so.. ;) 

yeah did that finally.. but now Administration>Software sources doesn't open now.. so using the good old gedit fashion :)

---

### Post by ranch hand on 2009-11-04
And leave Update Mangler alone.

---

### Post by scout4536 on 2009-11-04
When do you all think Lucid Alpha will become an .iso for download???  Or will it?

---

### Post by terry_gardener on 2009-11-04
think iso will be created for alpha 1 which is on the 10th Dec

---

### Post by nerdopolis on 2009-11-04
I think they have daily builds of the CD before alpha 1's release, but when I've seen them, they went over 700MB (in really early development) and couldn't  fit on a normal CD. 

I don't see Lucid's images yet. Maybe you'll have to remember remember the fifth of November, when the toolchain is uploaded? I don't really know, but I know their coming soon.

---

### Post by ranch hand on 2009-11-04
I will give you this link sense it is hard to find (top of page - testing forum - in stickies)

[http://ubuntuforums.org/showthread.php?t=1304172](http://ubuntuforums.org/showthread.php?t=1304172)

And 12-10-09 it is.

---

### Post by lonniehenry on 2009-11-04
rednus see this thread to solve your problem: [http://ubuntuforums.org/showthread.php?t=1308574](http://ubuntuforums.org/showthread.php?t=1308574) with thanks to Paul-in-London.

---

### Post by Yes_It's_Me on 2009-11-04
For those with issues with software-sources or add-apt-repository not working, the reason is that the python-apt template for lucid is not in the file /usr/share/python-apt/templates/Ubuntu.info

What I did was copy the entries for karmic and paste them at the top, replacing all references to karmic and 9.10 with lucid and 10.04. That fixes it. I imagine that will be fixed once the toolchain is out.

---

### Post by ranch hand on 2009-11-04
That is the way I do upgrades anyway if I am going to.  Then just "sudo apt-get dist-upgrade".

You are preforming a tricky procedure here, why put another layer between apt and the job it is going to do anyway?

---

### Post by flipper9 on 2009-11-04
> **nerdopolis said:**
> I think they have daily builds of the CD before alpha 1's release, but when I've seen them, they went over 700MB (in really early development) and couldn't  fit on a normal CD. 

I don't see Lucid's images yet. Maybe you'll have to remember remember the fifth of November, when the toolchain is uploaded? I don't really know, but I know their coming soon.
Why burn a CD?  Use unetbootin, a cheap 1GB or larger USB key, and get something that is...

1. Bootable on most modern systems
2. Reuseable
3. Fast
4. Reliable with no problems with burning at the wrong speed, a bad CD-ROM

---

### Post by ranch hand on 2009-11-04
Do you have any idea how many people do not have a "usb key"?  These are not readily available, for instance, in the largest town in this county (pop 500) and it is only 100 miles to anywhere bigger.

R-W is cheap and better yet, available.

---

### Post by rednus on 2009-11-04
> **lonniehenry said:**
> rednus see this thread to solve your problem: [http://ubuntuforums.org/showthread.php?t=1308574](http://ubuntuforums.org/showthread.php?t=1308574) with thanks to Paul-in-London.


Hey that solved the Software Sources Issue. Cheers though. 

rednus

---

### Post by flipper9 on 2009-11-04
> **ranch hand said:**
> Do you have any idea how many people do not have a "usb key"?  These are not readily available, for instance, in the largest town in this county (pop 500) and it is only 100 miles to anywhere bigger.

R-W is cheap and better yet, available.

Dang; every Walmart sells them.  Dang, you must be in the sticks! :D  (P.S. I'm from Wyoming originally).

Bleh; I still like the idea of the major increase in speed with USB, plus you don't have to worry about bad disc burns.  Just search ebay, they are sold everywhere.  Heck, even the grocery store sells them.  People give the 1gb ones away with everything nowadays as token gifts.

---

### Post by ranch hand on 2009-11-04
I would like one.  My son has a 4Gb.

I buy a lot on ebay.  This is one thing I want to go and have demonstrated before I buy it.  Never used one.  Need to see and feel it on the first one (personality flaw - I have lots).

There are 3 wallmarts around us.  All are about 100 miles or more.  I don't care about that because I won't do business with them (my wife will).  Sheridan and Gilette, WY are the "close" big towns.  Miles City, MT is the other town with actual "modern" shopping.  you can cut the distance to all of them if you don't mind increasing the time by about twice by taking back roads.

I like it.

---

### Post by VMC on 2009-11-04
> **ranch hand said:**
> That is the way I do upgrades anyway if I am going to.  Then just "sudo apt-get dist-upgrade".

You are preforming a tricky procedure here, why put another layer between apt and the job it is going to do anyway?
RH, is this in reference to editing this file:
"/usr/share/python-apt/templates/Ubuntu.info" ?

> **ranch hand said:**
> I would like one.  My son has a 4Gb.
...
There are 3 wallmarts around us.  .... Why are the biggest Wal-Marts in the remotest areas. I live in L.A., and my brother and parents lived in Prescott, AZ, and they had several huge Wal-Marts in there area. I don't get it.

---

### Post by sliketymo on 2009-11-05
> **flipper9 said:**
> Dang; every Walmart sells them.  Dang, you must be in the sticks! :D  (P.S. I'm from Wyoming originally).

Bleh; I still like the idea of the major increase in speed with USB, plus you don't have to worry about bad disc burns.  Just search ebay, they are sold everywhere.  Heck, even the grocery store sells them.  People give the 1gb ones away with everything nowadays as token gifts.

Contrary to popular belief,there is not a Wal-mart on every corner of every rural town in America.

---

### Post by W2IBC on 2009-11-05
> **sliketymo said:**
> Contrary to popular belief,there is not a Wal-mart on every corner of every rural town in America.

walmart is evil......

got my laptop (test machine) waiting just for the upgrade to lucid.

come on lucid!

---

### Post by akand074 on 2009-11-05
> **ranch hand said:**
> Do you have any idea how many people do not have a "usb key"? These are not readily available, for instance, in the largest town in this county (pop 500) and it is only 100 miles to anywhere bigger.
 
R-W is cheap and better yet, available.
 
Really? Must be difficult to get in your area, but I know generally, there is hardly anyone who doesn't have one at this point. Matter of fact I have two in my pocket right now and I'm thinking I'll get a third one to add to my keychain! Just about everyone I know has one even the ones who hardly ever use it. I work in retail and parents have been purchasing them or very young grade school students, its great for bringing work to school and such. There is hardly a store with any bit of tchnology that doesn't have them in stock, and they have gotten cheaper. (~15$ for a 2GB usb flash drive). It must be because you in a bit of a remote area, but you could always order it from any major technology store or superstores if they ship to your area (Ex: Bestbuy, futureshop, staples, wal-mart, etc.). Unless its only this big in select areas, but I'm quite confident USB drives are held by most people across North America and probably Europe and is very readily available.

---

### Post by Seventh Reign on 2009-11-05
> **sliketymo said:**
> Contrary to popular belief,there is not a Wal-mart on every corner of every rural town in America.

Correct .. its every THIRD corner :lolflag:

---

### Post by ranch hand on 2009-11-05
Not here.  Thank God.

---

