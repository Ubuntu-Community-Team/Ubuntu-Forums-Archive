---
title: "Ubuntu 12.04 LTS LibreOffice upgrade breaks report builder AGAIN"
date: 2013-06-25
forum: Installation &amp; Upgrades
---

### Post by rechapman on 2013-06-25
The most recent upgrade to LibreOffice (1:4.0.4~rc2-0ubuntu1~precise1)  has broken libre-office-report-builder  (1:1.2.3+LibO4.0.4~rc2-0ubuntu1~precise1) AGAIN! Any attempt to execute a  report built under the previous version of LibreOffice or to create a  new report under this version causes LibreOffice to CRASH and exit  without any error message.

I would really really like to use Ubuntu 12.04 for professional and  business applications but this is the 2nd time I have been burned by an  Update Manager update to LibreOffice and have had to move a project back  to Windows!

Is there any way I can revet my Ubuntu 12.04 to the previous version of LibreOffice (i.e. one that works)! :sad:

---

### Post by ajgreeny on 2013-06-25
You could always consider using the version of LO direct from [http://www.libreoffice.org/download/](http://www.libreoffice.org/download/) where three .deb files are available.

Just follow the instructions to install that are on that page.

NB:  Two potential caveats:-
[LIST=1]
[*]I'm not sure how, or even if that direct installed version will be updated. 
[*]I have no idea if the report builder utility of LO is included in that version, but I presume it will be as it seems to be the full version with everything in it.  However, see below for more on that. 
[/LIST]

Regarding report builder, have a look at the LO page at [http://ask.libreoffice.org/en/questions/scope:all/sort:relevance-desc/query:report%20builder/page:1/](http://ask.libreoffice.org/en/questions/scope:all/sort:relevance-desc/query:report%20builder/page:1/) which may help you sort out the problem, which perhaps is not specifically a Ubuntu problem, but an LO one.

---

### Post by TheFu on 2013-06-25
Downloading source or .deb files feels too much like manually managing installs. That is THE main reason I stopped using MS-Windows.  Hopefully, a PPA has been created to make LO install/update management easier.

I did see that 4.0.4 was released - not certain how that tracks to Ubuntu packages, but my 12.04 system (patched Sunday) has LO 1:3.5.7-0ubuntu4 installed.  Seeing any package with "RC" in the name is worrying.  Release Candidates shouldn't be installed by non-developers or non-QA people, IMHO.  Latest code isn't always ... actually ... seldom is a good thing.

---

### Post by ajgreeny on 2013-06-25
The libreoffice ppa (stable version) for 12.04 has just updated today to 4.0.4 from 4.0.3.

It works very well with no problems on my Xubuntu 12.04 64bit system, and has done for a while.

I have no idea about the report builder as I have no need for it, but the package is certainly in the repos for 4.0.4 along with the library package for report builder, however, this seems to be the version that the OP is complaining about, not the default precise repos version.

---

### Post by rechapman on 2013-06-26
> TheFu
> Release Candidates shouldn't be installed by non-developers or non-QA people, IMHO

Thanks for taking the time to reply! Couldn't agree more! ;) Anyone who installs a release candidate in a production system is asking for trouble!

As you know (I'm sure) LibreOffice explicitly recommends against installing pre-release versions on "mission critical" systems.  Canonical has fooled me twice -- Shame on me! ;o

---

### Post by rechapman on 2013-06-26
ajgreeny thanks for taking the time to reply!

At this point I guess there are 3 options:

(1) remove 1:4.0.4~rc2-0ubuntu1~precise1 and (with fingers crossed) download and install version 3.6 from LibreOffice

(2) do (1) above except with version 4.04 from LibreOffice

(3) transition my project back to Windows and wait and see if Update Manager ever comes up with a 'fixed' install (it happened once before but I don't know if the 'fix' was intentional or just a fortuitous accident).

It is really a disappointment but, based on my "upgrade"(sic) experiences, I can not recommend Ubuntu 12.04 LTS for business use or for any projects that have a firm schedule of deliverables! ;(

---

### Post by TheFu on 2013-06-26
> **rechapman said:**
> It is really a disappointment but, based on my "upgrade"(sic) experiences, I can not recommend Ubuntu 12.04 LTS for business use or for any projects that have a firm schedule of deliverables! ;(

Every OS has issues. Every program has issues.  The parts of a program that aren't used by 90% of the end-users are not tested and maintained as well.  Enterprises have known this for years, so before they deploy ANY new "**mission critical**" system/software, they test it carefully with their hardware, software and total systems to ensure there are not any show stoppers.  You'd be surprised how often there are .... from every software vendor you know.  It is just a fact of life.

So to put this in perspective .... libreoffice still works.  It is just a small part, that most people never use, that has a flaw ... on your system. Has anyone else reported the issue? Have you reported it to the libreoffice team through their bug system? [https://wiki.documentfoundation.org/BugReport](https://wiki.documentfoundation.org/BugReport)

Could running OpenOffice solve this issue?  It isn't like running on MS-Windows is really an alternative. There are 10,000 other reasons to stay on Linux after all.

Sometimes we forget all the days that other software, even commercial software, has failed us.  Any software failure is frustrating - even for the developers of the software. Trust me.  LO is a fairly new project after all.

---

### Post by rechapman on 2013-06-27
> **TheFu said:**
> Every OS has issues. Every program has issues.

I've spent (way too much of) my career in Software Testing, Software Quality Assurance, Independent Software Validation & Verification for this to be anything other than a sad fact of life. LOL  (FWIW, I have NEVER installed a Microsoft patch without crossing my fingers and holding my breath until the system successfully reboots -- and then some!!)

I too have been a devoted fan of Linux ever since using a Walnut Creek CD to set up a Slackware/W95 dual boot system in the 90's. Since then I have never been without at least one Linux system -- I went through most of the free Red Hat distributions; a CentOS box is the DNS Server and hosts the central version control repositories on my LAN; the Ubuntu 12.04 LTS is the "fun" system.

That being said -- based on my experience to date with Ubuntu 12.04 LTS, I do not consider it mature enough for business and professional applications (where cost and/or schedules matter) unless one is willing to pay for support or to maintain a non production system to qualify each and every update that Canonical provides through Update Manager.

As we both know TANSTAAFL (especially where software is involved :) ).

---

