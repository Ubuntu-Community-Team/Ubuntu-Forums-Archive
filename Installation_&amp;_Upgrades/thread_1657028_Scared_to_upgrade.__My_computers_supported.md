---
title: "Scared to upgrade.  My computers supported?"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by VanillaMozilla on 2010-12-31
I'd like to upgrade from 10.04 to 10.10 on two Pentium computers, but I found the following information in the upgrade notes:

* Dropped support for i586 processor.  (Huh?  Pentium!!?  How do I check?)

* Not compatible with nvidia-96 and nvidia-173 drivers.  ?? I have an NVidia graphics, but is it one of these?  I also have nvidia-96-modealiases and nvidia-173-modealiases installed, but NO proprietary drivers.


How do I check this stuff BEFORE I destroy my working 10.04 system?

---

### Post by mikewhatever on 2010-12-31
i586 is apparently Pentium I and Pentium IV is i686. Just google to verify that. As for nvidia cards, Gforce 4/5 don't have proprietary drivers in Maverick. All in all, you should be able to upgrade, but I don't quite see why you would. Is anything wrong with your 10.04 installations?

---

### Post by VanillaMozilla on 2010-12-31
No, it's great.

---

### Post by mikewhatever on 2010-12-31
So why upgrade? Lucid was a good solid release, and it has pretty much all Maverick does + longer support.

---

### Post by VanillaMozilla on 2011-01-02
Why update?  Because there are no bug fixes between versions.  You get security updates, but that's all.  You don't even get updates for buggy applications.


Detailed information on the current version and on the CPU are found in
System > Administration > System Monitor > System
and
cat /proc/cpuinfo.
You may need to consult both.

Thanks for the help.  With no info on the NVidia system, I decided to risk the update anyway.  It actually fixed a nasty problem with sound.  I could have saved myself a LOT of time.

By the way I don't think the designations i586 and i686 mean anything outside of Linux kernels.  With a Pentium III I found I supposedly have an 'i686' CPU, which seems peculiar since 'Pentium' comes from the Greek word 'penta', which means '5'.  Oh, well.

---

### Post by mikewhatever on 2011-01-02
> **VanillaMozilla said:**
> Why update?  Because there are no bug fixes between versions.  You get security updates, but that's all.  You don't even get updates for buggy applications.

Actually, you do. All recommended updates are bug fixes.

> Detailed information on the current version and on the CPU are found in
System > Administration > System Monitor > System
and
cat /proc/cpuinfo.
You may need to consult both.
The first most probably reads the info from the second.;)

> Thanks for the help.  With no info on the NVidia system, I decided to risk the update anyway.  It actually fixed a nasty problem with sound.  I could have saved myself a LOT of time.
... but you said it was great.:confused: Anyway, hope Maverick really is.

> 
By the way I don't think the designations i586 and i686 mean anything outside of Linux kernels.  With a Pentium III I found I supposedly have an 'i686' CPU, which seems peculiar since 'Pentium' comes from the Greek word 'penta', which means '5'.  Oh, well.
I doubt Linux has anything to do anything with Intel's numbering, which is all explained on Wikipedia.
[https://secure.wikimedia.org/wikipedia/en/wiki/P5_%28microarchitecture%29](https://secure.wikimedia.org/wikipedia/en/wiki/P5_%28microarchitecture%29)

---

### Post by VanillaMozilla on 2011-01-03
> **mikewhatever said:**
> Actually, you do. All recommended updates are bug fixes.I don't have complete information on upgrade policies, but it is common for a new Ubuntu version to include some more recent application versions, and some additional applications.

For example, with this upgrade Sound Juicer (Audio CD Extractor) got bumped from 2.28.2, I think, to 2.31.6, and this fixed a critical bug.  The upgrade also fixed two different sound problems.  I remember also that Firefox got a version increase with an update not long ago.  A few versions ago an upgrade fixed a problem on two of my computers with the default NVidia drivers.  I remember comparing maximum version numbers in Synaptic on side-by-side comparisons of Lucid with Maverick.  There were differences.  I think I'm getting the picture.  Don't fret about upgrades--just do it.

> **mikewhatever said:**
> The first most probably reads the info from the second.;)Probably, but what I meant to say was that it includes additional software information.

> **mikewhatever said:**
> ... but you said it was great.:confused: That was misleading, I guess.  Great but not perfect.

> **mikewhatever said:**
> I doubt Linux has anything to do anything with Intel's numbering, which is all explained on Wikipedia.  [https://secure.wikimedia.org/wikipedia/en/wiki/P5_%28microarchitecture%29](https://secure.wikimedia.org/wikipedia/en/wiki/P5_%28microarchitecture%29)Dunno.  I notice that 'i586' and 'i686' are not mentioned in that article, or in most other articles on Intel chip names, or in /proc/cpuinfo.

---

