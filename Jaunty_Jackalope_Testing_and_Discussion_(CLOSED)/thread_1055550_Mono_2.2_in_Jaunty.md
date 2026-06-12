---
title: "Mono 2.2 in Jaunty?"
date: 2009-01-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jmillikin on 2009-01-30
Will the new 2.2 release of Mono be included in 9.04? From the [release notes](http://www.mono-project.com/Release_Notes_Mono_2.2) the changes sound minor, and it has some very nice new debugging functionality in the REPL.

---

### Post by Starks on 2009-01-31
It probably will, unfortunately, it won't be enough for Silverlight 2 support in Moonlight.

---

### Post by RAOF on 2009-01-31
Possibly not; there's a fair amount of new packaging work that needs to be done for 2.2 - new Mono.SIMD packages, for example.  Also, 2.4 should (hopefully) be released quite soon, and will fix some bugs the Debian mono team hit.

Add to that the continuing Mono 2.0 transition, and the unexpected gnome-sharp2 transition, and there's quite a lot of work needed on the mono stack!

---

### Post by directhex on 2009-01-31
Regressions. The bane of any packager, especially a framework packager. Mono 2.2 appears to be littered with them - probably as a result of the new IL engine - and we're unlikely to have enough time to make a stable reliable 2.2 release AND fix bugs in any of the 40-odd apps or 40-odd libraries that use it

A partial 2.2 stack might happen (e.g. things like vbnc), but unless a horde of capable people swarm in to help us, mono 2.2 is looking unlikely

Sorry :(

---

### Post by gnomeuser on 2009-01-31
> **directhex said:**
> Regressions. The bane of any packager, especially a framework packager. Mono 2.2 appears to be littered with them - probably as a result of the new IL engine - and we're unlikely to have enough time to make a stable reliable 2.2 release AND fix bugs in any of the 40-odd apps or 40-odd libraries that use it

A partial 2.2 stack might happen (e.g. things like vbnc), but unless a horde of capable people swarm in to help us, mono 2.2 is looking unlikely

Sorry :(

Do you have a tracker bug for these issues? We are pushing Mono 2.2 back to our stable Fedora platforms and development is already tracking 2.4 from SVN. So far we have not encountered any major issues but I would love to test against your experiences in the interest of common good.

---

### Post by directhex on 2009-01-31
> **gnomeuser said:**
> Do you have a tracker bug for these issues? We are pushing Mono 2.2 back to our stable Fedora platforms and development is already tracking 2.4 from SVN. So far we have not encountered any major issues but I would love to test against your experiences in the interest of common good.

No, I haven't personally looked into it yet, but the Debian Mono team seems to have turned into a de-facto cross-distro packager hub. Reports from our peers in Gentoo include this one: [https://bugzilla.novell.com/show_bug.cgi?id=459630](https://bugzilla.novell.com/show_bug.cgi?id=459630) which is apparently fixed in [http://anonsvn.mono-project.com/viewvc?view=rev&revision=121787](http://anonsvn.mono-project.com/viewvc?view=rev&revision=121787)

The particular problem with this 2.2 thing is that it's the apps that break - so whilst Mono might seem fine, the apps will fail to run or fail to compile. I know Smuxi (IRC client) has similar problems

---

### Post by castrojo on 2009-01-31
Speaking of Mono we are still looking for someone to give monodevelop some long needed love:

[http://castrojo.wordpress.com/2009/01/11/monodevelop-rockstar-needed-inquire-within/](http://castrojo.wordpress.com/2009/01/11/monodevelop-rockstar-needed-inquire-within/)

---

### Post by directhex on 2009-01-31
> **whiprush said:**
> Speaking of Mono we are still looking for someone to give monodevelop some long needed love:

[http://castrojo.wordpress.com/2009/01/11/monodevelop-rockstar-needed-inquire-within/](http://castrojo.wordpress.com/2009/01/11/monodevelop-rockstar-needed-inquire-within/)

Monodevelop 2.0 is somewhat more likely to appear - although follow [http://www.mail-archive.com/ubuntu-motu@lists.ubuntu.com/msg04950.html](http://www.mail-archive.com/ubuntu-motu@lists.ubuntu.com/msg04950.html) for more on it

---

