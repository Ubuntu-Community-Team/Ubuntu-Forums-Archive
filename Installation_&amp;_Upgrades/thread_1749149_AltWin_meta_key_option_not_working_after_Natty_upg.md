---
title: "Alt/Win meta key option not working after Natty upgrade"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by ksix on 2011-05-04
After upgrading to Natty, my Alt/Win meta key option is no longer working.
I'm using System Settings -> Keyboard -> Layouts -> Options -> Alt/Win key behavior
and selecting "Meta is mapped to Win keys".

However the Win key still just pops up the files-and-folders window, and meta is not there.
This worked fine in 10.10.  Need this with Emacs...

Any ideas?

---

### Post by lechien73 on 2011-05-04
If you run:

```
unity --replace
```

from a terminal window, does the Alt/Win key behaviour work as expected, or does the problem remain?

---

### Post by ksix on 2011-05-04
That prints out a couple pages of errors and then segfaults.

And afterwards the alt/win keys still behave the same.

---

### Post by lechien73 on 2011-05-04
Ok, I was wondering if it was another manifestation of this bug: [https://bugs.launchpad.net/unity/+bug/729007](https://bugs.launchpad.net/unity/+bug/729007)

Perhaps if you go into System Settings, CompizConfig Settings Manager and disable, then re-enable the Unity plugin - does that make any difference? Even if it did, this would only be a workaround.

If the CCSM isn't available in System Settings, you can install it by typing:

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by ksix on 2011-05-04
Disabling and re-enabling the Unity plug-in didn't help, but...

while I was in there I noticed a "key to show the launcher" option
If I change that from <super> to disabled, then my meta key works!

Looks like the launcher hotkey kills the "Meta is mapped to Win keys" option.
Seems like a bug...

---

