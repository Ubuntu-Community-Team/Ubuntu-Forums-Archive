---
title: "Can't fix broken packages in Synaptic"
date: 2010-12-25
forum: Installation &amp; Upgrades
---

### Post by AbeJarano on 2010-12-25
My x-fi extreme (creative) audio card worked in 9.04 but won't in 10.10.  I'm trying to remove pulseaudio to see if it will work with alsa.  When Synaptic says it can't remove *pulseaudio* and its dependencies, it says that broken packages have to be fixed.  But when I try to fix them in the Edit menu it comes back with 

E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

So I tried

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

but all remains unchanged.

I don't know what is a held package!

thanx

---

### Post by AbeJarano on 2010-12-25
No questions even??

---

### Post by wilee-nilee on 2010-12-25
Is there a right click on the broken that is a information, dependencies...etc.

Your able to open and run without any errors and no command suggested?

---

### Post by sikander3786 on 2010-12-25
From, Applications > Accessories > Terminal, post the output of these commands.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update && sudo apt-get upgrade
```

While posting, click the # icon in post menu and paste your text in between the generated [code] tags.

---

### Post by AbeJarano on 2010-12-25
Thankx You Two,

I tried to follow Willee Nillee's question first and that did it. And to answer his there was nothing there. I noticed that fewer errors had popped up because I had selected fewer packages to remove.  Trying to Apply the removal one by one worked with the necessity of having to remove the simpler ones first libpulse0 or pulselib0 last.  Each time Synaptic fixed the broken dependencies if any were found.  Gloria! Pulse audio is gone!

---

