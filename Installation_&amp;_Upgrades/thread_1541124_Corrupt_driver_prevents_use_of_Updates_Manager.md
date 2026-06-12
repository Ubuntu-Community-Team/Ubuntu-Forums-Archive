---
title: "Corrupt driver prevents use of Updates Manager"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by CFO on 2010-07-28
I downloaded and installed a label printer driver in deb format. The driver appears to be corrupt and cannot delete or reinstall it. Because of this, Updates Manager also will not work. I get the message "Package in inconsistent state. The package 'ql500cupswrapperinch' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system." 
I tried removing it in Ubuntu Software Center, and was unable to do so. When I attempt to open Synaptic, I get the message "E: The package ql500cupswrapperinch needs to be reinstalled, but I can't find an archive for it." 
When I try to reinstall it using GDebi Package Installer, I cannot install it.
Any suggestions to clear this up would be greatly appreciated.

---

### Post by quixote on 2010-07-31
Fair warning: I haven't used this command myself, so this is just a best guess sort of thing.  Check "man dpkg" (that's the command to type in a terminal) or google dpkg to get a bit more background.

To force removal you'd use something like this:```
sudo dpkg --purge --force-remove-reinstreq ql500cupswrapperinch
```

Hope it works!

---

### Post by CFO on 2010-07-31
Quixote,

Thanks for the suggestion, but no joy. Here is the message I received after the attempt:

dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 168992 files and directories currently installed.)
Removing ql500cupswrapperinch ...
/var/lib/dpkg/info/ql500cupswrapperinch.postrm: 4: /etc/init.d/cupsys: not found
dpkg: error processing ql500cupswrapperinch (--purge):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 ql500cupswrapperinch

As I had said, besides not being able to delete, I am unable to reinstall.

---

### Post by quixote on 2010-08-01
dpkg has to work!  It's not allowed not to work.  ;)

Judging by the error message, it was removing ql500* as per instructions, but in the post-removal cleanup ("postrm" on line 5) it ran into a dependency and quit. Cups is pretty essential, but you don't need cupsys, so the thing may be to try to get it to ignore that. (Again: just guessing!)```
sudo dpkg --purge --force-remove-reinstreq --ignore-depends=cupsys ql500cupswrapperinch
```Possibly you'll need the full path: --ignore-depends=/etc/init.d/cupsys

I don't see anything to force installation, and I'm not sure it would be a good idea even if there were.  I'd concentrate on trying to get dpkg to understand that it should uninstall.  Something I've done on occasion when really desperate is used "find" to find the file and just physically deleted it, and then used synaptic or dpkg to mop up the remains.  But if you remove the wrong things, you could probably wind up in worse trouble that way, so I'm not sure I'd recommend it.

---

### Post by CFO on 2010-08-02
When I ran the command, I got this message: dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 168992 files and directories currently installed.)
Removing ql500cupswrapperinch ...
/var/lib/dpkg/info/ql500cupswrapperinch.postrm: 4: /etc/init.d/cupsys: not found
dpkg: error processing ql500cupswrapperinch (--purge):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 ql500cupswrapperinch

I then added the full path, and got message: dpkg: --ignore-depends requires a legal package name. `/etc/init.d/cupsys' is not; must start with an alphanumeric: No such file or directory


Any further ideas?

---

### Post by quixote on 2010-08-02
Well, combing through the "man dpkg" pages, I found one more option.  Maybe that'll do it:```
sudo dpkg --purge --force-remove-reinstreq --force-bad-path ql500cupswrapperinch
```

:?:

---

### Post by CFO on 2010-08-03
I'm still getting the "error exit status 127" message. I'm starting to think that the gdebi package installer might have gotten corrupted because I got the same message trying to install another app as I get when trying to reinstall ql500cupswrapperinch. I tried uninstalling gdebi installer in the Ubuntu Software Center, so I could reinstall it. but that failed as well.  It may be time to do a reinstall of the OS.

Thanks for offering your suggestions. If nothing else, I learned more about the Linux commands.

---

### Post by quixote on 2010-08-11
Yeah, that's starting to sound really iffy.  If you can reinstall, it would probably be a good idea.

(I just saw your location.  I lived in Billerica when I was about six years old!)

---

