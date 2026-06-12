---
title: "Removing one application removes more applications."
date: 2020-03-10
forum: Installation &amp; Upgrades
---

### Post by thecowmilk on 2020-03-10
HI all, the problem has occurred even before but it wasn't any special case like this one. All started when I tried to install `wine` in my Ubuntu 18.04.1 LTS. I did a simple `sudo install wine` and I hit enter.
I saw it was being downloaded from the repositories and while I was doing other thing on google and something happened. Firefox just was removed from my `favorites` and google icon disappeared.

I went staring at terminal and I was seeing that Ubuntu was removing a lot of packages like following: openjdk, firefox, google, files, settings, kerneloops and many more. The wors part is that I can't download them again because I will get a dependency error which I'm unable to fix. The fun thing is that when I was trying to remove one application by using command: `sudo apt remove --purge <package name>` it said me that more applications would get removed.

Please Help Me. I don't know what to do and why this happens..................... If you leave a message would be great........

---

### Post by TheFu on 2020-03-10
a) do you always run **sudo apt update** first?  Having current package lists and dependencies is very important.

b) do you properly patch the system at least weekly?  **sudo apt upgrade** or **sudo apt full-upgrade**

c) **aptitude** is smarter about dependencies.  If the dependency results aren't to your liking, just say 'N', and the next dependency solution may be better.  Answer 'N' until an alternative you can live with gets provided.

d) If a .deb file was installed directly, that package may be holding back some core package causing dependency issues which cannot be resolved until the .deb package manually installed directly is removed.  Perhaps someone else knows how to determine which .deb files where manually installed, breaking the dependencies.  There are ways, asking APT, to provide a list of dependent packages.

---

### Post by guiverc on 2020-03-11
This looks a lot like [https://askubuntu.com/questions/1216245/removing-one-applications-removes-even-more](https://askubuntu.com/questions/1216245/removing-one-applications-removes-even-more)

Where user535733 concludes

> "[COLOR=#242729][FONT=Arial]This looks like a Debian Jessie system, not Ubuntu at all. You have Debian sources, not Ubuntu sources. That's why you cannot find [/FONT][/COLOR]ubuntu-desktop[COLOR=#242729][FONT=Arial] -- it's not in Debian. I don't know how you installed [/FONT][/COLOR]ubuntu-desktop[COLOR=#242729][FONT=Arial], but mixing Debian and Ubuntu packages is Not Wise. It creates a [/FONT][/COLOR][FrankenDebian]("https://wiki.debian.org/DontBreakDebian")[COLOR=#242729][FONT=Arial] with version conflicts and ends in tears"[/FONT][/COLOR]

---

### Post by thecowmilk on 2020-03-11
So guys I solved it. The solution is in the `askubuntu` link... :D Thanks

---

