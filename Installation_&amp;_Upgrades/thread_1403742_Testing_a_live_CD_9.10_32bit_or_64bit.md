---
title: "Testing a live CD 9.10 32bit or 64bit"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by Fenris_rising on 2010-02-10
Hi Chaps

I am playing with a live cd of 9.10 both 64 and 32. At the moment 32bit is up and I am running a dual screen with compiz fully functional. I had to mirror the displays in order to be able to activate the effects so compiz would run then I unticked mirrored to get the dual display working. It may be that I will have to do this every time I start up but I am not worried at this time.

I tried the 64bit live CD as well which is the first time I have used 64bit ever. Although I couldn't get compiz to run but I didn't try the trick I did in the 32 bit version.

With no proprietary graphics drivers both are working fast smoothly and impressively. So other than making the decision to install 9.10 over my 8.10 what are the pros and cons of 32 bit and 64 bit?

My main PC related things are - music, watching AVI's , DVD's, Iplayer running a small number of windows based apps (I presume they are 32bit only) under wine, Blender, e mail, surf the net, aMSN. Network with my netbook either via SSH or Samba. Open office, some linux games.

Will I lose any capability with the above list if I went 64bit?

Thanks in advance

regards

Fenris

---

### Post by darkod on 2010-02-10
The main thing it would depend on is your ram size. 32bit can address only about 3.5GB ram, so if you have more and you want it used fully, you basically have no choice but to go with 64bit.

I don't know how one or the other might affect the things you mentioned, I just run 64bit on my desktop for general use.

---

### Post by dabl on 2010-02-10
It's not real recent, but still valid:

[http://ubuntuforums.org/showthread.php?t=765428](http://ubuntuforums.org/showthread.php?t=765428)

The only issue I can imagine is that some of the less popular proprietary media players (i.e. intended for Windows) used to only have a 32-bit version. Flash and Java are fine these days, but you might find a multimedia web site with a proprietary format stream that won't work in a 64-bit browser. Rhapsody.com used to be that way -- I haven't tried it lately.  They should be fine with Wine, however.

---

### Post by Fenris_rising on 2010-02-10
Hi There

Thanks for your input. I should have said -

My Setup

AMD 64 3200+ 2Ghz CPU
2 Gig of DDR2 ram
Radeon X300 ATI GPU

regards

Fenris

---

### Post by Fenris_rising on 2010-02-10
Thanks Dabl

An interesting read. Already I think 32 bit may be the best for me for now. I shall continue to 'play' for a while until I am happy all will be well, or at least only require a little tweaking =D

regards

Fenris

---

### Post by Fenris_rising on 2010-02-10
I have noticed that the 32 bit live CD is hellishly fast compared to the 64 bit. Whether this will translate with a full install I don't know.

regards

Fenris

---

### Post by dabl on 2010-02-10
Nah -- I've never seen any difference in performance between the two architectures.  You would have to run some heavy-duty encoding or transaction processing package to really have a noticeable difference.  At least that's my observation -- these forums are full of unsubstantiated claims that people see faster performance on 64-bit, but they never show any objective data to prove it.

I have 4G of RAM and it's all available to the system, and on one of my OSs I use the JFS filesystem, which is a native 64-bit filesystem, and it runs fast and smooth.  At times I have taken advantage of my dual-core CPU to run two instances of audio encoding, and that sucks up the RAM pretty hard -- perhaps I got faster results with my 64-bit OS, but I didn't have a 32-bit system to compare it with.

If you've been happy with a 32-bit system, and have some trepidation about going to a 64-bit system, I can about guarantee you'll have some problem, and you'll instantly suspect the 64-bit architecture.  I think that's why they shut down the 64-bit forum -- it was always full of "64-bit won't play my music" stuff.  :D

---

### Post by Fenris_rising on 2010-02-10
Hi Chaps

I have similar feelings about CPU speeds. You approach a point where the difference is negligible for most everyday work. I think I will stick with the 32 bit as I don't do anything that really demands anything else. I jsut have to complete some stuff in 8.10 then I will back up and go for it =)

regards and thanks for the advice gentlemen!

Fenris

---

### Post by Fenris_rising on 2010-02-14
Hi Chaps

Today was KK 32bit install day. I did a fresh install and everything is great. Compiz + dual screens the whole shebang is working very well and a boot time of around 30 seconds which I have never had. Fantastic!

It took me a little time to get mp3 playback sorted and to get my second HDD to auto boot and be accessible but nothing major. All in less time than it takes to install a windows OS =)

Interestingly I seem to have the shortest xorg file ever. Yet Compiz, dual screen and DVD playback all play together without issue. I used to have to disable compiz if I wanted to watch DVD's without an annoying flicker. No proprietry drivers are present either yet everything speeds along! This is great!

regards

Fenris

---

