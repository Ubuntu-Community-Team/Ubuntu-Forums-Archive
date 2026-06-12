---
title: "upgrade could not be completed - said it would restore but now won't start"
date: 2016-09-02
forum: Installation &amp; Upgrades
---

### Post by rachela on 2016-09-02
Got halfway through an upgrade when I got an error message saying it couldn't complete  and that my system may be unable to run. It then said it would restore the original settings and ran for a while longer.
My laptop reset and brought me to my sign in screen, but once I signed in it would blink and then reload the sign in.
So I reset the computer and now it won't even load the sign in.
Ugggggghhhhh.....

Any insight or tips would be greatly appreciated.

Also: I tried running safe mode but I forget my stupid login.

---

### Post by ian-weisser on 2016-09-02
Create a bootable USB on a different machine.
Boot using the USB, and backup all your data to an external device.
Nuke the old system with a full reinstall.
Then restore your data from the external device.

Release-upgrade failures are not easily recoverable without good command line and chroot skills. For most users, days of learning those skills and experimenting are not worthwhile. The fastest way to a working system is to nuke it and restore in one afternoon.

The most common reason for a release-upgrade to fail is non-Ubuntu software left on the system.
Best practice is to uninstall ALL software from non-Ubuntu sources before starting the release-upgrade.
Re-add non-Ubuntu sources and reinstall non-Ubuntu software after the release-upgrade is complete...after checking that you still need the non-Ubuntu version.

---

