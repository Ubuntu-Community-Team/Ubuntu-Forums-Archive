---
title: "Need a hand with Compiz"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by petronell on 2008-03-13
Hi,

I have been reading various posts about Compiz and I have got a bit stuck.

I have installed the package fine, and followed a guide in another thread on how to set it up, but it doesn't seem to work.

When I type Compiz in the terminal I get back...

compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

Can someone help me understand what this means?

My graphics card is an ATI Radeon 2400 and I installed those drivers with Envy which seems to work fine.

Any help would be gratefully received.

dr :confused:

---

### Post by Pumalite on 2008-03-13
If you have 7.10, it comes pre installed. All you have to do is enable it.
System>Preferences>Appearance>Visual Effects>Extra.
Your card might not be able to produce them.

---

### Post by petronell on 2008-03-15
Thanks - I am not sure the graphics card is installed right.

I used Envy to install the card and it did identify it as the right type.

But when I look at Hardware information under prefences it says the ATI card is an unknown type. Is this right? 

Is there a list somewhere that says what hardware is compatible with Compiz. It is a brand new laptop and the card has 248mb of onboard memory and is HD compatible so I would have thought it should work with Compiz?

---

### Post by Pumalite on 2008-03-15
Almost all ATI cards are 'unknown' because ATI does not support Linux.

---

### Post by petronell on 2008-03-15
Thanks Pumalite for your help.

---- I got the the answer on another thread.

---- What you need to do is remove compiz..

sudo aptitude remove compiz

---- Then reinstall the ATI graphics drivers with Envy

sudo envy -g

---- then re-install compix

sudo aptitude install compiz

And it all works well for me.

---

