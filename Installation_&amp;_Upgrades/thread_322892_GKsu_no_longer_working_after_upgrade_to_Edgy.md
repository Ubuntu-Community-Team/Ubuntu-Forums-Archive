---
title: "GKsu no longer working after upgrade to Edgy"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by ukch on 2006-12-21
After upgrading to Edgy, it seems that my GKsu no longer works. When I enter my password correctly, it says 'Incorrect Password... Try again'. However, sudo still works absolutely fine. Can anyone help me?

---

### Post by aysiu on 2006-12-22
Can you use *gksudo nautilus* from the terminal, try to enter your password, and then post the terminal output back here?

---

### Post by ukch on 2006-12-26
Trying GKsudo did seem to work, although it output the following:

```
(gksudo:7926): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
(nautilus:7930): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:7930): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
```

However, selecting an administrative application from the menu uses *gksu* instead. The login window to this looks different (offers to save my password in the keyring/session) and doesn't work. Output from *gksu nautilus* is:

```

(gksu:8270): GConf-CRITICAL **: gconf_value_free: assertion `value != NULL' failed
Sorry.
sn_launcher_context_initiate called twice for the same SnLaunchContext

```

This is after entering my password once and cancelling the second time. I'm reckoning that the problem isn't with *gksu*, which (assuming it works the same as *su*) shouldn't work at all. The problem is in fact that the desktop is calling *gksu* instead of *gksudo*. Do you think my diagnosis is correct? Also, do you have any idea how to correct the problem?

---

### Post by ukch on 2007-01-05
*bump* (hopefully that's allowed)

Ideas, anyone?

---

