---
title: "update to ubuntu 12.10 from 10.04"
date: 2013-10-15
forum: Installation &amp; Upgrades
---

### Post by Javed_iqbal on 2013-10-15
how to update to ubuntu 12.10 from ubuntu10.04.plz tell me.

---

### Post by TheFu on 2013-10-15
10.04 --> 12.04 --> 14.04

Most people should stop there.  12.10 isn't supported anymore (perhaps a week longer).* [update: this is incorrect .. read below]*
12.04 is supported until 2017.

To update between any other versions, the path requires installing each, in turn.  Or just backup your data, settings and program list, then perform a fresh install and restore everything.

Regardless, some things have changed, so be prepared to fix networking.

---

### Post by mörgæs on 2013-10-15
12.10 is supported until april 2014.

---

### Post by Javed_iqbal on 2013-10-15
But how to update this from either terminal or GUI?

---

### Post by TheFu on 2013-10-15
> **mörgæs said:**
> 12.10 is supported until april 2014.

According to this, [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases), > 
Normal Ubuntu releases are supported for 9 months. LTS releases are supported for 5 years. 

But there is a table below ... which confirms the 4/14 support for 12.10. Interesting. Didn't know that support dates were so variable.

Confusing, it is.

The upgrade path from 12.10 to 14.04 will suck.

---

### Post by TheFu on 2013-10-15
> **Javed_iqbal said:**
> But how to update this from either terminal or GUI?

# do-release-upgrade
over and over and over after each update from release to release to release to release. I'd go from 1004 to 12.04 first.
You will want to fix broken things along the way. Be certain to patch completely before doing the release-upgrade too inside each new version.

---

### Post by Bucky Ball on 2013-10-15
If you're running an LTS (10.04 LTS for instance) open update manager and at the top you should see 'A new LTS release is available for install' or something like it. Install 12.04 that way. LTS>LTS. You can leapfrog everything in between. You DO NOT need to upgrade to each one, eg 10.04>10.10>11.04 ... etc.

You shouldn't need to even open a terminal. The option to upgrade to the next LTS should be right there in Update Manager.

Not much point in going to 12.10. It dies the same time 14.04 LTS is released and you can go straight from 12.04 LTS to 14.04 LTS (if you have a reason to, that is).

---

### Post by heir4c on 2013-10-15
And if you get no message about the option for the new LTS, open "Software&Updates" and go to the 3th Tab and on the bottom of the window you can choose to get a message to upgrade to the next LTS.

---

