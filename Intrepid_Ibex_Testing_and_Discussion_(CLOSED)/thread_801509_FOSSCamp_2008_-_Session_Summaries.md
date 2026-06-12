---
title: "FOSSCamp 2008 - Session Summaries"
date: 2008-05-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by 23meg on 2008-05-20
The past Friday and Saturday, I've attended [FOSSCamp 2008]("http://fosscamp.org/"), which took place in Prague, Czech Republic just before the ongoing Ubuntu Development Summit. 

To quote the definition on [About page]("http://fosscamp.org/About") on the website, "FOSSCamp is a free, open, accessible un-conference event that is designed to help get members from different Open Source projects together to discuss how to work together in different ways". As a lucky attendee, I thought I'd share summaries of the sessions I attended.

**KDE - GNOME Collaboration**

Three sessions were held on this topic, with the attendance of more than thirty KDE and GNOME developers, including some freedesktop.org people. The first session focused on the general notion of "sharing", in an effort to determine what the concrete assets that the two projects can and should directly share are. Common areas in shared APIs (such as the D-BUS API, XESAM) that are up for improvement were highlighted. Another important part of the session was the discussion of data formats that was basically a continuation of previous fd.o discussions. The resolution was that it was a good idea to have a shared data format (for the desktop, themes, icons, etc.), not invent any new URI schemes and try to agree on as few as possible. The outcome of the discussions on sharing of code would be well summed up by David Zeuthen's conclusion that "sharing more code just for the sake of having done so" isn't a good idea, and that the projects should instead focus more on better sharing the D-BUS API. Benjamin Otte's reaction to the topic of the talk at the very beginning also stayed with me: "Does sharing mean doing the same thing?"

**Debian - Ubuntu Collaboration**

[Lucas Nussbaum]("http://www.lucas-nussbaum.net/"), who has been [thinking up new ways]("http://www.lucas-nussbaum.net/blog/?p=281") to enhance inter-distro collaboration in general, and collaboration between Ubuntu and Debian in special for a long time, led this session, which was dominated by the topic of collaboration on sharing and working on bug reports between the two projects.

**Ubuntu Brainstorm and Upstream**

This session was full of constructive debate on the relation of the Ubuntu Brainstorm website and Brainstorm project to various upstream projects, which is two-fold: first, in its current installation at [brainstorm.ubuntu.com]("http://brainstorm.ubuntu.com/"), Brainstorm serves as the Ubuntu project's "idea tracker", and since most ideas are directly dependent on upstream development, Brainstorm discussions are inherently tied to the status and intentions of upstreams, and second, various upstream projects have expressed interest in having their own Brainstorms.

**Ubuntu QA Portal**

Stéphane Graber, Lucas Nussbaum and Henrik Nilsen Omma led this session, which focused on the implementation details of a prospective Ubuntu QA portal, similar to the [Debian PTS]("http://packages.qa.debian.org/common/index.html"), which would provide global bug stats on a per package basis (including a per package version of the [Ubuntu Developer Weather Report]("https://code.launchpad.net/ubuntu-weatherreport")), general bug stats, categorized stats (Apport crash reports, reports with patches attached, reports with Bazaar branches linked) and points of contact for each each package (Ubuntu developer responsible, triagers, mailing list, Debian maintainer). An important priority of the site will be making it easier for upstream developers to get an overview of the status of their software in Ubuntu, and selectively subscribe to different subsets of bug mail (crashers, triaged bugs, normal bugs, etc.).

**Upstream Bug Collaboration**

With the attendance of representatives of various upstreams as well as distribution bug triagers and other QA personnel, this session was reserved to discussions on how bug triage workflows can be improved by better coordination between upstream projects and distributions. Upstream developers from Swfdec, gtkmm, Mozilla, OpenLDAP, KDE and Amarok stated their highly varied preferences regarding the kind and amount of bug mail they'd like to receive from distributions.

Some of the suggestions from the attendees were:

[list][*]having (more) bug days with upstream developer attendance (similar to the [Amarok hug day]("http://gamemank.wordpress.com/2008/03/13/amarok-hug-day-is-done/"))
[*]having more specialized groups of triagers who follow the development of certain upstreams closely and can better triage their bugs
[*]using distributed version control to keep track of the state of the upstream code in various places
[*]including the bug filing preferences of major upstream projects in distribution bug triage documentation[/list]

**Packaging Jam**

The legendary Daniel Holbach held a two hour packaging jam, where he went over the basics of Ubuntu/Debian packaging with a group of MOTU hopefuls, after which he ended up with a to-do list full of action items based on the feedback from the participants on the [packaging recipes]("https://wiki.ubuntu.com/PackagingGuide/Recipes").

**Stable Release Updates**

Led by Murray Cumming, who had previously voiced his concerns about the stable release update policy of Ubuntu which restricted his ability to ship a bug-free version of Glom for a while, this session expanded into a more general discussion of how distributions should adjust their update policies to better accomodate the expectations of a diverse range of upstreams. One conclusion was that distributions had to be more relaxed in their policies regarding stable release updates to software with a low potential of impact in the case of breakage, and could adjust the tightness of their policies per upstream, depending on how responsive they are and how well they can work with the distribution developers. Towards the end, Martin Pitt made a summary of the policy exceptions granted to certain software in Ubuntu so far, and Murray was also happy to know that his concerns had been addressed.

**Collaboration Between Distributions**

In this session, developers from OpenSUSE, Debian, Ubuntu and Fedora reviewed the current state of inter-distro collaboration and came up with various new ideas on how to improve it, some of which were

[list][*]a cross-distro package cross-reference list/database
[*]a single place for upstreams to see the versions and status of their software in all major distributions
[*]continued distribution collaboration meetings, possibly with support from the Linux Foundation
[/list]

**Ubuntu Software Website**

Michael Vogt held this session on a possible "software.ubuntu.com" (that's not necessarily the address, but sums up the idea) website, an online variant of gnome-app-install, that would provide a convenient way for end users to install applications from the official repositories via apturl, presenting screenshots, concise and non-technical descriptions and documentation. Michael Vogt held this session on a possible "software.ubuntu.com" (that's not necessarily the address, but sums up the idea) website, an online variant of gnome-app-install, that would provide a convenient way for end users to install applications from the official repositories via apturl, presenting screenshots, concise and non-technical descriptions and documentation. It was agreed that the site should present an end user oriented subset of the packages only (no libraries, etc.), and that care should be taken in mixing the "download from website, double click, next, next, finish" paradigm and "search in a local application that grabs packages from centralized repositories" paradigm, and the user should be well educated on what exactly is going on. An old prototype posted to the Ubuntu Forums in 2005 was also reviewed as an example.

If you have any questions about the event, let me know. If any attendees are reading this, feel free to add your impressions.

---

