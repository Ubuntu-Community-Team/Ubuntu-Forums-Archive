---
title: "Xubuntu: Firefox too heavy"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by Polish Rifle on 2007-09-10
I recently installed Xubuntu because Ubuntu was too slow on my 1.2Ghz 128MB Gateway solo 1450 laptop.  Everything runs lighting quick and faster than my old XP set up, except for when I browse the internet.

With a little assistance from Ryn0519 I turned off the cache of Firefox to free up some RAM.  It still lagged a lot and slowed down the computer.  

Now I feel I'm forced to try a new browser even though I really like how you can customize Firefox.  Are there any versitile *light* browsers out there for Xubuntu.  First priority being lighting quick but I like a lot of the add-ons for Firefox.

I've been recommended ephipany and I've read about Opera a little.

---

### Post by chrome307 on 2007-09-10
Don't know if this would be any better, but you could try using IE:

Tutorial here:

[http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

---

### Post by kerry_s on 2007-09-10
try mine-> [http://ubuntuforums.org/attachment.php?attachmentid=40587&d=1187045223](http://ubuntuforums.org/attachment.php?attachmentid=40587&d=1187045223)

grab the deb and double click or sudo dpkg -i
to install it, it's dillo i compiled with all the goodies.

run it from terminal to see if you got all the dependencies, i usually have to install libgtk1.2.

by the way dillo is not a full browser, but great for average surfing.

---

### Post by Polish Rifle on 2007-09-10
Tried Epiphany.  Also took a lot of resources.  Basically I would like to have my browser to:

- be light
- have adblock
- save passwords
- tab browsing


Firefox and now Epiphany are out.

---

### Post by kerry_s on 2007-09-10
> **Polish Rifle said:**
> Tried Epiphany.  Also took a lot of resources.  Basically I would like to have my browser to:

- be light
- have adblock
- save passwords
- tab browsing


Firefox and now Epiphany are out.

well my dillo can do 3 from your list. :)
there's no password manager.

---

### Post by vexorian on 2007-09-10
Epiphany should be light weight, something is telling me your issue is not browser related but could be something else.

Do you have a good swap? Also does it only hurt you when using the browser? Have you noticed similar slowdowns when you download packages ? (Synaptic / auto update)

---

### Post by Polish Rifle on 2007-09-10
> **kerry_s said:**
> well my dillo can do 3 from your list. :)
there's no password manager.

Haha Thanks.  That's the next one I'm gonna try.


As for my swap.  I don't know if I have a good one.  I'm new to Linux but I devoted 1 GB to swap.  Is there something else I should switch?  Epihphany was loading tabs, pages were taking 45 seconds to load, minimizing took forever....I could be missing something.

---

### Post by vexorian on 2007-09-10
are you on a wireless connection or something like that? And yep try Dillo if that doesn't work then your problems might be connection related.

---

### Post by Polish Rifle on 2007-09-10
LAN connection.  I primarily use my laptop for browsing.  So I want it to be fast like all other applications, and if it means sacrificing a few cool features I'll do that.  

Once again, I only have 128 MB of RAM.  Should that be enough for Epiphany?

---

### Post by kerry_s on 2007-09-10
> **Polish Rifle said:**
> Haha Thanks.  That's the next one I'm gonna try.


As for my swap.  I don't know if I have a good one.  I'm new to Linux but I devoted 1 GB to swap.  Is there something else I should switch?  Epihphany was loading tabs, pages were taking 45 seconds to load, minimizing took forever....I could be missing something.

you know how to create the launcher for dillo, right?
also the adblock is a text file, which should be empty.
mousepad ~/.dillo/adblock.txt

attached is mine.

---

### Post by kerry_s on 2007-09-10
> **Polish Rifle said:**
> LAN connection.  I primarily use my laptop for browsing.  So I want it to be fast like all other applications, and if it means sacrificing a few cool features I'll do that.  

Once again, I only have 128 MB of RAM.  Should that be enough for Epiphany?

with 128ram all browsers will be slow starting, but should be okay after that. heavy script sites might bring the browser to a crawl, make sure you have noscript and adblock+ for firefox.

---

### Post by vexorian on 2007-09-10
This is kind of making me think of trying dillo , let's see...

---

### Post by maybeway36 on 2007-09-10
Too bad dillo isn't maintained anymore.

---

### Post by Polish Rifle on 2007-09-10
Just heard about Swiftfox?  What's the report on that?

---

### Post by Wapush on 2007-10-30
> **maybeway36 said:**
> Too bad dillo isn't maintained anymore.

[http://lists.auriga.wearlab.de/pipermail/dillo-dev/2007-October/003214.html]("http://lists.auriga.wearlab.de/pipermail/dillo-dev/2007-October/003214.html")

---

### Post by maybeway36 on 2007-10-30
yay FLTK! but I don't think it's in the repos.

---

