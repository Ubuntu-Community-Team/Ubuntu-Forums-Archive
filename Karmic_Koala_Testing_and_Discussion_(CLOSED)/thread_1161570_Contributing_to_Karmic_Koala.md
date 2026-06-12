---
title: "Contributing to Karmic Koala"
date: 2009-05-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-05-16
Karmic Koala (9.10) will be the eleventh release of our favorite free open source operating system, Ubuntu. With the first Alpha release already out the door, now is a good time to recap what we can do to help make Karmic a quality release.

It has been said that Ubuntu, and the wider FOSS ecosystem contributes in a gift economy. Countless hours of work by human beings across the globe has been gifted to you. All people, of any skill level, have a way to gift back to the ecosystem.


**[SIZE="5"]First Things First[/SIZE]**

*** Get a Launchpad account if you don't already have one.** You'll need it to report and track bugs, do translations in Rosetta, track support requests, and share the karma. Launchpad is an excellent central hub for almost all your contributions to Ubuntu. Register [here]("https://launchpad.net/+login").

*** Familiarize yourself with how Ubuntu development works**, at least roughly. This will help you contribute more efficiently, and prevent many uncalled for misunderstandings. An excellent place to start is the [Ubuntu Development page]("https://wiki.ubuntu.com/UbuntuDevelopment") in the wiki. Even a brief look at the main page will give you a rough idea of how the pieces fit together, and it will help if you go deeper. If the puzzle in your head has missing pieces, don't hesitate to ask questions on how things work. The [Ubuntu Open Week]("https://wiki.ubuntu.com/UbuntuOpenWeek") is also a good opportunity to dive a bit deeper into Ubuntu.

*** Review the [Karmic Release Schedule]("http://ubuntuforums.org/showthread.php?t=1133054")**, to plan ahead when and what you can contribute at this point in the development cycle.

* If you're confused about and/or having too many problems with the development version and don't exactly feel on top of things, don't run it for the time being. The Ubuntu development process is a tough ride, tougher than most distros, due to the cutting edge technology policy and the [fixed development duration]("https://wiki.ubuntu.com/TimeBasedReleases") that's tightly packed with radical changes; if at any point you decide that you can't bear with it, drop it until a more stable phase, a milestone release, or entirely. **Karmic will be a development version until October 2009, and is prone to major breakage at any point. Do not rely on it as your main operating system. If you decide to test it, be aware that you're risking being left without a working operating system, and data loss.**


[SIZE="5"]**Reporting Bugs**[/SIZE]

Bug reporting is one of the most accessible, and yet most beneficial ways in which everyone can contribute. It's a good idea to start reporting bugs as early as possible, since towards the later stages, especially past [BetaFreeze]("https://wiki.ubuntu.com/BetaFreeze"), focus will most likely shift towards critical bugs only. Whenever you encounter a reproducible malfunction, [file a bug report]("https://help.ubuntu.com/community/ReportingBugs"). It's a good idea to start a thread in the development forum before submitting your report, to discuss it with others who may have experienced it, to make sure it's genuine. And it's very important that you do a search for the bug before submitting it; duplicate bugs make life more difficult for everyone. It's practical to keep the URL structure for the source package bug pages (where you can search for bugs in them) in mind:

[INDENT]```
https://bugs.launchpad.net/ubuntu/+source/<sourcepackagename>
```[/INDENT]

Take a look at the [Reporting Bugs page]("https://help.ubuntu.com/community/ReportingBugs") in the wiki to learn more about the procedure. The [best practices wiki page]("https://wiki.ubuntu.com/Bugs/BestPractices") also contains some useful information. Remember, how a bug is initially reported can have a huge effect on how it's handled and how quickly it gets fixed.

[Finding the right package]("https://wiki.ubuntu.com/Bugs/FindRightPackage") is important when filing a bug report. This makes sure that the right developers will see your bug report.

[Apport]("https://wiki.ubuntu.com/Apport") is very handy in gathering technical information for bugs. One way you can use Apport is through the "ubuntu-bug" command. Simply type

[INDENT]```
ubuntu-bug packagename
```[/INDENT]

in a terminal, where "packagename" is the name of the (binary) package you want to report a bug in, and Apport will be triggered to collect basic relevant information (such as release and package versions) and attach it to your report. This [makes life easier for everyone]("http://mdzlog.alcor.net/2009/03/31/please-dont-report-ubuntu-bugs-directly-to-launchpad/") (bug reporters, triagers and developers) by sparing them the time and effort needed for establishing the information Apport can automatically collect through dialogue.

If you've reported a bug directly through Launchpad, and want Apport to collect the information afterwards, use apport-collect:

[INDENT]```
apport-collect bugnumber
```[/INDENT]

will trigger Apport to attach the required information to the bug report you specify with "bugnumber".

When you need to provide in-depth technical information that's beyond the scope of Apport, you'll find the [debugging guides]("https://wiki.ubuntu.com/DebuggingProcedures") useful. The more information in a bug report, the easier it is for a bug triager or developer to get to the bottom for it.

Please keep in mind if you install unsupported software or tweak the configuration items of your install beyond a reasonably supportable state, do not report bugs. In such a case you should be mindful that you are doing your own support of your own configuration. People who want to contribute towards Ubuntu testing need to keep their configuration in a supportable state.

[SIZE="5"]**Triaging Bugs**[/SIZE]

If you have enough dedication to go a step beyond reporting, [this is where you're needed]("https://wiki.ubuntu.com/HelpingWithBugs").

Triaging bugs consists of the following:

[list]
[*] Responding to new bugs as they are filed
[*] Searching for duplicates in the bug tracking system
[*] Forwarding bug reports to their upstream authors, when applicable
[*] Cross-referencing bug reports from other distributions
[*] Classifying bug reports by package
[*] Prioritizing bugs
[*] Expiring old bug reports
[/list]

Since new bug reports never stop coming, there are never enough bug triagers. It's an excellent way to help out that's much appreciated, and it will teach you a lot about how Ubuntu works. Anyone can [help triage bugs]("https://wiki.ubuntu.com/Bugs/HowToTriage"), but you might also want to [join the Bug Squad]("https://wiki.ubuntu.com/BugSquad"). After you've triaged bugs for a while, you can become a member of the [Bug Control team]("https://wiki.ubuntu.com/UbuntuBugControl"), where you'll be allowed to change "Importance" and "Milestone" values of existing bugs.

When triaging, it's important to understand [bug statuses]("https://wiki.ubuntu.com/Bugs/Status"). For instance, confirming a bug means moving the status from new to confirmed, not simply say its confirmed in a comment in the bug.

And regardless of whether you've worked on bugs before or not, don't miss the [Hug Days]("https://wiki.ubuntu.com/UbuntuBugDay")!

**[SIZE="5"]Linking Upstream Bug Reports[/SIZE]**

Linking upstream bug reports to existing Ubuntu bug reports is an important way to help get bugs fixed.

This [blog post by Jorge Castro]("http://stompbox.typepad.com/blog/2008/08/feeding-the-har.html") explains why, and [this wiki page]("https://wiki.ubuntu.com/Bugs/Watches") shows you how.

[SIZE="5"]**Testing ISO Images**[/SIZE]

The [ISO Testing Team]("https://wiki.ubuntu.com/Testing/") tests daily ISO builds that lead to milestone CD images before the milestones are officially out, making sure they work as intended. To join the team and help out, follow the [instuctions on the team's wiki page]("https://wiki.ubuntu.com/Testing/ISO/Procedures"), and apply to [join the team on Launchpad]("https://edge.launchpad.net/~ubuntu-testing").


[SIZE="5"]**Submitting Ideas For New Features**[/SIZE]

[Ubuntu Brainstorm]("http://brainstorm.ubuntu.com/") is the best place for users to suggest new ideas and see what others are talking about.

At the start of each development period, a [developer summit]("https://wiki.ubuntu.com/DeveloperSummit") is held, where plans for the upcoming release are evaluated. The summit for Karmic will be held in Palau de Congressos de Catalunya, Barcelona, Spain between 25-29 May 2009.

Some ideas can be quickly implemented, while others can require a great deal of discussion or development work. Even a seemingly simple idea can be complex to implement if it affects other aspects of the system. Changes to the default look or behavior of the base system are always controversial and may cause extensive discussions.

A minor change can often be described in a bug report. The issue may actually be a bug (a fault in existing software). A simple change can be expressed as a 'wishlist' bug. For more complex changes we need to write a 'blueprint'. Blueprints (a.k.a. "specs") are documents suitable for developers to study and act upon. These should usually only be written by developers actively working on realizing the idea.

Take a look at the list of [existing specs for Ubuntu]("https://blueprints.launchpad.net/ubuntu/") first. If you can write concise, workable specs yourself, go ahead and submit them. If you can't, taking a look at some well written and accepted specs, or the [spec template]("https://wiki.ubuntu.com/SpecTemplate") may help.

A lot of the ideas submitted so far either already have corresponding specs (some being worked on), or have already been proposed in another form by others, so please do a [Brainstorm search]("http://brainstorm.ubuntu.com/advanced_search"), a [spec search]("https://blueprints.launchpad.net/"), and a [forum search]("http://ubuntuforums.org/search.php") to see if what you're proposing has already been proposed by someone else, or is already being worked on.


[SIZE="5"]**Doing Translations**[/SIZE]

Ubuntu puts a special emphasis on the right and ability of all its users to comfortably use Free software in their native languages, so translations have their special place. If you're fluent with a second language beside English, your contribution to translations in [Rosetta]("https://translations.launchpad.net/"), Launchpad's translation module, will be valuable. With Rosetta's web interface, you can translate as much as you want, at any time, in any package.

Make sure you're familiar with the software you translate, for your translations to have as much sensitivity on wording context as possible. The freedom of multiple translators to non-linearly edit translations at will can bring problems with it as well, such as consistency; it's a good idea to keep in touch with your fellow translators in your language's translation team in Launchpad and/or the upstream contacts for the software you're translating to tackle such possible difficulties.


[SIZE="5"]**Bug Fixing, Code and Packaging Work**[/SIZE]

There are various ways and venues through which you can contribute code and packaging work to Ubuntu.

[list][*] [You don't have to be an Ubuntu developer to fix bugs]("https://wiki.ubuntu.com/Bugs/HowToFix"). You can contribute your fixes in the form of patches and branches, which can be reviewed and included in Ubuntu through the [sponsorship process]("https://wiki.ubuntu.com/SponsorshipProcess"). 

[*]Ubuntu developer Daniel Holbach has created a tool called **[Harvest]("http://daniel.holba.ch/harvest/")** to help find and fix the so-called "low hanging fruit", which is, bugs that should be easy to fix that might be lost among the thousands of bug reports in Launchpad. He explains it [here]("http://daniel.holba.ch/blog/?p=139"). It's a great place for aspiring developers to start.

[*] You can [package new software to be included in Ubuntu and Debian]("https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages") (again, no need to be an Ubuntu developer). We're now having regularly scheduled Packaging Training sessions. These are aiming to be short (~15-30 min) hands on sessions followed by questions and answers. Check out [the wiki page]("https://wiki.ubuntu.com/Packaging/Training/") and [the blog]("http://ubuntupackaging.wordpress.com/") for more information.

[*] You can draft, discuss and most importantly, implement [feature specifications]("https://wiki.ubuntu.com/FeatureSpecifications").  

[*] Through sustained contribution, you can become [an Ubuntu developer]("https://wiki.ubuntu.com/UbuntuDevelopers").
[/list]

[SIZE="5"]**Doing Design**[/SIZE]

If you do graphics and user interface design, you can [get involved in one of the Ubuntu-related community artwork projects]("https://wiki.ubuntu.com/Artwork").

[SIZE="5"]**Writing Documentation**[/SIZE]

If you can write good documentation, you can work with the [Documentation Team]("https://wiki.ubuntu.com/DocumentationTeam"), or by yourself on the [community documentation]("https://help.ubuntu.com/community/").


[SIZE="5"]**5-A-Day**[/SIZE]

The idea with 5-A-Day is simple - everyone in the Ubuntu community works to tend to at least five bugs every day, and to make it fun, we have produced some tools and rankings to make those 5 bugs count.

See the [5-A-Day wiki page]("https://wiki.ubuntu.com/5-A-Day") for all the info!

(This guide originally was produced by 23meg in the Gutsy cycle. Since, andrewsomething refreshed it and many other people have contributed to it. Please add any additional information that you think is important for people to know about in the comments. Thanks!)

---

### Post by StooJ on 2009-05-16
> **Nullack said:**
> ... now is a good time to recap what we can do to help make Jaunty a quality release.
[--snip--]

"Jaunty" should be "Karmic" :)

---

### Post by taavikko on 2009-05-17
I smell "sticky"...

Please feel free to delete this message, as this happens.

---

### Post by Nullack on 2009-05-17
23meg says he has some improvements he's editing and I felt that until we kinda have a consensus about the content it wont confuse new users by it being sticky.

---

### Post by andrewsomething on 2009-05-17
Thanks for updating this again, Nullack!

Could you add something to Bug Fixing, Code and Packaging Work for me?

We're now having regularly scheduled Packaging Training sessions. These are aiming to be short (~15-30 min) hands on sessions followed by Q&A.

More info:

Wiki - [https://wiki.ubuntu.com/Packaging/Training/](https://wiki.ubuntu.com/Packaging/Training/)
Blog - [http://ubuntupackaging.wordpress.com/](http://ubuntupackaging.wordpress.com/)

Maybe we could start a wiki page of this post? It would make getting it up with each new release easier and allow for more collaboration.

---

### Post by 23meg on 2009-05-17
> **andrewsomething said:**
> 
Maybe we could start a wiki page of this post? It would make getting it up with each new release easier and allow for more collaboration.

That's what I was thinking as well, but one problem that will make it somewhat less efficient than it can be is that wiki and forum markup differ.

---

### Post by nyarnon on 2009-05-17
Updating right now, thanks for yhe warnin Nullack was very busy setting up a geocache team so I almost missed out on the fun. Lets see what Koala brings us, I find it adorable creatures so lets hope something of that sticks to the distro.:popcorn:

---

### Post by castrojo on 2009-05-17
It'd probably be a good idea to mention ubuntu-bug and apport first and then the web form on launchpad, as the first two get better data and more complete reports.

---

### Post by 23meg on 2009-05-17
> **whiprush said:**
> It'd probably be a good idea to mention ubuntu-bug and apport first and then the web form on launchpad, as the first two get better data and more complete reports.

The web form (I'm assuming you mean [https://launchpad.net/ubuntu/+filebug](https://launchpad.net/ubuntu/+filebug)) isn't mentioned directly anywhere. If you mean the source package page URL, that's meant for searching for / browsing bug reports before attempting to file a new one (probably a good idea to provide a link to the LP plugin for Firefox too). Do you mean mentioning ubuntu-bug before even linking to [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) (which contains ubuntu-bug information as well)?

I'll also post a separate thread dedicated to more detailed bug reporting information.

---

### Post by Gourgi on 2009-05-17
> **23meg said:**
> I'll also post a separate thread dedicated to more detailed bug reporting information.
i think this a better way ;)

---

### Post by Nullack on 2009-05-17
Thanks for all the suggestions folks, and a big thank you to 23meg for his improvements.

I like the idea of a more detailed bug reporting thread. In particular, I think we could go into more detail about how to engage upstream, how to determine if its an upstream issue and generally help out the Ubuntu devs by engaging upstream more.

---

### Post by castrojo on 2009-05-18
> **23meg said:**
> Do you mean mentioning ubuntu-bug before even linking to [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) (which contains ubuntu-bug information as well)?

Ahh, indeed it does, thanks!

---

### Post by ranch hand on 2009-06-02
As you can see from my join date I am real new.

I have Kinky Kitten (9.10) on a partition and am real impressed.

I have one problem that I wasn't sure what to do with and filed a report and followed (or at least tried to) this post.

It may not be a real good bug report but is a lot better than it would have been without this post.  Thank you very much.

---

### Post by Daniel_le_Rouge on 2009-06-10
Hi!

I am a newbie in the whole development topic. Please do not stone me. ;)

I would like to contribute to the development of ubuntu in this release cycle of Karmic Koala. I read a bit in the wiki, but I am still not quiet sure how I can do something. My idea was to install Karmic on my external hard drive and look for bugs to report.

The problem is that I do not get if there is a special way of searching for bugs which are important for this release. During the development of Jaunty I read that there is an automated way of looking for bugs. Is there something like that for Karmic? Or to cut a long story short: Where and how shall I begin when I am looking for bugs?

Thanks a lot,

Daniel

---

### Post by ranch hand on 2009-06-10
Daniel_le_Rouge
Bob Dylan
> 
Everybody must get stoned

Just use 9.10 and use it hard.  Try to overload it.  Have lots of apps open at once.

HAVE FUN.

---

### Post by taavikko on 2009-06-19
Little bit offtopic:

when replying to bug on LP via gmail, is it normal to have long latency before the message appears on LP? or does it ever?

Wrote response to bug, via gmail 15 minutes ago, still haven't appeared on launchpad.
```
recipient	Bug 389340 <389340@bugs.launchpad.net>
date (date)	19. kesäkuuta 2009 9:58
subject	Re: [Bug 389340] Re: firefox-3.5 crashed with SIGSEGV "Save image as" Select destination folder
sender	gmail.com
```

---

### Post by RainCT on 2009-06-20
> **taavikko said:**
> When replying to bug on LP via gmail, is it normal to have long latency before the message appears on LP? or does it ever?


I don't think so. I reply to bugs on GMail quite often and though I don't look at the watch I guess in 5-10 minutes the comment should be there.

---

### Post by taavikko on 2009-06-21
> **RainCT said:**
> I don't think so. I reply to bugs on GMail quite often and though I don't look at the watch I guess in 5-10 minutes the comment should be there.

Somehow my reply address was corrupted and doesn't behave nicely.
All sorted now :)

---

### Post by Merk42 on 2009-06-25
Is there anything I can do to contribute to the **official** artwork?  I was eagerly awaiting changes to Karmic Desktop Artwork, but weeks after UDS it has remained unchanged.

---

### Post by andrewsomething on 2009-06-26
> **Merk42 said:**
> Is there anything I can do to contribute to the **official** artwork?  I was eagerly awaiting changes to Karmic Desktop Artwork, but weeks after UDS it has remained unchanged.

The default artwork is mostly done by Canonical itself, but there are some ways to pitch in. You should checkout [https://wiki.ubuntu.com/Artwork/](https://wiki.ubuntu.com/Artwork/)

One place community contributions might be used in the default artwork is the background: [https://wiki.ubuntu.com/Artwork/Incoming/Karmic/Backgrounds](https://wiki.ubuntu.com/Artwork/Incoming/Karmic/Backgrounds)

You might also want to check out this thread: [http://ubuntuforums.org/showthread.php?p=7520803#post7520803](http://ubuntuforums.org/showthread.php?p=7520803#post7520803)

There are other initiatives for non-default stuff like the community-themes package: [https://wiki.ubuntu.com/Artwork/Documentation/CommunityThemes](https://wiki.ubuntu.com/Artwork/Documentation/CommunityThemes)

---

### Post by Merk42 on 2009-06-26
I know about the community ones, that's why I accented official.
It's just so frustrating seeing the community blueprints so active and the official ones ***seemingly*** dormant.

I'll think about stuff for branding and definitely look into the boot experience.

---

### Post by juancarlospaco on 2009-06-27
im on **Karmic + Gnome Shell + Metacity Compositing + NotifyOSD + EXT4 + UbuntuOne-Client**
its really amazing :)
*no bugs ATM*

---

### Post by taavikko on 2009-09-01
If responding to bug reports.
Use the "affects me too" function.
Don't spam the reports with "mee too"
Pretty useless of the report is already confirmed and worked on.

---

### Post by Claus7 on 2009-09-07
Hello ubuntu community and ubuntu developers,

I'm searching quite sometime in the links of this thread, trying to find out the best way -according to my likes and abilities- in order to help in the ubuntu development. The problem is that, even though there are many guides on the subject, I have to admit that I got lost in the process.

What I would like to do (the order does not indicate importance): 

[LIST]
[*]I would like to translate pages of ubuntu wiki in the hellenic (greek) language. I have seen that the hellenic team is going pretty well on the gnome section, so I do not think that I can contribute much there. For example I have seen wiki pages that they are written in the Hellenic language, yet some links of them are in English. 

[*]I would like to contribute to the building and construction of packages (as a starter at first and in the process as a more experienced user). I think that this process will enhance my knowledge on linux and also provide some help to the community. In this part do you think that another section might be more appealing? For example instead of building packages the updating issue. Should I come in contact with one of the ubuntu developers?
[/LIST]

As far as reporting bugs I think that installing Karmic on one's system, apport is working pretty nicely. Looking at the pages of the bug support I came across some things that I would most like to be clarified to me: 

[LIST]
[*]I have sent via apport notification to the developers both on jaunty and now in karmic. In one of these notifications (in karmic) it required also from me to create an account in launchpad. I did so, yet I didn't know how to continue from there. Is there an explanation about that? Is it really required to use the launchpad, while using apport?

[*]Also it says that apport collects vital information of one's system. Is there a way I can identify which kind of information I'm giving (it might be the root password for example?), and before sending the report to cancel it? I have checked the information collected while apport is running and I have not seen my root password in there. For example I was able to see the type of my graphics card. I do not think that this is something so vital. Is it?
[/LIST]
In all the above I have to mention that I'll be able to contribute during my free time. Even though that means that my contribution will be small, I would gladly do it according to my (humble) abilities.

Excuse my long e-mail or the dummy(?) questions, yet I would be glad if someone could shed more light on these issues for me.

Regards!

---

### Post by 23meg on 2009-09-08
Hi Claus7,

> **Claus7 said:**
> 
I would like to translate pages of ubuntu wiki in the hellenic (greek) language. I have seen that the hellenic team is going pretty well on the gnome section, so I do not think that I can contribute much there. For example I have seen wiki pages that they are written in the Hellenic language, yet some links of them are in English. 

Do you mean translations of the community documentation? Could you post a link? Keep in mind that you can also contribute to Hellenic translations of Ubuntu itself.

> **Claus7 said:**
> I would like to contribute to the building and construction of packages (as a starter at first and in the process as a more experienced user). I think that this process will enhance my knowledge on linux and also provide some help to the community. In this part do you think that another section might be more appealing? For example instead of building packages the updating issue. Should I come in contact with one of the ubuntu developers?


You can contribute to any area of packaging (new packages, updates, package reviews etc.) at any rate you like. Don't hesitate to contact the MOTU team (through the [MOTU mentors mailing list]("https://lists.ubuntu.com/mailman/listinfo/Ubuntu-motu-mentors") or at #ubuntu-motu on [irc]("https://help.ubuntu.com/community/InternetRelayChat").freenode.net); take a look at the [mentoring program information]("https://wiki.ubuntu.com/MOTU/Mentoring") if you need a mentor to guide you.

> **Claus7 said:**
> I have sent via apport notification to the developers both on jaunty and now in karmic. In one of these notifications (in karmic) it required also from me to create an account in launchpad. I did so, yet I didn't know how to continue from there. Is there an explanation about that? Is it really required to use the launchpad, while using apport?

Yes. It sounds as if there's been a problem with Apport or Firefox during your reporting the bug. If you created an account and logged in to Launchpad, the next time you use Apport, it should proceed correctly. 

> **Claus7 said:**
> Also it says that apport collects vital information of one's system. Is there a way I can identify which kind of information I'm giving (it might be the root password for example?), and before sending the report to cancel it? I have checked the information collected while apport is running and I have not seen my root password in there. For example I was able to see the type of my graphics card. I do not think that this is something so vital. Is it?


Apport will not purposefully collect any personal information, including any of your passwords. The sensitive information it mentions is limited to what your crashing applications may contain in their crash dumps; this can include passwords, as well as names of and data from files they're accessing at the time of the crash. However, such bugs will be set as "Private" by default, and will be viewable only by you and Ubuntu Bug Control team members, whom you can trust to remove such information from your bug if they find it before making it public.

> **Claus7 said:**
> In all the above I have to mention that I'll be able to contribute during my free time. Even though that means that my contribution will be small, I would gladly do it according to my (humble) abilities.

Excuse my long e-mail or the dummy(?) questions, yet I would be glad if someone could shed more light on these issues for me.

No worries; don't hesitate to ask further if you have any more questions.

---

### Post by Claus7 on 2009-09-09
Hello 23meg,

thank you for your comprehensive answers! They were really helpful. I'll look them further and act accordingly.

Regards!

---

### Post by 23meg on 2009-09-09
You're welcome; good to know it helps you.

---

### Post by executorvs on 2009-09-18
I know this may not be the best place to ask but I'm in a rush and don't want to forget later.

how much effective hardware testing can be done from a live disc or a persistent usb install? I've got friends who've had issues with their hp tx1000series and tx2500series tablets. I'm also concerned about the extent of functionality on my phenom X3 705e.

I would love to send as much useful info as I can back... I'm just not always sure how to do that when I can't do installs on these machines for various reasons.

I'm installing karmic on my acer timeline 5810T and old toshiba satelite 1905-s301 for my birthday tomorrow.

Everytime I bork an install I get much better in the command line. here's to learning

---

