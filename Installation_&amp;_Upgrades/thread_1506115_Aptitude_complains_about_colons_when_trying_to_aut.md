---
title: "Aptitude complains about colons when trying to auto-complete a remove operation"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by Surlent777 on 2010-06-10
Well, the title is fairly self-explanatory, so let me just give a live example here, using Celestia as an example:

cory@cory-desktop:~$ sudo aptitude remove celestgrep-status: /var/lib/dpkg/status:61204: expected a colon
.ia

Now, look at the last part. It is able to complete the auto-complete. What's highly annoying is the error message every time I try this. It seems to only affect remove and reinstall operations.

Figuring I could fix this manually, I went and looked at line 61204:

Package: openoffice.org-common
Status: install ok installed
Priority: optional
Section: editors
Installed-Size: 45780
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: openoffice.org
Version: 1:3.2.0-7ubuntu4.1

Obviously, that's more than one line, but I wanted to provide some context. The line in question happens to be the "Installed-Size" section. As you can clearly see, it does indeed contain a colon, and seemingly in quite the appropriate place. I am at a loss. I've tried deleting that whole category there from the status file and reinstalling, but that did nothing of use. Any suggestions?

---

### Post by Surlent777 on 2010-07-29
Bump

---

