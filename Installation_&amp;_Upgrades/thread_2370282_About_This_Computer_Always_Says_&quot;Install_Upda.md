---
title: "About This Computer Always Says &quot;Install Updates&quot; Even After Updating"
date: 2017-09-01
forum: Installation &amp; Upgrades
---

### Post by HDTimeshifter on 2017-09-01
When I select the upper right menu, "About This Computer", the panel always comes up with the button in the lower right saying "Install Updates". Even after I click "Install Updates", and it checks, it says "The software on this computer is up to date". But it never changes the button in "About This Computer" to "Up to Date" like it used to. Ubuntu 16.04 LTS.

I've been running Ubuntu for 9 years on another computer (which is now 16.04 LTS as well), and I've never seen this behavior before.

---

### Post by Autodave on 2017-09-01
Are you still running 16.04 on the problem one?

I have one machine that gives me issues like that. If I update it from the command line, it is fine.

In a terminal run:

sudo apt-get update
sudo apt-get upgrade

See if that makes it behave at least for awhile.

---

### Post by HDTimeshifter on 2017-09-01
That fixed it.
Thanks.

---

