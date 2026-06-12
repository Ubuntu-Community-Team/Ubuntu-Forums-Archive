---
title: "[SOLVED] Remove old available packages"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by hufman on 2008-07-25
I installed Kubuntu 6.06 a long time ago, and I keep dist-upgrading to the latest version when they get released.
However, because of this, I believe I have tons of unavailable packages in apt that I can't easily remove.
I've tried dpkg --clear-avail and dpkg --forget-old-unavail without any improvement. I've cleared /var/cache/apt several times, and apt-get update keeps rebuilding it.
I have one package in particular that I use to test whether my tweaks have worked, audacious-mac. It's an old package that contained the Monkey Audio Codec for Audacious, which has been moved into audacious-plugins. Whenever I try to install audacious-mac now, I get the following message:
> Package audacious-mac is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package audacious-mac has no installation candidate

Is there a way to clear out these outdated packages? Or are they stuck in a broken state in the repository side?

---

### Post by Sef on 2008-07-26
In Synaptic, there is Edit > Fix Broken Packages.  There should be something similar in Adept.

---

### Post by hufman on 2008-07-26
Nope, that does not fix it. I prefer Synaptic to Adept :)
Another puzzle! audacious-mac shows up in a Synaptic search, but not in an apt-cache search.

Well, I solved it! I opened up /var/lib/dpkg/status and looked for audacious-mac, and it had a status of "deinstall ok config-files". I opened up Synaptic and told it to purge the package, and it's gone! Woo!

Sorry for the pointless post.

---

### Post by Sef on 2008-07-26
> Sorry for the pointless post.

It was not pointless.  You had a question, so you asked.

---

