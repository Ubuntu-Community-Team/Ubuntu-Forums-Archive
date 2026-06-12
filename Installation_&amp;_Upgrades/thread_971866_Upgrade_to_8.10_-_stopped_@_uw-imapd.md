---
title: "Upgrade to 8.10 - stopped @ uw-imapd"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by tfrancov on 2008-11-05
I am upgrading from Hardy to Intrepid. I kicked it off and went home for the night. This morning I am stalled with the following in the terminal part of the distro upgrade window:

>begin>
Setting up  openbsd-inetd (0.20080125-1)...
Installing new version of config file /etc/init.d/openbsd-inetd...
 * Stopping internet superserver inetd
   ...done
 * Not starting internet superserver: no services enabled

Setting up uw-imapd (7:2007b-dfsg-2)...
Installing new version of config file /etc/logcheck/ignore.d.server/uw-imapd...
WARNING: Port "imap3" unselected in debconf but possibly handled locally.
You already have /etc/ssl/certs/imapd.pem
<end<

The system shows no activity, but is responsive. The progress bar shows "About 1 hour 19 minutes remaining" - and has for over 2 hours.

Any help will be appreciated. Thanks in advance.

---

### Post by tfrancov on 2008-11-05
Update:
I killed an instance of /usr/bin/dpkg, and the install choked up an error that went by quickly, and then continued. More info later...

---

