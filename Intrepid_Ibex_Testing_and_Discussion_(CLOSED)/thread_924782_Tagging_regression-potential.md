---
title: "Tagging regression-potential"
date: 2008-09-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-09-19
Recently I saw one of our testers from this forum ask about tagging in a bug comment. I think it's better to explain here so more people see it.

Henrik has introduced a new process that will make raising visibility for regressions in Intrepid much easier. If you encounter a bug with your tests in the dev builds of Intrepid that used to work on Hardy, please tag it regression-potential if it is not tagged that way already.

***********

Henrik Nilsen Omma
 to Ubuntu-Devel, Ubuntu
	
	
We are preparing a new procedure for tracking regressions in Ubuntu.
This should help us prioritise our bug fixing work as we approach the
release and over a few releases we can study the trends and work to
reduce regressions in Ubuntu overall.

Regressions in functionality are not always caused by regressions in an
individual package, but may result from interaction of a number of
packages or by replacing one package with a newer technology. These
feature regressions are jarring to users even if they are done for
technically sound reasons - we should therefore track them, release note
as appropriate and work to minimise them over time.

To start with we'll be using the following tags:

 * regression-potential - a bug in the development release
 * regression-release - a regression in a stable release
 * regression-update - regression in a stable release update

See [1] for more detailed descriptions of these tags and example bugs.

Tagged bugs can be viewed at [2] and [3]. We are also working on a
custom tracking page that will also have an archive view and statistics
(based on the SRU pages [4]). Brian and Steve will also perform some
keyword searches of current bugs to backfill these lists.

Please apply these tags to bugs you come across that fit the criteria
and let us know if you would like to see extensions to this tracking or
have other feedback.


Henrik

---

### Post by TheMemphisExperience on 2008-09-20
Thanks for noting that. I wouldn't have thought about it otherwise nor known where or what to tag as. Well then, Thank You and Good Night.

---

### Post by plun on 2008-09-20
Thanks Nullack for claryfying this  :)

This is the bug:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/259343](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/259343)

Nautilus scripts works but its nothing for a "newbie"...

---

### Post by plun on 2008-09-20
Database error double post

---

### Post by UbuWu on 2008-09-20
Here are the links referred to in that mailing list post:

[1] [https://wiki.ubuntu.com/QATeam/RegressionTracking](https://wiki.ubuntu.com/QATeam/RegressionTracking)
[2] [https://bugs.launchpad.net/ubuntu/+bugs?field.tag=regression-potential](https://bugs.launchpad.net/ubuntu/+bugs?field.tag=regression-potential)
[3] [https://bugs.launchpad.net/ubuntu/+bugs?field.tag=regression-release](https://bugs.launchpad.net/ubuntu/+bugs?field.tag=regression-release)
[4] [http://people.ubuntu.com/~sbeattie/sru_todo.html](http://people.ubuntu.com/~sbeattie/sru_todo.html)

And here is the regression tracker:
[http://people.ubuntu.com/~sbeattie/regression_tracker.html](http://people.ubuntu.com/~sbeattie/regression_tracker.html)

---

### Post by Nullack on 2008-09-20
I notice were now at 100 regressions for Intrepid. Im convinced we could get this to 300! Its a good thing, because it means raising visibility to the right people about what the problems are with things that used to work on Hardy.

---

### Post by UbuWu on 2008-09-21
Well and hopefully a lot of them can still be fixed before release. Although so far I haven't seen any increased attention of developers for these bugs...

---

### Post by Nullack on 2008-10-05
I see the list now exceeds 150.

---

### Post by UbuWu on 2008-10-05
But on the other hand, [41 potential regressions]("https://bugs.launchpad.net/ubuntu/+bugs?field.status%3Alist=FIXRELEASED&field.tag=regression-potential") have been fixed in the mean time.

---

