---
title: "Brave browser install on 18.04.3 LTS"
date: 2019-12-17
forum: Installation &amp; Upgrades
---

### Post by cam17 on 2019-12-17
When I go to "Ubuntu Software" I do not see Brave browser. This is on a new install  on a desktop. A previoous install had the web browser software "brave"

Why is it missing?

---

### Post by SeijiSensei on 2019-12-17
Install it from brave.com. If you follow the instruction for 14.04+, it will be added to your repository list and automatically updated when needed.

---

### Post by cam17 on 2019-12-17
Why is it not available in the Canada repository anymore? Was it removed?

---

### Post by Skaperen on 2019-12-17
just guessing, it was probably moved to a PPA.

---

### Post by deadflowr on 2019-12-18
It was never available in the official Ubuntu apt repositories.

It has always been available as a 3rd party install.
(PPAs are something unique and different among 3rd party packages, a PPA is more or less exclusive to launchpad.)

Brave installation basics 101:
[https://brave-browser.readthedocs.io/en/latest/installing-brave.html#linux]("https://brave-browser.readthedocs.io/en/latest/installing-brave.html#linux")
other notes:
[https://support.brave.com/hc/en-us/articles/360018666072-How-do-I-install-Brave-on-Linux-using-the-terminal-]("https://support.brave.com/hc/en-us/articles/360018666072-How-do-I-install-Brave-on-Linux-using-the-terminal-")



FWIW, Brave is a snap package but it doesn't seem to show in search results anymore.
But if you open a terminal and run
```
snap info brave
```
it'll show the brave snap information page.
But running
```
snap find brave
``` just says no matching snaps for brave.

Interesting is if you go to the online snap store the search results for brave is this:
[https://snapcraft.io/search?q=brave]("https://snapcraft.io/search?q=brave")

However if you use a web search you'll find this page:
[https://snapcraft.io/brave]("https://snapcraft.io/brave")

But all moot to me as the snap now tries to push users to follow the linked instructions I posted and install the 3rd party apt versions repository method instead.

---

