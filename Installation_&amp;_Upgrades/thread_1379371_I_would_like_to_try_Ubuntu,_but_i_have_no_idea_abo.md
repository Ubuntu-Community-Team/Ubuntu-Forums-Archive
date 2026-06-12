---
title: "I would like to try Ubuntu, but i have no idea about partitions"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by IcyRhythms on 2010-01-12
i'm currently running windows 7 in raid 0. i'm not sure how to partition one of the two hdds. any help would be appreciated. also, is there a 64bit version of ubuntu? thanks

not sure if it makes a difference...but some of my specs are

Intel Core i7 920@2.67ghz, 1.5TB HDDx2, 8GB DDR3@1066mhz, Nvidia Geforce  GT220

---

### Post by darkod on 2010-01-12
Yes, there is 64bit version. And don't be confused that it has amd64 in the image name, it works on Intel CPUs.
But if you're running RAID 0 how do you plan to partition only one of the hdds?
Also, installing ubuntu as new user on raid setup is not quite easy as single drive setup. Not a really good way to try ubuntu.
One option to try it, if that's what you want for a start, is to download the desktop 64bit image, burn it to a cd, and boot with that cd and the Try Ubuntu option. That option will not install anything on your hdds and it will run from the cd as a fully functioning desktop version. You can see whether your internet works, browse, check audio/video, etc. Basically, see how you like it.

---

### Post by IcyRhythms on 2010-01-12
this computer came pre installed with a partition already. i just can't figure out why 5.88gb of the 14.6 is being taken up.(and by what exactly) i could possibly use that one if i knew what i was doing

---

### Post by darkod on 2010-01-12
> **IcyRhythms said:**
> this computer came pre installed with a partition already. i just can't figure out why 5.88gb of the 14.6 is being taken up.(and by what exactly) i could possibly use that one if i knew what i was doing

It might be a restore image that restores windows to factory condition if anything happens. Like most PCs these days don't ship with windows install media. In that case you might have to keep that image/partition.

---

### Post by IcyRhythms on 2010-01-12
yeah, but this computer came with vista. it does say recovery for the information. i'll be sticking with my windows 7 home that i paid a considerable amount for. would i be able to use that?

---

### Post by automaton26 on 2010-01-12
The x64 version (amd64) is great. Haven't had any problems with it.

From memory (!), you'll need 2 partitions somewhere - one for ubuntu and one for the swap partition. But because a disc can only have a maximum of 4 Primary partitions, you might need to be careful because Windows 7 installations now reserves 2 partitions instead of 1 (sigh!). And if your OEM has put a diagnostic partition on there, then you'll only have 1 free.

Although, if you have 8Gb, you can probably forget the swap partition anyway. I've done that with a 4Gb machine and never had any problems.

Also, I think the next version of ubuntu will allow swap *files* within the ubuntu partition, like Windows used to have.

But regardless, do as much reading around as you can, especially with a RAID setup. Take a look at the "Disk Management" utility (diskmgmt.msc)

Good luck!

---

### Post by darkod on 2010-01-12
> **IcyRhythms said:**
> yeah, but this computer came with vista. it does say recovery for the information. i'll be sticking with my windows 7 home that i paid a considerable amount for. would i be able to use that?

You mean use that partition for ubuntu? Yes, if you have win7 install dvd you don't need that vista recovery partition any more.
But in order to install ubuntu on fakeraid (mobo raid) you need to use the alternate install cd, not the standard desktop cd.
There is some guide here. I haven't installed on raid yet.
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by IcyRhythms on 2010-01-12
ultimately, this would be a lot easier to try out, if i like it, do a clean install on the C: and erase windows after backing everything up. what are some cons of ubuntu in comparison to windows 7?

---

### Post by SuperSonic4 on 2010-01-12
Gaming
Eye-Candy
Professional Programs (office, photoshop etc)
BSOD

---

### Post by IcyRhythms on 2010-01-12
thanks

---

### Post by IcyRhythms on 2010-02-26
i'm in need of resurrecting thread at the moment. someone mentioned that if i'm in raid, it's a little tough to install ubuntu. is there a way to know if i'm in raid? i'm not a total noob with comps or anything. i'm just a bit confused.

1.5TB Serial ATA 2 Hard Drive 7200 RPM
1.5TB Serial ATA II Hard Drive 7200RPM


my receipt says exactly that. if that helps anyone help me

---

### Post by IcyRhythms on 2010-02-26
anyone?

i just tried booting up the demo to check this os out, and it won't open for me. i've tried it twice, it gets half way, and windows tells me that permission is denied.

---

