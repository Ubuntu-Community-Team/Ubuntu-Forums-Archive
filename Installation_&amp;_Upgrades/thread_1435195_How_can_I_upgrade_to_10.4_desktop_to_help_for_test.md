---
title: "How can I upgrade to 10.4 desktop to help for testing it"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2010-03-21
I am using 9.10 desktop I want to participated to testing to 10.4, how can I upgrade to it, then report to the bugs ubuntu ?

---

### Post by emyr42 on 2010-03-21
update-manager -d should show the new version.

---

### Post by Mark Phelps on 2010-03-21
> **hoboy said:**
> I am using 9.10 desktop I want to participated to testing to 10.4, how can I upgrade to it, then report to the bugs ubuntu ?

Well, the first thing you need to do is find the correct forum for your question ...

If you're going to do 10.04 testing, go to the Development forum and look for the Lucid Lynx Testing subforum.

Second, you do realize that Lucid only just entered beta, right? Meaning it's still unstable.  As a matter of fact, if you visit the subforum I mentioned, you will see a thread advising AGAINST installing the beta1 right now due to problems.

---

### Post by garvinrick4 on 2010-03-21
sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade

This is for karmic to lucid.

As said before, use lucid as second system. Is nice to bug report and fun for me on dailys to see whats up next.
And what is down. 

I would say if you are stable keep it that way and make a new partition of say 10 gig or so and stick lucid in there.
Do not need a lot of home. I keep maybe fifty documents and 10 albums of music and 2 gig of downloads and I am at
7.4 gig of lucid right now. My downloads are a few .iso's that I made Live USB's with do not really need to keep them but
have room. Have a Live USB around they are much faster to work with. If will not boot into a USB then of course Live CD.
That is just recommended by personal opinion. But if you know your way around a Live CD and you want to fly by the seat of
your pants and use Lucid as your main OS then have at it. Enjoy hoboy.

---

