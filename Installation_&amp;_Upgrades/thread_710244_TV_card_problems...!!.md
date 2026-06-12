---
title: "TV card problems...!!"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by shasullah on 2008-02-28
Hello dear friends:KS

how can I install my Tv card from cd ?:confused:

Please tell me :(

---

### Post by shasullah on 2008-02-29
Why you no one give response me?:mad:

Please tell my the way of that :(

---

### Post by risby on 2008-02-29
> **shasullah said:**
> Why you no one give response me?:mad:

Please tell my the way of that :(

Perhaps you should try explaining your problem a bit more clearly.

What sort of computer has you got? eg laptop, destop.

What sort of card is it? eg. PCI, PCMCIA, AGP

Manufacturer, model

What do you mean by install from CD? What CD do you have?

---

### Post by shasullah on 2008-02-29
> What sort of computer has you got? eg laptop, destop.

it is desktop

> What sort of card is it? eg. PCI, PCMCIA, AGP

I don't know but it has a cd by the name of Genie ultia_V1_4 

> Manufacturer, model

Zciber 

> What do you mean by install from CD? What CD do you have?

my mean was cd of that card tv, it has a cd with itself

thanks :KS

---

### Post by shasullah on 2008-03-01
Hi....

There is not any one to tell me can I install it or no, I should leave the TV on Ubuntu ;(

---

### Post by xc3RnbFO8P on 2008-03-01
In terminal:

> sudo apt-get install mercurial linux-headers-$(uname -r) build-essential
> hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)
> cd v4l-dvb
> make all
> sudo make install

Then install **Tvtime** in Add/Remove (all available application)

---

### Post by risby on 2008-03-01
> **shasullah said:**
> Hi....
There is not any one to tell me can I install it or no, I should leave the TV on Ubuntu ;(

You probably would be able to use this card with ubuntu. You probably won't be able to use the software on the CD that came with it.

The problem you have in getting help is mainly that you are not stating clearly what your problem is but also that you haven't tried anything and so have no symptoms of failure and you are not giving enough information for others to work on. There is also the problem of attempting to communicate in something other than your mother tongue. Your phrase "I should leave the TV on Ubuntu" implies you already have it working. Perhaps you could post in your mother tongue and see if anyone responds.

I don't understand how you could not know which interface the card needs to plug into your PC. You could try describing the connector.

Anyway why not just plug it in and see if Ubuntu autodetects the new hardware. It may give you more information.

EDIT: Wow, Ringi got there already. How bout dat!

---

