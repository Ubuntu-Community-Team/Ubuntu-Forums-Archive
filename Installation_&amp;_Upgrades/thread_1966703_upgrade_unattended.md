---
title: "upgrade unattended"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by r+9 on 2012-04-27
Perhaps I've been asking google the wrong questions but I can't find a solution so I wanted to pose the question here.

Is it possible to upgrade a ubuntu distro unattended?  
I'll try to explain. 

When I hit "I want to upgrade" or $sudo do-release-upgrade
That means I want to approve everything the upgrade is going to sit and wait for me to click, [approve, replace, clean up] etc.

apt-get install has the "-y" why doesn't do-release-upgrade?

It's very frustrating to come back to an upgrade 3-6 hours later and find it stuck on some silly question for the last 2.5-5.5 hours.

---

### Post by jadtech on 2012-04-27
it should ask  if you  want it to stop so you can confirm various things just answer the right way it will continue no stopping yes you can do the install while not watching there is not much you can do if there is a problem at that point untill its all finished ..

i am starting to see why many here were pushing the back up  your system install the release fresh  biggest issue you are at the mercy of the internet one power glitch one packet drop minor disconnect  and starts a cascading efect in the install that can take hours to repair ..

---

### Post by r+9 on 2012-04-27
Perhaps I just missed it then.
I understand the risks, but I'd gladly "retry" if I could do it while sleeping.
I suppose I should just fresh install if I'm that hasty, that usually only takes an hour or less and I've got scripts to keep things up dated.

---

### Post by oldfred on 2012-04-27
I never have used this, but you have to give the system the responses it needs. May have to have updates for each version?

Kickstart - Unattended Ubuntu installations made easy
[http://www.linuxuser.co.uk/tutorials/unattended-ubuntu-installations/2/](http://www.linuxuser.co.uk/tutorials/unattended-ubuntu-installations/2/)

I had changed to using USB flash as it was quicker than the CD. But now I use hard drive and it is quicker still. With my dual core 6 year old system I can install in less than half an hour. Longer on slower writing flash drive as I also install to that. 

And my install from a hard drive to my new SSD was extremely fast. Even with updates as part of the install which I did not do as it was slower before.

---

