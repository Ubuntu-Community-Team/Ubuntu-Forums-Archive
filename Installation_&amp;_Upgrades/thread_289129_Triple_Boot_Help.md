---
title: "Triple Boot Help"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by Micahb on 2006-10-30
I have windows and ubuntu installed already, and I also want to install Kubuntu to a newly formatted partition. I don't know much about manually partitioning, so I just took two screenshots. 
Please tell me if this will be the correct way to do it, without overwriting an old partition/losing files.

Thanks.

---

### Post by Henry Rayker on 2006-10-30
This will do to you what I did yesterday.

The / directory is going to be installed over the hda2 directory (which is bad news for you, because hda2 appears to be where your Ubuntu installation is currently sitting).

(I am correct in assuming you want Kubuntu on the 7GB partition, Ubuntu is on the 27GB partition, correct?)

What you'll want to do is:
/media/hda1 38Gb Partition 1 Disc IDE/ATA 1 (Primary) [hda1]
/media/hda2 28Gb Partition 2 Disc IDE/ATA 1 (Primary) [hda2]
swap        2Gb  Partition 5 Disc IDE/ATA 1 (Logical) [hda5] x
/           7Gb  Partition 4 Disc IDE/ATA 1 (Primary) [hda4] x


I hope this helps. I believe the x in the swap should be there, but I may be incorrect on that little detail. Possibly wait for someone else to check my work, as well.

---

### Post by Micahb on 2006-10-30
That looks more correct to me, thanks for the reply.
I will wait for somebody else to reply as well, but just so the next person knows, you are correct - I want Kubuntu on the 7gb.

---

### Post by Kateikyoushi on 2006-10-30
2GB swap seems a bit like an overkill, I wouldn't make it bigger than a GB, make the  / partition 8 GB.

---

### Post by gn2 on 2006-10-30
You don't necessarily have to install to a separate partition, kubuntu-desktop can be added to your Ubuntu installation.
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

After installing just create a new user for Kubuntu.

---

### Post by Micahb on 2006-10-30
Oh cool, I didn't know you could do that. Well, I already installed but I will try that out anyway just to experiment.

Thanks guys.

---

