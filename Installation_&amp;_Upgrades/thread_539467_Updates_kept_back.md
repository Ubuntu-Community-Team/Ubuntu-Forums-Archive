---
title: "Updates kept back"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by jim_p on 2007-08-31
Here is the story:
Last night I saw that wine was recently updated to 0.9.44 so I decided to update mine.
I un-commented the wine's repository line in my sources.list and issued a 

sudo apt-get update && sudo apt-get upgrade 

from the terminal.This updated wine and some nvidia stuff along with something named restricted modules.
All went ok, so I re-commented out wine's repository.

Earlier this morning, I ran the same thing again and I was prompted for 1 update,
something containing linux-something. It was just a tiny little ~20kb update.
I updated that too and I ran the same thing again to make sure there are no updates

Then i got this message (in plain translation from Greek) :
```
The followin packages will remain as they are
  linux-image-386 linux-restricted-modules-386
0 updated, 0 newly installed, 0 to be removed and 2 are not updated.
```

Should I worry about that? I mean, I wouldn't mind if it was for gxine or bmp not being updated,
but it says LINUX on, and that is enough to make me nervous!

---

### Post by mckryptyk on 2007-08-31
I don't think you should worry.

It usually just means that there are dependencies for those packages that haven't made it into updates yet.

Just wait and in time they will.

Cheers.

---

### Post by jim_p on 2007-08-31
Oh! Thank you for your reply
That relieved me somehow

---

