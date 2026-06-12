---
title: "suggestion for &quot;next release&quot; vs. &quot;features&quot; management"
date: 2010-02-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by SaintDanBert on 2010-02-15
I've read lots of postings about the "next release" of *buntu and the inclusion of "new features" and such. I have a couple of thoughts.

[highlight]"Fixes" vs. "Features"[/highlight]
I would like to see the Fall release (v*.10) become the new feature release and the Spring release (v*.04) become the maintenance release.
[grin] we get new features in time for Christmas... 

This does not preclude feature introduction any time or maintenance any time. Instead, it helps with expectations. In another life, this cycle helped us plan deployments and made our systems more productive. We knew that once each year -- during the feature release -- the tide could turn in significant ways and we could prepare for that. We would get monthly updates for security and critical operation fixes and knew that all the vendor cruft would get sorted and merged and purged at the next maintenance release.

[highlight]Which Features are Important[/highlight]
Years ago, I was part of a mainframe computer user group. Here is how they handled the issue of "feature requests" and "next release" planning.

1. Requests were collected and placed on a public list... every one could see what was requested
2. Members voted for some small number of items -- say 20 votes if there were 100 features on the list.
3. Votes were tallied and the list published with wide distribution
4. The mainframe vendor then announced which of the top-N features were part of the next release.
5. New requests were added to the list over time
6. Members voted again
7. The vendor implemented again

Who votes and similar issues is another discussion. We can solve that if we like this idea in general.

The published list included a date for each feature so that folks could see how long it had been on the list. In addition, any previous vote counts and ranking appeared so folks could see how important (or not) an item was.

One item that was "sticky" to the list involved "bug fixes" and similar stability matters.

This system was so successful that the list spawned other similar lists. For example, the database folks, the productivity suite folks and the programmer workbench folks each started their own lists and voting.

May a sailing cheshire cat smile on you,
~~~ 0;-Dan

---

### Post by bapoumba on 2010-02-16
I've moved the thread to the devel release (currently Lucid).

---

### Post by emarkay on 2010-02-16
Very interesting, logical and intriguing.  

Of course I think **all** releases should devote **majority of efforts** to ***bug fixes and reliability validation*** instead of "dog and pony/gee whiz" pretty fluffies (for the easily amused and trendy).

But then again my cell phone doesn't text or take pictures and I still like Rear Wheel Drive cars...

---

### Post by SaintDanBert on 2010-02-16
> **emarkay said:**
> Very interesting, logical and intriguing.  
...
But then again my cell phone doesn't text or take pictures and I still like Rear Wheel Drive cars...

A professor in an early software development effort once said, 
[indent]
"Effectiveness" is making the right things work.
Efficiency is making effective things work right.
[/indent]

I suggest that the "... every release ... bug fix ..." effort might focus on per component unit-test level effectiveness.  For example, answering the question, "Does program XXX do the right things according to the specification and documentation."

During the annual maintenance release, that effort could then focus on efficiency issues and on those defects that stem from the system integration of a very large number of disparate programs. If I know that each **program XXX** meets its specification on its own, but that it fails in concert with some other program(s) that I also know meets specification, my effort to troubleshoot can focus on the intersections with little concern for other inner springenwerks.

~~~ 0;-Dan

---

### Post by seeker5528 on 2010-02-17
> **SaintDanBert said:**
> [highlight]"Fixes" vs. "Features"[/highlight]
I would like to see the Fall release (v*.10) become the new feature release and the Spring release (v*.04) become the maintenance release.
[grin] we get new features in time for Christmas...

With the LTS releases comeing every 18 months, that doesn't really fit the plan, but on the bright side, you still get significant new feature/feature advancement work every Christmas that doesn't come during an LTS development cycle. :p

Later, Seeker

---

### Post by emarkay on 2010-02-18
> **SaintDanBert said:**
> A professor in an early software development effort once said,[INDENT]"Effectiveness" is making the right things work.
Efficiency is making effective things work right.
[/INDENT]I suggest that the "... every release ... bug fix ..." effort might focus on per component unit-test level effectiveness.  For example, answering the question, "Does program XXX do the right things according to the specification and documentation."

During the annual maintenance release, that effort could then focus on efficiency issues and on those defects that stem from the system integration of a very large number of disparate programs. If I know that each **program XXX** meets its specification on its own, but that it fails in concert with some other program(s) that I also know meets specification, my effort to troubleshoot can focus on the intersections with little concern for other inner springenwerks.
~~~ 0;-Dan

Yes, bit as long as the devs are motivated by "eye candy" and "gee whiz", bugs 1 through current will still be active. And still, some users may not even be able to get to the basic desktop, or the network, or the document, or the Internet, or their floppy, or their camera, or their old DOS game, or their new automotive interface tool, or....  

Ya see where the breakdown is?

Pretty is pointless when it doesn't work...

---

### Post by Merk42 on 2010-02-18
> **emarkay said:**
> Yes, bit as long as the devs are motivated by "eye candy" and "gee whiz", bugs 1 through current will still be active. And still, some users may not even be able to get to the basic desktop, or the network, or the document, or the Internet, or their floppy, or their camera, or their old DOS game, or their new automotive interface tool, or....  

Ya see where the breakdown is?

Pretty is pointless when it doesn't work...

But depending on your definitions of 'pretty', the people doing that would have no idea how to make something 'work'

---

### Post by BackwardsDown on 2010-02-18
> I would like to see the Fall release (v*.10) become the new feature release and the Spring release (v*.04) become the maintenance release.

How would you do that? Are you going to fix bugs in every program? What if this bug is fixed in the new version of the software, are you going to backport it (costs time)? Do you know how much time it takes for a random developer to get used to the code and how much faster it is to let the developers of the application do the bug-fixing?

How are you going to fix hardware bugs, without using a newer driver/kernel? (because that would bring in features)

There are not many bugs in 'Ubuntu', most of the time they are in certain programs, and most of them are being squashed by uploading a new version we get from the maintainers. If there are too many bugs, you have to go to the source (haha) of that bug, to the people that write those programs.

And having random people vote is not handy. If there is 1 bug easy to fix, and 1 very very hard to fix (and is fixed in the new version of the app), please let a developer decide where his time will go, and let him fix the easy bug first.

---

### Post by seeker5528 on 2010-02-18
> **BackwardsDown said:**
> How would you do that? Are you going to fix bugs in every program? What if this bug is fixed in the new version of the software, are you going to backport it (costs time)? Do you know how much time it takes for a random developer to get used to the code and how much faster it is to let the developers of the application do the bug-fixing?

I think you are reading too much into:

> I would like to see the Fall release (v*.10) become the new feature release and the Spring release (v*.04) become the maintenance release.

Without taking into consideration:

> This does not preclude feature introduction any time or maintenance any time.

Which I would say actually describes what we have now, just on an 18 month cycle instead of yearly.

Later, Seeker

---

### Post by SaintDanBert on 2010-02-18
I would not have heartburn if Long Term Support (LTS) releases shifted to every other year -- 24 months -- in cooperation with the shift to a **maintenance release** and **feature release** system. My planning and thinking would easily wrap around something like
[indent]
This is an even year (pick one) release, therefore it is an LTS release.
[/indent]

It could also be the case that LTS releases happen in parallel with the Spring and Fall release cycle.  I know that is more work to do an *extra* release, but what is best for the product line and customers.

Over the years, I've shipped all sorts of software based and software intensive products using this sort of release cycle. There was some start-up heart burn, but everyone liked it -- they could plan, their plans were mostly stable for 6 to 12 months at least, it was easy to ride the splash when new features arrived, significant defects were fixed each month and the cruft sorted out.

Yes, this changes the status quo. Yes, there will be some wrangling to make this work. However, I think that this offers a good opportunity to resolve some of the fixes vs. features vs. planning troubles that are clearly manifest with Karmic.

Cheers,
~~~ 0;-Dan

---

### Post by cariboo on 2010-02-18
The LTS release is not done in parallel with the regular release. With this release we only get a little bit of cool stuff, and have to wait for the next release in October to feed our need for cool stuff. LTS releases come out every 2 years and are supported for 3 years for the desktop version and 5 years for the server version.

---

### Post by seeker5528 on 2010-02-18
> **SaintDanBert said:**
> Over the years, I've shipped all sorts of software based and software intensive products using this sort of release cycle. There was some start-up heart burn, but everyone liked it -- they could plan, their plans were mostly stable for 6 to 12 months at least, it was easy to ride the splash when new features arrived, significant defects were fixed each month and the cruft sorted out.

To some extent all planning is around the LTS releases. There is a set, known, predictable schedule so planning doesn't really seem like an issue.

It's not like the Ubuntu developers control all the software included in the distribution, the majority of development is done upstream and out of the control of Ubuntu developers and follow their own development schedules. If they moved to doing a more conservative release every other release instead of every third release, that would mean a higher percentage of time where the software in the distribution was lagging what upstream is working on by a larger degree making it harder to get things fixed upstream.

I don't think the 6 and 18 month schedules were chosen arbitrarily. The reasoning behind releasing every 6 months would lean more toward development concerns giving 2 releases where they can track closer to the upstream and be more actively involved in helping to fix/getting upstream to fix the issues with stuff they are currently working on at the time and provide windows where user feed back/feature requests to upstream developers may still relevant to what the upstream developers are working on.

Choosing 18 months between the more conservative releases for which long term support is planned is more of a practical decision based on what Canonical thinks they can reasonably support over the long haul, taking into consideration what upstream developers will provide fixes for versus what Ubuntu developers will have to fix themselves during the time the release is supported.

Later, Seeker

---

### Post by Ibidem on 2010-02-18
@seeker,SaintDanBert:
Can't you guys get it straight?
It's 2 years=24 months from LTS to LTS, not 18 months!
6.06 (would have been 6.04)
8.04
10.04
NEXT:12.04
NOT:
6.10
8.04
9.10
NOR:
7.04
8.10
10.04

The proposal is a lot easier to fit in the schedule than you seem to think.

---

### Post by lykwydchykyn on 2010-02-18
> **SaintDanBert said:**
> 
[highlight]Which Features are Important[/highlight]
Years ago, I was part of a mainframe computer user group. Here is how they handled the issue of "feature requests" and "next release" planning.

1. Requests were collected and placed on a public list... every one could see what was requested
2. Members voted for some small number of items -- say 20 votes if there were 100 features on the list.
3. Votes were tallied and the list published with wide distribution
4. The mainframe vendor then announced which of the top-N features were part of the next release.
5. New requests were added to the list over time
6. Members voted again
7. The vendor implemented again

Who votes and similar issues is another discussion. We can solve that if we like this idea in general.

The published list included a date for each feature so that folks could see how long it had been on the list. In addition, any previous vote counts and ranking appeared so folks could see how important (or not) an item was.

One item that was "sticky" to the list involved "bug fixes" and similar stability matters.

This system was so successful that the list spawned other similar lists. For example, the database folks, the productivity suite folks and the programmer workbench folks each started their own lists and voting.

May a sailing cheshire cat smile on you,
~~~ 0;-Dan
What you describe sounds an awful lot like a bug tracker.  The difference being that a bug tracker scales a whole lot better.

Launchpad allows you to submit "wish list" or feature request items as well as bugs, and you can vote on existing bugs if they affect you.

If you aren't signed up, you should.

---

### Post by seeker5528 on 2010-02-19
> **Ibidem said:**
> 
It's 2 years=24 months from LTS to LTS, not 18 months!

Ooops!!! :oops:

That does change what my first response would have been.

Doesn't change anything for my later post except for having 3 releases that track closer to the upstream instead of 2 in between LTS releases.

Later, Seeker

---

### Post by snowpine on 2010-02-19
It all makes sense if you understand Ubuntu's relationship with Debian. The Debian project already offers:

1. An ultra-stable, non-rolling release with no fixed release date (it's ready when it's ready)
2. A slightly-stable rolling release, which is the testing ground for the next stable release
3. An unstable rolling release for those who want the newest stuff

Ubuntu fills a 4th niche: a moderately-stable, non-rolling release that comes out every 6 months (with LTS every 2 years). It is a waste of time for Ubuntu to duplicate any of the 3 existing (and excellent, IMHO) Debian branches.

Y'all also need to understand that Canonical does not write most of the applications in Ubuntu. :) If Mozilla releases a major new version of Firefox, Canonical needs to include it in the next Ubuntu or suffer the consequences, regardless of whether or not it is "convenient" for the Ubuntu release cycle.

---

