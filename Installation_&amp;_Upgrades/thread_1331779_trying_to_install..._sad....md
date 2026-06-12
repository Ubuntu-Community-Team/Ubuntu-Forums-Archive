---
title: "trying to install... sad..."
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by bzsolt on 2009-11-19
Hi Guys,

I am a bit sad now. This is the 5th time me trying to install (/migrate to) Linux. I have tried it over the last 5-7 years.

Now I have Vista and need it for work but want to have something stable.

I burned the CD, loaded the "try me" which works fab. And then clicked install ubuntu icon.

Now the bad news. I have very limited idea about partitioning but no idea whatsoever about dev/sda what the hell. Why should I? Why am I not being offered a solution?! Would that be so hard? Just resize one partition and put Linux there but no I was bombarded with warnings that everything will be lost and questions to select filesystem or what....

Users do not want to spend time with this stupid partitioning, come on!

Hope someone reads this who can do something about it. I would really like to use Linux!

---

### Post by darkod on 2009-11-19
Just to remind you, the more automatic you make the process the higher the possibility for major mess up. :)
If you tell us the hdd size and your current windows partitions and what you want to do with them (how much space you need for windows), there is easy way out.
And believe me, it's not because I'm using linux for years, I'm new to it too. It really is easy.

---

### Post by bzsolt on 2009-11-19
Hi,

thanks for quick reply.

I have a 70GB partition for Vista and other 230Gb or so for pics, etc. This I could shrink.

Now I realize I might have misunderstood the installer since it says it wants to 'erase Windows Vista (loader)'. So maybe it doesn't want to erase all partitions just the loader bit?

Gparted tells me:
dev/sda1 ext2 70Gig boot
dev/sda2 unkown 230gig lvm
Does that help?
Gparted doesn't offer changing partition size... Maybe I should make it space with partitionmagic from within vista...

I am afraid of loosing all my stuff.

Happened before with linux....

z

---

### Post by darkod on 2009-11-19
First rule: Anything that includes Erase, NO. :)
I see you have LVM actually. That is bit different and I have no experience with that so I wouldn't like to give you wrong information. You'll have to wait someone else to jump in. Sorry.

---

### Post by aysiu on 2009-11-19
Instead of messing with partitions, just use Wubi:
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

