---
title: "Errors were encountered while processing"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by Robby23 on 2008-04-05
I get these errors when I run the command

sudo apt-get -f install

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
6 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up gettext (0.16.1-2ubuntu3) ...
install-info: unrecognized option `--description='
        Try `install-info --help' for a complete list of options.
dpkg: error processing gettext (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of intltool-debian:
 intltool-debian depends on gettext; however:
  Package gettext is not configured yet.
dpkg: error processing intltool-debian (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of po-debconf:
 po-debconf depends on gettext (>= 0.16); however:
  Package gettext is not configured yet.
 po-debconf depends on intltool-debian (>= 0.34.2+20060512); however:
  Package intltool-debian is not configured yet.
dpkg: error processing po-debconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of debhelper:
 debhelper depends on po-debconf; however:
  Package po-debconf is not configured yet.
dpkg: error processing debhelper (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of alien:
 alien depends on debhelper (>= 3); however:
  Package debhelper is not configured yet.
dpkg: error processing alien (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gambas:
 gambas depends on alien; however:
  Package alien is not configured yet.
dpkg: error processing gambas (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gettext
 intltool-debian
 po-debconf
 debhelper
 alien
 gambas
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

When I try and reinstall the packages in synaptic i get the following:

```
E: gettext: subprocess post-installation script returned error exit status 1
E: intltool-debian: dependency problems - leaving unconfigured
E: po-debconf: dependency problems - leaving unconfigured
E: debhelper: dependency problems - leaving unconfigured
E: alien: dependency problems - leaving unconfigured
E: gambas: dependency problems - leaving unconfigured

```

Anyone know whats going on?

---

### Post by prshah on 2008-04-05
> **Robby23 said:**
> 
```
E: gettext: subprocess post-installation script returned error exit status 1

```


All your problems seem to be starting with gettext. why not try ```
 sudo apt-get -f install gettext
```. (I think it is being run with some invalid option). If you still get an error message, the contents of ```
cat /var/log/messages | tail -15
``` will be helpful.

---

### Post by Robby23 on 2008-04-05
contents of cat /var/log/messages | tail -15:

```
Apr  5 02:04:38 robby-laptop kernel: [   74.080000] NET: Registered protocol family 17
Apr  5 02:04:40 robby-laptop kernel: [   75.196000] SoftMAC: Open Authentication completed with 00:18:f8:de:60:e5
Apr  5 02:04:40 robby-laptop kernel: [   75.208000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Apr  5 02:04:55 robby-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.domain_name
Apr  5 02:04:55 robby-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_domain
Apr  5 02:04:55 robby-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.nis_servers
Apr  5 02:08:13 robby-laptop kernel: [  289.120000] ieee1394: raw1394: /dev/raw1394 device initialized
Apr  5 02:08:14 robby-laptop kernel: [  289.248000] NOTE: The dv1394 driver is unsupported and may be removed in a future Linux release. Use raw1394 instead.
Apr  5 02:23:51 robby-laptop -- MARK --
Apr  5 02:43:51 robby-laptop -- MARK --
Apr  5 02:46:12 robby-laptop kernel: [ 2567.444000] audit(1207377971.946:4):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=11120 profile="/usr/sbin/cupsd"
Apr  5 03:03:51 robby-laptop -- MARK --
Apr  5 03:23:51 robby-laptop -- MARK --
Apr  5 03:43:52 robby-laptop -- MARK --
Apr  5 04:03:52 robby-laptop -- MARK --

```

---

### Post by Robby23 on 2008-04-05
edit: oops posted twice

---

### Post by Robby23 on 2008-04-06
Anyone?

---

### Post by Robby23 on 2008-04-09
Anyone?

---

