---
title: "Creating a custom edubuntu spin?"
date: 2013-06-20
forum: Installation &amp; Upgrades
---

### Post by UsernameNumber on 2013-06-20
Hello all, 

I'm working with [a non-profit]("http://www.tunapanda.org/") to create a Linux-based educational platform that hosts local mirrors of online educational materials like Kahn Academy, as well as whatever other educational software we can cram in, for schools in places like rural Kenya where bandwidth can be prohibitively expensive, if there is internet access at all. 

The plan is to start with Edubuntu+LTSP, and add some customizations like trimming the package set, installing the extra courseware we plan to provide, and probably replacing Unity with something more lightweight like XFCE. 

I've been a Linux guy for a long time, but have spent most of that time in Red Hat land, so I'm not as familar with the Debian/Ubuntu ways of doing things like automated installs and repo/package management as I'd like, so I have some questions I wanted to put up here for discussion before I get too deep into this:


[LIST]
[*][This]("https://help.ubuntu.com/community/InstallCDCustomization") is the most up to date doc I can find on creating a custom spin, but it assumes I want to start from stock Ubuntu. Is there an Edubuntu equivalent of the Ubuntu "alternate" installer? Should I be able to substitute the Edubuntu iso for the Ubuntu alt iso in those instructions?
[*]I want to create a local apt repository since our systems won't be able to access the online ones. Can my preseed/late_command script just copy $cdimage/dists to the disk and add it to /etc/apt/sources.list, or is there more to it? [This doc]("https://help.ubuntu.com/community/AptGet/Offline/Repository") has you downloading everything from archive.ubuntu.org, which I can do, but shouldn't everything I need just be on the DVD anyway?
[*]Xubuntu seems to have a nicer XFCE install than Edubuntu. What would be involved in "migrating" xubuntu packages into our custom spin?
[/LIST]

I have plenty more questions where those came from, but I'll leave it there for now. Many thanks to anyone who can help with any of the above, even if it's just linking to an appropriate doc!

By the way, if anyone out there is interested in helping out, especially if you have expertise with this kind of stuff, please let me know and I'll be glad to tell you more!

---

### Post by Bucky Ball on 2013-06-20
You might be better to do some pre-planning and go for a minimal install, install only the packages you want so it is really lightweight, then create a LiveCD of that (create an ISO of your current install). Good luck. 

PS: There is an absolute ton of info out there about how to create an ISO of your current install. You might start with remastersys.

[http://www.dogpile.com/search/web?q=create%20iso%20current%20install%20ubuntu&fcoid=300&fcop=topnav&fpid=2&qlnk=True](http://www.dogpile.com/search/web?q=create%20iso%20current%20install%20ubuntu&fcoid=300&fcop=topnav&fpid=2&qlnk=True)

PPS: If, of course, you are intending to install edubuntu-desktop rather than just the artwork or packages (you can install just bit if you want) then don't bother with the mini install. No point. Just install Edubuntu and work your way down rather than the mini and work your way up.

---

### Post by UsernameNumber on 2013-06-21
Thanks for suggesting remastersys. I should have mentioned that I'd been looking at remastersys as an option, too. It looks like the maintainer [recently abandoned the project]("http://www.geekconnection.org/remastersys/"), though another group [is picking it up]("http://system-imaging.blogspot.com/2013/05/status-of-fork.html"), albeit with some delays. Anyway, that made me wonder enough about the project's future to look elsewhere for solutions, but since there is a remastersys for the current LTS release, I guess there's no harm in using it for now. Thanks for reminding me! :)

---

### Post by Bucky Ball on 2013-06-21
Guess Clonezilla's also an option, though not sure if the right one:

[http://clonezilla.org/](http://clonezilla.org/)

---

