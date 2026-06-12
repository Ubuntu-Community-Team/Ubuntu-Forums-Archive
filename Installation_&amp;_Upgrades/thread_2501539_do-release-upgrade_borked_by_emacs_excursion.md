---
title: "do-release-upgrade borked by emacs excursion"
date: 2024-10-11
forum: Installation &amp; Upgrades
---

### Post by aathan on 2024-10-11
This is at least the third time I've accidentally borked a do-release-upgrade over ssh by selecting the "Z" option during a dpkg config file conflict issue.

I have muscle memory and I don't quite know exactly what sequence of keystrokes I issued. However, I was "looking around" to resolve a config file update after being dropped into a shell using "Z"

I had loaded emacs, and I subsequently had to drop back out to a shell from emacs. I'm pretty sure I hit ^Z at this point, to get back to the shell.

Following this, I believe I did an "fg" to get back to emacs, and did not get the expected behavior.

I may have then hit ^C at this point because nothing was behaving the way I expected (or due to muscle memory).

I realize this description of events is not terribly well determined. However, suffice it to say that the ^C ended up killing the do-release-upgrade, and I then had to terminate some in-flight dpkg processes, and do a dpkg --configure -a to finish the upgrade.

I wish I could re-create the scenario to better describe the issue, but I can't. Therefore I'm posting here.

There's some unfortunate (but possibly necessary) set of choices about signals, terminal screen buffers, interruptibility of the upgrade, etc.
I'm really not sure exactly what happened here, but I'm guessing the ^Z in emacs did not drop me back to the expected shell, and things broke from there.

I'm sure there are plenty of emacs users left out there, and these issues don't seem specific to emacs. If I'm right about this it sure would be nice if the upgrade process (or possibly dpkg?) to set things up for more safety while using the "Z" option to look around.

---

