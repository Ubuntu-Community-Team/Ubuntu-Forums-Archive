---
title: "Evolution fails to install"
date: 2008-06-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by macroshaft on 2008-06-07
I have attempted to enable compiz on my system and caused several issues so decided a full re-install would be the best solution. I installed hardy and dist-upgraded.

Upon going to ceck my mail I discovered evolution was not there, attempting to install results in 

evolution:
  Depends: evolution-data-server (<2.23.0) but 2.23.3-0ubuntu2 is to be installed

Ideas?

---

### Post by spamzilla on 2008-06-07
That's because Evolution has unmet dependencies, so it cannot be installed. Look for a fix, or wait till the dependencies are uploaded to the repos.

---

### Post by MaX on 2008-06-07
> **macroshaft said:**
> I have attempted to enable compiz on my system and caused several issues so decided a full re-install would be the best solution. I installed hardy and dist-upgraded.

Upon going to ceck my mail I discovered evolution was not there, attempting to install results in 

evolution:
  Depends: evolution-data-server (<2.23.0) but 2.23.3-0ubuntu2 is to be installed

Ideas?

This is going to sound harsh... but here goes...

If you can't figure out that message, you probably shouldn't be running Intrepid Ibex at this time... Hardy was released less than 2 months ago and should full fill your computer needs until then.

---

### Post by macroshaft on 2008-06-07
Yes, it is harsh. As I have explained to numerous people too busy making assumptions to ask about what's going on I am running intrepid to learn.

I was just curious as to whether this is something I have done or a result of the natural process of building a new version:

Has anyone else experienced it
it seems odd that it was working until I re-installed
and nobody ever learns how to cope with these scenarios by playing it safe

Ubuntu claims to have a user friendly forum as one of it's selling points but time and time again I've seen the attitude 'If you don't know the answer then don't bother trying'. That is no way to win over new users!

---

### Post by ShirishAg75 on 2008-06-08
mashcroft, we are in the same boat as far as dependancy-filling is there. I have put up similar stuff. 

What I would suggest is you could have also thunderbird if you just wanna download your mail and check it offline and stuff. It is similar to evolution and unless there are dependancy issues there you should be able to play/use it. 

Been there as far as the dependancy issues are there. What some people fail to figure out that some people would need the assurances that yes, I'm facing the same/similar issues as you which tells them that this is natural.  That is the way atleast for a potential user/contributor to grow. I don't see things happening any other way.

---

### Post by macroshaft on 2008-06-08
As well as our own development and education I was under the impression that one of the functions of this section of the forum was to inform others of issues we are experiencing in order to determine if it is:
a) just a wait for the next update job
b) something that needs officially filing as a bug
c) a genuine problem on your system that is unrelated to intrepid's development

How can we determine what a problem is unless we pop our heads up to ask 'Is it just me or...'

---

### Post by psyke83 on 2008-06-09
> **macroshaft said:**
> Yes, it is harsh. As I have explained to numerous people too busy making assumptions to ask about what's going on I am running intrepid to learn.

I was just curious as to whether this is something I have done or a result of the natural process of building a new version:

Has anyone else experienced it
it seems odd that it was working until I re-installed
and nobody ever learns how to cope with these scenarios by playing it safe

Ubuntu claims to have a user friendly forum as one of it's selling points but time and time again I've seen the attitude 'If you don't know the answer then don't bother trying'. That is no way to win over new users!

I hope you don't misinterpret this reply as an attack on you, and of course, bear in mind that my reply to you does not necessarily represent the opinion of anyone else on this forum...

I would not necessarily say that you should stop testing Intrepid, but judging from the question you pose in your reply to MaX, it does seem you do not currently have the prerequisite knowledge to test the development version.

Here is a small sample of things you are expected to know and accept before testing the development release:
1. In the first few weeks/months of development, not even the developers run the development system themselves, as the core toolchain/packages  are not fully built and uploaded to the repository. Right now, Intrepid does not even have a proper kernel release and as you noticed, some packages are uninstallable.
2. Your system can routinely break due to buggy pre-release software versions or faulty scripts in the actual packaging.
3. Certain components get a low priority during development, like restricted drivers.
4. You can expect X to break routinely (sometimes due to point 3, but not always).
5. You should *never* perform a dist-upgrade (or Partial Upgrade) when it elects to remove packages, unless you are certain it is removing obsolete packages.

Unfortunately it seems this forum is not displaying the regular disclaimer regarding development releases, so users aren't being given sufficient warning, and I hope that will be resolved soon. 

The reason why I'm apprehensive of users testing the development release without sufficient experience, is that it floods this forum with *duplicate* threads regarding the same issue, ad nauseum. Sometimes a user will create a new thread when there is an identical thread with a slightly different topic name right underneath their post (and often the other thread will already contain the answer). I feel that too much energy is wasted on user support here (which is *not* the Absolute Beginner section, after all) when we can have more constructive and productive conversations regarding the development release.

I'm not asking you to stop using the development release, in fact would welcome new testers. I do wish that we can have fruitful discussions and keep duplication of effort to a minimum, however.

---

### Post by macroshaft on 2008-06-09
I don't dispute any of what you say, I understand the issues involved in running Intrepid at this stage but it is purely through a desire to learn how the system works in areas I do not normally interact with in a stable release.

My question was not intended to request full support, more just a pointer 'my computer is broken, did I do that or is yours dead too'

I can fix problems myself but if I'm unsure of whether it is a genuine problem I could spend days barking up the wrong tree!

Hopefully, in time, it'll be me handing out these answers and doing the testing, rather than just 'prodding the system' as I do now.

---

### Post by Nullack on 2008-06-12
This happened in hardy proposed today.

I think what is needed is an automated regression test library that runs at a gui level to assure basic unit functionality before being promoted into hardy proposed.

---

### Post by Raptor45 on 2008-06-12
A solution already exists. People just ignore the warnings.

> I installed hardy and dist-upgraded.

Theres your problem.

Regular updates will *not* uninstall anything. Ever. People only run into issues when they blindly do dist-upgrades and partial updates, ignoring the warnings provided that packages may be removed. In this case, evolution did not yet have the correct dependencies, so part of it was removed.

Intrepid and hardy-proposed exist for *testing purposes*, and warnings are indeed provided. Issues and bugs are acceptable, and even to be expected, in both the development release and the proposed repository.

---

### Post by RAOF on 2008-06-12
> **Nullack said:**
> This happened in hardy proposed today.

I think what is needed is an automated regression test library that runs at a gui level to assure basic unit functionality before being promoted into hardy proposed.

We'd *absolutely love* one of these.  Please get back to us when you've found one :).

Also, there's not much that can be done about this particular problem.  You need to build evolution-data-server before evolution, so there's going to be a time while there's a new e-d-s but not the corresponding evolution.

---

### Post by macroshaft on 2008-06-12
Again I point out that I expected these things to happen and understand that you can't upgrade A without breaking B and vice-versa.

Evolution has now re-installed but I have yet to test it.

I see people warning about doing dist-upgrades but they quoted me on 'I installed hardy and dist upgraded' and said that was my problem, but if I didn't do the initial dist-upgrade I wouldn't be running intrepid would I!!

They have said don't do a partial dist-upgrade if it includes potential breakages but when this happens it gives an 'upgrade' button and a 'cancel' button. There is no 'do everything but the dist-upgrade' button, so how am I supposed to install that days updates?

Also the gui regression manager idea sounds great but that almost sounds like you'd be encouraging the average idiot like me to use alpha test software and it would side-step my point for doing so - THE LEARNING. Anyone agree?

---

### Post by plun on 2008-06-12
> **macroshaft said:**
> 
Also the gui regression manager idea sounds great but that almost sounds like you'd be encouraging the average idiot like me to use alpha test software and it would side-step my point for doing so - THE LEARNING. Anyone agree?

Well, everyone which wants to learn is welcome, no one is an idiot...

But... there are no easy answers about this challenge with packages and especially broken packages.  GUIs such as the update-manager is nothing to use during breakages.

This is a good start from Debian

**Apt howto**
[http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/)
[B]
Aptitude howto[/B]
[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/)


Also to learn how the package system looks and how to to see dependencies
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

and down to search.


Note, within **Firefox 3** you have a **new search engine** directly to Ubuntus repo.


This is indeed not easy and of course we help each other with trouble.



But... we don't like "whinings" or "help me directly" threads within this forum :)


Good Luck and Have Fun   !!!

---

### Post by Raptor45 on 2008-06-12
> **macroshaft said:**
> I see people warning about doing dist-upgrades but they quoted me on 'I installed hardy and dist upgraded' and said that was my problem, but if I didn't do the initial dist-upgrade I wouldn't be running intrepid would I!!

Although it sounds a bit hack-ish, a better solution for moving to intrepid (until alpha 1 comes out at least) is to edit your sources.list and replace references to hardy with intrepid. Ideally do this from a fresh install of hardy. This allows you to safely do an update, and skip broken packages. Once alpha 1 comes out it is obviously much better and safer to install from there; or else wait until real updates are supported through the update manager.

> They have said don't do a partial dist-upgrade if it includes potential breakages but when this happens it gives an 'upgrade' button and a 'cancel' button. There is no 'do everything but the dist-upgrade' button, so how am I supposed to install that days updates?

If you hit cancel on the partial update window, and then press install on the regular update manager screen, it will only do a regular upgrade NOT a partial. You can also just use synaptic to pick and choose what to install.

---

### Post by macaholic on 2008-06-13
I'd just like to reiterate a point that raptor brought up concerning dist-upgrades and partial upgrades. When you hit partial upgrade in update manager, or run dis-upgrade from a terminal, ALWAYS know exactly what it is goign to be removiing and installing. Upgrades will most often times remove packages, some of which cannot be reinstalled due to dependency issues, and this is essentially what happened with evolution. If you do however run into this issue, you could always just install an older version of evolution again, or you could install 2.23.1 from the source and wait for the dependency issue to be resolved.

---

