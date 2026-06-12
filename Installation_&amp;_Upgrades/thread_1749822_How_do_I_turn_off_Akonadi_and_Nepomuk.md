---
title: "How do I turn off Akonadi and Nepomuk?"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by tarahmarie on 2011-05-04
I've already been through all the KDE documentation, and they're outdated when it comes to Akonadi and Nepomuk in Natty.

I've disabled Desktop Search in System Settings, which is supposed to disable Nepomuk. For some reason, nepomukserver and akonadiserver along with about twelve other memory-sucking processes autostart and have to be manually killed after my upgrade to Natty.

I can't simply remove all packages that contain akonadi in the name; one of its dependencies is kubuntu-desktop, which would suck to remove.

WTH?

---

### Post by tarahmarie on 2011-05-09
bump

---

### Post by AlphaLexman on 2011-05-09
I don't have access to a KDE system right now, but basically they are both daemons running in the background. You can find the processes from a terminal by
```
ps ax | grep daemon
```to get the [pid] of the culprit, and
```
kill [pid]
```for each daemon.

Unfortunately, this will have to be done at each boot, until you can find a way to avoid loading the daemons at startup. But like I said I don't have access to a KDE box right now, so I can't test anything to that regard.

Good Luck.

---

### Post by tarahmarie on 2011-05-09
Just checked it out; thanks for the help, btw!

That command does not find akonadi or nepomuk daemons; all the processes can be seen in sys mon. I've killed them there, and I'll keep killing them until someone can tell me how to shut them down at an interface level.

---

