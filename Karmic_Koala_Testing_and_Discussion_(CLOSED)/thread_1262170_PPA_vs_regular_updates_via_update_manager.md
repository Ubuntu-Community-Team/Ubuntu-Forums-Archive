---
title: "PPA vs regular updates via update manager"
date: 2009-09-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rajeev1204 on 2009-09-09
Hi

I know that ppa's are more cutting edge,my question is..........

How does the package manager avoid conflicts with a regular update.

For example , lets say iam using pulseaudio from the PPA, what happens to the pulseaudio package from the regular repos.



Thanks

rajeev

---

### Post by SuperSonic4 on 2009-09-09
The regular one is removed, assuming you give it the go ahead. However, it won't remove it if it has version specific dependencies

---

### Post by rajeev1204 on 2009-09-09
> **SuperSonic4 said:**
> The regular one is removed, assuming you give it the go ahead. However, it won't remove it if it has version specific dependencies


Hi

How exactly is the regular one removed? You mean the one i see in synaptic is from the PPA and not from the regular repo?

---

### Post by novafluxx on 2009-09-09
This is correct, as long as you have Synaptic setup to only show/offer the latest version available from the repos.

It may offer you both and its up to you to view the package and decide which to install, or it'll only show the most recent version/highest version number:guitar:

---

