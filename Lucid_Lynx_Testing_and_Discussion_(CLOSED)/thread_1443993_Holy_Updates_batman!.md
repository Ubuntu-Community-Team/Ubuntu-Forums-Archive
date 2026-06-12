---
title: "Holy Updates batman!"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 98cwitr on 2010-03-31
Im getting from 100MB to 300MB of updates per day...anyone else getting this much?!

---

### Post by dbowlin17 on 2010-03-31
yes

---

### Post by Owen.C93 on 2010-03-31
mmmmm libs.

---

### Post by Scott82 on 2010-03-31
not really, but i'm only installing them when it doesn't have the partial upgrade thing going on. don't think there were any avail at all over the weekend though.

at least you know someone out there is working on something to (hopefully) improve Ubuntu :D i'd look at it as a good sign.

---

### Post by NightwishFan on 2010-03-31
You can avoid partial updates by using this command from the terminal. (Or I think just hit no when prompted to partial upgrade and it does the same as the following).
```
sudo aptitude safe-upgrade
```

---

### Post by Scott82 on 2010-03-31
Thanks! new post-it on my monitor :D for some reason i'm lazy to the point that clicking no annoys after a while, but i don't mind using a terminal...... kinda odd, right? (wasn't being sarcastic)

---

### Post by NightwishFan on 2010-03-31
I like the terminal. It is more manual, efficient, and verbose.

---

### Post by Scott82 on 2010-03-31
i love how if something does error you actually get decent info when using terminal rather than a 1/2 decent program has crashed or yada yada thing that i can't read faster than my instinct to click ok, closing the window.

---

### Post by Duf_Sh on 2010-03-31
I wonder though, since we are able to use rsync and zsync to download only the changes in daily-build of CDs, why it was not implemented in apt. It obviously would work only on packages that are already installed and that are still in /var/cache/apt/archives, so no good after a "apt-get clean", but that might save us (and Canonical) a heck of bandwidth - as far as I know I'm ok but my local coffee shop / internet hotspot (much better when comes the time to study) might have a problem with me in the not-so-distant future...

---

### Post by bigsmitty64 on 2010-03-31
> **NightwishFan said:**
> You can avoid partial updates by using this command from the terminal. (Or I think just hit no when prompted to partial upgrade and it does the same as the following).
```
sudo aptitude safe-upgrade
```


Nice! just did the update with this, flawless. Thank you for that . Wait.....I haven't rebooted yet, here goes nothing... :)

**EDIT:** Back up and running, I always worry after HUGE updates like that.

---

### Post by Ibidem on 2010-03-31
> **Duf_Sh said:**
> I wonder though, since we are able to use rsync and zsync to download only the changes in daily-build of CDs, why it was not implemented in apt. It obviously would work only on packages that are already installed and that are still in /var/cache/apt/archives, so no good after a "apt-get clean", but that might save us (and Canonical) a heck of bandwidth - as far as I know I'm ok but my local coffee shop / internet hotspot (much better when comes the time to study) might have a problem with me in the not-so-distant future...
That would be neat.  FWIW, Fedora has done that with RPMs.

---

### Post by psyke83 on 2010-03-31
> **Ibidem said:**
> That would be neat.  FWIW, Fedora has done that with RPMs.

I believe they're called delta rpms (or has some better method been introduced since I last read about them)? Windows Vista and 7 also propagate updates via a similar delta/binary diff method in order to reduce filesize.

Edit: Fedora calls it "Presto": [http://fedoraproject.org/wiki/Releases/FeaturePresto](http://fedoraproject.org/wiki/Releases/FeaturePresto)

---

### Post by lavinog on 2010-03-31
> **Duf_Sh said:**
> I wonder though, since we are able to use rsync and zsync to download only the changes in daily-build of CDs, why it was not implemented in apt. It obviously would work only on packages that are already installed and that are still in /var/cache/apt/archives, so no good after a "apt-get clean", but that might save us (and Canonical) a heck of bandwidth - as far as I know I'm ok but my local coffee shop / internet hotspot (much better when comes the time to study) might have a problem with me in the not-so-distant future...

I am almost considering setting up a proxy server just for the 5 machines in my house.

Just from apt-get update in lucid:
```

Get:7 http://us.archive.ubuntu.com lucid/universe Packages [5,536kB]
...
Fetched 11.1MB in 32s (342kB/s)

```
11MB for the package listings!
Is this just because it is in beta...or can we expect this once it is released?
Is this data compressed?

---

### Post by cariboo on 2010-03-31
The devs are working hard squashing bugs, that's why there are so many updates during the testing cycle. Once the final release comes out, there won't be as many updates.

---

### Post by 23meg on 2010-03-31
Now that [Beta 2 Freeze]("https://wiki.ubuntu.com/Beta2Freeze") is in effect, there will be very few.

---

