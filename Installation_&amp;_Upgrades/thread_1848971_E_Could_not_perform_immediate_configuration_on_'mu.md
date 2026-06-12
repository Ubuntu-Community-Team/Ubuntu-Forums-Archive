---
title: "E: Could not perform immediate configuration on 'multiarch-support'"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by pndragon on 2011-09-23
Why do I need multiarch support on 32bit??? How do I enable it?

This message is driving me nuts:

```
E: Could not perform immediate configuration on 'multiarch-support'. Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
```
man apt.conf:
```
       Immediate-Configure
           Defaults to on which will cause APT to install essential and
           important packages as fast as possible in the install/upgrade
           operation. This is done to limit the effect of a failing dpkg(1)
           call: If this option is disabled APT does treat an important
           package in the same way as an extra package: Between the unpacking
           of the important package A and his configuration can then be many
           other unpack or configuration calls, e.g. for package B which has
           no relation to A, but causes the dpkg call to fail (e.g. because
           maintainer script of package B generates an error) which results in
           a system state in which package A is unpacked but unconfigured -
           each package depending on A is now no longer guaranteed to work as
           their dependency on A is not longer satisfied. The immediate
           configuration marker is also applied to all dependencies which can
           generate a problem if the dependencies e.g. form a circle as a
           dependency with the immediate flag is comparable with a
           Pre-Dependency. So in theory it is possible that APT encounters a
           situation in which it is unable to perform immediate configuration,
           errors out and refers to this option so the user can deactivate the
           immediate configuration temporarily to be able to perform an
           install/upgrade again. Note the use of the word "theory" here as
           this problem was only encountered by now in real world a few times
           in non-stable distribution versions and was caused by wrong
           dependencies of the package in question or by a system in an
           already broken state, so you should not blindly disable this option
           as the mentioned scenario above is not the only problem immediate
           configuration can help to prevent in the first place. Before a big
           operation like dist-upgrade is run with this option disabled it
           should be tried to explicitly install the package APT is unable to
           configure immediately, but please make sure to report your problem
           also to your distribution and to the APT team with the buglink
           below so they can work on improving or correcting the upgrade
           process.
```

Any assistance would be greatly appreciated!!!

---

### Post by pndragon on 2011-09-27
Reinstalled again.

---

### Post by sicotico on 2011-10-12
> **pndragon said:**
> Reinstalled again.

Thaks but reinstall the SO or the package with this error

---

