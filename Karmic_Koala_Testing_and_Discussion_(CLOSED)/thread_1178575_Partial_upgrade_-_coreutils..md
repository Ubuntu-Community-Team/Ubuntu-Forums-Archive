---
title: "Partial upgrade - coreutils."
date: 2009-06-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Vanishing on 2009-06-04
There is another partial upgrade happening now, package is coreutils, anyone having same trouble?
and I see that there are xorg updates too, does this update solve any intel graphic problems?

---

### Post by Vanishing on 2009-06-04
appearently coreutils want to remove mktemp(package for creating temp files), and somehow thats where the conflict occurs..

---

### Post by castrojo on 2009-06-04
Just wait for it to resolve itself, don't try to remove mktemp.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=531846](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=531846)

---

### Post by 23meg on 2009-06-04
> **Vanishing said:**
> 
and I see that there are xorg updates too, does this update solve any intel graphic problems?

Take a look at the changelog to learn what a certain update includes.

---

### Post by Vanishing on 2009-06-04
thank you whiprush and 23meg. I will check the changelog.

---

### Post by ghindo on 2009-06-04
> **whiprush said:**
> Just wait for it to resolve itself, don't try to remove mktemp.

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=531846](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=531846)Looks like the bug has been closed; now we wait for it to make it downstream. :popcorn:

---

### Post by meeples on 2009-06-05
apparently were not supposed to do partial upgrades...

i got a telling :O

---

### Post by davideotape on 2009-06-05
> **meeples said:**
> apparently were not supposed to do partial upgrades...

i got a telling :O

Hehe, you certainly did ;)

---

### Post by celticbhoy on 2009-06-05
I also got 

[COLOR="Red"][B]linux-generic
linux-headers-generic
linux-image-generic[/B][/COLOR]

sitting in update manager

---

### Post by Slug71 on 2009-06-05
> **Vanishing said:**
> There is another partial upgrade happening now, package is coreutils, anyone having same trouble?
and I see that there are xorg updates too, does this update solve any intel graphic problems?

DONT do partial upgrades.

---

### Post by autocrosser on 2009-06-05
Yes--Partial upgrades will eat your computer & spit out your harddrive in very tiny bits ;)

As to the poster about the linux meta--I installed it last night & am running it right now---use only if you do not need any restricted drivers (other than video stuff).......

---

### Post by taavikko on 2009-06-05
> **Slug71 said:**
> DONT do partial upgrades.

You can do "partial upgrades" but when it wants to remove packages, alarm bells have to go on.

---

### Post by autocrosser on 2009-06-05
The update just cleared my unit--7am Pacific time---using the main repo--time to go get it!!!!

---

### Post by pferraro on 2009-06-05
N.B. the mktemp package can now be safely removed (read the package description) - as that was the original intention.

---

### Post by Vanishing on 2009-06-05
Yes yes..I see the update just now..installed.

---

### Post by nyarnon on 2009-06-06
> **celticbhoy said:**
> I also got 

[COLOR="Red"][B]linux-generic
linux-headers-generic
linux-image-generic[/B][/COLOR]

sitting in update manager

Don't use the manager or synaptic, always stick to apt during alfa and beta the rest will give you pain sooner or later.

---

### Post by seeker5528 on 2009-06-06
> **nyarnon said:**
> Don't use the manager or synaptic, always stick to apt during alfa and beta the rest will give you pain sooner or later.

Alfa/beta gives you pain sooner or later, if a package is borked, it's going to be borked no matter what front end you use.

If apt-get doesn't treat recommends as dependencies, then that may be an advantage, but you can turn that off in Synaptic.

I've been using Synaptic for a long time with Debian unstable except for the odd occasion when something got borked that probably would have got borked anyway and I have to use force options, or go to other extremes.

While Synaptic does have it's little quirks and shortcomings at times, I never had a problem that resulted because I use it.

I upgraded A and Synaptic removed B-F (past tense) is not a valid complaint to me, and not something you avoid by using apt-get.

Later, Seeker

---

### Post by ronacc on 2009-06-06
I use apt and synaptic interchangeably , the main thing you have to do is to be aware of what it is proposing to do and if you aren't sure don't click apply until you have checked that it is safe , the ultimate protection for your system is between your ears .

---

### Post by autocrosser on 2009-06-06
> **ronacc said:**
> I use apt and synaptic interchangeably , the main thing you have to do is to be aware of what it is proposing to do and if you aren't sure don't click apply until you have checked that it is safe , the ultimate protection for your system is between your ears .

Many thumbs up!!!!! ;);)

---

### Post by davideotape on 2009-06-07
> **ronacc said:**
> I use apt and synaptic interchangeably , the main thing you have to do is to be aware of what it is proposing to do and if you aren't sure don't click apply until you have checked that it is safe , the ultimate protection for your system is between your ears .

Agreed. My friend decided to uninstall python 2.6 after installing python 3.0. They just clicked apply, without checking what was being removed. Bad mistake :P

---

