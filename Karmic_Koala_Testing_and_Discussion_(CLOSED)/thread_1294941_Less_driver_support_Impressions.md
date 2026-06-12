---
title: "Less driver support? Impressions"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by joshrobinson on 2009-10-18
Just installed Karmic on a laptop ive used ubuntu on since dapper or earlier (yes its old i know but i only use it for surfing).

My wireless never works out of the box since its a broadcom, but my ethernet ALWAYS works.  So i plug in via the cable, download b43-fwcutter and install, wireless working.  Before that i did the whole ndiswrapper crap.

So Installed Karmic, no wireless (expected), and NO ethernet!!  I had to go to someone else's house to download the packages and drivers i needed.  Very inconvenient.  Was some driver support removed?  Isnt this a step in the wrong direction for ubuntu gaining new users?

I also have a Bios frequency bug starting up that makes the boot time double, not sure what thats about.  First install wouldnt get past the error, second install it gets past it now.

Got a BUNCH of updates to go through, hopefully that fixes the slow boot time and bios bug.

Other then that, I'm happy with the look and feel.

---

### Post by cariboo on 2009-10-18
Are you sure the drivers weren't loaded, and there wasn't something causing the problem?

---

### Post by kansasnoob on 2009-10-19
I do know that Karmic has currently dropped support for my sound card:

[https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/451813](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/451813)

Sort of sad since it'd been supported since at least Gutsy.

---

### Post by joshrobinson on 2009-10-19
Yeah im sure the drivers didnt load, unless some new module is causing it to not work.

Either way, more problems came up.  B43-fwcutter and its drivers are running TERRIBLE for my wifi, so i wanted to go back to ndiswrapper.  Tried compiling ndiswrapper with constant errors (multiple versions), and ive done this a million times before.  Tried to install ndiswrapper from the repo's, it installed fine but when i try to load the module it says ndiswrapper.ko is missing!?
I run a locate on ndiswrapper.ko, it says its in the right directory, i look in that directory, and theres nothing there!?

EDIT: Finally got it working after a bunch of manual work.
Hope this all gets ironed out before karmic releases, because less advanced users will be screwed if they run into these issues.

---

### Post by NCLI on 2009-10-19
> **joshrobinson said:**
> Yeah im sure the drivers didnt load, unless some new module is causing it to not work.

Either way, more problems came up.  B43-fwcutter and its drivers are running TERRIBLE for my wifi, so i wanted to go back to ndiswrapper.  Tried compiling ndiswrapper with constant errors (multiple versions), and ive done this a million times before.  Tried to install ndiswrapper from the repo's, it installed fine but when i try to load the module it says ndiswrapper.ko is missing!?
I run a locate on ndiswrapper.ko, it says its in the right directory, i look in that directory, and theres nothing there!?

EDIT: Finally got it working after a bunch of manual work.
Hope this all gets ironed out before karmic releases, because less advanced users will be screwed if they run into these issues.
Please report bugs where you describe your problems to the developers so they know about this ;)

---

### Post by mikedep333 on 2009-10-19
What's your wired ethernet adapter? Show us your output from lspci.
```
lspci
```

---

