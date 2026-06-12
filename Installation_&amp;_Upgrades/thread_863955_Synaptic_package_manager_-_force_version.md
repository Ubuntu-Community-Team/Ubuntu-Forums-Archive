---
title: "Synaptic package manager - force version"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by ilantal on 2008-07-19
In going from Open Office 2.4.0 to 2.4.1, there is a problem with Calc with Sheet names in Hebrew. When the sheet is active all is OK, but when you press on another sheet, the inactive sheets don't display the Hebrew characters properly.
Since I know 2.4.0 works properly, and I don't know of any work around for 2.4.1, I wanted to drop back to 2.4.0.
The Synaptic Package Manager has a nice feature under the Package menu to force the version. This is just what I need, so I was happy to find it. I highlighted the calc package, pressed the force version menu option and found 2 choices: 2.4.0 and 2.4.1. Beautiful - I chose 2.4.0 and told it to force it back. It told me that I had to force most of the other Open Office suite back to 2.4.0. OK, no problem - do that as well.
I went and executed the command and it removed my Open Office completely! Not exactly what I was looking for. I fixed broken packages and I was back to 2.4.1 with its problems in Hebrew names.
Is this a bug or am I doing something wrong?

Thanks,
Ilan

---

### Post by bobbocanfly on 2008-07-19
You could try removing the whole of openoffice, then manually downloading and installing the debs from packages.ubuntu.com, then using the lock versions thing in Synaptic.

Have you filed a bug about this? If not please do! Otherwise it will never get fixed.

---

### Post by ilantal on 2008-07-21
Thanks for the reply. I have never filed a bug report, but I figured out how to do so and filed the message as a bug. If I can figure out how to file an Open Office bug, I'll file it there as well since the reason for wanting to fall back a version was a bug in Open Office.
I'm still new enough at Ubuntu that I don't yet have the courage to stray too far away from the beaten path. One of the nice things about the Package manager is that it prevents me from screwing up the system.

---

