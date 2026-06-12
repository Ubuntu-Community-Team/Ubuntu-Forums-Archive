---
title: "I can't upgrade mk 2"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by Scott_fakename on 2007-12-04
Nobody responded to my last one, and my only theorys on why were a) I had no profile so they though I was a troll, or B) I responded to my own thread instead of editing the original post. So I am posting it again.

So, today I was looking around at upgrades for my linux partiton (i'm running Feisty) and I wanted to upgrade to gutsy. So i came to school to do it (My modem doesn't work in ubuntu and I cant find any drivers but that's for a different post)

So I looked up how to upgrade the system, and did it once. I couldn't do it with update manager because update manager thinks i'm up to date. So I ran the way they recommend for servers running ubuntu (Probably a bad idea but what the hey). It seemed to work. But when it got to the screen where it tells you "This could take hours, do you want to continue?" I hit no because I needed to shut down and go back into windows to check off some homework I had.

Then I came back up in ubuntu and tried doing it again, and now it doesn't even seem to realize that it's out of date. I run the update manager and it says "Your system is up to date". It did that before anyway, but I ran the command they recommend at ubuntu.org for servers again, and it said it couldn't find anything.

So how can I upgrade now if synaptic, upgrade manager, aptitude, and apt-get all think that I'm up to date and cant find gutsy on any server I can find?

--Scott

---

### Post by Pumalite on 2007-12-04
Try this:

sudo sed -i 's/feisty/gutsy/' /etc/apt/sources.list 

sudo apt-get update 

sudo apt-get dist-upgrade

---

