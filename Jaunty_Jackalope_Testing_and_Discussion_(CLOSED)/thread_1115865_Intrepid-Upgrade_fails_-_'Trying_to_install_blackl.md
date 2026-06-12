---
title: "Intrepid-Upgrade fails - 'Trying to install blacklisted version 'python2.6_2.6.1-1'"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by TroyMcClure on 2009-04-04
Hi,

[Short update: two mistakes in one posting: I meant upgrading from intrepid to jaunty, and I now see that Xubuntu 9.04 is not yet available... But nevertheless, after switching to kubuntu-desktop and deinstalling xubuntu-desktop, the problem persists as before]

hope I can get some help on this problem. This is my first posting here, so in case I'm doing something wrong, just let me know... Forum search did not find any match for my problem so far.

When trying to upgrade from Xunbuntu 8.10 to jaunty, I get the following error message (taken from /var/log/dist-upgrade/main.log):

2009-04-04 12:59:23,212 DEBUG Marking 'kubuntu-desktop' for upgrade
2009-04-04 12:59:23,434 DEBUG Marking 'xubuntu-desktop' for upgrade
2009-04-04 12:59:36,286 ERROR Dist-upgrade failed: 'Trying to install blacklisted version 'python2.6_2.6.1-1ubuntu8''
2009-04-04 12:59:36,288 DEBUG openCache()
2009-04-04 12:59:36,751 DEBUG /openCache()

Any ideas what causes this error? How do I find the package which prevents the upgrade? And how is a package defined as "blacklisted"?

Searching for "blacklisted packages" unfortunately gave me absolutely no results, so I really appreciate any help here to clean up my system. Probably I messed it up myself, but still I'd like to understand how to get out of it again, and why any change would prevent to upgrade to python 2.6.

Thanks!
Martin

(I appended the logs from /var/log/dist-upgrade in case there's more interesting things in there...)

---

### Post by Radulf on 2009-04-04
Hello,

i have the same problem here with Ubuntu.

Ralf

---

### Post by Chickenstein on 2009-04-04
Same here when trying to dist-upgrade from (Ubuntu) Intrepid during the calculation of the changes.

> Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
Trying to install blacklisted version 'python2.6_2.6.1-1ubuntu8'

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.

The logfiles are not very specific here. I removed/purged all "unofficial" packages (at least I think so, a dpkg listing didn't show me any non-ubuntu packages), same result. "Upgrading to a pre-release version of Ubuntu" certainly applies, but that's the point in upgrading :)

Before reporting this bug, any idea, anyone?

---

### Post by cariboo on 2009-04-04
Have you tried in a terminal:

```
sudo apt-get install -f
```

then

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Jim

---

### Post by Radulf on 2009-04-04
Sorry, still the same. No change.

Ralf

---

### Post by Eyeless Blond on 2009-04-04
Getting the same error over here. Obviously we're trying to "upgrade to a pre-release version of ubuntu"... does this mean that we just can't right now? Why is 'python2.6_2.6.1-1ubuntu8' a blacklisted version, and what does that mean?

---

### Post by Eyeless Blond on 2009-04-04
Hmm. Well, I don't know if this is the problem or not, but it looks like python 2.6, the source package that 'python2.6_2.6.1-1ubuntu8' was released under, has been superseded by a new release, but for some reason dist-upgrade is trying to install the older release. Um, so what's the protocol for getting things like this fixed?

Ref: [https://launchpad.net/ubuntu/+source/python2.6](https://launchpad.net/ubuntu/+source/python2.6)

---

### Post by Eyeless Blond on 2009-04-04
On further digging, it looks like the powers that be have temporarily halted upgrades entirely due to some sort of python problem:

[https://bugs.launchpad.net/ubuntu/+source/python-central/+bug/354228](https://bugs.launchpad.net/ubuntu/+source/python-central/+bug/354228)

Looks like this happened yesterday, too.

---

### Post by edwin.galloway on 2009-04-05
Thank goodness: I think this is related to a problem I am having. Whenever I try to install any package (through synaptic or whatever) I get the following error: 

E: python-wxgtk2.8: subprocess post-installation script returned error exit status 1

When I look at the details, if I am reading correctly, I have python 3.0 installed now (I assume from an earlier upgrade) but the package manager is still looking for the older python bits, i.e.:

...
Setting up python-wtgk2.8 (2.8.9.1-0ubuntu5) ...
INFO: using unknown version  '/usr/bin/python3.0' debian_defaults not up -to-date?)
file does not exist: /usr/lib/python2.6/dist-packages/wx-2.8-gtk-unicode/wx/_init_.py

etc., over and over, then:

pycentral: pycentral pkginstall: error byte-compiling files (434)
dpkg: error processing python-wxgtk2.8 (--configure):
 subprocess post-installation script returnes error exit status 1
Errors were encountered while processing:
 python-wxgtk2.8

Does this sound reasonable?

I can't shake the feeling that if I was smarter I could hop into terminal and get this sorted in a jiffy.

---

### Post by Eyeless Blond on 2009-04-05
Well, don't get too excited. All that above is pure speculation; I've no idea if it's correct or not. I don't know much about linux's repository system, or if it even makes sense for a bug in a package to cause the entire distribution update system to be taken deliberately offline; in fact it sounds a little ridiculous, and I suspect I could well be wrong.

Let's see if someone more knowledgeable shows up for comments.

---

### Post by taavikko on 2009-04-05
> **Eyeless Blond said:**
> Well, don't get too excited. All that above is pure speculation; I've no idea if it's correct or not. I don't know much about linux's repository system, or if it even makes sense for a bug in a package to cause the entire distribution update system to be taken deliberately offline; in fact it sounds a little ridiculous, and I suspect I could well be wrong.

Let's see if someone more knowledgeable shows up for comments.

Upgrade intrepid->jaunty were held back for a day or two, due to python issues.

By Michael Vogt
> Hi,
 
 I disabled the upgrades from intrepid to jaunty via the release
 upgrader temporarlly. The rational is bug #354228 that hits everybody
 doing a release upgrade.
 
 The problem is that when python2.6-minimal gets install the rtinstall
 scripts get run. Those scripts are designed to byte-compile files for
 the new python runtime just installed (used by python-support and
 python-central, among others). There was a bug that prevents those
 scripts from being run (and some python modules were not available for
 python2.6 because of this bug).
 
 This bug got fixed yesterday. But the fix trigger the bug mentioned
 above in python-central (#354228 ) and it affects every upgrade from
 intrepid to jaunty. The fix is being worked on and the upgrade should
 be available again by the end of the day.
 
 Cheers,
  Michael

---

### Post by TroyMcClure on 2009-04-05
OK, upgrading now works for me again - but only after changing the update server from de.archive.ubuntu.com to archive.ubuntu.com. Looks like the update needs some time to get distributed to the other servers.

Regarding the not very helpful error message: would it be possible to get a more helpful message, e.g. a link to some web page, where the status of possible errors is displayed? If there had been a place that said "upgrade intrepid->jaunty is currently broken", I would not have wasted several hours on my Saturday on this... At least to me, the "blacklisted" info was not at all helpful...

Anyway, thanks for all the information added to this thread, and the quick solution of the problem. Let's see how the upgraded release looks like ;-)

Cheers,
Martin

---

### Post by Daimonion on 2009-04-06
Hi

I have the same problem.

Today i tried to upgrade intrepid with german archive (de.archive.ubuntu.com) but at the moment it doesn't work. I'll try it with archive.ubuntu.com.

Daimonion

---

