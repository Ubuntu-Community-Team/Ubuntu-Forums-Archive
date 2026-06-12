---
title: "netbook remix upgtade failed at the end but..."
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by jimmy2time on 2010-06-04
... the update manager states I'm up to date on Lucid.

Here are the series of errors I received before the failure message.

I received the following errors during the install.  I was doing this at work so I hopefully caught them all.

Could not install 'b43-fwcutter'
subprocess installed post-installation script returned error exit status 4

Configuring RPM
The database which rpm keeps about installed packages is not usable with the new version.  The old database has been moved to /var/backups. Please read /usr/share/doc/rpm/README.Debian for details.

Then I received this message.  I clicked okay to inform the developers

Sorry, the package for "b43-fwcutter" failed to install or upgrade
You can help the developers to fix the package by reporting the problem

Then it said it could not send the file and then

Could not install the upgrades
 the upgrade is now aborted. Your system could be in an unusable state. A recovery will run now (dpkg -- configure -a ).

The install script appeared to stop, before it ran the clean-up step

So I rebooted the computer and it started up.

Things appear to be working okay.  I was able to reconnect to the wireless network.

There is a new folder, "system tools" that contains a program called KPackageKit, that wasn't there before.

I'm not sure it finished properly and I wonder what I can check or do next.

thanks

---

