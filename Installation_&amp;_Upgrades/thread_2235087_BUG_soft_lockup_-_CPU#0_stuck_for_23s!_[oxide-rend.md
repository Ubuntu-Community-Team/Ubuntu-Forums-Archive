---
title: "BUG: soft lockup - CPU#0 stuck for 23s! [oxide-renderer:7556]"
date: 2014-07-18
forum: Installation &amp; Upgrades
---

### Post by hottarod on 2014-07-18
Finally got 14.04 to clean install today from a live cd but the live cd did not install properly.  There were some 295 packages that did not install from the live cd install process.  I had to finish it up under terminal using apt-get.  Once that was done I began to get a plethora of errors with the message that is listed in the title box.  By trial and experimentation I discovered that simply installing **oxideqt-codecs-extra:i386**, the problem went away.  I'm running 64 bit and the 64 bit version of Ubuntu 14.04 was installed.  I have no clue why this fixed it but perhaps somebody should investigate the issue.

Cheers from Texas;
Mac.

---

### Post by grahammechanical on 2014-07-18
The architecture of 64bit CPUs is backward compatible with the architecture of 32 bit CPUs. So, we can install and run Ubuntu 32 bit (i386) on a 64 bit CPU. We can also install and run 32 bit applications on Ubuntu 64 bit (amd64). To make these 32 bit applications more efficient Ubuntu has what are called multiarch libraries.

So, what is this Oxide thingy? I find that difficult to explain because I an ignorant of this kind of stuff but to put it simply, Ubuntu developers are moving away from Webkit and over to Oxide.

> [COLOR=#444444][FONT=Ubuntu]Oxide is a library that allows you to embed a Chromium-powered webview in QML applications.  It currently provides a fairly trivial API that is quite similar to the current QML QtWebkit webview API for simple use cases, although it is nowhere near feature complete yet.[/FONT][/COLOR]

[http://www.chriscoulson.me.uk/blog/?p=196](http://www.chriscoulson.me.uk/blog/?p=196)

Which it seems is proving useful for Ubuntu phones and tablets. There is even a Ubuntu Web Browser (Browser) that is making use of Oxide. It is installed by default on 14.04. As you know over the next year or so the Ubuntu phone/tablet code base will be converged into the Ubuntu desktop code base. So, future Ubuntu releases will get more of this kind of stuff.

Why Ubuntu did not install properly I do not know. How you were able to fix a broken install using the terminal I do not know. And why you should get that error I do not know. I have done many installs of Ubuntu and I have never seen that error.

I am running 64 bit Utopic Unicorn and that has oxideqt-codecs installed but not oxideqt-codecs-extra.  So, why your system should need it I have no idea. But this is a user forum. We are often ignorant of the doings of the developers.

Are you sure that those 295 packages were not simply updates to 14.04 that have been put in the archive since 14.04 was released? That does not mean that the install did not install properly. The download ISO image is an build of the code as it was on 14.04 release day.

Oh, by the way, if I run Ubuntu Web Browser it freezes the desktop. sounds like a soft lockup if you ask me, but I get no error message. I have to do a hard power off. Perhaps I should install oxideqt-codecs-extra.

Regards.

---

