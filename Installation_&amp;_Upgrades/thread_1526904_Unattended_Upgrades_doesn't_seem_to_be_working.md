---
title: "Unattended Upgrades doesn't seem to be working"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by MaindotC on 2010-07-08
The update manager keeps popping up to tell me there are updates available.  I installed the unattended-upgrades package so the updates would install without user interaction.  Here are a few lines of my /etc/apt/apt.conf.d/50unattended-upgrades file which I believe are relevant:
```
// Automatically upgrade packages from these (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
	"Ubuntu lucid-security";
	"Ubuntu lucid-updates";
};

```

What seems to be the problem?

---

### Post by MaindotC on 2010-07-08
bump

---

### Post by Sonsum on 2010-07-08
I installed it too, but I've been doing all my updates manually.

So it doesn't work for me either. I had forgotten about it :lolflag:

---

### Post by MaindotC on 2010-07-09
:( I wonder if we're the only ones that noticed :D  I suppose I could just write a cron but I'd really like this package to work :(

---

### Post by Sonsum on 2010-07-09
> **strAlan said:**
> :( I wonder if we're the only ones that noticed :D  I suppose I could just write a cron but I'd really like this package to work :(

It'd be nice if it did. Haha. Although years and years of Windows scarring has actually made me like doing maintenance services like updates. 

I really, really miss having to start a defragmenting service every time I leave the house. ;)

---

### Post by MaindotC on 2010-07-09
> **Sonsum said:**
> I really, really miss having to start a defragmenting service every time I leave the house. ;)

Don't forget reformatting every 2 months...

---

### Post by Sonsum on 2010-07-09
> **strAlan said:**
> Don't forget reformatting every 2 months...

I've actually never had any big issues with Windows. So I'm one of those Ubuntu converts that came not cause they were tired of windows, but because they see it as better :)

---

### Post by MaindotC on 2010-07-09
Well, I don't really have issues now either but that's because I'm much more knowledgable on it's operation and vulnerabilities so I guess I can identify with that.

---

### Post by Sonsum on 2010-07-09
Yeah, I suppose nobody really knows how to fix this.

Cause our conversation has bumped this quite a bit. haha

---

### Post by MaindotC on 2010-07-12
:( bump :(

---

### Post by spikyjt on 2011-01-20
I hope you got this sorted in a timely manner, but just in case someone else finds this post looking for the same problem...

In addition to unattended-upgrades, install update-notifier-common and edit /etc/apt/apt.conf.d/10periodic to include ```
APT::Periodic::Unattended-Upgrade "1";
``` as well as the change to /etc/apt/apt.conf.d/50unattended-upgrades that you already did. This will get the job done.

Thankfully this is all sorted out by the unattended-upgrades package alone in Lucid (and possibly before that). I still have several Hardy servers running, however, so I needed to sort this out too.

---

### Post by nanonils on 2011-01-29
Finally working: [http://ubuntuforums.org/showthread.php?t=1401845](http://ubuntuforums.org/showthread.php?t=1401845)

---

