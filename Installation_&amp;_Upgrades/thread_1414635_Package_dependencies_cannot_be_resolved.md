---
title: "Package dependencies cannot be resolved?"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by WatTwo on 2010-02-23
Well  I have "wine" and i wanted to try the beta to see if a game would run any better.

I did the instructions on how to add it, updated it in the update manager and now when i try to upgrade it this comes up:

> Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time.

Details: Wine
EDIT:  Took alot of forum searching but finally found a solution.

So to anyone else having this problem (alot of unanswered threads about this)

Here is what i did,

Go to the terminal and type:

> sudo apt-get install wine1.2

And that's it :)

---

