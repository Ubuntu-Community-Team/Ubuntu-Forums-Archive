---
title: "Consecutive Hardy Install Hangs at 0%"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by DeLaNooch on 2008-05-20
I have been using Feisty on my notebook happily since the beginning of the last school year. Last night I decided to finally upgrade. 

I downloaded the Hardy AMD64 .iso and a fresh install went off without a hitch. Once it was up and running, everything seemed smooth and fast for the few minutes I poked around. (I didn't get to actually start messing with my wireless card or video drivers or anything.) 

I then realized that I forgot to set a mount point for my FAT32 partition that I use for all my file storage. Meaning I couldn't figure out how to access all the files still in that partition. The only way I knew to go back and set that mount point was to fresh install again. Multiple installs don't bother me, since I had to do it about a dozen times to finally get Feisty working how I wanted it. 

However, the second install hung at 0%. It said something along the lines of "Removing existing OS files" (not verbatim by any means). They system didnt actually "freeze" it just sat there working for a very long time. I tried a few more times and the same thing happened.

What gives? Anyone know a way around it? Maybe uncheck the format box besides my root partition? Maybe just be more patient?

Thanks.

---

### Post by PmDematagoda on 2008-05-20
How long did you actually wait? Also, did you try formatting the drive manually using the partition editor provided in the Live CD to see if that fixes the problem?

---

### Post by DeLaNooch on 2008-05-20
I'd say I waited in the ball park of 20 minutes.  Yes, I did (and always) use the "manual" partition editor when installing.  I have 4 partitions on my drive that never change. Ext3 root, Swap, Fat32, and unused space.  The former 2 are formatted and mounted at each install, the Fat32 partition is mounted as /j but not formatted, and the unused space is just that.  I simply forgot to mount the Fat32 partition as /j on my first install, so was reinstalling to fix that problem.  Now the consecutive installs hang.

---

### Post by PmDematagoda on 2008-05-20
Did you try formatting the drive using the built-in partition editor prior to the reinstall?

---

### Post by DeLaNooch on 2008-05-20
Ah! Sorry, I didn't realize that's what you meant on your first reponse.  I'll give that a shot.  Thanks.

---

### Post by DeLaNooch on 2008-05-21
That did the trick! Thanks.

---

### Post by PmDematagoda on 2008-05-21
> **DeLaNooch said:**
> That did the trick! Thanks.

Glad it worked out:).

---

