---
title: "Crash reporter needs an Launchpad opt-out option"
date: 2009-09-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by X10N on 2009-09-05
The restart program button is a nice touch, but not everyone wants to sign into Launchpad everytime a problem happens. I just want to report the problem and get on with whatever.

---

### Post by taavikko on 2009-09-05
Seems to me there is a "close" button, so what's the issue?

And if mistakenly pressing "report" there still a cancel opportunity.

---

### Post by X10N on 2009-09-05
> **taavikko said:**
> Seems to me there is a "close" button, so what's the issue?

And if mistakenly pressing "report" there still a cancel opportunity.

That's kind of missing the point isn't it?

I want to be able to report the problem, but have the option to not have to sign into Launchpad.

Not reporting helps no one, but being forced to sign in everytime is just annoying.

---

### Post by gnomeuser on 2009-09-05
The correct approach might be "report upstream". I am pretty damn tired of using the official tool, do all the work only to have the maintainer close the bug and tell me to go upstream.

Upstream is the right choice, it's harder to do and some applications don't have an API we can use but it's needless better than having bugs languish in Launchpad without attention or having them closed by annoying maintainers who often doesn't even read the report instead close them using scripts.. so what is the point really.

---

### Post by 23meg on 2009-09-05
> **X10N said:**
> The restart program button is a nice touch, but not everyone wants to sign into Launchpad everytime a problem happens. I just want to report the problem and get on with whatever.

> **X10N said:**
> That's kind of missing the point isn't it?

I want to be able to report the problem, but have the option to not have to sign into Launchpad.

Not reporting helps no one, but being forced to sign in everytime is just annoying.

Could that be a problem with your browser? If you've logged in once and your cookie hasn't expired, it shouldn't keep asking you to log in - and if it does, you can have your browser remember your login details, so that's it's a one-click annoyance at worst.

> **gnomeuser said:**
> The correct approach might be "report upstream". I am pretty damn tired of using the official tool, do all the work only to have the maintainer close the bug and tell me to go upstream.

Upstream is the right choice, it's harder to do and some applications don't have an API we can use but it's needless better than having bugs languish in Launchpad without attention or having them closed by annoying maintainers who often doesn't even read the report instead close them using scripts.. so what is the point really.

I don't think you'll make upstream very happy by flooding them with thousands of invalids, already knowns and false positives. There's a point in distribution-level triage; if it's failing in certain aspects, it needs to be improved.

---

### Post by taavikko on 2009-09-05
> **X10N said:**
> That's kind of missing the point isn't it?

I want to be able to report the problem, but have the option to not have to sign into Launchpad.

Not reporting helps no one, but being forced to sign in everytime is just annoying.

took me a while to understand what you were after, now I get it :)

This shouldn't be impossible to achieve, as apport-collect is able to add info to bugs without 
need to login to launchpad via browser. 

ubuntu-bug/apport is evolving rapidly (thanks to pitti) and who knows in the next cycle we might have an tool for automatically loading the .crash file to LP with all the info needed without user intervention.

---

### Post by castrojo on 2009-09-05
> **gnomeuser said:**
> The correct approach might be "report upstream". I am pretty damn tired of using the official tool, do all the work only to have the maintainer close the bug and tell me to go upstream.

That's because you know the difference between when a bug is upstream and when a bug is a distro bug. Most people have no idea.

Most new bugs that are filed are worthless, a triager has to spend time asking "What version?" and "What arch?" and all these questions. apport does this all for you so you can at least get that part of the conversation out of the way. If we forwarded every bug to upstream they would hunt us down and kill us.

However if we do a good job filtering out all the crap and doing a good job researching, adding information and forwarding a really god bug then that has a better chance of getting that bug fixed. There's been plenty of times when upstreams have told me the value of apport crashers for example. 

Now that GNOME bugzilla has been upgraded to 3.0.x we can do things like use the bugzilla/launchpad plugin to make upstreaming a bug much easier and provide the upstream maintainers with all the information they need without spamming them with tons of crap bugs. The lp bugs guys and the gnome bugzilla guys have been talking about this for a while, it's just been insanely difficult to move GNOME bugzilla from a heavily customized 2.0 to a newer version. 

There are plenty of instances when filing a bug upstream instead of lp is appropriate, you just need to make sure you can reproduce it with the vanilla  upstream code as well.

---

### Post by gnomeuser on 2009-09-05
> **23meg said:**
> 
I don't think you'll make upstream very happy by flooding them with thousands of invalids, already knowns and false positives. There's a point in distribution-level triage; if it's failing in certain aspects, it needs to be improved.

Wrong way: Having user spend time collecting data, writing up a report with steps to reproduce followed by immediate closing and a request to take the bug upstream.. without giving the url for the bugtracker (a considerable problem for applications not on the major trackers such as bugzilla.gnome.org), and often requiring the user in most cases to open yet another account. This is a waste of my time and angers me considerably.

Right way: Offer me a button to default to or report directly to this time especially for packages where the maintainer repeatedly has taken the above approach (you could even allow the maintainer to request the default as being upstream for these cases). If it ends up showing of Ubuntu breakage perhaps the request upstream could make was for Ubuntu to control it's breakage. One might even wish for an easier way to upstream a bug than closing it and telling the reporter to basically start all over with little if any information on how (especially for autocompiled bug reports via apport, which pieces are relevant.. who knows?).

I have done QA work in Open Source for years, I know it's not easy to automate upstreaming of bugs, however in 99% of all cases the bug is valuable for upstream e.g. it is nice to know that your application is broken for Ubuntu users even if it is their problem (certain projects e.g. refuse to take bugs from certain distributions based on the consistently bad maintainership or bugs inherit to the distributions - Gentoo e.g. has been a popular target for this treatment). The tools should weed out duplicates that is what they are there for.

---

### Post by castrojo on 2009-09-05
> **gnomeuser said:**
> Right way: Offer me a button to default to or report directly to this time especially for packages where the maintainer repeatedly has taken the above approach (you could even allow the maintainer to request the default as being upstream for these cases). If it ends up showing of Ubuntu breakage perhaps the request upstream could make was for Ubuntu to control it's breakage. 

This is exactly the kind of thing the bugzilla plugin for launchpad will allow us to do.

---

### Post by X10N on 2009-09-05
> **23meg said:**
> Could that be a problem with your browser? If you've logged in once and your cookie hasn't expired, it shouldn't keep asking you to log in - and if it does, you can have your browser remember your login details, so that's it's a one-click annoyance at worst.



I don't think you'll make upstream very happy by flooding them with thousands of invalids, already knowns and false positives. There's a point in distribution-level triage; if it's failing in certain aspects, it needs to be improved.

Keeping cookies in your browser cache is a big nono, but that isn't what I meant. I basically mean it shouldn't force Firefox open and autostart Launchpad. It's phenomenally annoying to say the least.
Give me the option of turning this off. If I want to sign into Launchpad and track the bug, let that be my choice.

> **taavikko said:**
> took me a while to understand what you were after, now I get it :)

This shouldn't be impossible to achieve, as apport-collect is able to add info to bugs without 
need to login to launchpad via browser. 

ubuntu-bug/apport is evolving rapidly (thanks to pitti) and who knows in the next cycle we might have an tool for automatically loading the .crash file to LP with all the info needed without user intervention.

Hopefully even though apport can be pretty strange. Firefox crashed and it wanted to upload a 300MB+ crash report. :confused:

---

### Post by 23meg on 2009-09-05
[QUOTE=gnomeuser]Wrong way: Having user spend time collecting data, writing up a report with steps to reproduce followed by immediate closing and a request to take the bug upstream.. without giving the url for the bugtracker (a considerable problem for applications not on the major trackers such as bugzilla.gnome.org), and often requiring the user in most cases to open yet another account. This is a waste of my time and angers me considerably.[/QUOTE]

I didn't say that's the right way; if that happens considerably often, it's indeed something we have to improve upon.

---

### Post by 23meg on 2009-09-05
[QUOTE=X10N]I basically mean it shouldn't force Firefox open and autostart Launchpad. It's phenomenally annoying to say the least.
Give me the option of turning this off. If I want to sign into Launchpad and track the bug, let that be my choice.[/QUOTE]

I'm not sure if this is possible / feasible at this point. You may want to file a bug report in Apport, or ask Martin Pitt directly, to find out.

---

