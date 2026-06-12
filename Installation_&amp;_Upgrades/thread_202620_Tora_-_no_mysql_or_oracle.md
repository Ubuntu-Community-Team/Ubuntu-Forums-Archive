---
title: "Tora - no mysql or oracle"
date: 2006-06-23
forum: Installation &amp; Upgrades
---

### Post by smylie on 2006-06-23
I've just installed Tora from synaptic (again), and it only comes up with Postgres as the only available connection type - no mysql or oracle.
I've had a hunt round the forums and found one suggestion for manually compiling to get the oracle support, but nothing in regards for mysql.

I've installed mysql (client and server) first, so all the libraries should be there . . .

am I over looking something obvious here, or do i need to compile tora from source to get mysql to work? (I'm really trying to use synaptic as much as possible to avoid upgrade headaches . . .)

Cheers
Dave

---

### Post by kavanutz on 2006-06-27
to get mysql to work with tora you have to install the libqt3-mt-mysql package.

...but the tora package from ubuntu was not built with oracle support, so the only way i could get oracle to work was to [compile it myself.]("http://www.ubuntuforums.org/showthread.php?t=189381&highlight=tora")

hope this helps..

---

### Post by smylie on 2006-06-29
god - so simple when you know how...

i'd actually given up and was trying to compile tora manually. unfortunately i was getting errors re qscintilla, but happened to recall i'd seen a post (prob yours) on compiling tora and on searching for it, found someone (you!) had finally replied to this thread. 

cool. thanks heaps =)

---

### Post by enmanuelr on 2006-11-21
Dude, thanks a bunch. You wont imagine the amount of time i spent looking for a way get around that problem. Let's hope the tool is worth it.

---

### Post by samandiriel on 2007-10-03
Kavanutz, I worship at your toesie-woesis!  That was exactly the information I needed as well.

---

### Post by huggy77 on 2007-10-25
Linux is really a wonderfull development platform....  I ditched windows about a year ago...  My office is all MAC and Linux... Gutsy is beautiful....

---

### Post by mmichalik on 2008-02-19
kavanutz, that helped me out a bit as well.

Thanks!

Mike

---

