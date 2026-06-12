---
title: "RAID0 Dual Boot W7 and..."
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by cthulhuxxx on 2010-01-14
Hello all. Like you see so many of here, I am a newb to installing multiple Operating Systems. I will try to explain my situation exactly. My hope is to get simple answers. Nothing too techie.

Ok, here I go...

I am ordering a new laptop. It will have 3 hard drives. 2 160Gb SSDs which will be in RAID0, and one 500Gb 7200RPM. Obviously the 2 SSDs will be for the OS(s). It will arrive with Windows 7 (64 Bit) already installed on the RAID array. I plan on dual booting, having W7 for for gaming and work.

With RAID0, the 2 SSDs at 160Gb apiece will wind up being one 160Gb hard drive; isn't that right?

So I am thinking of choosing half for W7 (80Gb), and the remainder for Ubuntu (5Gb swap partition, remainder for for OS). So that's 3 partitions total. A 5Gb swap is more than enough; right (with having 12Gb of RAM)?

BTW: The Ubuntu I will be installing is *Ultimate Edition 2.5 64 bit* if that makes any difference

I did try and do some research before starting this thread. Unfortunately, I have to say that I don't think I've learned quite enough.

When I used the live CD and ran the disk partitioning tool on Ubuntu just to see what I could see...it appears that Ubuntu did not see the RAID. It looks as if it was still seeing the two hard drives as separate drives.

So it saw this:

______________
|             |
|   XP        | ------- Hard Drive 1
|             |
|             | ------- Hard Drive 2
|             |
|             |
_______________


So ultimately, I really am looking for someone who has patience enough to baby me through this. I am not too proud to admit that I am very exited about making this happen, yet I have no clue on how to do it.

End Result:
Dual boot W7 (64 bit)/Ubuntu (64 bit) with swap, residing on RAID0 array.

So I'm looking for help literally from starting the computer with the Ubuntu disk in the drive, to seeing my new desktop ready to go, step by step explained like you're explaining to a 5 year old.

Thanks to anyone who replies, sincerely.

Edit:
Oops, my text drawing didn't show up the same as I had it. :(

---

### Post by darkod on 2010-01-14
I'm not sure you can install on raid with the standard desktop cd. For raid the recommendation is to use alternate install cd. I have no idea if that exists for Ultimate edition.

For the raid0, you are wrong. Two drives of 160GB will give you 320GB. In raid0 you have no redundancy. All space of the drives is used, but it is divided in small parts (stripes) and the data is written at the same time to both drives, but half of the data goes to one, the other half to the other one. That's why some people dislike raid0 because if one drive dies, you lose all the data because only half parts of the data will be on the other drive. You can't recover anything in that situation. The benefit is that writing to both drives at same time, you gain sped, at least in theory.

Now, raid1 is another story. That's so called mirror. Two 160GB drives will give you 160GB usable space. One disk is copy of the other. If any disk fails, the computer keeps on working. But you sacrifice half of the space for that.

---

### Post by cthulhuxxx on 2010-01-14
I plan on using the 3rd hard drive for backing up both OSs and storage. I'm  planning on setting up both OSs to exactly where I want them, and then doing entire backups of both for any crashes on the 3rd hard drive. I may possibly create partitions for them on the 3rd hard drive, so if I store anything on the 3rd drive that may be corrupt, it won't spread. I haven't decided on that yet.

Right now I'm just trying to get the RAID dual boot set up.

And if I have to just use the vanilla Ubuntu alternative CD to set up Ubuntu...no problem. Ultimate Edition just has all the eye candy set up, all kinds of programs, and various other things ready to go.

---

### Post by darkod on 2010-01-14
There is info for fakeraid (motherboard raid) here:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by cthulhuxxx on 2010-01-14
I've actually seen that long convoluted page before. Ugh! And in ALL of that tech talk, they actually only cover RAID 1 & RAID 5. No coverage of RAID 0. And it's only updated to 9.04.

---

### Post by cthulhuxxx on 2010-01-14
I know it can be done, because AVADirect can do it. You can order a laptop with Raid 0, with a dual boot setup with W7 & Ubuntu (+swap). So, it can be done. Can anyone walk me through how? If I use the alternative CD, is it easy to do; or do you have to know techie stuff? I'm definitely lost with this.

3 Partitions wanted:
W7
Swap for Ubuntu
Ubuntu

Any help, sincerely appreciated.

---

