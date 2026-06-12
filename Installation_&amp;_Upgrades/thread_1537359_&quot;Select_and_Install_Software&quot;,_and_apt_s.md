---
title: "&quot;Select and Install Software&quot;, and apt sources post install."
date: 2010-07-23
forum: Installation &amp; Upgrades
---

### Post by Plus1Life on 2010-07-23
[SIZE=3]Hello All,

I am new to the Ubuntu Forums. So this is not a new user question so much as, I wasn't sure if it should go here or in Security. Recently my employer and coworkers have expressed desire for me to use a more "Controlled" version of Linux than Debian. I know that is open to many forms of interpretation ,so we don't have to go there. My main operating system for years has been Debian with Red Hat, Fedora, Ubuntu, and CentOS being my secondary flavors (Mostly Virtual). So what better to replace Debian than Ubuntu huh? :D
[/SIZE]
[SIZE=3]My first question deals with my Custom preseed file. It worked great on a USB Startup Disk made from Lucid 10.04 Alternate install. But I am unclear on one thing, even after reading the help documentation. If I set Universe to true, can I then select and install packages from it?
[/SIZE][SIZE=1]```
[COLOR=#000000][FONT=Arial]d-i apt-setup/universe  boolean true
[/FONT][/COLOR]
```[/SIZE]```
[COLOR=#000000][FONT=Arial]d-i pkgsel/include  string aptitude [package] [package] ...[/FONT][/COLOR]
```[SIZE=3]

My next question deals with the Universe Repository. I was lead to believe some of the packages (though community projects) are Security Reviewed and/or have Security Update Packages available in Security. Reading the apt source list after install I see comments that say Security Team _Never _reviews anything in Universe. So are there security releases for Universe? And so these releases mesh with the Security Team?

I could build from source, or manually version control, source audit, dpkg the packages I would use from Universe. But I am sure you can see where this would be greatly time consuming... I also never automatically install Recommends nor Suggestions (edit apt.conf and preseed) so I am used to this kinda thing.

Input :?
[/SIZE]

---

### Post by Plus1Life on 2010-07-23
[SIZE=3]:-k
Well I have one official answer.

[/SIZE][URL="http://www.ubuntu.com/project/about-ubuntu/components"][SIZE=3]http://www.ubuntu.com/project/about-ubuntu/components
[/SIZE][/URL][SIZE=2]Universe Paragraph 2[/SIZE]
> [SIZE=1]
[/SIZE][SIZE=1][COLOR=black]Canonical does not provide a guarantee of regular [COLOR=black]security[/COLOR] updates for  software in the [COLOR=black]universe[/COLOR] component, but will provide these where they are  made available by the community. Users should understand the risk  inherent in using these packages.[/COLOR][/SIZE]

[SIZE=3]So looks like I will have some work to do.

Maybe I shouldn't add Universe to my Repos. But I am left with a lot of software to self manage.
[/SIZE]

---

