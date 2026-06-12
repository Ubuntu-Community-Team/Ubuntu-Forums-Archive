---
title: "Better clipboard management?"
date: 2009-06-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by DPic on 2009-06-16
I've recently been bothered more and more by Ubuntu's lack of better clipboard management. I don't know all the details but i think we could really do with a clipboard manager installed by default. I don't know much about this, and would appreaciate input, but from what i've read, Parcellite or Glipper seems to be two good candidates for the job.*
[http://parcellite.sourceforge.net/](http://parcellite.sourceforge.net/)
[http://glipper.sourceforge.net/](http://glipper.sourceforge.net/)

---

### Post by izizzle on 2009-06-16
Well, I love Klipper in KDE....The two you provided seem like great candidates for a GNOME system indeed.

---

### Post by inportb on 2009-06-16
Indeed, Klipper rox0rs my box0rs.

---

### Post by Talon2 on 2009-06-16
This is a very sore subject for me.

I saw the new "100 Paper Cuts" program announced the other day.  The first thing I thought of was this...but, of course, this isn't a trival fix so it won't be considered.

[Bug 11334]("https://bugs.launchpad.net/ubuntu/+bug/11334") dates from 2004.  To quote the first line from the bug:

"This bug is an EPIC failure!"

---

### Post by DPic on 2009-06-16
> **Talon2 said:**
> This is a very sore subject for me.

I saw the new "100 Paper Cuts" program announced the other day.  The first thing I thought of was this...but, of course, this isn't a trival fix so it won't be considered.

[Bug 11334]("https://bugs.launchpad.net/ubuntu/+bug/11334") dates from 2004.  To quote the first line from the bug:

"This bug is an EPIC failure!"

That is EXACTLY the bug that has been killing me lately!

---

### Post by SKLP on 2009-06-17
The problem is that Glipper and the likes are hacks, and the proper solution would be to fix any software that does not comply with the freedesktop.org clipboard specification (I guess Firefox and OpenOffice, maybe something else?). This should not be that hard of a fix, nevertheless, I tried to report it as a paper cut, but they denied it saying it is not a trivial fix. But it really should not be that hard of a fix for a person who is used to working with the mozilla source code (or the openoffice source code in the other case).
Ubuntu bug: [http://bugs.launchpad.net/ubuntu/+bug/106644](http://bugs.launchpad.net/ubuntu/+bug/106644)
Mozilla bug: [http://bugzilla.mozilla.org/show_bug.cgi?id=311340](http://bugzilla.mozilla.org/show_bug.cgi?id=311340)

Upstream (in the mozilla case, at least) has known about this bug for a while now, but I guess they don't care at all about their linux port :/

---

### Post by Talon2 on 2009-06-17
> **DPic said:**
> That is EXACTLY the bug that has been killing me lately!

Of course.  This bug is a 10,000 paper cut bug.

I've been working on selling the IT folks where I work on moving to Ubuntu instead of Windows 7 when the time comes (still on XP now).  They have deployed a selective test.  The two top issues on the problem list are:

1) User interface very different than what users have been trained on.

2) Clipboard is buggy.

I have no answers.  I can't say "If you buy a service contract they will fix it." because the simple truth is that I've seen no indication that a service contract will get anything fixed...and that is a major problem in this industry.

---

### Post by DPic on 2009-06-17
> **Talon2 said:**
> Of course.  This bug is a 10,000 paper cut bug.

I've been working on selling the IT folks where I work on moving to Ubuntu instead of Windows 7 when the time comes (still on XP now).  They have deployed a selective test.  The two top issues on the problem list are:

1) User interface very different than what users have been trained on.

2) Clipboard is buggy.

I have no answers.  I can't say "If you buy a service contract they will fix it." because the simple truth is that I've seen no indication that a service contract will get anything fixed...and that is a major problem in this industry.

To quote the bug page:
> David Siegel wrote on 2009-06-11: 
The amount of discussion and divergent opinions expressed on this bug help show that this bug is well beyond the complexity of a paper cut.

Changed in hundredpapercuts:
status:	 Confirmed &#8594; Invalid

I recommend using one of the apps listed above. As for the user interface, i am positive users will warm up to it. I've been getting students and teachers at my school to switch, and they all find that in Ubuntu everythin "just works" =] --and they're all switching from macs!

---

### Post by froggyswamp on 2009-06-17
> **SKLP said:**
> 
Upstream (in the mozilla case, at least) has known about this bug for a while not, but I guess they don't care at all about their linux port :/

Canonical seems to care about its users a lot.
You see, as Mark said, Canonical is about to take over Windows and Mac OS and they think having a proper copy/paste behavior in Ubuntu isn't all that necessary, because copying and pasting is such a seldom task for a desktop user! It happens like once in a year, so it's really not worth the time fixing.

And besides it's much of a fun for a novice to stumble across this issue, then figure out that it's actually a bug (or maybe it's even a feature!!) and google for this issue, then find the answer and get the corresponding app installed - just to have a proper copy/paste. 
Another example: if your mom thinks the copy/paste isn't good enough - Ubuntu is open source - so tell her to study the source code and fix it, chances are, if she likes doing it, she could start programming for Ubuntu for the rest of her life!
The wise Ubuntu strategy and the wonders of open source folks!

---

### Post by super.rad on 2009-06-17
Was going to try both out, glipper won't install at the moment but parcellite is nice, lightweight but does what it's supposed to. My votes going for parcellite

---

### Post by ktp on 2009-06-17
> **super.rad said:**
> Was going to try both out, glipper won't install at the moment but parcellite is nice, lightweight but does what it's supposed to. My votes going for parcellite

parcellite also seem to be more active these days.

---

### Post by pluckypigeon on 2009-06-18
> **super.rad said:**
> Was going to try both out, glipper won't install at the moment but parcellite is nice, lightweight but does what it's supposed to. My votes going for parcellite

+1 

In my experiences...
Glipper uses too much ram and sometimes causes errors at login. Klipper uses even more ram and cpu. Parcellite does what a clipboard needs to do. I only need copy, paste and the middle mouse button.

Anyway, I'm surprised that ubuntu doesn't have a clipboard installed by default.

---

### Post by Tibuda on 2009-06-18
I like Parcellite too. Something I don't like about Glipper is that I have to add an applet to my panel.

---

### Post by pluckypigeon on 2009-06-19
> **danielrmt said:**
> I like Parcellite too. Something I don't like about Glipper is that I have to add an applet to my panel.

And it uses too much ram because of that.

I only have 512mb so I have to be careful, I also removed the volume applet and swapped it with an alsamixer launcher.

---

### Post by vaibhav on 2009-06-19
I cannot fully reproduce this bug.

Open Gedit -> Type something -> Copy -> Close Gedit -> Paste in another application. Works!

Firefox -> Copy some text from some website -> Close Firefox -> Paste in another application. Fail.

Doesn't work in case of Firefox but works in case of Gedit. Is it that the applications have to be fixed rather than the framework?

---

### Post by ugm6hr on 2009-06-19
Agree, parcelite is often the first app I add after a fresh install.

Is there any reason it isn't in the default install?

It's only an extra 40K in the archive.

I know it doesn't work with images or spreadsheet tables etc, but it works well with simple text.

---

### Post by SKLP on 2009-06-19
> **vaibhav said:**
> I cannot fully reproduce this bug.

Open Gedit -> Type something -> Copy -> Close Gedit -> Paste in another application. Works!

Firefox -> Copy some text from some website -> Close Firefox -> Paste in another application. Fail.

Doesn't work in case of Firefox but works in case of Gedit. Is it that the applications have to be fixed rather than the framework?
There are two possible solutions:

a) install an old-fashioned (if you will) clipboard manager that simply keeps a copy of the clipboard like Parcellite or glipper. All the apps will work, but it will not work with more complex content than text.

b) gnome already provides a freedesktop.org compliant clipboard manager (which is why gedit works for you), firefox doesn't since it isn't completely a GTK app, hence it does not (yet) access the clipboard through gtk, but instead it uses some old code that's not freedesktop.org clipboard manager compliant. Firefox and openoffice.org could be fixed to use the clipboard through gtk, (or directly, just in an fdo compliant way). Most other apps in the ubuntu desktop are pure gtk apps, so they should afaik for the most part work well already. Maybe fix Qt also (if it isn't already fdo clipboard compliant) in case people want to use Qt apps in their gnome desktop.

Solution b is probably the best solution in the long-term(that said, it could probably be fixed pretty quickly), but really, we should have had something like glipper included since warty. This bug is terrible as users expect the clipboard to work like in other operating systems, so the bug therefore causes data loss.

---

### Post by Seventh Reign on 2009-06-21
> **Talon2 said:**
> This is a very sore subject for me.

I saw the new "100 Paper Cuts" program announced the other day.  The first thing I thought of was this...but, of course, this isn't a trival fix so it won't be considered.

[Bug 11334]("https://bugs.launchpad.net/ubuntu/+bug/11334") dates from 2004.  To quote the first line from the bug:

"This bug is an EPIC failure!"

I thought that was the whole point of the 100 Papercuts program.  To fix the trivial bugs that dont necessarily effect usability but are annoying.

---

### Post by Talon2 on 2009-06-21
> **Seventh Reign said:**
> I thought that was the whole point of the 100 Papercuts program.  To fix the trivial bugs that dont necessarily effect usability but are annoying.

I don't consider this a trivial bug and the severity goes well beyond annoying.  In my opinion this bug should be considered CRITICAL as it involves data loss.

This is the number 2 issue causing problems when I try to convert windows users to Ubuntu.  Windows users that make use of cut, copy and paste will run into problems and it isn't obvious what the problem is unless an experienced user is readily available to tell them what to do to work around the bug.

This bug simply needs to be fixed asap!

---

### Post by SKLP on 2009-06-22
Posted a patch which seems to fix firefox: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/21202/comments/50](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/21202/comments/50)

Feel free to try it ;-)

---

### Post by scaine on 2009-06-22
I disagree with David Seigel's rejection of this as a papercut - it's the ultimate papercut - affecting thousands of linux (and of course therefore Ubuntu) users since desktop Linux became feaible.  Sadly, I think that it's going to be too much work to be (re-)added to the papercut program.

Despite this, I've queried David's decision on the bug report, added myself to the massive list of "affects me too" and proposed that this bug is fixed for Karmic, regardless of whether it falls into the papercut project or not.

So much for [Bug #1]("https://bugs.launchpad.net/ubuntu/+bug/1") if [Bug 11334]("https://bugs.launchpad.net/ubuntu/+bug/11334") can sit open for  four and a half years!  :(

---

### Post by inportb on 2009-06-22
> **scaine said:**
> I disagree with David Seigel's rejection of this as a papercut - it's the ultimate papercut - affecting thousands of linux (and of course therefore Ubuntu) users since desktop Linux became feaible.

You seem to agree -- this is more of a plague than a papercut :o

---

### Post by MacUntu on 2009-06-22
> **scaine said:**
> So much for [Bug #1]("https://bugs.launchpad.net/ubuntu/+bug/1") if [Bug 11334]("https://bugs.launchpad.net/ubuntu/+bug/11334") can sit open for  four and a half years!  :(

Four years just isn't enough. [http://bugzilla.gnome.org/show_bug.cgi?id=47893](http://bugzilla.gnome.org/show_bug.cgi?id=47893) :twisted:

---

### Post by scaine on 2009-06-22
> **MacUntu said:**
> Four years just isn't enough. [http://bugzilla.gnome.org/show_bug.cgi?id=47893](http://bugzilla.gnome.org/show_bug.cgi?id=47893) :twisted:

Well, at least that bug is assigned and is in fact targeted - gnome 2.24.x no less.

Eh, wait a minute...  :o

7 years, eh?  Ach well, there's always gnome 3, right?  Maybe it'll also have other useful functions, like, you guessed it, copy/paste.

---

### Post by seeker5528 on 2009-06-24
> **SKLP said:**
> Posted a patch which seems to fix firefox: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/21202/comments/50](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/21202/comments/50)

Feel free to try it ;-)

A: Since the basic clipboard works, and is designed to be transient, I don't see the logic in filing bug reports against it. If both apps remain open and copy/paste fails, that is a bug. Anything else is left for other utilities to provide.

B: Since the clipboard works as designed, I don't really see the logic in "fixing" the transient behaviour in individual applications.

C: If you want clipboard management and history, install klipper. (Yes it should work fine with Gnome. Why wouldn't it?)

D: Some of us prefer the don't-have-to-worry-about-what-may-be-hanging-around-in-the-clipboard-from-some-app-we-are-not-even-running-anymore approach. :P

Later, Seeker

---

### Post by ugm6hr on 2009-06-25
> **seeker5528 said:**
> D: Some of us prefer the don't-have-to-worry-about-what-may-be-hanging-around-in-the-clipboard-from-some-app-we-are-not-even-running-anymore approach. :P

I think the problem is the inconsistency between applications.

If Gnome developers accept your view here, that would be acceptable (but undesirable from my viewpoint).

Having some apps store "permanently" and others not is very annoying.

---

### Post by SKLP on 2009-06-25
> **seeker5528 said:**
> D: Some of us prefer the don't-have-to-worry-about-what-may-be-hanging-around-in-the-clipboard-from-some-app-we-are-not-even-running-anymore approach. :PThe clipboard won't be stored (in gtk apps, and with firefox and my patch) unless you are running gnome (or there maybe some other desktop which also has a fdo compliant clipboard manager included)

---

### Post by seeker5528 on 2009-06-26
> **SKLP said:**
> The clipboard won't be stored (in gtk apps, and with firefox and my patch) unless you are running gnome (or there maybe some other desktop which also has a fdo compliant clipboard manager included)

I don't see anything in the settings or administration menus relating to clipboard stuff, or in control center.

So where do I look to see/delete what's in the clipboard configure behaviour and other management fucntions? And if I can manage the clipboard, why have a manager at all?

Later, Seeker

---

### Post by PGScooter on 2009-07-30
I love parcellite. However, I do not think it should be part of Karmic unless it is further developed.

The developer says that "I don&#8217;t plan to significantly develop Parcellite much further than its current state". 
[http://parcellite.sourceforge.net/?p=78](http://parcellite.sourceforge.net/?p=78)

Also, the actions are buggy:
[http://sourceforge.net/tracker/index.php?func=detail&aid=2785628&group_id=235597&atid=1097277](http://sourceforge.net/tracker/index.php?func=detail&aid=2785628&group_id=235597&atid=1097277)
[https://bugs.launchpad.net/ubuntu/+source/parcellite/+bug/404700](https://bugs.launchpad.net/ubuntu/+source/parcellite/+bug/404700)

---

### Post by lean on 2009-07-30
Anyone up for making af ppa with the patch included?

---

### Post by Arup on 2009-07-30
I am quite satisfied with Glipper, absolutely no issues here.

---

### Post by PGScooter on 2009-08-17
The only problem with Glipper and Parcellite is that neither is being maintained. It would not be a good idea to add either one to koala if it is not maintained.

---

### Post by ugm6hr on 2009-08-18
> **PGScooter said:**
> The only problem with Glipper and Parcellite is that neither is being maintained. It would not be a good idea to add either one to koala if it is not maintained.

I have found another problem with Parcellite.

It intereferes with OpenOffice's internal clipboard.  Trying to copy a table from Base to Calc doesn't work unless you disable Parcellite.

As a default application, that is unacceptable.

---

