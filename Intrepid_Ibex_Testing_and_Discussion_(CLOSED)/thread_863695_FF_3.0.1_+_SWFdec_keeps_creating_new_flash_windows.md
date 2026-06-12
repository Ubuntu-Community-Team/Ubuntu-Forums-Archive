---
title: "FF 3.0.1 + SWFdec keeps creating new flash windows??"
date: 2008-07-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by litemotiv on 2008-07-18
has anyone else already experienced this one? since one of the recent updates firefox keeps creating new popup flash windows for *each* window/tab with flash content being closed or navigated away from. happens here with both swfdec0.6.9 and 0.6.0. it's quite nasty, since trying to close any of the new popups makes the whole thing go down.

(not really sure if it's a firefox or a xulrunner bug actually, i haven't downgraded them - yet)

---

### Post by plun on 2008-07-19
Maybe its about this bug which is resolved upstream

[https://bugzilla.mozilla.org/show_bug.cgi?id=435764](https://bugzilla.mozilla.org/show_bug.cgi?id=435764)


swfdec must probably be upgraded to later version.

Upstream is working with 0.7.2

---

### Post by psyke83 on 2008-07-19
> **plun said:**
> Maybe its about this bug which is resolved upstream

[https://bugzilla.mozilla.org/show_bug.cgi?id=435764](https://bugzilla.mozilla.org/show_bug.cgi?id=435764)


swfdec must probably be upgraded to later version.

Upstream is working with 0.7.2

Here's the same bug on Launchpad, and it also causes instability with Flash 10 beta2: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182)

---

### Post by plun on 2008-07-19
> **psyke83 said:**
> Here's the same bug on Launchpad, and it also causes instability with Flash 10 beta2: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/239182)

Well,  I took the upstream bug from that but it was just about Adobes Flash, the upstream bug is more against swfdec  

Maybe its time to test Free Desktops plugin :)


I also lost version control with Ubuntus versions and bugs.
(Firefox and Xulrunner)

Are we running the fixed version...  :confused:

---

### Post by psyke83 on 2008-07-19
> **plun said:**
> Well,  I took the upstream bug from that but it was just about Adobes Flash, the upstream bug is more against swfdec  

Maybe its time to test Free Desktops plugin :)


I also lost version control with Ubuntus versions and bugs.
(Firefox and Xulrunner)

Are we running the fixed version...  :confused:

1. The upstream bug is a bug with "windowless mode" that was added to the latest swfdec *and* Flash 10 beta 2. This problem is a bug in Firefox's "windowless mode" support (so, the plugins are not to blame). See the Launchpad bug and here: [http://blogs.adobe.com/penguin.swf/2008/07/addessing_wmode_crashes.html](http://blogs.adobe.com/penguin.swf/2008/07/addessing_wmode_crashes.html)

2. Nope, we're not running the fixed version. Firefox 3.0.1 was built from the trunk on 3/7, and the fix for this problem landed in the trunk on 8/7. It may be included in 3.0.2 (I see blocking1.9.0.2? tagged upstream).

---

### Post by plun on 2008-07-19
> **psyke83 said:**
> 1. The upstream bug is a bug with "windowless mode" that was added to the latest swfdec *and* Flash 10 beta 2. This problem is a bug in Firefox's "windowless mode" support (so, the plugins are not to blame). See the Launchpad bug and here: [http://blogs.adobe.com/penguin.swf/2008/07/addessing_wmode_crashes.html](http://blogs.adobe.com/penguin.swf/2008/07/addessing_wmode_crashes.html)

2. Nope, we're not running the fixed version. Firefox 3.0.1 was built from the trunk on 3/7, and the fix for this problem landed in the trunk on 8/7. It may be included in 3.0.2 (I see blocking1.9.0.2? tagged upstream).

Well,  the first one i knows.:)

Ok about the second one.

If Ubuntu-Mozilla team follows Mozillas releases (and Debian unstable)...:confused:

I have also a nightly build on desktop for testing purposes.

---

### Post by psyke83 on 2008-07-19
> **plun said:**
> Well,  the first one i knows.:)

Ok about the second one.

If Ubuntu-Mozilla team follows Mozillas releases (and Debian unstable)...:confused:

I have also a nightly build on desktop for testing purposes.

Well, I think you may have misdiagnosed the original poster's problem - their plugin is detaching from the browser. It may be a related, but the upstream bug causes crashes - not the behaviour litemotiv seems to experience.

The 8/7 nightly build is the best way to test this bug, as per this comment: [https://bugzilla.mozilla.org/show_bug.cgi?id=435764#c27](https://bugzilla.mozilla.org/show_bug.cgi?id=435764#c27)

---

### Post by plun on 2008-07-19
> **psyke83 said:**
> Well, I think you may have misdiagnosed the original poster's problem - their plugin is detaching from the browser. It may be a related, but the upstream bug causes crashes - not the behaviour litemotiv seems to experience.

The 8/7 nightly build is the best way to test this bug, as per this comment: [https://bugzilla.mozilla.org/show_bug.cgi?id=435764#c27](https://bugzilla.mozilla.org/show_bug.cgi?id=435764#c27)

Therefore I wrote "Maybe".....

I haven't seen other swfdec problems except that I tested it myself a few months ago and sound was broken.


The nightly is the latest....:)   Debian Sid for Mozilla..:)

---

### Post by psyke83 on 2008-07-19
> **plun said:**
> Therefore I wrote "Maybe".....

I haven't seen other swfdec problems except that I tested it myself a few months ago and sound was broken.


The nightly is the latest....:)   Debian Sid for Mozilla..:)

Hmm, ok... I notice your penchant for all things bleeding-edge, but the point of testing the 8/7 build (and not anything later) is to see if it fixes that particular bug. Therefore, litemotiv will know with reasonable certainty that it was bug #435764 causing the issue and not something else.

---

### Post by plun on 2008-07-19
> **psyke83 said:**
> Hmm, ok... I notice your penchant for all things bleeding-edge, but the point of testing the 8/7 build (and not anything later) is to see if it fixes that particular bug. Therefore, litemotiv will know with reasonable certainty that it was bug #435764 causing the issue and not something else.

Well.. its still a "maybe", then its up to Litemotiv to judge about it and eventually file a bug.

"Bleeding edge" is rather necessary in this world for finding out...or its just to wait.  Up to the user to use upstream information and/or code or not for fixing issues.  

Firefox  nightly is perfect for testing because its just to unpack a file and run a shell script...

---

### Post by litemotiv on 2008-07-21
> **plun said:**
> 

Firefox  nightly is perfect for testing because its just to unpack a file and run a shell script...

well yes, but in that scenario it doesn't have access to any existing plugins.. i'll wait just a bit for upstream FF to get packaged and see if it solves the issue, thanks for your (and psyke83's) feedback thusfar. ;)

---

### Post by litemotiv on 2008-07-22
update: the firefox build from 2008071816 does not solve the issue. 

i am using swfdec 0.7.0 now though, so it could be that upstream 0.7.2 produces different results.

**correction:** i *am* using swfdec 0.7.2-1, silly me. ;)

---

### Post by litemotiv on 2008-07-22
Launchpad: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/250769](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/250769)

---

