---
title: "Dual booting"
date: 2006-12-11
forum: Installation &amp; Upgrades
---

### Post by pyrokinetic on 2006-12-11
Hi there, 

I currently have my computer set up with two partitions, a 50 gig partition with Win XP Pro installed, and a 30 gig unformatted partition. What I'd like to know is this, how do I install Ubuntu (Dapper Drake) onto my 30 gig partition? I tried doing it before but the options confused me a little bit, I didn't want to do a 'default' installation as it didn't look right, so I went to "Manually edit partitions" (I think that's what it was?) and got even more confused.

Also - after I manage to install it, how will I be able to choose which OS I boot at startup? Sorry if these questions have been asked a million times, I did try searching the forum (and google) and found most of the terms a little confusing, so any help for this extreme noob would be much appreciated. :D

Thanks!

---

### Post by fritz_monroe on 2006-12-11
You will probably want to use that 30 gig section of the drive mostly as a linux partition but with about 500 meg of linux swap partition.  Sorry I can't give a step by step, but I'm sure it's around here somewhere.

As for picking which OS, when you power on the computer, Grub will start up and will allow you to choose to boot Linux or XP.  I think that it defaults to booting Ubuntu, but it gives you a couple seconds to decide.

---

### Post by pyrokinetic on 2006-12-11
> **fritz_monroe said:**
> You will probably want to use that 30 gig section of the drive mostly as a linux partition but with about 500 meg of linux swap partition.  Sorry I can't give a step by step, but I'm sure it's around here somewhere.

As for picking which OS, when you power on the computer, Grub will start up and will allow you to choose to boot Linux or XP.  I think that it defaults to booting Ubuntu, but it gives you a couple seconds to decide.

Thanks fritz! Do you have any idea where that guide is? I tried looking, but can't seem to find it.. :(

---

### Post by dorcssa on 2006-12-11
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Try this. ;)

---

### Post by pyrokinetic on 2006-12-11
> **dorcssa said:**
> [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Try this. ;)

Thanks dorcssa, 

That's a really helpful guide, but I'm confused about a couple of things, in the example pictures he has swap and all of his mount points on completely different partitions, does that mean that I'll have to delete my 30 gig partition and chop it up into smaller partitions? or can I install the swap (and the other things mentioned) on that same partition?

Sorry about all the questions, I just don't quite 'get it' yet.

---

### Post by jexxie on 2006-12-11
Hi pyrokinetic,

It's easiest to delete that 30GB partition you have set up, and create two partitions, one swap file (size as twice your RAM, unless you have 2GB ram, then you don't really need a swapfile for a desktop), and the remaining space as your /

---

