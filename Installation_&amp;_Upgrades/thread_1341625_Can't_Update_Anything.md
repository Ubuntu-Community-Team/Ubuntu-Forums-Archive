---
title: "Can't Update Anything"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by Tinieblas on 2009-11-29
When I open the update manager and click "Check" this error message pops up:

[INDENT]An error occurred

The following details are provided:

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures were invalid: BADSIG 5A9A06AEF9CB8DB0 Launchpad PPA for Ubuntu Wine Team
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/karmic-security/Release](http://security.ubuntu.com/ubuntu/dists/karmic-security/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

[/INDENT]There are some updates listed, so I check them and tell it to install updates and it runs for a while, says it's downloading everything and running everything, then after a long time of it saying that it's doing everything I get this error message:

[INDENT]Update information

Apt Authentication issue

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".

[/INDENT]So I click "Run this action now" and it gives me the first error again. Same thing if I click "Check" again in the update manager.

Any ideas would be appreciated! Thanks!

---

### Post by Tinieblas on 2009-12-07
Nobody knows anything to help me? Every time I turn on my computer I get this same error:

[INDENT]Apt Authentication issue

Problem during package list update. The package list update failed with a authentication failure. This usually happens behind a network proxy server. Please try to click on the "Run this action now" button to correct the problem or update the list manually by running Update Manager and clicking on "Check".

[/INDENT]And like I said before, when I do what it tells me to do I just get more errors...

---

### Post by Tinieblas on 2009-12-09
Well apparently no one knows how to fix this problem... Luckily I just figured it out, so in case anyone else ever has a similar problem, it was actually incredibly simple. I don't know how the config files and everything for Ubuntu work, so I don't know what my fix actually did, but I was trying to update the flash player plugin for Firefox and it kept giving me an error. Finally it popped up a box that said there was a configuration file error and to run this code to fix it:
[INDENT]sudo dpkg --configure -a
[/INDENT]I ran the code in the terminal and it (at least this is what it said it was doing) completely removed the old config files and created new ones. It didn't take too long for it all to finish and then it restarted everything and just like that, it all works. Flash player is updated, the update manager works, I don't get an error when I start my computer, and life is good...

---

### Post by msayed2004 on 2009-12-10
[http://ubuntuforums.org/showthread.php?t=1152619](http://ubuntuforums.org/showthread.php?t=1152619)

:)

---

