---
title: "Residual Config Help"
date: 2009-09-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-09-14
If I delete the items in Residual Config will it honestly render my system unusable?

Edit: I can post a screenshot but not sure if it will scroll to see all entries, thus im concerned about Klogd, fast user switcher applet, syslogd, system services, upstart-logd.
I shouldnt touch these im thinking cause my system will fail to boot..am i right?

---

### Post by jpeddicord on 2009-09-14
> **sox fan Matt said:**
> If I delete the items in Residual Config will it honestly render my system unusable?

Edit: I can post a screenshot but not sure if it will scroll to see all entries, thus im concerned about Klogd, fast user switcher applet, syslogd, system services, upstart-logd.
I shouldnt touch these im thinking cause my system will fail to boot..am i right?

Please be more specific. Are you talking about items in Computer Janitor or Synaptic? If you mean the "Not installed (residual config)" filter under Status in Synaptic, none of those packages are installed anyway. All of the packages you mentioned were removed or replaced in Karmic anyway.

So yes, you can remove packages listed with residual config, since they are not installed. The only reason to keep them is if you want to reinstall those packages later.

---

### Post by sports fan Matt on 2009-09-14
Hi Jacob :)

I was referring to Synaptic.  I assume by your post I can remove those packages and all will be ok with system startup?  

I have seen a lot of things in that filter replaced and I have always wondered, on every version since Gutsy what the impact were if said packages were removed.

---

### Post by sports fan Matt on 2009-09-14
When I did remove them, I received : E: sysklogd: subprocess installed post-removal script returned error exit status 1

---

### Post by sports fan Matt on 2009-09-14
That error was easily fixed:)

---

### Post by VMC on 2009-09-14
This is quite interesting. I rarely use Synaptic. I use Aptitude for most of my updates, installs. I had a ton of stuff in that Residual area. Is their an aptitude equivalent? This is the first time I've heard of this.

---

### Post by taavikko on 2009-09-15
> **VMC said:**
> This is quite interesting. I rarely use Synaptic. I use Aptitude for most of my updates, installs. I had a ton of stuff in that Residual area. Is their an aptitude equivalent? This is the first time I've heard of this.

```
aptitude search ~o
```

---

### Post by jpeddicord on 2009-09-15
> **taavikko said:**
> ```
aptitude search ~o
```

Don't quite think that's the same listing. That appears to just list packages that were locally installed or don't exist in the archives. The residual config list in Synaptic shows packages that have already been removed and left behind configuration.

EDIT: Found it!

```
aptitude search ~c
```

---

### Post by taavikko on 2009-09-15
> **jacobmp92 said:**
> Don't quite think that's the same listing. That appears to just list packages that were locally installed or don't exist in the archives. The residual config list in Synaptic shows packages that have already been removed and left behind configuration.

EDIT: Found it!

```
aptitude search ~c
```

Whups, could have read the question bit more carefully :)
Equivalent to "aptitude search ~c" is "dpkg -l |grep ^rc"

---

