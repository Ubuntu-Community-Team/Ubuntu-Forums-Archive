---
title: "Can't update openprinting-ppds-pxlcolor-ricoh (something about untrusted packages)"
date: 2013-03-04
forum: Installation &amp; Upgrades
---

### Post by lordnimon on 2013-03-04
The Update Manager is prompting me to update openprinting-ppds-pxlcolor-ricoh, but when I do so, I get an error message:

> Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.

I've been having this problem for over a week.  How can I fix this?  And how was I able to install this package in the first place, if the updates are untrusted?

---

### Post by Profan on 2013-03-11
I run into the same problem and my solution was to open a terminal and type:

```
sudo apt-get install openprinting-ppds-pxlcolor-ricoh
```
[COLOR=#000000]
When it prompts to, type "y" and enter.

Hope this helps!

[/COLOR]

---

