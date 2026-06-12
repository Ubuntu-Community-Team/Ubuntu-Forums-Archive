---
title: "Whatever happend to grip"
date: 2009-08-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by eyelessfade on 2009-08-31
I see that grip is no longer in repos. What happend to it? Just when I had it just how I wanted...

---

### Post by MacUntu on 2009-08-31
[https://launchpad.net/ubuntu/+source/grip/3.3.1-16](https://launchpad.net/ubuntu/+source/grip/3.3.1-16)

It says RoM (request of maintainer) which means the project is probably no longer maintained/developed AKA dead.

---

### Post by eyelessfade on 2009-08-31
To bad. Have to find another ripper now. :/

---

### Post by slakkie on 2009-08-31
try abcde, really nice cli ripper.

---

### Post by andrew.46 on 2009-09-03
Hi slakkie,

> **slakkie said:**
> try abcde, really nice cli ripper.

Mind you abcde is a little unmaintained at the moment too...

Andrew

---

### Post by slakkie on 2009-09-03
> **andrew.46 said:**
> Hi slakkie,



Mind you abcde is a little unmaintained at the moment too...

Andrew

[http://code.google.com/p/abcde/updates/list](http://code.google.com/p/abcde/updates/list)

Updates from Aug 2009, pretty recent.

---

### Post by mdurham on 2009-09-03
> **eyelessfade said:**
> To bad. Have to find another ripper now. :/

You don't need to find another, Grip works just fine.

---

### Post by johnnybirdman on 2009-09-03
> **mdurham said:**
> You don't need to find another, Grip works just fine.

Agreed that Grip works fine but as the OP says, it is not in the 9.10 repo.
J.

---

### Post by mdurham on 2009-09-03
> **johnnybirdman said:**
> Agreed that Grip works fine but as the OP says, it is not in the 9.10 repo.
J.

Get if from the link supplied above by MacUntu or from the Jaunty repo or probably many other places too.

---

### Post by Seventh Reign on 2009-09-03
I prefer Sound-Juicer over Grip.  So much easier to use and set up.

---

### Post by hugmenot on 2009-09-03
Also RubyRipper.

---

### Post by ghindo on 2009-09-03
> **hugmenot said:**
> Also RubyRipper.Absolutely.  Check out the tutorial in my sig! :)

Also, can we get somebody to package RubyRipper?  I filed a bug like two years ago and haven't seen any progress :(

---

### Post by andrew.46 on 2009-09-03
Hi slakkie,

> **slakkie said:**
> [http://code.google.com/p/abcde/updates/list](http://code.google.com/p/abcde/updates/list)

Updates from Aug 2009, pretty recent.

Indeed I stand well and truly corrected, looks like a fair bit of development since July this year. My apologies for spreading misinformation :(.

Andrew

---

### Post by talkingwires on 2009-09-04
> **Seventh Reign said:**
> I prefer Sound-Juicer over Grip.  So much easier to use and set up.
Was that supposed to be a troll? Sound-Juicer is notorious for being difficult to configure in general, and configuring it to rip MP3s is the most common question that pops up on Google.

---

### Post by Kareeser on 2009-09-04
I've had no problems with sound juicer whatsoever. I also rip to .flac, though, so perhaps that helps?

Grip worked great for me when I used it in the past. Nice, compact, and very utilitarian (mostly due to the lack of aesthetic features, though, not due to any differring functionality.)

---

### Post by Seventh Reign on 2009-09-04
> **talkingwires said:**
> Was that supposed to be a troll? Sound-Juicer is notorious for being difficult to configure in general, and configuring it to rip MP3s is the most common question that pops up on Google.


Juicer gives me absolutely no problems ripping to mp3.  Now I dunno if its faster or slower than Grip .. I've never compared speed.  But I love it.

---

### Post by mc4man on 2009-09-06
> Also, can we get somebody to package RubyRipper? I filed a bug like two years ago and haven't seen any progress

Well I happen to be on the alpha5 live cd (first time on karmic) so I grabbed the .deb I made from my hardy install and installed it. Seems to work fine, none of the dep's are version specific anyway. ( it installed all the needed deps (16 on the live cd

Note that I didn't include any encoders as deps, that's up to you (listed some in the description.

I did make cd-discid a depend, install is worthless without it

Will attach, give it a try, if any adjustments needed can try

Also attached is a .diff that can be applied to any recent rr source, then build off of the debian/rules (fakeroot, dpkg, debuild ect. (if using on source other than 0.5.7 male appropriate ver. change in changelog

I actually prefer 0.5.5 atm
 the diff shuld be good for any recent source

the .deb should be good for hardy thru karmic, any arch

Best way to dl is right click -> save link as

newer .deb here # 86 (forgot all about this post
[http://ubuntuforums.org/showthread.php?t=799621&page=9](http://ubuntuforums.org/showthread.php?t=799621&page=9)

---

### Post by adam_kimber on 2009-10-24
If you use the Jaunty package from [here]("http://packages.ubunut.com/jaunty/grip") it works. However it does not install any dependancies. To enable ogg encoding you will need to install the package vorbis-tools and to use cdda2wav (much much faster ripping) you will need the package icedax.

---

