---
title: "can someone make me an auto install command for ff3 in gutst"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by exneo002 on 2008-06-22
I'm running on gutsy I can't upgrade to hardy and I want ff3. Can someone make me a command that downloads and installs ff3 in gutsy with wget?

---

### Post by jocko on 2008-06-22
FF3 is available in the repos (alpha 8 in gutsy, beta 4 in gutsy-backports), so just activate the backports repo (in synaptic, go to Settings --> Repositories --> Updates), reload the package list and install firefox-3.0.
Or:
```
sudo apt-get update
sudo apt-get install firefox-3.0
```

---

### Post by djb6 on 2008-06-22
did this with Hardy as well, and it still worked...thanks a lot, considering I'm not very good at this Linux stuff, I just switched from Windows Vista.

---

### Post by bsmith1051 on 2008-06-23
> **djb6 said:**
> did this with Hardy as well
Why?  Hardy already comes with FF3 -- and the 'final' version, too, not an alpha, beta or RC.

Does the backports repo for Gutsy have the final?  I never saw any major bugs with the pre-final versions but I'd still rather get 3.0-final (yes, I'm still running Gutsy)

---

### Post by djb6 on 2008-06-26
I got my version the day it came out, and it still had the beta version instead of the final, since the final I don't think was out yet...

---

