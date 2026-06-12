---
title: "problem with the new firefox 1.0.7 instalation"
date: 2005-10-04
forum: Installation &amp; Upgrades
---

### Post by raspa_sete on 2005-10-04
Hi I am having a problem with the upgrade of my firefox browser, when I try to do the upgrade it gives this: (taken from the console)

> 
Preconfiguring packages ...
(Reading database ... 75038 files and directories currently installed.)
Preparing to replace mozilla-firefox 1.0.6-1ubuntu1~5.04ubp1 (using .../mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb) ...
Unpacking replacement mozilla-firefox ...
dpkg: error processing /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace mozilla-firefox-gnome-support 1.0.6-1ubuntu1~5.04ubp1 (using .../mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb) ...
Unpacking replacement mozilla-firefox-gnome-support ...
dpkg: error processing /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb
 var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb


Is the package the problem or something else? I also don't understand why the program has problems overwriting those two files above! what's that broken pipes stuff?

PS: by the way, it seems that I can't access the hoary-backports: main, universe, multiverse and restricted for some days now. Is there something I should know about this?

(the failed instalation on the firefox 1.0.7 broke my firefox 1.0.6, and since I can't access the above repositories I am out of firefox)

---

### Post by darkmatter on 2005-10-04
The unofficial backports are closed since backports are now an official part of Ubuntu. See here for details and for the changes to sources.list
[http://www.ubuntuforums.org/showthread.php?t=71624](http://www.ubuntuforums.org/showthread.php?t=71624)

After updating your repositories, Just mark the broken packages for reinstallation , this usually fixes the problem.

---

### Post by raspa_sete on 2005-10-04
although the link was not that one, I managed to find the thing

[http://www.ubuntuforums.org/showthread.php?t=69681](http://www.ubuntuforums.org/showthread.php?t=69681)

I tried to make the instalation of the new firefox (or upgrade, uninstall/install the 1.0.6 firefox) but got the same error that I pasted above...

---

### Post by raspa_sete on 2005-10-04
hum... I tried to install fluxbox, and I got the same error.

the depackaging was cancelled because:

> trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
dpkg-deb: subprocess paste killed by signal (Broken pipe)

and it's the same when I try to uninstall the firefox 1.0.6...

---

### Post by shizow on 2005-10-04
[QUOTE=raspa_sete]hum... I tried to install fluxbox, and I got the same error.
the depackaging was cancelled because:
and it's the same when I try to uninstall the firefox 1.0.6...[/QUOTE]

i have exactly the same error
how can i repair this using apt?

and i cannot start firefox anymore
with no error coming up

---

### Post by raspa_sete on 2005-10-05
I've managed to do something about this.
I did:

sudo apt-get remove mozilla-firefox

this removed the mozilla-firefox which is the base for the firefox, then I did the same for firefox. note that I couldn't also upgrade mozilla-firefox from 1.0.6 to 1.0.7

then I installed fluxbox: sudo apt-get install fluxbox

then sudo apt-get install mozilla-firefox (this time the 1.0.7 version)

of course not everything is OK, when I tried
sudo apt-get install firefox

I got:
> Reading package lists... Done
Building dependency tree... Done
Package firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package firefox has no installation candidate

which is quite odd, since I though apt would get it from the internet...
enlightenment please!!!

EDIT: I rebooted the PC, and now firefox vanished from the synaptic

---

