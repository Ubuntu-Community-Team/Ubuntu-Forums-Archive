---
title: "Contributing to Jaunty"
date: 2008-11-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2008-11-28
Jaunty Jackalope (9.04) will be the tenth release of everyone's favorite Free operating system, Ubuntu. With the first Alpha release already out the door, now is a good time to recap what we can do to help make Jaunty a quality release.


**[SIZE="5"]First Things First[/SIZE]**

*** Get a Launchpad account if you don't already have one.** You'll need it to report and track bugs, do translations in Rosetta, register blueprints, track support requests, and share the karma. The newly updated Launchpad can be an excellent central hub for almost all your contributions to Ubuntu and beyond. Register [here]("https://launchpad.net/+login").

*** Familiarize yourself with how Ubuntu development works**, at least roughly. This will help you contribute more efficiently, and prevent many uncalled for misunderstandings. An excellent place to start is the [Ubuntu Development page]("https://wiki.ubuntu.com/UbuntuDevelopment") in the wiki. Even a brief look at the main page will give you a rough idea of how the pieces fit together, and it will help if you go deeper. If the puzzle in your head has missing pieces, don't hesitate to ask questions on how things work. The [Ubuntu Open Week]("https://wiki.ubuntu.com/UbuntuOpenWeek") is also a good opportunity to dive a bit deeper into Ubuntu.

*** Review the [Jaunty Release Schedule]("https://wiki.ubuntu.com/JauntyReleaseSchedule")**, to plan ahead when and what you can contribute at this point in the development cycle.

* If you're confused about and/or having too many problems with the development version and don't exactly feel on top of things, don't run it for the time being. The Ubuntu development process is a tough ride, tougher than most distros, due to the cutting edge technology policy and the [fixed development duration]("https://wiki.ubuntu.com/TimeBasedReleases") that's tightly packed with radical changes; if at any point you decide that you can't bear with it, drop it until a more stable phase, a milestone release, or entirely. **Jaunty will be a development version until April 2009, and is prone to major breakage at any point. Do not rely on it as your main operating system. If you decide to test it, be aware that you're risking being left without a working operating system, and data loss.**


[SIZE="5"]**Reporting Bugs**[/SIZE]

Bug reporting is one of the most accessible, and yet most beneficial ways in which everyone can contribute. It's a good idea to start reporting bugs as early as possible, since towards the later stages, especially past [BetaFreeze]("https://wiki.ubuntu.com/BetaFreeze"), focus will most likely shift towards critical bugs only. Whenever you encounter a reproducible malfunction, [file a bug report]("https://help.ubuntu.com/community/ReportingBugs"). It's a good idea to start a thread in the development forum before submitting your report, to discuss it with others who may have experienced it, to make sure it's genuine. And it's very important that you do a search for the bug before submitting it; duplicate bugs make life more difficult for everyone. It's practical to keep the URL structure for the source package bug pages (where you can search for bugs in them) in mind:

[INDENT]```
https://bugs.launchpad.net/ubuntu/+source/<sourcepackagename>
```[/INDENT]

Take a look at the [Reporting Bugs page]("https://help.ubuntu.com/community/ReportingBugs") in the wiki to learn more about the procedure. The [best practices wiki page]("https://wiki.ubuntu.com/Bugs/BestPractices") also contains some useful information. Remember, how a bug is initially reported can have a huge effect on how it's handled and how quickly it gets fixed.

[Finding the right package]("https://wiki.ubuntu.com/Bugs/FindRightPackage") is important when filing a bug report. This makes sure that the right developers will see your bug.

Advanced users will find the [guide to debugging]("https://wiki.ubuntu.com/DebuggingProcedures") useful. The more information in a bug report, the easier it is for a developer to get to the bottom for it.


[SIZE="5"]**Triaging Bugs**[/SIZE]

If you have enough dedication to go a step beyond reporting, [this is where you're needed]("https://wiki.ubuntu.com/HelpingWithBugs").

Triaging bugs consists of the following:

- Responding to new bugs as they are filed
- Searching for duplicates in the bug tracking system
- Sending bugs to their upstream authors, when applicable
- Cross-referencing bugs from other distributions
- Classifying bugs by package
- Prioritizing bugs
- Expiring old bugs

Since new bugs never stop coming, there are never enough bug triagers. It's an excellent way to help out that's much appreciated, and it will teach you a lot about how Ubuntu works. Anyone can [help triage bugs]("https://wiki.ubuntu.com/Bugs/HowToTriage"), but you might also want to [join the Bug Squad]("https://wiki.ubuntu.com/BugSquad"). After you've triaged bugs for a while, you can become a member of the [Bug Control team]("https://wiki.ubuntu.com/UbuntuBugControl"), where you'll be allowed to change "Importance" and "Milestone" values of existing bugs.

When triaging, it's important to understand [bug statuses]("https://wiki.ubuntu.com/Bugs/Status"). For instance, confirming a bug means moving the status from new to confirmed, not simply say its confirmed in a comment in the bug.

And regardless of whether you've worked on bugs before or not, don't miss the [Hug Day]("https://wiki.ubuntu.com/UbuntuBugDay")!


[SIZE="5"]**Testing ISO Images**[/SIZE]

The [ISO Testing Team]("https://wiki.ubuntu.com/Testing/") tests daily ISO builds that lead to milestone CD images before the milestones are officially out, making sure they work as intended. To join the team and help out, follow the [instuctions on the team's wiki page]("https://wiki.ubuntu.com/Testing/ISO/Procedures"), and apply to [join the team on Launchpad]("https://edge.launchpad.net/~ubuntu-testing").


[SIZE="5"]**Submitting Ideas For New Features**[/SIZE]

[Ubuntu Brainstorm]("http://brainstorm.ubuntu.com/") is the best place for users to suggest new ideas and see what others are talking about.

At the start of each development period, a [developer summit]("https://wiki.ubuntu.com/DeveloperSummit") is held, where plans for the upcoming release are evaluated. The summit for Jaunty will be held in Mountain View, CA, US in December 2008. At this point it is too late for any major new ideas to be proposed for Jaunty, but it's never too early to start thinking about next time. So if you have any ideas that you strongly feel should be realized in Jaunty +1, you should start thinking about how to make them a reality.

Some ideas can be quickly implemented, while others can require a great deal of discussion or development work. Even a seemingly simple idea can be complex to implement if it affects other aspects of the system. Changes to the default look or behavior of the base system are always controversial and may cause extensive discussions.

A minor change can often be described in a bug report. The issue may actually be a bug (a fault in existing software). A simple change can be expressed as a 'wishlist' bug. For more complex changes we need to write a 'blueprint'. Blueprints (a.k.a. "specs") are documents suitable for developers to study and act upon. These should usually only be written by developers actively working on realizing the idea.

Take a look at the list of [existing specs for Ubuntu]("https://blueprints.launchpad.net/ubuntu/") first. If you can write concise, workable specs yourself, go ahead and submit them. If you can't, taking a look at some well written and accepted specs, or the self-referential [SpecSpec]("https://wiki.ubuntu.com/SpecSpec") may help.

A lot of the ideas submitted so far either already have corresponding specs (some being worked on), or have already been proposed in another form by others, so please do a [Brainstorm search]("http://brainstorm.ubuntu.com/advanced_search"), a [spec search]("https://blueprints.launchpad.net/"), and a [forum search]("http://ubuntuforums.org/search.php") to see if what you're proposing has already been proposed by someone else, or is already being worked on.


[SIZE="5"]**Doing Translations**[/SIZE]

Ubuntu puts a special emphasis on the right and ability of all its users to comfortably use Free software in their native languages, so translations have their special place. If you're fluent with a second language beside English, your contribution to translations in [Rosetta]("https://translations.launchpad.net/"), Launchpad's translation module, will be valuable. With Rosetta's web interface, you can translate as much as you want, at any time, in any package.

Make sure you're familiar with the software you translate, for your translations to have as much sensitivity on wording context as possible. The freedom of multiple translators to non-linearly edit translations at will can bring problems with it as well, such as consistency; it's a good idea to keep in touch with your fellow translators in your language's translation team in Launchpad and/or the upstream contacts for the software you're translating to tackle such possible difficulties.


[SIZE="5"]**Submitting Code**[/SIZE]

Why not? The Ubuntu core developers and [MOTU]("https://wiki.ubuntu.com/MOTU") almost always have their hands full, and may occasionally need a hand with certain issues. You may also want to have a go at becoming a MOTU hopeful, and eventually, a MOTU; check their wiki page for details. There will also be lots of specs floating around that no core developers or MOTU will be able to work on; you can try your hand at realizing them.


[SIZE="5"]**Doing Design**[/SIZE]

If you do graphics design, you can get involved in one of the Ubuntu-related artwork projects. [Start here]("https://wiki.ubuntu.com/Artwork").


[SIZE="5"]**Writing Documentation**[/SIZE]

If you can write good documentation, you can work with the [Documentation Team]("https://wiki.ubuntu.com/DocumentationTeam"), or by yourself on the [community documentation]("https://help.ubuntu.com/community/").


**[SIZE="5"]Link Upstream Bugs[/SIZE]**

Linking upstream bugs to existing Ubuntu bugs is an important way to help get bugs fixed.

This [blog post by an Ubuntu dev]("http://stompbox.typepad.com/blog/2008/08/feeding-the-har.html") explains why, and [this wiki pag]("https://wiki.ubuntu.com/Bugs/Watches")e shows you how.


[SIZE="5"]**5-A-Day**[/SIZE]

The idea with 5-A-Day is simple - everyone in the Ubuntu community works to tend to at least five bugs every day, and to make it fun, we have produced some tools and rankings to make those 5 bugs count.

See the [5-A-Day wiki page]("https://wiki.ubuntu.com/5-A-Day") for all the info!


**[SIZE="5"]Harvest[/SIZE]**

Ubuntu dev Daniel Holbach has created a tool to help find and fix the so-called "low hanging fruit," bugs that should be easy to fix that might be lost among the thousands of bugs in Launchpad. He explains it [here]("http://daniel.holba.ch/blog/?p=139").

[Check it out]("http://daniel.holba.ch/harvest/"). It's a great place for future MOTUs and aspiring developers to start.


(This guide originally was produced by 23meg in the Gutsy cycle. Since, andrewsomething refreshed it and many other people have contributed to it. Please add any additional information that you think is important for people to know about in the comments. Thanks!)

---

### Post by Gina on 2008-11-29
Thank you for posting that - it should be a big help to those just embarking on Ubuntu testing :)  And maybe even to those already involved :)

---

### Post by Gina on 2008-11-29
[duplicate post]

---

### Post by ubuntu27 on 2009-03-28
I am posting this in to this thread since those who want to contribute or help Ubuntu Jaunty are more likely to visit this thread. Beside the fact that it is sticked.



To the MODs: I have created [another thread]("http://ubuntuforums.org/showthread.php?t=1108507") with the same post. You can delete that one as it is a duplicate. :) Or you can leave like that, if more people see it the better. The decision is yours.


I am copying and paste the message that I have received from the Ubuntu's  [Developer-related announcements and information]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce") mailing list.

*******************Suspend/Resume Call for Testing - Ubuntu 9.04 Beta*********************

Hi Everyone,

With the Ubuntu Jaunty Jackalope 9.04 [Beta release]("http://www.ubuntu.com/testing/jaunty/beta") [1], the Ubuntu
Kernel Team would like to request your assistance with suspend/resume
testing.  

The team has been gathering information about Ubuntu's suspend/resume support for varying pieces of hardware.  If you would like to participate and volunteer to perform tests, the Ubuntu Kernel Team has provided a suspend_test script [2].  The script has been packaged with checkbox 0.7 and should be available with the Jaunty 9.04
Beta release.  The script will perform a number of suspend/resume tests. The first few tests will require human interaction.  In total, the tests should take approximately 30min to complete and will perform 34 suspend/resume cycles.  For information on how to run the script and other details, refer to the [SuspendResumeTesting wiki]("https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting") [3].

Test results are also being tracked on the [Ubuntu wiki]("https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting/Feedback") [4] so please be sure to add any information for hardware that is not yet listed.  Also, feel free to include any additional information for hardware that is currently listed. 

In the event that a test should fail, hooks have been added to apport to automatically detect failures and subsequently file a report in Launchpad.  Upon rebooting the system after a failure, apport will try to gather as much information from the system and guide one through the bug filing process.  Please be sure to also visit the corresponding debugging page [5] which documents additional requested information that apport is unable to gather.  Please include this information in the bug report as well.

The team appreciates all the time and feedback that can be dedicated to
suspend/resume testing and reporting.  Please let us know your results.

Thanks in advance,
The Ubuntu Kernel Team

[1] [http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)
[2] /usr/share/checkbox/scripts/suspend_test
[3] [https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting](https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting)
[4] [https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting/Feedback](https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting/Feedback)
[5] [https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume](https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume)


-- 
ubuntu-devel-announce mailing list
[email]ubuntu-devel-announce@lists.ubuntu.com[/email]
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)

---

### Post by afv on 2009-04-06
> **Nullack said:**
> 
…
[SIZE="5"]**Reporting Bugs**[/SIZE]
… Whenever you encounter a reproducible malfunction in **Intrepid**, [file a bug report]("https://help.ubuntu.com/community/ReportingBugs"). …

Jaunty :P

---

