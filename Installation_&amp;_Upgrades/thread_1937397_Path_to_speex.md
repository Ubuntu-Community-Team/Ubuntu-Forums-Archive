---
title: "Path to speex"
date: 2012-03-07
forum: Installation &amp; Upgrades
---

### Post by jim_deadlock on 2012-03-07
I'm trying to install linphone-3.5.2 from source because the repo version is broken. I've already installed/upgraded a few dependencies but I'm stuck on this:

```
configure: error: Package requirements (speex >= 1.1.6) were not met:

No package 'speex' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you installed software in a non-standard prefix.

```

I've installed speex 1.2 from the repos but it still can't see it, I've tried adding various paths to PKG_CONFIG_PATH and it currently looks like this:

$PKG_CONFIG_PATH
```
/usr/lib:/usr/lib/x86_64-linux-gnu:/usr/bin:/usr/lib/gstreamer-0.10
```

... but it still won't configure. Any ideas? Which speex file is it looking for?

---

### Post by oldos2er on 2012-03-07
Most likely it needs libspeex-dev, and possibly libspeexdsp-dev.

---

### Post by jim_deadlock on 2012-03-08
Perfect thanks.

---

