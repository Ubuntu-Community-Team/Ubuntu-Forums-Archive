---
title: "Confirm electricsheep as screensaver problem in Intrepid?"
date: 2008-09-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mattisking on 2008-09-17
A full description is listed in the bug report: [https://bugs.launchpad.net/ubuntu/+source/electricsheep/+bug/271229]("https://bugs.launchpad.net/ubuntu/+source/electricsheep/+bug/271229")

In short, could anyone interested confirm this bug? I can't run electricsheep as my screensaver with compiz enabled.

Thanks!

---

### Post by converted on 2008-10-03
I haven't tried turning compiz off, but I can confirm that I just upgraded to ibex, and now can't run electric sheep.  It previews OK, but won't actually run.

---

### Post by BwackNinja on 2008-10-03
install compizconfig-settings-manager and uncheck "unredirect fullscreen windows"

---

### Post by macroshaft on 2008-10-04
> **mattisking said:**
> A full description is listed in the bug report: [https://bugs.launchpad.net/ubuntu/+source/electricsheep/+bug/271229]("https://bugs.launchpad.net/ubuntu/+source/electricsheep/+bug/271229")

In short, could anyone interested confirm this bug? I can't run electricsheep as my screensaver with compiz enabled.

Thanks!

I don't even HAVE that screensaver, how comes you guys do?

---

### Post by hyper7 on 2008-10-04
You can add these to your repos if you want to check it out.


deb [http://ppa.launchpad.net/flam3/ubuntu](http://ppa.launchpad.net/flam3/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/flam3/ubuntu](http://ppa.launchpad.net/flam3/ubuntu) hardy main

Then:
```
sudo apt-get update
apt-get install electricsheep
```

PS: Doesn't work here when running compiz.

---

### Post by stewacide on 2008-10-04
The version from the Flam3 PPA works great for me.

---

### Post by mikeize on 2008-10-10
> **BwackNinja said:**
> install compizconfig-settings-manager and uncheck "unredirect fullscreen windows"

I've seen this in a couple of threads, but for the life of me I can't find it in the compizconfig settings manager!  Searching keyword "unredirect" returns no matches.  Please tell me exactly where this option is located.

---

### Post by BwackNinja on 2008-10-10
General Options

4th setting from the bottom.

---

### Post by techdude3177 on 2008-10-10
i am unable to run any screensavers...the screen will start to fade to go into the screensaver and then once its 100% black to run the screensaver the desktop will show clear again. meaning the screensaver has errored.

---

### Post by mikeize on 2008-10-10
working now, thank you very much BwackNinja.

---

### Post by BwackNinja on 2008-10-10
> **BwackNinja said:**
> install compizconfig-settings-manager and uncheck "unredirect fullscreen windows"

> **BwackNinja said:**
> General Options

4th setting from the bottom.

Reposted together.

---

### Post by metalgearac!d on 2008-10-16
my problem with electric sheep is not that it will not run, but that after running for a few minutes it seems to freeze and then when exiting the screensaver everything is so slow that I have to turn off the computer via the power button because nothing will load,
I tried the above solution and Ill post again if it helped.

---

