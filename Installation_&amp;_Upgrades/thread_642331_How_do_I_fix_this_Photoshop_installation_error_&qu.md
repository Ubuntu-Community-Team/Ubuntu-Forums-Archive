---
title: "How do I fix this Photoshop installation error &quot;Sorry...error with system hardware..&quot;"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by radlations on 2007-12-16
I followed this simple guide to install Photoshop CS2. It involved running a portable version of PS CS2.
[http://youralternative.blogspot.com/2007/06/photoshop-cs2-on-linux-in-3-easy-steps.html#c3823190287166647195](http://youralternative.blogspot.com/2007/06/photoshop-cs2-on-linux-in-3-easy-steps.html#c3823190287166647195)


It ran the first time with out problems. But Now it wont run.

I get this after the loading screen is done.
Unable to continue because of a hardware or system error. Sorry, but this error is unrecoverable

Any help is appreciated.

EDIT: Also I've tried installing a full(Ahem cracked) version of photoshop CS2. Still doesnt work. Same Error.

---

### Post by radlations on 2007-12-17
I know I'm not the only one thats encountered this problem. Argh my life is incomplete without photoshop! Someone help.

---

### Post by omax on 2008-01-05
I know this is a really old thread, but I found a solution to this error....

locate *.psp in your .wine/-folder... Should be called something like "Adobe Photoshop X Prefs.psp

```

$ rm -rf ~/.wine/drive_c/windows/profiles/yournick/Application\ Data/Adobe/Photoshop/9.0/Adobe\ Photoshop\ CS2\ Settings/Adobe\ Photoshop\ CS2\ Prefs.psp

```

That should do it, it deletes your corrupt preferences.

---

### Post by h20skier on 2008-06-11
I did this but the file re-creates itself and gives the error message again. If I remoeve the file again I can run photoshop, but have to keep removing that file before running ps.



> **omax said:**
> I know this is a really old thread, but I found a solution to this error....

locate *.psp in your .wine/-folder... Should be called something like "Adobe Photoshop X Prefs.psp

```

$ rm -rf ~/.wine/drive_c/windows/profiles/yournick/Application\ Data/Adobe/Photoshop/9.0/Adobe\ Photoshop\ CS2\ Settings/Adobe\ Photoshop\ CS2\ Prefs.psp

```

That should do it, it deletes your corrupt preferences.

---

