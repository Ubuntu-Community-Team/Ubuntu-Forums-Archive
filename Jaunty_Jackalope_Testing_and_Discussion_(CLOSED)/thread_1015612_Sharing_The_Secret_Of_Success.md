---
title: "Sharing The Secret Of Success"
date: 2008-12-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dholbach on 2008-12-19
Hello my friends,

we’re gearing up towards another Ubuntu Developer Week in January. Again we’ll have a week worth of IRC sessions where you can jump right in, participate, learn and ask all your questions. Ubuntu is all about the people and we have a bunch of very sharp people in our community you can learn from.

Did you ever wonder
 * how Magic Seb manages to package an entirely new version of GNOME in just 24h
 * what Martin Pitt’s breakfast consists of to get so much stuff done during the day (interesting for this lot)
 * how Pete Graner manages to mass-test the Kernel
 * which kind of tea helps Michael Vogt to produce bundles of awesome every day
 * what kind of black Ninja suits you get once you join the Ubuntu QA team

You get the idea: we want to make Ubuntu Developer Week ROCK, therefore we need to know what you like, what you want to learn, what would excite you and help you get started.

Please leave a comment on this blog post and I’ll make sure to get good presenters for Ubuntu Developer Week.

---

### Post by dinxter on 2008-12-19
personally i'd be interested in how different developers and maintainers use launchpad and the kind of things that would make their lives easier in dealing with bugs. often i find myself with either packaging bugs or lines of code that i can easily change on my own computer but am still not sure how to best pass this on through launchpad (or otherwise) and dont have the time to do anything more significant about. although the way to put these things is undoubtedly diferent by the programs concerned and by developer too, i would be interested to know what the people on the other end of the bug reports look for and what bug reports make them wince :)

---

### Post by plun on 2008-12-19
Well... add to this, something comes from Debian as stable but its clearly **_unstable_**.   

Why wait for this stable/unstable :confused:

Must be better to fix it ourself.....   :confused:

Or unstable/stable must be clarified...?

Or contribute to upstream maybe....):P

---

### Post by dinxter on 2008-12-19
i may be wrong but i think ubuntu syncs with debian 'unstable' and then tries to stablise it based on the gnome release schedule. debian stable can be quite out of date but thats not its primary goal. unstable in debian speak probably translates better as their 'experimental' repository! i forget where the actual debian framework for all these things are but they are quite distinct categories and i think reasonable given what theyre aiming for overall

---

### Post by plun on 2008-12-19
> **dinxter said:**
> i may be wrong but i think ubuntu syncs with debian 'unstable' and then tries to stablise it based on the gnome release schedule. debian stable can be quite out of date but thats not its primary goal. unstable in debian speak probably translates better as their 'experimental' repository! i forget where the actual debian framework for all these things are but they are quite distinct categories and i think reasonable given what theyre aiming for overall

Well, we have a few areas which I think Ubuntu can do it ourself...100% sure !!!  

X-org, PulseAudio, Firefox, Mono, Ext4....

Those must be minimized in number but as Gentoo says "**** upstream"....):P

---

### Post by chrisccoulson on 2009-01-09
Just bumping this back up again for the benefit of those of you who might be interested but aren't subscribed to the ubuntu-devel-announce or ubuntu-devel-discuss mailing lists, as you will have missed the reminder sent today by dholbach:

> Hello everybody,

The Ubuntu Developer Week is back again.

- From Jan 19th to Jan 23rd we&#8217;re going to have loads of awesome sessions
where Ubuntu developer share their secret of success, spend time asking
all of your questions, help you to get involved. It&#8217;s an awesome
opportunity to get started, get to know a lot of people and it&#8217;s going
to be a lot of fun.

A lot of things are going to stay the same: we&#8217;ll have top-class
talkers, top-notch talks and time for asking lots and lots of questions.
One thing I&#8217;m totally excited about is this one: we&#8217;ll have a two-hour
Getting Started session in English, French, German, Italian and Spanish.
Fantastic! If English is not your mother tongue and you&#8217;d like to know a
bit more about how it all works to feel comfortable, this is your
opportunity to ask your questions.

[LIST]
 [*] Timetable: [https://wiki.ubuntu.com/UbuntuDeveloperWeek]("https://wiki.ubuntu.com/UbuntuDeveloperWeek")
 [*] Session Details: [https://wiki.ubuntu.com/UbuntuDeveloperWeek/Sessions]("https://wiki.ubuntu.com/UbuntuDeveloperWeek/Sessions")
 [*] Joining in: [https://wiki.ubuntu.com/UbuntuDeveloperWeek/JoiningIn]("https://wiki.ubuntu.com/UbuntuDeveloperWeek/JoiningIn")
 [*] Digg: [http://digg.com/linux_unix/3rd_Ubuntu_Developer_Week_announced]("http://digg.com/linux_unix/3rd_Ubuntu_Developer_Week_announced")[/LIST]

Have a great day,
 Daniel

---

### Post by Eclipse. on 2009-01-09
> **plun said:**
> Well, we have a few areas which I think Ubuntu can do it ourself...100% sure !!!  

X-org, PulseAudio, Firefox, Mono, Ext4....

Those must be minimized in number but as Gentoo says "**** upstream"....):P

We basically do everything you mentioned ourselfs.;)

---

### Post by plun on 2009-01-09
> **Eclipse. said:**
> We basically do everything you mentioned ourselfs.;)

Nope... :D   IMHO...

"The Debian mess" must be sorted out... maybe  its time to take a chat with Ken VanDine and Foresight.

Debian will probably be trapped within endless discussions about nothing....


**Duke Nukem Forever** must also be sorted out...   I can wait..:D

---

### Post by Eclipse. on 2009-01-09
> **plun said:**
> Nope... :D   IMHO...

"The Debian mess" must be sorted out... maybe  its time to take a chat with Ken VanDine and Foresight.

Debian will probably be trapped within endless discussions about nothing....


**Duke Nukem Forever** must also be sorted out...   I can wait..:D

I was meaning the packages you mentioned, we have our own firefox, xorg ect.

---

### Post by plun on 2009-01-09
> **Eclipse. said:**
> I was meaning the packages you mentioned, we have our own firefox, xorg ect.

Well....  PulseAudio must be "self-punishment",  patch a broken version with a complete GIT instead of taking a GIT snapshot.

Something must be terrible wrong...IMHO

Also to not running FF3.1 as default browser for a development version

Debian seems to be more fighting within mailing lists then fixing software....

---

### Post by gnomeuser on 2009-01-09
> **plun said:**
> Well, we have a few areas which I think Ubuntu can do it ourself...100% sure !!!  

X-org, PulseAudio, Firefox, Mono, Ext4....

Those must be minimized in number but as Gentoo says "**** upstream"....):P

You seem to confuse the terms Debian and Upstream.. it happens a lot in Ubuntu sadly.

Debian is not upstream for any of the projects you mention. **** upstream is never ever a good approach, working with upstream is. It increases the quality of new features to get them in upstream directly instead of carrying them singlehandedly, it decreases the QA and bug workload. So many advantages of doing things upstream and working directly there, so few advantages of not doing so.

---

### Post by plun on 2009-01-09
> **gnomeuser said:**
> You seem to confuse the terms Debian and Upstream.. it happens a lot in Ubuntu sadly.

Debian is not upstream for any of the projects you mention. **** upstream is never ever a good approach, working with upstream is. It increases the quality of new features to get them in upstream directly instead of carrying them singlehandedly, it decreases the QA and bug workload. So many advantages of doing things upstream and working directly there, so few advantages of not doing so.

Well... Debian is upstream for the majority of packages, it has historically been a good platform for Ubuntu.

But... now Debian seems to lost its focus.

For a few important (main stream) handful of packages it might be strong reasons for bypassing Debian. 

Foresight and their backend seems to be a good alternative...really good also IMHO...:)

---

### Post by chrisccoulson on 2009-01-09
> **plun said:**
> Well... Debian is upstream for the majority of packages, it has historically been a good platform for Ubuntu.

But... now Debian seems to lost its focus.

For a few important (main stream) handful of packages it might be strong reasons for bypassing Debian. 

Foresight and their backend seems to be a good alternative...really good also IMHO...:)

Whilst we inherit a lot of packages from Debian, Debian is still not what we consider upstream for most of those. We inherit the packaging of these packages from Debian (and any bugs affecting specifically the packaging or Debian patchset should be directed towards Debian), but the upstream authors of the packages are still the people who provided the original tarballs that both Debian and Ubuntu use.

---

### Post by plun on 2009-01-09
> **chrisccoulson said:**
> Whilst we inherit a lot of packages from Debian, Debian is still not what we consider upstream for most of those. We inherit the packaging of these packages from Debian (and any bugs affecting specifically the packaging or Debian patchset should be directed towards Debian), but the upstream authors of the packages are still the people who provided the original tarballs that both Debian and Ubuntu use.

Yes but why then wait for Debian...:confused:

IMPORTANT  This is just for a few important packages such as for example PulseAudio and Firefox

-------------

This blog post is also important to read.... not so nice but I understand him !

[http://pthree.org/2008/12/21/debian-what-it-means-to-me/](http://pthree.org/2008/12/21/debian-what-it-means-to-me/)
[B]
And READ it carefully !!!![/B]

----

---

### Post by directhex on 2009-01-09
> **plun said:**
> Well, we have a few areas which I think Ubuntu can do it ourself...100% sure !!!  

X-org, PulseAudio, Firefox, Mono, Ext4....

Those must be minimized in number but as Gentoo says "**** upstream"....):P

There is no Ubuntu-specific Mono packaging effort - all work is done collaboratively by Debian and Ubuntu developers, using Debian infrastructure. Frankly, there isn't anyone within the Ubuntu world who has the experience and time to package Mono and package it well independently of pkg-mono in Debian

---

### Post by gnomeuser on 2009-01-09
> **directhex said:**
> There is no Ubuntu-specific Mono packaging effort - all work is done collaboratively by Debian and Ubuntu developers, using Debian infrastructure. Frankly, there isn't anyone within the Ubuntu world who has the experience and time to package Mono and package it well independently of pkg-mono in Debian

And a mighty fine effort it is, I have to say your Mono work is one major reason I have Ubuntu installed, I always aspired to have the Mono packages in Fedora work as well (but we admittedly still have a work to do).

---

### Post by directhex on 2009-01-09
> **gnomeuser said:**
> And a mighty fine effort it is, I have to say your Mono work is one major reason I have Ubuntu installed, I always aspired to have the Mono packages in Fedora work as well (but we admittedly still have a work to do).

The current quality of Mono in Debian/Ubuntu is mostly down to one Debian developer, who will be gracing us with his presence for this UDW session. Collaboration allows offloading of boring and/or annoying tasks (e.g. maintenance of apps like IKVM), and for discussions about possible ways to tackle problems. And the more boring/annoying things which meebey doesn't need to do, the more time he has for the "heavy hitters" like MonoDevelop, or Mono itself

---

### Post by Slug71 on 2009-01-09
> **plun said:**
> Well... Debian is upstream for the majority of packages, it has historically been a good platform for Ubuntu.

But... now Debian seems to lost its focus.

For a few important (main stream) handful of packages it might be strong reasons for bypassing Debian. 

Foresight and their backend seems to be a good alternative...really good also IMHO...:)


The Conary backend does seem very good but i very much doubt we'll get that.

Hopefully Smart Package Manager will be good.

---

