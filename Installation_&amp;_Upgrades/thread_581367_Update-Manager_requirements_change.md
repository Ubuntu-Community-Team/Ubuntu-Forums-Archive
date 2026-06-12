---
title: "Update-Manager requirements change"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by gondoi on 2007-10-19
I am trying to upgrade to Gutsy through the Update Manager, but it's not working out.

I have a / file system that is 4G and I currently have ~1G free.  When I ran the Update Manager for the first time, I had about 600M free, and it complained saying that it need ~800M of free disk space, to please free up about 300M.  Well, I freed up 356M and attempted to run the Update Manager again and upgrade to Gutsy.  This time around though it claims it needs ~1200M of free space and that I still need to free up 250M.

Why did this increase?  Is there anything I can do to return the settings to default?  I tried re-installing Update Manager in case there were some settings that got jacked, but it didn't help.  I can't free up any more space cause it's all system stuff on the / file system.

Thanks.

---

### Post by gondoi on 2007-10-22
*sigh*

No response.

---

### Post by jazzgossen on 2007-10-30
I have exactly the same problem. Haven't found a solution yet. Have you?

---

### Post by gondoi on 2007-10-30
I figured out why the space requirements grew.  It was because I cleared the apt cache... lol... doesn't help me or you out, but I was able to get the upgrade accomplished by downloading the alternate install cd.  I just downloaded it to my home partition and mounted it up loopback and typed Alt-F2. Here I executed:

```
gksu "/mount/cd/cdromupgrade"
```

Upgrade complete.

---

### Post by jazzgossen on 2007-10-31
I also downloaded and mounted the alternate CD, but the disk space requirements still grow bit by bit. At first it said it needed about 1560 MB, I removed some programs to free up a bit more than that, but now it needs more than 1600 MB of free space, and I'd rather not remove any more programs. Sigh...

---

