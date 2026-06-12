---
title: "KDE System Monitor or ksysguard broken (Solved)"
date: 2009-02-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by RIchard James13 on 2009-02-06
I had a problem running System Monitor in KDE

It would give me a dialog with a error
"Connection to localhost has been lost"

So I tried to google for a cause but there are many causes.

Then I tried to run it from the console and it gave the following error
```
ksysguard(8439) KSGRD::SensorShellAgent::daemonError: failed to run "ksysguardd"                 
ksysguard(8439) KSGRD::SensorShellAgent::daemonError: error  "Could not run daemon program 'ksysguardd'."                                                                         
```

So I tried to execute ksysguardd
```
sudo ksysgaurd
sudo: ksysgaurd: command not found
```

Then I though what if I just type sudo apt-get install ksysguardd it should tell me what package it is in. However apt-get just proceeded to download and install the ksysguardd program/daemon.

Now System Monitor works perfectly.:D

---

### Post by Kevbert on 2009-02-06
It may be worth reporting it on launchpad so that the programmers know that there's a missing dependency. I can't confirm this as I don't have a working network plasmoid and don't see the error with Alpha 4 64 bit.

---

### Post by RIchard James13 on 2009-02-06
Before I do that I thought I might test it. So I purged ksysguard and ksysguardd. Then I installed ksysguard and it included ksysguardd. My explanation for why my system was missing the daemon was that at some point in jaunty testing time the packages came apart and my machine only updated the ksysguard package and left the ksysguardd behind, because now ksysgaurdd and ksysguard are no longer in the same package.

---

### Post by Kevbert on 2009-02-07
There's updates on both those programs today...

---

