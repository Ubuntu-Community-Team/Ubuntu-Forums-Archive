---
title: "Thunderbird bundled with Ubuntu 8 - Profile problem"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by none-letmebe on 2008-05-07
Dear all, 



In the version of T'Bird I used the profiles were in .thunderbird/<randomname>.default

In the version shipped with Ubuntu 8 these are now in 
.mozilla-thunderbird/<randomname>.default

I copied the profile into the new directory name and started thunderbird, but received the error message:
"Thunderbird cannot start because it is already running"... forgotten rest of error message.

I have removed all files that are either .lock .parentlock
and it made no difference.

I have tried this on three different user profiles, each known to work on the earlier version from two different archives (tar and cpio) so am certain that these are uncorrupted.

I realise that this is not specific to Ubuntu move from version 7 to 8, but since the latest Thunderbird is bundeled with Ubuntu 8, then there is some relevance here for others that run into the same problem.

Any clues about this?

Best regards, LMB

---

### Post by none-letmebe on 2008-05-08
problem solved.
created a new profile in .mozilla-thunderbird.
cd'ed into new profile dir and rm -rf ./*
cd'ed into old profile dir in .thunderbird/<random>.default
find .|cpio -pdm ~/.mozilla-thunderbird/<newprofile>.default
started T'Bird and all was well.

---

