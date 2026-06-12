---
title: "how to start CPU Frequency Scaling Monitor in &quot;OnDemand&quot; mode?"
date: 2010-04-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by mdurham on 2010-04-27
Quite often it starts up in Performance mode, I'd prefer OnDemand. Is there a setting somewhere to fix this. At the moment it seems a bit random.
Cheers, Mike

---

### Post by nwadams on 2010-04-27
i find that it boots into performance mode, but if you leave it for 30 seconds or so it then switches to on-demand after bootup is finished.

---

### Post by brian183 on 2010-04-27
I think if you edit the file /etc/init.d/ondemand file.

Change the line that probably looks like this:
```
echo -n performance > $CPUFREQ
```

to set it to ondemand:
```
echo -n ondemand > $CPUFREQ
```

---

### Post by 2hot6ft2 on 2010-04-27
And you can find a lot of things here to adjust. It starts out with laptop mode but there is a whole lot on the page like setting the CPU frequency.
[http://manpages.ubuntu.com/manpages/karmic/man8/laptop-mode.conf.8.html](http://manpages.ubuntu.com/manpages/karmic/man8/laptop-mode.conf.8.html)

---

### Post by mdurham on 2010-04-28
> **brian183 said:**
> I think if you edit the file /etc/init.d/ondemand file.

Change the line that probably looks like this:
```
echo -n performance > $CPUFREQ
```

to set it to ondemand:
```
echo -n ondemand > $CPUFREQ
```
Thanks brian183, I had a look at that file but it's already set to "ondemand". The strange (annoying) thing is that it isn't consistent.

and thanks 2hot6ft2 (really?) I'll take a look at your recommendation.

Cheers, Mike

---

### Post by psyke83 on 2010-04-28
> **mdurham said:**
> Quite often it starts up in Performance mode, I'd prefer OnDemand. Is there a setting somewhere to fix this. At the moment it seems a bit random.
Cheers, Mike

It's not random; the governor is deliberately set to performance mode so that your computer will boot faster. This is actually a good thing and will probably reduce your battery usage.

As nwadams mentioned already, the governor goes back to ondemand after ~30 seconds, so you don't need to do anything.

---

### Post by nwadams on 2010-04-28
Thanks psyke83. Yes it is deliberate. It appears that it is 60 seconds from when the daemon gets initialized to the cpu frequency scaler set to on-demand (if i'm reading the /etc/init.d/ondemand script correctly). But either way, it helps your computer boot faster, and since its only 1 minute, it will have a negligible impact on battery life.

---

### Post by mdurham on 2010-04-28
Thanks guys, marking as [solved]
Cheers, Mike

---

