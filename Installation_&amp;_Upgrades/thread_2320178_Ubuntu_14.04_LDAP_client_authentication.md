---
title: "Ubuntu 14.04 LDAP client authentication"
date: 2016-04-11
forum: Installation &amp; Upgrades
---

### Post by smurphy_it on 2016-04-11
Good day.  I didn't find a tutorial for Ubuntu 14.04 LDAP Client configuration, so I followed [this]("https://www.digitalocean.com/community/tutorials/how-to-authenticate-client-computers-using-ldap-on-an-ubuntu-12-04-vps") tutorial for Ubuntu 12.04.

In my case, this is what happens.  After I do the ```
sudo apt-get install lbpam-ldap nscd
``` and after editing /etc/nsswitch.conf and pre-pending LDAP to the compat lines, like below:

```

passwd:         ldap compat
group:          ldap compat
shadow:         ldap compat

```

a reboot of the system fails.  Removing "quiet splash" from the boot line, the system boots to a point.  Then it has issues "mounting /tmp", and just sits there... never going any further.

Last few lines are:

```

The disk drive for /tmp is not ready yet or not present.
keys:Continue to wiat, or Press S to skip mounting or M for manual recovery

keys:
* Starting userspace bootsplash                      [ OK ]
* Starting system logging daemon                   [ OK ]
* Stopping userspace bootsplash                    [ OK ]

Pressing S or M has no affect BTW.

mounting /dev/sda1 to /mnt after booting from LIVE media, and removing the LDAP part from /etc/nsswitch.conf allows reboot of the system normally.

```

---

