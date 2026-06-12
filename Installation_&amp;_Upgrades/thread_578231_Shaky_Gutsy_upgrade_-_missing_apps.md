---
title: "Shaky Gutsy upgrade - missing apps"
date: 2007-10-17
forum: Installation &amp; Upgrades
---

### Post by manatee7 on 2007-10-17
I read the post on the official method for the upgrade, and restored my sources.list to its original state (i modified it to download the ubuntu studio theme and google desktop). These were removed from sources.list before I did the upgrade.

Anyway, I tried it using 
```
update-manager -d
```
and it kept failing with a 404 error on a package that actually existed. 

Anyway, then I opened update manager through the gui, and it told me that it had to do a partial upgrade. I went ahead with it, assuming that it was gutsy. 

Upgrade finished successfully, I rebooted and it seems that I'm now running gutsy. Few minor problems - mainly being that there is now two "Printing" options under administration (one is the old one, one is new), and gaim is gone, I can't install it, it says this:

```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gaim: Depends: libnss3 but it is not going to be installed
E: Broken packages

```

It seems like other stuff is missing, but those are a few examples so I'm sure that something isn't quite right. There is lots of stuff missing from add / remove programs, maybe it's because its still rc?

Would I be better off to do a clean install or is there a way to just get it to revert to default packages and remove everything else (i don't mind loosing what i have installed)

---

### Post by zvacet on 2007-10-17
**synaptic<edit<fix broken packages**

---

