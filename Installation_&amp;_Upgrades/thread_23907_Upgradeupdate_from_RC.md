---
title: "Upgrade/update from RC"
date: 2005-04-04
forum: Installation &amp; Upgrades
---

### Post by bkgwatfiv on 2005-04-04
Maybe a foolish question, but if I install (as I have) the Hoary Release Candidate now and then to an apt-get update (or something) after the actual release, will I be updated to the new release?  

Put another way, since a new release is days away, is there any advantage to waiting to install until this is out or can I go ahead with confidence in the fact that automatic updates will solve any final issues?

Thanks and sorry if this is a foolish question

---

### Post by Xian on 2005-04-04
If you've installed Hoary RC then you are set. Just issue this command to upgrade your system to the final release when it is announced:

$ sudo apt-get dist-upgrade

---

### Post by grendelkhan on 2005-04-04
And it should actually be updating almost every day anyways.  I installed ages ago and I get shiny new versions of stuff constantly.

---

### Post by GeneralMacsimus on 2005-04-05
Let me add a possibly foolish followup question: to upgrade from Hoary RC to Hoary final, do you need to do:

$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get dist-upgrade

or **just** the final command, as Xian suggested?

---

