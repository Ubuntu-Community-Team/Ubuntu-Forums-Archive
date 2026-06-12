---
title: "Contributing To Intrepid"
date: 2008-08-21
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by andrewsomething on 2008-08-21
Intrepid Ibex (8.10) will be the ninth release of everyone's favorite Free operating system, Ubuntu. With Alpha 5 already out the door, now is a good time to recap what we can do to help make Intrepid a quality release.

**[SIZE="5"]First Things First[/SIZE]**

*** Get a Launchpad account if you don't already have one.** You'll need it to report and track bugs, do translations in Rosetta, register blueprints, track support requests, and share the karma. The newly updated Launchpad can be an excellent central hub for almost all your contributions to Ubuntu and beyond. Register _[here]("https://launchpad.net/+login")_.

*** Familiarize yourself with how Ubuntu development works,** at least roughly. This will help you contribute more efficiently, and prevent many uncalled for misunderstandings. An excellent place to start is _[the Ubuntu Development page]("https://wiki.ubuntu.com/UbuntuDevelopment")_ in the wiki. Even a brief look at the main page will give you a rough idea of how the pieces fit together, and it will help if you go deeper. If the puzzle in your head has missing pieces, don't hesitate to ask questions on how things work. The _[Ubuntu Open Week]("https://wiki.ubuntu.com/UbuntuOpenWeek")_ is also a good opportunity to dive a bit deeper into Ubuntu.

*** Review the _[Intrepid Release Schedule]("https://wiki.ubuntu.com/IntrepidReleaseSchedule")_**, to plan ahead when and what you can contribute at this point in the development cycle.

***** If you're confused about and/or having too many problems with the development version and don't exactly feel on top of things, don't run it for the time being. The Ubuntu development process is a tough ride, tougher than most distros, due to the cutting edge technology policy and the _[fixed development duration]("https://wiki.ubuntu.com/TimeBasedReleases")_ that's tightly packed with radical changes; if at any point you decide that you can't bear with it, drop it until a more stable phase, a milestone release, or entirely. **Intrepid will be a development version until October 2008, and is prone to major breakage at any point. Do not rely on it as your main operating system. If you decide to test it, be aware that you're risking being left without a working operating system, and data loss.**
[B][SIZE="5"]
Reporting Bugs[/SIZE][/B]

Bug reporting is one of the most accessible, and yet most beneficial ways in which everyone can contribute. It's a good idea to start reporting bugs as early as possible, since towards the later stages, especially past _[BetaFreeze]("https://wiki.ubuntu.com/BetaFreeze")_, focus will most likely shift towards critical bugs only. Whenever you encounter a reproducible malfunction in Intrepid, **_[file a bug report]("https://help.ubuntu.com/community/ReportingBugs")_**. It's a good idea to start a thread in the development forum before submitting your report, to discuss it with others who may have experienced it, to make sure it's genuine. And it's very important that you do a search for the bug before submitting it; duplicate bugs make life more difficult for everyone. It's practical to keep the URL structure for the source package bug pages (where you can search for bugs in them) in mind:

```
https://bugs.launchpad.net/ubuntu/+source/<sourcepackagename>
```

Take a look at the **_[Reporting Bugs page]("https://help.ubuntu.com/community/ReportingBugs")_** in the wiki to learn more about the procedure. The _[best practices wiki page]("https://wiki.ubuntu.com/Bugs/BestPractices")_ also contains some useful [_information_]("http://www.chiark.greenend.org.uk/~sgtatham/bugs.html"). Remember, how a bug is initially reported can have a huge effect on how it's handled and how quickly it gets fixed.

[_Finding the right package_]("https://wiki.ubuntu.com/Bugs/FindRightPackage") is important when filing a bug report. This makes sure that the right developers will see your bug.

Advanced users will find the [_guide to debugging_]("https://wiki.ubuntu.com/DebuggingProcedures") useful. The more information in a bug report, the easier it is for a developer to get to the bottom for it. 
[B][SIZE="5"]
Triaging Bugs[/SIZE][/B]

If you have enough dedication to **_[helping with bugs]("https://wiki.ubuntu.com/HelpingWithBugs")_** to go a step beyond reporting, this is where you're needed.

Triaging bugs consists of the following:

- Responding to new bugs as they are filed
- Searching for duplicates in the bug tracking system
- Sending bugs to their upstream authors, when applicable
- Cross-referencing bugs from other distributions
- Classifying bugs by package
- Prioritizing bugs
- Expiring old bugs

Since new bugs never stop coming, there are never enough bug triagers. It's an excellent way to help out that's much appreciated, and it will teach you a lot about how Ubuntu works. Anyone can help **_[triage bugs]("https://wiki.ubuntu.com/Bugs/HowToTriage")_**, but you might also want to join the _[Bug Squad]("https://wiki.ubuntu.com/BugSquad")_. After you've triaged bugs for a while, you can become a member of the _[Bug Control team]("https://wiki.ubuntu.com/UbuntuBugControl")_, where you'll be allowed to change "Importance" and "Milestone" values of existing bugs.

When triaging, it's important to understand **_[bug statuses]("https://wiki.ubuntu.com/Bugs/Status")_**. For instance, confirming a bug means moving the status from new to confirmed, not simply say its confirmed in a comment in the bug. 

And regardless of whether you've worked on bugs before or not, don't miss the **_[Hug Day]("https://wiki.ubuntu.com/UbuntuBugDay")_**!

**[SIZE="5"]Testing ISO Images[/SIZE]**

The [_ISO Testing Team_]("https://wiki.ubuntu.com/Testing/") tests daily ISO builds that lead to milestone CD images before the milestones are officially out, making sure they work as intended. To join the team and help out, follow the _[instuctions on the team's wiki page]("https://wiki.ubuntu.com/Testing/ISO/Procedures")_, and apply to _[join the team]("https://edge.launchpad.net/~ubuntu-testing")_ on Launchpad.
[SIZE="5"][B]
Submitting Ideas For New Features[/B][/SIZE]

_**[Ubuntu Brainstorm]("http://brainstorm.ubuntu.com/")**_ is the best place for users to suggest new ideas and see what others are talking about. 

At the start of each development period, a _[developer summit]("https://wiki.ubuntu.com/DeveloperSummit")_ is held, where plans for the upcoming release are evaluated. The summit for Intrepid was _[held in Prague]("https://wiki.ubuntu.com/UDS-Intrepid")_ from 19th to 23rd May 2008. At this point it is too late for any major new ideas to be proposed for Intrepid, but it's never too early to start thinking about next time. So if you have any ideas that you strongly feel should be realized in Intrepid +1, you should start thinking about how to make them a reality. 

Some ideas can be quickly implemented, while others can require a great deal of discussion or development work. Even a seemingly simple idea can be complex to implement if it affects other aspects of the system. Changes to the default look or behavior of the base system are always controversial and may cause extensive discussions.

A minor change can often be described in a bug report. The issue may actually be a bug (a fault in existing software). A simple change can be expressed as a 'wishlist' bug. For more complex changes we need to write a 'blueprint'. Blueprints (a.k.a. "specs") are documents suitable for developers to study and act upon. These should usually only be written by developers actively working on realizing the idea. 

Take a look at the _[list of existing specs for Ubuntu]("https://blueprints.launchpad.net/ubuntu/")_ first. If you can write concise, workable specs yourself, go ahead and submit them. If you can't, taking a look at some well written and accepted specs, or the self-referential _[SpecSpec]("https://wiki.ubuntu.com/SpecSpec")_ may help.

A lot of the ideas submitted so far either already have corresponding specs (some being worked on), or have already been proposed in another form by others, so please do a [_Brainstorm search_]("http://brainstorm.ubuntu.com/advanced_search"), _[a spec search]("https://blueprints.launchpad.net/")_, and a _[forum search]("http://ubuntuforums.org/search.php")_ to see if what you're proposing has already been proposed by someone else, or is already being worked on.


**[SIZE="5"]Doing Translations[/SIZE]**

Ubuntu puts a special emphasis on the right and ability of all its users to comfortably use Free software in their native languages, so translations have their special place. If you're fluent with a second language beside English, your contribution to translations in [_Rosetta_]("https://translations.launchpad.net/"), Launchpad's translation module, will be valuable. With Rosetta's web interface, you can translate as much as you want, at any time, in any package.

Make sure you're familiar with the software you translate, for your translations to have as much sensitivity on wording context as possible. The freedom of multiple translators to non-linearly edit translations at will can bring problems with it as well, such as consistency; it's a good idea to keep in touch with your fellow translators in your language's translation team in Launchpad and/or the upstream contacts for the software you're translating to tackle such possible difficulties.

**[SIZE="5"]Submitting Code[/SIZE]**

Why not? The Ubuntu core developers and [_MOTU_]("https://wiki.ubuntu.com/MOTU") almost always have their hands full, and may occasionally need a hand with certain issues. You may also want to have a go at becoming a MOTU hopeful, and eventually, a MOTU; check their wiki page for details. There will also be lots of _[specs]("https://blueprints.launchpad.net/ubuntu")_ floating around that no core developers or MOTU will be able to work on; you can try your hand at realizing them.

**[SIZE="5"]Doing Design[/SIZE]**

If you do graphics design, you can get involved in one of the Ubuntu-related artwork projects. Start _[here]("https://wiki.ubuntu.com/Artwork")_.

**[SIZE="5"]Writing Documentation[/SIZE]**

If you can write good documentation, you can work with the _[Documentation Team]("https://wiki.ubuntu.com/DocumentationTeam")_, or by yourself on the _[community documentation.]("https://help.ubuntu.com/community/")_


(This guide is a refresh of 23meg's great _[Contributing To Gutsy]("http://ubuntuforums.org/showthread.php?t=411868")_ guide. Please add any additional information that you think is important for people to know about in the comments. Thanks!)

---

### Post by andrewsomething on 2008-08-21
Some further topics:

**[SIZE="5"]Link Upstream Bugs[/SIZE]**

Linking upstream bugs to existing Ubuntu bugs is an important way to help get bugs fixed. 

This _[blog post by an Ubuntu dev]("http://stompbox.typepad.com/blog/2008/08/feeding-the-har.html")_ explains why, and this _[wiki page]("https://wiki.ubuntu.com/Bugs/Watches")_ shows you how.

**[SIZE="5"]5-A-Day[/SIZE]**

The idea with 5-A-Day is simple - everyone in the Ubuntu community works to tend to at least five bugs every day, and to make it fun, we have produced some tools and rankings to make those 5 bugs count.

See the_**[ 5-A-Day wiki]("https://wiki.ubuntu.com/5-A-Day")**_ page for all the info!

**[SIZE="5"]Harvest[/SIZE]**

Ubuntu dev Daniel Holbach has created a tool to help find and fix the so-called "low hanging fruit," bugs that should be easy to fix that might be lost among the thousands of bugs in Launchpad. He explains it _[here]("http://daniel.holba.ch/blog/?p=139")_. 

_[Check it out.]("http://daniel.holba.ch/harvest/")_ It's a great place for future MOTUs and aspiring developers to start.

---

### Post by Nullack on 2008-08-21
I had hoped that we would discuss it and edit drafts before trying to post one. Can you please refer to my original thread that had a number of things I conside rimportant beyond the old 23meg post, thanks.

---

### Post by andrewsomething on 2008-08-21
I think this stands on its own. The majority of the links you point to are in this post. If you feel that there is a need for something more, feel free to write it. Either way, I think this is useful even if it's only a temporary stand-in for something more in depth.

---

### Post by danbuter on 2008-08-21
**Don't be a jerk when people have problems with a beta.** Especially by saying "It's a beta!!!". Instead, post helpful comments or don't post at all.

---

### Post by Nullack on 2008-08-23
Can I suggest two items please:

1. The importance of including the Ubuntu package revision in the report. This makes it easier to suggest retesting on new versions to see if the problem can still be replicated.

2. The importance of "fessing up" if your a non default install. Akey design principle of Ubuntu is:

"There should be exactly one recommended way to accomplish a task in the default installation, to promote consistent documentation and support"

Many so called howtos and guides do potentially dangerous things like using repos outside of Ubuntu, not so stable obscure packages etcetc. Ofcourse users are free to do whatever they want with the software, but consideration should be given to support and the many volunteers who help out. Filing a bug about your own custom compiled kernel on LP breaking Ubuntu for example is not helpful.

---

### Post by olskar on 2008-08-23
I would also, again, like to suggest something to be added.

I talked to cjwatson on #ubuntu-dev about the problem that many non-developers make blueprints of things they are not able to capable of doing. I have seen lots of blueprints containing nothing but a link to a brainstormidea. Correct me if I am wrong, but this is not the idea of
blueprints, they are (or rather should be) detailed software design documents.

There has been a trend for people to follow up to all wishlist bugs and say that they should be blueprints, and it's completely wrong - complex things that require careful design work sometimes merit being blueprints, but simple enhancements don't.

---

### Post by YokoZar on 2008-08-24
> **olskar said:**
> I would also, again, like to suggest something to be added.

I talked to cjwatson on #ubuntu-dev about the problem that many non-developers make blueprints of things they are not able to capable of doing. I have seen lots of blueprints containing nothing but a link to a brainstormidea. Correct me if I am wrong, but this is not the idea of
blueprints, they are (or rather should be) detailed software design documents.

There has been a trend for people to follow up to all wishlist bugs and say that they should be blueprints, and it's completely wrong - complex things that require careful design work sometimes merit being blueprints, but simple enhancements don't.
Yes.  As a rule of thumb, if you're not physically attending the Ubuntu Developer Summit, bringing it up in a session, and actively designing the feature collaboratively, there's little hope for your blueprint.

That said, most blueprints are actually feature requests, and don't require underlying changes or design work on behalf of the rest of the development team - instead, you can often just do the work yourself, especially if it's upstream or in universe.  

Improving the UI, for instance, is often done through the Gnome project rather than as a specific spec/blueprint for Ubuntu.

---

