---
title: "How do I ask to get a program in the repos?"
date: 2009-12-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by CoreyB. on 2009-12-17
What would be the proper way to get a program in the repos?  The programs I would like are [Frostwire]("http://www.frostwire.com/") and [HandBrake]("http://handbrake.fr/").

Thanks.

---

### Post by dino99 on 2009-12-17
Don't know about those progs, but:

- if they are "windoz progs": install wine
- if they are "open linux world": search on getdeb / launchpad.ppa or else (rpm ...) (googling around should return some info)
- else, try a linux clone

---

### Post by VMC on 2009-12-17
> **CoreyB. said:**
> What would be the proper way to get a program in the repos?  The programs I would like are [Frostwire]("http://www.frostwire.com/") and [HandBrake]("http://handbrake.fr/").

Thanks.

[Handbrake]("https://launchpad.net/~handbrake-ubuntu/+archive/ppa") PPA

[Frostwire installation]("https://help.ubuntu.com/community/FrostWire")

---

### Post by SevenMachines on 2009-12-17
see the  [new package requesting guide]("https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages")

---

### Post by CoreyB. on 2009-12-17
> **VMC said:**
> [Handbrake]("https://launchpad.net/~handbrake-ubuntu/+archive/ppa") PPA

[Frostwire installation]("https://help.ubuntu.com/community/FrostWire")

I know that they are available through non official Ubuntu repos, but it would be nice if they were available through the official repos.

EDIT: Both of these packages are already reported [here]("https://launchpad.net/ubuntu/+bugs?field.tag=needs-packaging"), but there doesn't seem to be much progress.

---

### Post by chrisccoulson on 2009-12-17
> **CoreyB. said:**
> I know that they are available through non official Ubuntu repos, but it would be nice if they were available through the official repos.

EDIT: Both of these packages are already reported [here]("https://launchpad.net/ubuntu/+bugs?field.tag=needs-packaging"), but there doesn't seem to be much progress.

There isn't any progress on Frostwire because the issues raised in the needs-packaging bug report have still not been addressed. The source claims to be licensed under the GPL, but they ship pre-compiled libraries in the tarball, with no corresponding source code available anywhere. Frostwire is not legally distributable in its current form. This also ties the source to the specific architecture that these libraries were compiled for (presumably, i386).

That would need to be addressed before it could be distributed by Ubuntu

---

### Post by hikaricore on 2009-12-18
Among the things we'll never see in the repos is pcsx2...
A request was made for it to be added over two years ago, sadly things in repo land move slower than a brick through the human digestive tract.

---

### Post by chrisccoulson on 2009-12-18
> **hikaricore said:**
> Among the things we'll never see in the repos is pcsx2...
A request was made for it to be added over two years ago, sadly things in repo land move slower than a brick through the human digestive tract.

Rather than moaning about it though, why not have a go at packaging it yourself? As a contributor who devotes most of his spare time to Ubuntu, I find comments like yours slightly insulting.

There is a phenomenal amount of packages in Universe to maintain by quite a small group of developers (there are 154 people in the ubuntu-dev group on Launchpad, which includes indirect members through other groups such as motu). The volume of work involved to maintain all these packages currently is quite significant, and, sadly this means that some things will take longer than users would like. Some packages will naturally get less attention than others if there is nobody available that has an interest in working on them.

A quick search on Launchpad [here]("https://bugs.edge.launchpad.net/ubuntu/+bugs?field.searchtext=&orderby=-importance&assignee_option=any&field.assignee=&field.bug_reporter=&field.bug_supervisor=&field.bug_commenter=&field.subscriber=&field.component-empty-marker=1&field.status_upstream-empty-marker=1&field.omit_dupes.used=&field.omit_dupes=on&field.has_patch.used=&field.has_cve.used=&field.tag=needs-packaging&field.tags_combinator=ANY&field.has_no_package.used=&search=Search") shows that there are currently 1707 open packaging requests - those are requests for a particular application to be packaged and added to the archive.

Anyone can get involved with this. If there is anyone interested in helping out, then there is a lot of documentation in the wiki, starting with [https://wiki.ubuntu.com/MOTU]("https://wiki.ubuntu.com/MOTU")

---

### Post by SevenMachines on 2009-12-18
if anyone is wanting to try packaging something themselves i'd just add that there is a lot of VERY good documentation about packaging on the wiki mentioned, including the 'school' section of past irc classrooms. if you need specific advice then the people on irc dev channels are very helpful too (patience of saints :)).

---

### Post by JohnAStebbins on 2009-12-18
A few people have tried packaging handbrake.  The issues with packaging it are not technical, but rather more pragmatic packaging rules vs. handbrake stability and support issues.  The handbrake team strongly discourages dynamic linking system libs for certain of the libraries used in the program for several reasons:
[LIST=1]
[*]certain features in the ui are tied to a specific version of a lib
[*]extensive testing has been done against specific versions of libs
[*]the libs have been patched to add features or fix bugs
[/LIST]

The packaging rules strongly discourage static linking libraries that are available in the repositories.  So there's a catch-22.  The argument has been made that support issues could be directed to the distribution rather than to the handbrake team, but in practice this doesn't work at all.  There have been unofficial builds of handbrake that didn't follow guidelines and the issues invariably end up in handbrake forums.

---

### Post by VMC on 2009-12-18
> **chrisccoulson said:**
> There is a phenomenal amount of packages in Universe to maintain by quite a small group of developers (there are 154 people in the ubuntu-dev group on Launchpad, which includes indirect members through other groups such as motu). The volume of work involved to maintain all these packages currently is quite significant, and, sadly this means that some things will take longer than users would like. Some packages will naturally get less attention than others if there is nobody available that has an interest in working on them.

A quick search on Launchpad [here]("https://bugs.edge.launchpad.net/ubuntu/+bugs?field.searchtext=&orderby=-importance&assignee_option=any&field.assignee=&field.bug_reporter=&field.bug_supervisor=&field.bug_commenter=&field.subscriber=&field.component-empty-marker=1&field.status_upstream-empty-marker=1&field.omit_dupes.used=&field.omit_dupes=on&field.has_patch.used=&field.has_cve.used=&field.tag=needs-packaging&field.tags_combinator=ANY&field.has_no_package.used=&search=Search") shows that there are currently 1707 open packaging requests - those are requests for a particular application to be packaged and added to the archive.

Anyone can get involved with this. If there is anyone interested in helping out, then there is a lot of documentation in the wiki, starting with [https://wiki.ubuntu.com/MOTU]("https://wiki.ubuntu.com/MOTU")

I wasn't aware of this. Thanks for taking the time explain how difficult it is maintaining the repos!

---

### Post by hikaricore on 2009-12-20
> **chrisccoulson said:**
> Rather than moaning about it though, why not have a go at packaging it yourself?

*yawn*

Pcsx2 has been packaged a number of times by a number of third parties and in a number of PPAs.
There is no valid reason why it is not in the repos yet and it has nothing to do with me not packaging it.

I spent a lot of time devoting myself to Ubuntu and helping when and where I could.
Why don't you hop down off your horse and use your damn brain, instead of replying hastily with pointless hostility at someone making a point.

---

### Post by chrisccoulson on 2009-12-20
> **hikaricore said:**
> *yawn*

Pcsx2 has been packaged a number of times by a number of third parties and in a number of PPAs.
There is no valid reason why it is not in the repos yet and it has nothing to do with me not packaging it.

I spent a lot of time devoting myself to Ubuntu and helping when and where I could.
Why don't you hop down off your horse and use your damn brain, instead of replying hastily with pointless hostility at someone making a point.

Just because someone packaged it somewhere in some random PPA doesn't mean that there is zero effort required to get it in to the archive, and doesn't mean there is no valid reason why it is not in the archive either. We don't spend our spare time scouring the internet in the hope of finding some random piece of software we never use, packaged in some obscure PPA, to then review and upload it.

I assume that the request to package pcsx2 which you refer to, submitted over 2 years ago - is this one: [https://bugs.edge.launchpad.net/ubuntu/+bug/103791]("https://bugs.edge.launchpad.net/ubuntu/+bug/103791"). Well, it hasn't just sat there for 2 years because we are slow (which is what you seemed to imply). Nobody has ever requested for the work to be reviewed, by uploading to REVU (as documented in [https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages#Packaging%20it%20yourself]("https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages#Packaging%20it%20yourself")).

You say that you spend a lot of time devoting yourself to Ubuntu, but surely that effort would be better directed at helping progress that packaging request, rather than launching personal attacks at me and criticising the work that we do.

---

### Post by hikaricore on 2009-12-20
> **chrisccoulson said:**
> Rather than moaning about it though, why not have a go at packaging it yourself? As a contributor who devotes most of his spare time to Ubuntu, I find comments like yours slightly insulting.

Lets talk about personal attacks shall we?

I just don't have the patience for this self righteous crap anymore, I put up with too much of it in SCC.
Really doesn't matter to me if you think you won or lost this, as long as you shut up about it things will be over.

I thought I'd happen along and simply point out another request that's gone unpackaged and I had to get this as a response.
How exactly did you think someone would feel about that?  I don't take people shoveling crap in my face ever, ask anyone..

---

### Post by twright on 2009-12-20
Apparently however, in future versions of Ubuntu ppas will have a much more prominent role (like some kind of distributed packaging) - not sure what is would fully entail but the first changes are landing in lucid (which I am running) already.

---

### Post by hikaricore on 2009-12-20
> **twright said:**
> Apparently however, in future versions of Ubuntu ppas will have a much more prominent role (like some kind of distributed packaging) - not sure what is would fully entail but the first changes are landing in lucid (which I am running) already.

That's actually wonderful news, since the ppas use an automated build system  I always wondered why they didn't play a more important role in ubuntu.
I realize there would have to be some overseeing of them to weed out the problematic ones, but without actual packaging concerns it would make the job of a maintainer much easier.
Maybe even have them approved for something beyond the universe/multiverse repos but still something easy to add without having to add 5 dozen ppas.

---

