---
title: "disabled on upgrade to hirsute hirsute"
date: 2021-04-27
forum: Installation &amp; Upgrades
---

### Post by jgw on 2021-04-27
I just upgraded a machine from 20.10 to 21.04  I then went to software & updates to check my ppa's  Found a pile of them with "disabled on upgrade to hirsute hirsute" as a comment.  I then went to the Y PPA manager and ran "Re-Enable working ppa's".  It fixed all but one: deb [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu) groovy main  The problem, I think, is that this one was "disabled on upgrade to groovy" which, I guess, was either missed when I went to groovy or which is just bad.  

What should I do?  (my thought is to just delete it and add it but don't know if that will work.

Thank you.................

---

### Post by CelticWarrior on 2021-04-27
Delete it and don't add it because it doesn't support 21.04 yet.
And there's really no point anyway. An enough up-to-date version is in the normal repositories and you can install newer snap versions.

---

