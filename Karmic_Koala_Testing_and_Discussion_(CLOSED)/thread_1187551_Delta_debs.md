---
title: "Delta debs"
date: 2009-06-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by super.rad on 2009-06-14
Pretty sure I've seen a thread about this before but can't remember if it was from Jaunty forums.
I'm using fedora 11 as my main OS at the moment and have installed the delta-rpm plugin and it's great, is there any plans to use delta deb's for ubuntu? It would be a great feature especially for people who have slower or capped internet connections

---

### Post by UbuWu on 2009-06-14
There are some plans for this, see this spec (which is still in the drafting phase)):

[https://wiki.ubuntu.com/AptSyncInKarmicSpec](https://wiki.ubuntu.com/AptSyncInKarmicSpec)

---

### Post by ktp on 2009-06-14
that looks interesting.

---

### Post by Simian Man on 2009-06-14
It actually took Red Hat quite a while to get it working well - since Fedora 7 or so I think.  Given the slow moving nature of Ubuntu and Debian, I doubt this will happen within 3 years.

Maybe Ubuntu should switch to the standard rpm format :)?

---

### Post by shifty_powers on 2009-06-14
or maybe red hat should move to the standard deb format :P

---

### Post by ktp on 2009-06-14
> **shifty_powers said:**
> or maybe red hat should move to the standard deb format :P

:lolflag:

---

### Post by freeman2000 on 2009-06-14
> **UbuWu said:**
> There are some plans for this, see this spec (which is still in the drafting phase)):

[https://wiki.ubuntu.com/AptSyncInKarmicSpec](https://wiki.ubuntu.com/AptSyncInKarmicSpec)


That would be great!  Should be a top priority.  Sometimes I have to leave my laptop & internet (slow 3g USB modem) on all night to download the latest updates, as they are huge.  Can we say "global warming"?

---

### Post by Simian Man on 2009-06-14
> **shifty_powers said:**
> or maybe red hat should move to the standard deb format :P

No, actually rpm is part of the Linux Standard Base - in addition to being used by more distros .  Plus there are deltarpms :).

---

### Post by ssam on 2009-06-15
> **Simian Man said:**
> No, actually rpm is part of the Linux Standard Base - in addition to being used by more distros .  Plus there are deltarpms :).

but it lacks many nice features, eg distinguishing between depends, recommends and suggests.

also even if debian/ubuntu switched to rpm, you would need separate fedora-rpms from ubuntu-rpms

---

### Post by super.rad on 2009-06-15
> **UbuWu said:**
> There are some plans for this, see this spec (which is still in the drafting phase)):

[https://wiki.ubuntu.com/AptSyncInKarmicSpec](https://wiki.ubuntu.com/AptSyncInKarmicSpec)

Looks good, looking forward to getting it

---

### Post by inportb on 2009-06-15
This should be a choice, not the default. Many of us prefer to download more data rather than more files; there is a substantial overhead when making tons of connections for tiny files in the case of delta updates.

Debian uses deltas by default for the testing builds, and it was so slow that I had to disable the feature.

---

### Post by psyke83 on 2009-06-15
> **inportb said:**
> This should be a choice, not the default. Many of us prefer to download more data rather than more files; there is a substantial overhead when making tons of connections for tiny files in the case of delta updates.

Debian uses deltas by default for the testing builds, and it was so slow that I had to disable the feature.

Perhaps using [LZMA compression for debs]("https://wiki.ubuntu.com/dpkg-lzma") is an intermediary answer?

---

### Post by olskar on 2009-06-15
> **inportb said:**
> This should be a choice, not the default. Many of us prefer to download more data rather than more files; there is a substantial overhead when making tons of connections for tiny files in the case of delta updates.

Debian uses deltas by default for the testing builds, and it was so slow that I had to disable the feature.

Hm, are there more files with deltas than regular updates? How come?

---

### Post by inportb on 2009-06-15
> **olskar said:**
> Hm, are there more files with deltas than regular updates? How come?

I have no idea... but I did notice that apt was making far more requests than normal.

---

### Post by super.rad on 2009-06-15
What do you mean by more files? On fedora I had 68 updates and it didn't download any extra files, just the 68 updated packages and all of those were tiny as it was only downloading what had changed since the last version.

---

### Post by psyke83 on 2009-06-15
> **super.rad said:**
> What do you mean by more files? On fedora I had 68 updates and it didn't download any extra files, just the 68 updated packages and all of those were tiny as it was only downloading what had changed since the last version.

AptSync is not exactly like delta rpms, though. I assume that Fedora packages the deltarpms against specific previous packages, including only the changes. The AptSync solution seems to use rsync in an attempt not to rely on specific packages being available to complete the upgrade.

---

### Post by Starks on 2009-06-15
Why is aptsync even in the blueprints if it has practically zero chance of making the release or the subsequent Lucky Liger.

---

### Post by ghindo on 2009-06-15
> **Starks said:**
> Why is aptsync even in the blueprints if it has practically zero chance of making the release or the subsequent Lucky Liger.I think a lot of ideas get turned into blueprints, even if they aren't ready in time for the release.  For example, the free Flash spec has been in there since Hardy or Intrepid.

---

### Post by 23meg on 2009-06-15
> **Starks said:**
> Why is aptsync even in the blueprints if it has practically zero chance of making the release or the subsequent Lucky Liger.

> **ghindo said:**
> I think a lot of ideas get turned into blueprints, even if they aren't ready in time for the release.  For example, the free Flash spec has been in there since Hardy or Intrepid.

Note the values of the "Series goal" and "Milestone target" fields.

---

### Post by handaxe on 2009-06-15
I once asked the OPs question a way back:

[http://ubuntuforums.org/showthread.php?t=399290](http://ubuntuforums.org/showthread.php?t=399290)

Delta debs would be a "good to have" option for those in need.

HA

And 23meg contributed there too...

---

### Post by ssam on 2009-06-15
> **psyke83 said:**
> AptSync is not exactly like delta rpms, though. I assume that Fedora packages the deltarpms against specific previous packages, including only the changes. The AptSync solution seems to use rsync in an attempt not to rely on specific packages being available to complete the upgrade.

that sounds like it will put a huge load on the server. why not just have diffs relative to the most likely installed versions (probably the previous version, and the version on the install cd). for the 5% of times there is not a match, then you can apt could just grab the full package.

---

### Post by ktp on 2009-06-15
> **ssam said:**
> that sounds like it will put a huge load on the server. why not just have diffs relative to the most likely installed versions (probably the previous version, and the version on the install cd). for the 5% of times there is not a match, then you can apt could just grab the full package.

Most of the operation happens on the client side; server only has one time check sum of the files...so not really rsync but zsync.  You can read more about on the wiki.

---

