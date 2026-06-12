---
title: "The list of changes is not available yet."
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by rusty0101 on 2008-05-13
8 updates in my queue this morning, seven of them have a 'updates' field that reads: 
```

The list of changes is not available yet.
Please try again later.

```

Considering this is on an LTS platform, and the packages I see those notes on are:
```

cpp
g++
gcc
gij
libgcj-bc
libgcj-common
mozilla-player

```
I'm personally a little concerned about why someone wants to update compilers, and bytecode interpreters, and isn't putting a reason into the update packages to what the problem these things are supposed to be addressing. They are all in 'proposed' rather than required, but I'm still concerned.

The only package that has some sort of an explanation is bash. And although it cites a bug that it addresses, I'm not exactly of the opnion that the explanation is 'human readable.'

Not that my message of concern specifically qualifies.

Thank you...

---

### Post by rusty0101 on 2008-05-13
Bad form I suppose to reply to one's own message, but considering the fact that there has been an update to the ssl and ssh stuff today for problems with key creation, I have to state that having packages, even in 'Proposed' that have no information as to what the update affects, or why someone should load the update, does bother me a bit.

I'm making a basic presumption that the packaging system is OK because it is using gpg keys rather than ssh keys for signing, but even without those concerns, putting out packages without having an explanation as to what the updated package provides seems like a generally bad idea.

---

### Post by johann_p on 2008-11-12
I have upgrade manager proposing 32 upgrades to me today and none of them shows a description of what has been changed. "The list of changes is not available" is shown instead. I have waited more than a day but there is still no explanation of what the changes are about.

Is this a bug or what is going on there? Surely there is a reason why update manager propses those changes and surely the affected packages will have an entry in the changelog, so why am I not shown what has been changed?
Among the affected packages are nvidia-settings, f-spot, gedit, gnome-panel, update-manager and others.

---

### Post by lemonberry on 2008-11-12
Same here - updates available but no descriptions.  Sorry to say, but even windoze tells me what I'm updating...

---

### Post by Dazed_75 on 2008-11-12
As a general rule, when I see the list of changes not being available yet, I do not allow the updates to be done.  Generally the description of changes shows up in a day or two.

There have been a few exceptions over the last couple of years (they  do not show up) and then I make a conscious decision one way or the other based on what it is.  On one occasion, I actually deleted the package that was to be updated as I had no use for it anyway.  BTW, then I had update manager do a recheck.

---

### Post by Dazed_75 on 2012-06-15
Ok, here it is 4 years later and this problem seems to be MUCH more common.  There are mostly updates being made available via Update Manager which give no clue what the changes are.  Have we acquired a M$ mentality or what?

---

