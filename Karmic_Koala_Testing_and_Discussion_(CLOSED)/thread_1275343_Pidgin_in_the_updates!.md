---
title: "Pidgin in the updates?!"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by steev182 on 2009-09-25
So I just ran the update tool in karmic alpha 6 and Pidgin and libpurple were in there.

Anyone else getting this?

I wonder what impact this has on empathy being included in the beta/release of karmic.

---

### Post by vredley on 2009-09-25
> **steev182 said:**
> So I just ran the update tool in karmic alpha 6 and Pidgin and libpurple were in there.

Anyone else getting this?

I wonder what impact this has on empathy being included in the beta/release of karmic.

Same here. Has there been a last-minute rethink?

---

### Post by novafluxx on 2009-09-25
I believe telepethy-haze requires libpurple.

---

### Post by LKjell on 2009-09-25
It is not that it install libpurple but it wants to install Pidgin as well

---

### Post by MacUntu on 2009-09-25
It's about time to accept defeat. >:****)

---

### Post by hanzomon4 on 2009-09-25
Say Whaaaaat?!

---

### Post by b3n87 on 2009-09-25
Can anyone get Empathy to work with MSN Messenger?

---

### Post by Eclipse. on 2009-09-25
Nobody bother to check the changelog?

> 
pidgin (1:2.6.2-1ubuntu5) karmic; urgency=low

  * debian/control:
    - Recommends pidgin-libnotify

 -- Sebastien Bacher <email address hidden>   Fri, 25 Sep 2009 17:22:36 +0200


Just means anybody using pidgin will have notifications for it by default.

---

### Post by hanzomon4 on 2009-09-25
> **Eclipse. said:**
> Nobody bother to check the changelog?



Just means anybody using pidgin will have notifications for it by default.
Yes and this still makes no sense if empathy is still the default 

I never installed pidgin-notify or pidgin, this is a fresh install.

---

### Post by rajeev1204 on 2009-09-25
pidgin has been installed with the latest updates.I just installed a daily build and updated.We can fairly assume that pidgin will make it to the beta.

---

### Post by rajeev1204 on 2009-09-25
> **MacUntu said:**
> It's about time to accept defeat. >:****)

:)

---

### Post by novafluxx on 2009-09-25
Issue is probably that Empathy just won't be ready for prime time before the final freeze goes in effect.

---

### Post by novafluxx on 2009-09-25
> **b3n87 said:**
> Can anyone get Empathy to work with MSN Messenger?

It works, but I'm always hidden/invisible, I can't change the status. Been like that for a week at least.

---

### Post by Amaranth on 2009-09-25
Pretty sure this is actually a packaging bug. libpurple0 (used in empathy) gained a Recommends for pidgin-libnotify which depends on pidgin. Since we install Recommends by default now...

It should be fixed soon, pidgin is not replacing empathy.

---

### Post by hanzomon4 on 2009-09-25
Take that you scary purple bird!!

---

### Post by Stereotypical Rage on 2009-09-25
> **Amaranth said:**
> Pretty sure this is actually a packaging bug. libpurple0 (used in empathy) gained a Recommends for pidgin-libnotify which depends on pidgin. Since we install Recommends by default now...

It should be fixed soon, pidgin is not replacing empathy.

:sadpanda:

---

### Post by rajeev1204 on 2009-09-25
> **Stereotypical Rage said:**
> :sadpanda:

I think i wont update for the next few days,i can enjoy pidgin a little more.heh.But iam hoping its not really a packaging bug and a rethink to include pidgin.

---

### Post by Amaranth on 2009-09-25
I can guarantee it's a packaging bug based on the pidgin changelog. The idea was clearly to add the Recommends to pidgin and not libpurple0 because why would libpurple0 need that?

---

### Post by vredley on 2009-09-25
Maybe it's divine intervention. :P

---

### Post by kestal on 2009-09-25
I've slowly accepted Empathy. It just needs lovin' with some decent MSN support and some kind of API to import its own set of themes from anything to everything, and I will gladly contribute. (Only selecting a very few compatible adium themes of a certain type is a bit limiting)

At the moment for MSN, I do not use Pidgin anyway, I use Emesene 1.5. If they say this a package bug, then its a package bug. However, if this is left alone long enough (and potentially not locked) there will be a vocal riot, or a long-winded thread about how everyone misses Pidgin. -_-

---

### Post by tretle on 2009-09-25
I have msn working perfectly with empathy including voice/video and full presence support without the need for libpurple. Use this ppa->

deb [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) karmic main

---

### Post by Mr. Picklesworth on 2009-09-25
> **tretle said:**
> I have msn working perfectly with empathy including voice/video and full presence support without the need for libpurple. Use this ppa->

deb [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) karmic main

OMG!
I said that to a friend with a voice chat over MSN. He basically sighed and said "uh... yah, you just press the webcam button." I was perplexed for a minute, and stammered out "b-b-but it's with free software!" before realizing how truly doomed we all are :P
Come to think of it, it was a rather historical moment for another reason: my microphone was working.

Thanks for pointing out the PPA. I didn't realize its telepathy-butterfly package for Karmic was newer than for Jaunty.


In related news, rather than be renamed "Software Center" Software Store, like a good properly spelt program, disappeared in a huge puff of smoke to be mysteriously replaced with "Add/Remove Applications" in the Administration menu. I imagine it will only come back when someone gives it en_CA strings.

---

### Post by hanzomon4 on 2009-09-25
> **Mr. Picklesworth said:**
> OMG!
I said that to a friend with a voice chat over MSN. He basically sighed and said "uh... yah, you just press the webcam button." I was perplexed for a minute, and stammered out "b-b-but it's with free software!" before realizing how truly doomed we all are :P
Come to think of it, it was a rather historical moment for another reason: my microphone was working.

Thanks for pointing out the PPA. I didn't realize its telepathy-butterfly package for Karmic was newer than for Jaunty.


In related news, rather than be renamed "Software Center" Software Store, like a good properly spelt program, disappeared in a huge puff of smoke to be mysteriously replaced with "Add/Remove Applications" in the Administration menu. I imagine it will only come back when someone gives it en_CA strings.

What do you mean misspelled?

---

### Post by Merk42 on 2009-09-25
> **hanzomon4 said:**
> What do you mean misspelled?

I'm guessing he's referring to how Canadian spelling, like British, spells it "centre".

---

### Post by hanzomon4 on 2009-09-25
> **Merk42 said:**
> I'm guessing he's referring to how Canadian spelling, like British, spells it "centre".

OOOOOOh....

---

### Post by Stereotypical Rage on 2009-09-25
> **tretle said:**
> I have msn working perfectly with empathy including voice/video and full presence support without the need for libpurple. Use this ppa->

deb [http://ppa.launchpad.net/telepathy/ppa/ubuntu](http://ppa.launchpad.net/telepathy/ppa/ubuntu) karmic main

sudo add-apt-repository ppa:telepathy :lolflag:

---

### Post by novafluxx on 2009-09-25
> **Stereotypical Rage said:**
> sudo add-apt-repository ppa:telepathy :lolflag:

Thank you! I hope this continues to get updated post Karmic's release!

---

### Post by sliketymo on 2009-09-27
> **hanzomon4 said:**
> Take that you scary purple bird!!

I've kinda grown to love the little fellow !
:lolflag:[IMG]file:///home/rickey/Pictures/Pictures/GNU%20avatars/pidgin.jpg[/IMG]

---

### Post by aamukahvi on 2009-09-27
> **Merk42 said:**
> I'm guessing he's referring to how Canadian spelling, like British, spells it "centre".
> After much discussion with community members and others, sabdfl has determined that "Software Store" should become "Software Center" in US English. Note that this should be expressed as "Software Centre" in UK English. The package should be named "software-center"
[https://bugs.launchpad.net/ubuntu/+source/software-store/+bug/436648]("https://bugs.launchpad.net/ubuntu/+source/software-store/+bug/436648")

---

### Post by cgroza on 2009-09-27
Yes...there are updates for pidgin...

---

