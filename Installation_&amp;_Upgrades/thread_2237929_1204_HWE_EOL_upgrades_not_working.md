---
title: "1204_HWE_EOL upgrades not working"
date: 2014-08-04
forum: Installation &amp; Upgrades
---

### Post by caitifty on 2014-08-04
Hi all

I have a mac mini running ubuntu 12.04.4 server edition and have been getting the login message about the hardware enablement stack (HWE) going out of support on 2014-08-07.  The message offers two solutions: upgrade to 14.04 or installing a newer HWE version.  However, neither option seems to work for me.  Specifically, the message I get is:

```
To upgrade to a supported (or longer supported) configuration:

* Upgrade from Ubuntu 12.04 LTS to Ubuntu 14.04 LTS by running:
sudo do-release-upgrade 

OR

* Install a newer HWE version by running:
sudo apt-get install 

and reboot your system.
```

Starting with upgrading to 14.04, the login message says upgrade by doing 'sudo do-release-upgrade', however on doing so all I get is:
```
Checking for a new Ubuntu release
No new release found
```

The second option, installing a newer HWE also doesn't really help.  As you'll note from the upgrade instructions above, no install candidates are offered following the 'apt-get install' command.  Googling around, I see other people are being given specific install candidates.

Does anyone have any suggestions on (preferably) just updating the HWE or on getting the upgrade to 14.04 to work?

Just to save anyone asking, uname -r gives '3.8.0-42-generic' and lsb_release -d gives 'Ubuntu 12.04.4 LTS'.

Thanks in advance for any suggestions.

Pete

---

### Post by kansasnoob on 2014-08-04
I can only assume that Canonical is on vacation or taking an extended lunch break:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1341320](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1341320)

[https://bugs.launchpad.net/ubuntu-release-notes/+bug/1351826](https://bugs.launchpad.net/ubuntu-release-notes/+bug/1351826)

[http://ubuntuforums.org/showthread.php?t=2237479](http://ubuntuforums.org/showthread.php?t=2237479)

---

### Post by caitifty on 2014-08-05
A long liquid lunch by the looks of it..  Might just wait a month and see if it all settles out then.  Thanks for replying.

---

