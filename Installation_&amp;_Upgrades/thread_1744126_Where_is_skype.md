---
title: "Where is skype?"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by ebbr.bugs on 2011-04-30
Since there is no notification area any more in 11.04, where is the skype icon of the running skype instance?

---

### Post by raffaeleserafini on 2011-04-30
I have the same problem, the upgrade has a big bug
no skype icon is visible. I tried to reinstall, but no wai it does not work.
I also have serious problem when spend some hours off and the pc completely paralizes and the only way is to turn it off and restart, it behaves like window! Unbelievable.
I use HP 610 and 11.04 ubuntu in the english version.
regards

---

### Post by awam66 on 2011-04-30
> **ebbr.bugs said:**
> Since there is no notification area any more in 11.04, where is the skype icon of the running skype instance?
You need to run the following:
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Skype', 'Dropbox', 'Wine']" 
```

Insert your own apps instead of mine.

To see the default do ```
gsettings get com.canonical.Unity.Panel systray-whitelist 
```

---

### Post by kakk on 2011-10-24
Thanks, awam66, but as this does not work in 11.10 as well, and there is no obvious way to find out how to do this, shouldnt it be added by default?

---

