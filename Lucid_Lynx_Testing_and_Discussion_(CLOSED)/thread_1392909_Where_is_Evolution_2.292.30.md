---
title: "Where is Evolution 2.29/2.30?"
date: 2010-01-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by glasen on 2010-01-28
Does anybody know if Evolution 2.30 will be included in Lucid? 

Every piece of Gnome was updated to the latest version, only Evolution stays at version 2.28.3.

Is there any reason why there is no version 2.29.x?

---

### Post by Gourgi on 2010-01-29
my evolution is held back by evolustion-rss plugin.
i hope it is included soon :p

---

### Post by thib on 2010-03-04
Still with evolution 2.28.3 here. Hope package are coming out soon with the latest evolution!

---

### Post by Technoviking on 2010-03-04
There was going to be a major changes in the latest version Evolution, the devs decided to stick with 2.28 for the LTS release.

T-V

---

### Post by cyberkilla on 2010-03-05
Is there a way to circumvent this? A repository to add, perhaps?

I use Evolution mail a lot and I'd rather have the latest version (without compiling myself, switching distribution or upgrading to lucid+1):p

---

### Post by Tompalaz on 2010-03-05
I like jhbuild for building gnome stuff.
I'll try this one. [http://projects.gnome.org/evolution/build.shtml](http://projects.gnome.org/evolution/build.shtml)

---

### Post by nickpj on 2010-03-07
> **Technoviking said:**
> There was going to be a major changes in the latest version Evolution, the devs decided to stick with 2.28 for the LTS release.

That is unfortunate. The Evo devs have been great about fixing a number of quirks and polishing the software, and each release keeps getting incrementally better, and 2.30 definitely continues that trend (e.g. I count 20 Evo bugs/enhancements that I care about that have been resolved in the 2.30 series, so from my perspective it's looking like a great release). And yes, 2.30 includes some [behind-the-scenes updates]("http://www.go-evolution.org/KillBonobo"), but those [landed in September 2009]("http://mbarnes.livejournal.com/3367.html"), and so were deliberately allocated an extra long settling-in period. There are [;product=Evolution;long_desc_type=substring;long_desc=;status_whiteboard_type=allwordssubstr;status_whiteboard=evolution[kill-bonobo];keywords_type=allwords;keywords=;bug_status=UNCONFIRMED;bug_status=NEW;bug_status=ASSIGNED;bug_status=REOPENED;bug_status=NEEDINFO;emailassigned_to1=1;emailtype1=substring;email1=;emailassigned_to2=1;emailreporter2=1;emailqa_contact2=1;emailcc2=1;emailtype2=substring;email2=;bugidtype=include;bug_id=;chfieldfrom=;chfieldto=Now;chfieldvalue=;cmdtype=doit;order=Reuse%20same%20sort%20as%20last%20time;query_based_on=Kill%20Bonobo%20%28Regressions%29;field0-0-0=noop;type0-0-0=noop;value0-0-0="]some related regressions]("https://bugzilla.gnome.org/buglist.cgi?query_format=advanced;short_desc_type=allwordssubstr;short_desc=[regression) (10 outstanding at last count), but those are being tracked and presumably this count will go down as 2.30 final & any point updates get released. It's a shame if we're going to have a full Gnome 2.30, but with Evo as the only exception, held back at the previous version.

---

### Post by francesco_m on 2010-03-09
I'm using the unstable Evo for a while now (mail and addressbook mostly) and it's quite usable.
I've set up a PPA based on packages from Debian experimental, please report bugs directly upstream:
[https://launchpad.net/~francesco-marella/+archive/unstable-evolution](https://launchpad.net/~francesco-marella/+archive/unstable-evolution)

---

### Post by Tompalaz on 2010-03-09
> **francesco_m said:**
> I'm using the unstable Evo for a while now (mail and addressbook mostly) and it's quite usable.
Here it is a PPA I've set up, please report bugs directly upstream:
[https://launchpad.net/~francesco-marella/+archive/unstable-evolution](https://launchpad.net/~francesco-marella/+archive/unstable-evolution)

Thank you!

---

### Post by Mr. Picklesworth on 2010-03-09
> **nickpj said:**
> That is unfortunate. The Evo devs have been great about fixing a number of quirks and polishing the software, and each release keeps getting incrementally better, and 2.30 definitely continues that trend (e.g. I count 20 Evo bugs/enhancements that I care about that have been resolved in the 2.30 series, so from my perspective it's looking like a great release). And yes, 2.30 includes some [behind-the-scenes updates]("http://www.go-evolution.org/KillBonobo"), but those [landed in September 2009]("http://mbarnes.livejournal.com/3367.html"), and so were deliberately allocated an extra long settling-in period. There are [;product=Evolution;long_desc_type=substring;long_desc=;status_whiteboard_type=allwordssubstr;status_whiteboard=evolution[kill-bonobo];keywords_type=allwords;keywords=;bug_status=UNCONFIRMED;bug_status=NEW;bug_status=ASSIGNED;bug_status=REOPENED;bug_status=NEEDINFO;emailassigned_to1=1;emailtype1=substring;email1=;emailassigned_to2=1;emailreporter2=1;emailqa_contact2=1;emailcc2=1;emailtype2=substring;email2=;bugidtype=include;bug_id=;chfieldfrom=;chfieldto=Now;chfieldvalue=;cmdtype=doit;order=Reuse%20same%20sort%20as%20last%20time;query_based_on=Kill%20Bonobo%20%28Regressions%29;field0-0-0=noop;type0-0-0=noop;value0-0-0="]some related regressions]("https://bugzilla.gnome.org/buglist.cgi?query_format=advanced;short_desc_type=allwordssubstr;short_desc=[regression) (10 outstanding at last count), but those are being tracked and presumably this count will go down as 2.30 final & any point updates get released. It's a shame if we're going to have a full Gnome 2.30, but with Evo as the only exception, held back at the previous version.

Especially since this is the version before GNOME 3, which brings us major API breaks with all sorts of possible regressions. People may want to stick with Lucid!

It would be awesome in Evolution 2.30 was packaged alongside 2.28, so those who wanted it could install it.

---

### Post by grubdude on 2010-03-09
The current version of Evolution is buggy on 10.04...Constantly locks up and drives the processor nuts while trying to retrieve email....

This usually occurs after the application has been running for a while....I hope they fix that first. Works okay on 9.10, though.

---

### Post by dannew on 2010-03-17
Interesting choice to go with different Gnome releases, won't that come back to bite us to stay with an older release in an LTS?

---

### Post by cyberkilla on 2010-03-18
It's a shame there are no PPAs for it. JHBuild ( ? ) makes a mess in my home folder. :p

---

### Post by Mr. Picklesworth on 2010-03-18
> **grubdude said:**
> The current version of Evolution is buggy on 10.04...Constantly locks up and drives the processor nuts while trying to retrieve email....

This usually occurs after the application has been running for a while....I hope they fix that first. Works okay on 9.10, though.

Heey, same here. It's evolution-data-server that is doing it, basically whenever I try to retrieve an email without first sacrificing a chicken. Seems crazy to me that this is happening, really, given that Evolution itself is definitely the same. I guess it's some odd compatibility issue. Hopefully it's something simple and not a problem that'll cost some poor developer his life over the next four years to maintain...

---

### Post by beow on 2010-04-07
Or why not backport it to 10.04.1? In that way only users that actively enable backports will get access to it. As thrilled as I am on the new features and changes I think it is absolutely the right decision to keep the old version for the LTS release. I'll go for the PPA when I see its working properly.

---

### Post by apalacheno on 2010-04-08
Well, I don't think this is justified.

My greatest grief is that Evolution <2.30 wasn't able to handle LDAP address books well. I've patched Evolution in upstream so it works in 2.30, since this is a must-have for companies that use this kind of infrastructure.

Unfortunately this is a somewhat contradictionary statement (LTS versions for the enterprise, but not containing the needed feature in this case).

I guess since the freeze is already in place, there is no chance to see 2.30 in lucid. What a missed chance!

---

### Post by phill on 2010-04-27
I was using Francesso's PPA for a while but I couldn't get Indicator to work (it compiled and installed as a plugin but didn't work).  After a bit more searching I've found a new PPA that does have Evolution 2.30.1 and a deb for Indicator (although I've yet to get that working).  As an added bonus, Jacob has also compiled Tracker 0.8.3!  
You can find it here [https://launchpad.net/~jacob/+archive/evo230/]("https://launchpad.net/~jacob/+archive/evo230/") or add ppa:jacob/evo230 to your source lists to try it out.

---

