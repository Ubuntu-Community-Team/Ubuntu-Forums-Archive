---
title: "Lucid upgrade broke login"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by pinkunicorn on 2010-06-23
I had a working workstation with Karmic. Then I decided to upgrade to Lucid. Bad move, it turns out.

First the upgrade crashed. Just stopped doing something for hours on end, and I eventually had to reboot. After that, I had to apply lots of apt-get and dpkg love to get the machine to book. Now, I *think* I have a Lucid system, at last. Only that it doesn't work where the Karmic system used to...

Our setup uses kerberos and autofs. To begin with, the upgrade lost my /etc/krb5.keytab (making it impossible to log in), but that can be easily replaced.

Now, I can log in, but my home directory doesn't get mounted. In /var/log/auth.log, I get this:

```

Jun 23 11:13:58 pc13477 gdm-session-worker[1801]: pam_krb5(gdm:auth): pam_sm_authenticate: entry (0x0)
Jun 23 11:13:58 pc13477 gdm-session-worker[1801]: pam_krb5(gdm:auth): (user hans) attempting authentication as hans@IFM.LIU.SE
Jun 23 11:14:02 pc13477 gdm-session-worker[1801]: pam_krb5(gdm:auth): user hans authenticated as hans@IFM.LIU.SE
Jun 23 11:14:02 pc13477 gdm-session-worker[1801]: pam_krb5(gdm:auth): pam_sm_authenticate: exit (success)
Jun 23 11:14:02 pc13477 gdm-session-worker[1801]: pam_krb5(gdm:setcred): pam_sm_setcred: entry (0x2)
Jun 23 11:14:02 pc13477 gdm-session-worker[1801]: pam_krb5(gdm:setcred): (user hans) initializing ticket cache FILE:/tmp/krb5cc_121_6wbjNL
Jun 23 11:14:02 pc13477 gdm-session-worker[1801]: pam_krb5(gdm:setcred): pam_sm_setcred: exit (success)
Jun 23 11:14:02 pc13477 gdm-session-worker[1801]: pam_unix(gdm:session): session opened for user hans by (uid=0)
Jun 23 11:14:02 pc13477 gnome-keyring-daemon[1957]: unable to create keyring dir: /home/hans/.gnome2/keyrings
Jun 23 11:14:02 pc13477 gnome-keyring-daemon[1957]: couldn't connect to dbus session bus: /bin/dbus-launch terminated abnormally with the following error: No protocol specified#012Autolaunch error: X11 initialization failed.
Jun 23 11:14:02 pc13477 gnome-keyring-daemon[1957]: gkd_dbus_secrets_startup: assertion `dbus_conn' failed

```

I assume that "unable to create keyring" really means "hey, you don't have any home directory", and I don't know why. I fail to find any log messages that have anything to do with this in /var/log. Are there other places to look?

I also wonder about "/bin/dbus-launch terminated abnormally" since /bin/dbus-launch doesn't even exist. /usr/bin/dbus-launch does, though. Any ideas about this?

I have tried reinstalling the dbus, dbus-x11 and gnome-keyring packages to no avail.

---

### Post by pinkunicorn on 2010-06-23
If I bypass gdm, I can log in, but I don't get any home directory.

On the other hand, I can mount my home directory statically. The normal setup uses autofs, but that has no effect. I suppose this could be the same problem as [https://bugs.launchpad.net/ubuntu/+source/autofs/+bug/573919](https://bugs.launchpad.net/ubuntu/+source/autofs/+bug/573919) but none of the workarounds listed there work.

---

