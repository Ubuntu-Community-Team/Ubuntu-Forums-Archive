---
title: "Switch Back to Karmic?"
date: 2010-01-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by LegendarySandwich on 2010-01-29
Hi everyone, I just upgraded to Lucid Lynx Alpha 2. Well, no problems so far (except for a couple minor ones) so I think I'm going to continue using Lynx. However, I might want to switch back until the official release, so how would I do that?

---

### Post by dudude on 2010-01-29
I could be wrong, but I think that you can only go up releases and not down.

---

### Post by LegendarySandwich on 2010-01-29
> **dudude said:**
> I could be wrong, but I think that you can only go up releases and not down.
So I would have to stick with Lucid?

---

### Post by oldfred on 2010-01-29
I have gone to having two partitions for Ubuntu installs. I have all my data in a separate partition which I link into /home so all my data is available. With an install only needing 10GB just install Karmic. I do not know if you try to down grade /home settings if that will work since most applications will upgrade or add new settings with a new version.

---

### Post by phillw on 2010-01-29
The only issue I had, and was okay with, was rsyncing my bookmarks / history between FFox in 9.10 & 10.04. This was because I was running two different versions. Now that I'm on 3.6.1 in both, it no longer keeps checking the extensions / add-ons each time I rsync over. My MySQL dbases I copied over using mysqldump without any problem and documents in OOo seem quite happy.

I was cautioned against sharing my /home partition directly with 10.04, Just In Case. My Muizik is on a seperate data partition. I just mount the /home partiton do a quick rsync if I'm going from 10.04 back onto 9.10. From 9.10 to 10.04, I mount the new 10.04 partition and rsync to it's /home. It may sound complicated - But it's simply a case of mount the /home I am rsyncing **to** then a quick ```
sudo rsync -aS /home/phillw/. /media/home/phillw/.
```

Regards,

Phill.

---

### Post by philinux on 2010-01-29
> **LegendarySandwich said:**
> So I would have to stick with Lucid?

Yes or reinstall karmic.

---

### Post by Starks on 2010-01-29
> **dudude said:**
> I could be wrong, but I think that you can only go up releases and not down.
Downgrade pinning is possible, but it's easily one of the craziest operations (in terms of motivation and complexity) you can do in Ubuntu.

[https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)

---

### Post by donniezazen on 2010-01-29
> **LegendarySandwich said:**
> Hi everyone, I just upgraded to Lucid Lynx Alpha 2. Well, no problems so far (except for a couple minor ones) so I think I'm going to continue using Lynx. However, I might want to switch back until the official release, so how would I do that?

Better create a separate home partition for things like this in future.

---

