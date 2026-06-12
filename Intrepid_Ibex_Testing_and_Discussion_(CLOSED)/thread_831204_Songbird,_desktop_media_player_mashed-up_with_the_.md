---
title: "Songbird, desktop media player mashed-up with the Web"
date: 2008-06-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ubulette on 2008-06-16
Hi,

some weeks ago, I decided to package Songbird.
Since that, I've been maintaining it in my [PPA]("https://launchpad.net/~fta/+archive"). In order to get it in Intrepid, we (the Ubuntu MozillaTeam) would like to, among other things, make it use our xulrunner-1.9 SDK package, but it requires some real efforts, and we have so many things to do.

In the meantime, preview packages live in my PPA.
Feedbacks welcome. Needless to say it's meant to evolve a lot, it's still pretty raw on my side.

(I'll bump it to 0.6 later this week, i.e. when upstream will have the branch tagged properly)

---

### Post by Gina on 2008-06-16
I tried Songbird a while back and rather liked it.  That was in my early days of Ubuntu :)  I'll give it another go :)

---

### Post by Ejas12 on 2008-06-16
The latest version of songbird rocks!!, it works sweet in ubuntu 8.04.
I started with songbird when i Used XP (not very proud about de MS part) but it was so much faster than Itunes or WinAmp

---

### Post by kk0sse54 on 2008-06-16
Just installed songbird and so far it really does rock :guitar: definitely replaces Exaile for me. Really like it's performance too

---

### Post by Gina on 2008-06-17
Just installed it too, let it scan my music folder and now playing the music :)  Working well :):)  Looking good so far :)

---

### Post by plun on 2008-06-17
Songbird for Intrepid within your ppa looks broken to me....:confused:

----------------------

Thunderbird 3 is also broken, crash boom bang > seg fault ,  nightly build works ok.

:) 


PS  Songbird cannot beat Exaile...but I must test it. "Mozilla freak"..:lolflag:  DS

---

### Post by vishzilla on 2008-06-17
Songbird is gradually improving. It has good potential. I haven't tried it since 0.4. I read a positive review on 0.6, I will try it once again.

---

### Post by Gina on 2008-06-17
> **plun said:**
> Songbird for Intrepid within your ppa looks broken to me....:confused:I'm running it in Hardy ATM - i386 version.  I'll try it in Intrepid (AMD64) later.

---

### Post by ronacc on 2008-06-17
I was not very impressed by the earlier version , I'll give this one a try as soon as the AMD64 version for intrepid is available .

---

### Post by ubulette on 2008-06-17
> **plun said:**
> Songbird for Intrepid within your ppa looks broken to me....:confused:


a little bit of information would help. What is broken? anything in the error console?

> **plun said:**
> 
Thunderbird 3 is also broken, crash boom bang > seg fault ,  nightly build works ok.


same thing, logs ? gdb stack ?

both works fine for me, intrepid i386 & amd64.

---

### Post by ronacc on 2008-06-17
in your ppa songbird for intrepid has a red X for amd64 i386 and ipla , and songbird does not show in synaptic with your ppa added to sources ( it did add because I installed flock that way ).

---

### Post by plun on 2008-06-17
> **ubulette said:**
> a little bit of information would help. What is broken? anything in the error console?



Well, just take look at your PPA... red x for all variants as also ronacc wrote...

(going to check Thunderbird with gdb)

---

### Post by ubulette on 2008-06-17
> **plun said:**
> Well, just take look at your PPA... red x for all variants as also ronacc wrote...

oops, I forgot to push my fix. I have it at home. I'll post it later today.

---

### Post by plun on 2008-06-17
> **ubulette said:**
> oops, I forgot to push my fix. I have it at home. I'll post it later today.

Ok, thanks  :D


----------------------------
TB3 crash, maybe its easier to visit IRC and discuss this.
[http://paste.ubuntu.com/20850/](http://paste.ubuntu.com/20850/)

---

### Post by Eclipse. on 2008-06-17
For anyone who cant wait the hardy version works ok on intrepid.;)

---

### Post by ubulette on 2008-06-18
Here is 0.6. Enjoy.

---

### Post by plun on 2008-06-19
Thanks !

I directly was trying to find LastFm and it was a plugin.

This one was working, other Audioscrobblers was broken

[http://addons.songbirdnest.com/addon/1208](http://addons.songbirdnest.com/addon/1208)

A little strange solution when using the standard LastFM client but
it works.


Really "polished" app anyway and everything equal with Firefox.

:)

---

### Post by smbm on 2008-06-22
I used the version from your PPA on my Hardy 32 bit install.

I noticed a couple of problems, the iPod plugin doesn't seem to do anything. The cover art plugin is also broken.

That being said your version started much quicker than the tar.gz version from the website that I'm using now.

Let me know if you need any more info.

Thanks for all your hard work maintaining the PPA and what not.

---

