---
title: "Ubuntu 12.04 - updating crashes (and damages) the system"
date: 2012-05-27
forum: Installation &amp; Upgrades
---

### Post by Bliepo32 on 2012-05-27
Hello everyone,

I did a clean install of Ubuntu 12.04 using the alternate install cd today. After the install completed I booted the system and proceeded to install all the updates. It crashed during the installation of the updates, returning to a black-white console-like screen, saying there was an error dereffencing a null pointer in the kernel. Then it displayed a few lines of what I think is the stack.

This left me with a damaged system, so I decided to reinstall it after formatting it. I decided it would be wise to update the kernel first and others packages after this, but the system crashed again during the update of the kernel. Same error as before.

How can I solve this problem? Could I try installing the updates from the recovery mode instead? Or is there some other problem?

===EDIT with extra information====
I just did a new clean install of the same system. I did not install any updates and began installing the following software (in the order provided): truecrypt, dnscrypt and teamviewer 7. During the installation of Teamviewer 7 the system crashed once more, in the same way as before. This time I wrote down the error:

```
1079.532904] BUG: unable to handle kernel NULL pointer dereference at      (null)
```
Strange enough the first "[ " seemed to be missing.

---

