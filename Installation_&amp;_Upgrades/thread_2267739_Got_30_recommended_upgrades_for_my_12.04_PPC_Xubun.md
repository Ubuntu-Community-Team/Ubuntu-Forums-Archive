---
title: "Got 30 recommended upgrades for my 12.04 PPC Xubuntu on G4!!!"
date: 2015-03-03
forum: Installation &amp; Upgrades
---

### Post by este.el.paz on 2015-03-03
Folks:

Just posting over here to notify that yesterday I ran update/upgrade from Terminal and got 30+- upgrades for my 12.04 Xu system running on a PPC "Sawtoothe" G4 . . . including a kernel upgrade. Firefox, T-bird . . . so as of then it appears that 12.04 is still "supported" . . . .  

Just letting the mods know that for many PPC machines 12.04 makes an easier install and runs better on PPC machines than 14.04 . . . and appears to still be getting upgrades.

e.e.p.

---

### Post by Impavidus on 2015-03-03
Of course, Xubuntu 12.04 will be supported until end of next month or so. After that the parts in common with Ubuntu, Kubuntu or server will remain supported for another 2 years, but using a partially supported system is dangerous.

---

### Post by este.el.paz on 2015-03-03
> **Impavidus said:**
> Of course, Xubuntu 12.04 will be supported until end of next month or so. After that the parts in common with Ubuntu, Kubuntu or server will remain supported for another 2 years, but using a partially supported system is dangerous.

Thanks for the reply . . . so, it seems like the base parts would be supported for another two years?  Whereas the Xubuntu parts would remain as they are after the next month . . . ???  And, so then the question is what would be the parts that are unsupported, and then what about that would be dangerous?  And, what type of dangers?  Unsupported browsers with security vulnerability?  Incomplete kernels that might do hardware damage?  Or, just that the system would be "old" and not "up to date" . . .  and so possibly exploitable from some kind of attacks??  It's just somewhat difficult to think that hackers would be wasting their time trying to commandeer a 450 MHz processor for their evil purposes . . . ????  No??

e.e.p.

---

### Post by Bucky Ball on 2015-03-03
Easiest to do an upgrade though the updater or a clean install. LTS releases can upgrade directly to the next LTS (12.04 LTS>14.04 LTS in your case) leapfrogging the interim releases in between. Just disable any PPAs you've installed manually (Other Software) and BACK UP any valuable data prior to upgrading.

The other option is to do a clean install of 14.04 LTS over 12.04 or on another partition. Xubuntu 12.04 is supported until April this year. 

If you click on 'Software Update' in Apps> System> 'Settings' in the bottom left corner of that GUI> 'Updates' tab> set 'Notify me of a new Ubuntu version' to 'Long term support releases'> close that Window and it should do an update. You will then be offered 14.04 LTS.

---

### Post by Impavidus on 2015-03-04
The basic parts will receive upgrades for another 2 years, but the Xubuntu-specific parts won't. You will still get browser upgrades (firefox at least, don't know about other browsers) and kernel upgrades, as these parts are in common with Ubuntu. You can see the support status of your packages by running the command```
ubuntu-support-status --show-all
```You may already see some unsupported packages, but this is not much of a problem as these packages are not vital to the functionality of your computer (if a simple game breaks, you can still use your computer), usually only rely on some interfaces to standard libraries that don't change during normal upgrades (if they rely on anything at all) and often are not very likely attack vectors.

But any upgrade to a supported package may break unsupported packages (upgrades are not checked against unsupported packages). If for example a kernel upgrade breaks the xfce4 desktop environment, a package deeply integrated into your system, you have a problem. Last year an upgrade for 10.04 server broke the GUI of 10.04 desktop. Many complained, but it could only happen because the server components were still supported, but the desktop components were not, and these complainers were running an unsupported release.

---

### Post by grahammechanical on 2015-03-04
It is my understanding that the kernel in particular in LTS releases will get security updates for the full term of the LTS release period. Xubuntu 12.04 as a distribution may get a shorter support period that of Ubuntu 12.04 but the kernel will get the full 12.04 LTS support period. This is my understanding. What kernel do you have? Please run

```
aname -a
```

If you have Linux kernel 3.2 then you will get the full support period. If you search for wiki ubuntu hardware enablement stack you will find a wiki page link with some charts showing the support periods for the kernel being used in Ubuntu and its flavours.

Regards.

---

### Post by este.el.paz on 2015-03-04
To each of you, thanks for the details . . . much appreciated. @BB: Well, I am aware that I could upgrade, but there are "tradeoffs" that go along with that as far as support for PPC goes, so I've gotten the software updater notifications for 14.04 . . . and I did do that on my iBook, but it took a very long time on my DSL line . . . I'm looking to push that off for as long as possible.

So, it could be an "experiment" to see how long I can get it to work, I don't have enough CL experience to play around with, so it could be one of those, "the developer has changed this, would you like to accept? (Y/N) . . . and I would step firmly on the banana peel . . . when I chose Y instead of N . . . .  It's not "mission critcal" at this point as I have dual-boot set up I can always restart out of it.

Running command brings:
```
uname -a
Linux e.e.p.-desktop 3.2.0-77-powerpc-smp #112-Ubuntu SMP Tue Feb 10 15:19:30 UTC 2015 ppc ppc ppc GNU/Linux


```

e.e.p.

---

