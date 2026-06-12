---
title: "Upgrade Jaunty Aplha to Beta"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by davorao on 2009-03-27
Hi, i would like to know as the tittle shows how to upgrade from the Jaunty alpha to the beta release, i would assume update did it somehow, but it doesn't. Or should i download the Beta alternate ISO and upgrade with that. Been really happy running on my DELL XPS m1530, where everything is better already in Alpha and would like to continue testing.

Thanks in advance :)

---

### Post by novafluxx on 2009-03-27
No joke:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by taavikko on 2009-03-27
> **novafluxx said:**
> No joke:

```
sudo apt-get update && sudo apt-get upgrade
```

+1

I would use 
```
sudo apt-get update && sudo apt-get dist-upgrade
```
In case's if packages have new dependencies, which won't get installed by mere "upgrade"

For the OP and the rest of you wondering "over n' over again" ;)

Alpha* /beta /rc are just an snapshot of the current repository.
And certain milestones.

If you'r sources.list point to jaunty, that's what you get when doing upgrades (official release) I mean.

Case is different if running Debian (it's sources.list might point to anywhere :D (stable,unstable etc...))

---

### Post by davorao on 2009-03-27
Thank you both for the quick reply :)
worked perfectly with sudo apt-get dist-upgrade

---

