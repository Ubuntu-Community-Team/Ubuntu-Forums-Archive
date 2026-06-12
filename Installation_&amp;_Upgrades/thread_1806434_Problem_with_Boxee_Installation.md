---
title: "Problem with Boxee Installation"
date: 2011-07-17
forum: Installation &amp; Upgrades
---

### Post by sgy on 2011-07-17
I am trying to install Boxee and when I run dpkg I get the following:

```

sudo dpkg -i boxee-0.9.22.13692.x86_64.modfied.deb 
Selecting previously deselected package boxee.
(Reading database ... 177077 files and directories currently installed.)
Unpacking boxee (from boxee-0.9.22.13692.x86_64.modfied.deb) ...
dpkg: dependency problems prevent configuration of boxee:
 boxee depends on libxmlrpc-c3; however:
  Package libxmlrpc-c3 is not installed.
dpkg: error processing boxee (--install):
 dependency problems - leaving unconfigured
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 boxee
```After seeing this I installed libxmlrpc-core-c3-0, libxmlrpc-c3-0, libxmlrpc-core-c3-dev, libxmlrpc-c3-dev, libxmlrpc-client-java, and libxmlrpc-common-java via the Synaptic Package Manager.

I still get the same error.

Here is the corresponding log entry from /var/log/dpkg.log

> 2011-07-17 17:44:54 startup archives install
2011-07-17 17:44:54 install boxee <none> 0.9.22.13692
2011-07-17 17:44:54 status half-installed boxee 0.9.22.13692
2011-07-17 17:44:56 status triggers-pending bamfdaemon 0.2.90-0ubuntu3
2011-07-17 17:44:56 status half-installed boxee 0.9.22.13692
2011-07-17 17:44:56 status triggers-pending desktop-file-utils 0.18-0ubuntu4
2011-07-17 17:44:56 status half-installed boxee 0.9.22.13692
2011-07-17 17:44:56 status triggers-pending python-gmenu 2.30.5-0ubuntu3
2011-07-17 17:44:56 status half-installed boxee 0.9.22.13692
2011-07-17 17:44:56 status unpacked boxee 0.9.22.13692
2011-07-17 17:44:56 status unpacked boxee 0.9.22.13692
2011-07-17 17:44:56 trigproc bamfdaemon 0.2.90-0ubuntu3 0.2.90-0ubuntu3
2011-07-17 17:44:56 status half-configured bamfdaemon 0.2.90-0ubuntu3
2011-07-17 17:44:56 status installed bamfdaemon 0.2.90-0ubuntu3
2011-07-17 17:44:56 trigproc desktop-file-utils 0.18-0ubuntu4 0.18-0ubuntu4
2011-07-17 17:44:56 status half-configured desktop-file-utils 0.18-0ubuntu4
2011-07-17 17:44:56 status installed desktop-file-utils 0.18-0ubuntu4
2011-07-17 17:44:56 trigproc python-gmenu 2.30.5-0ubuntu3 2.30.5-0ubuntu3
2011-07-17 17:44:56 status half-configured python-gmenu 2.30.5-0ubuntu3
2011-07-17 17:44:56 status installed python-gmenu 2.30.5-0ubuntu3
2011-07-17 17:44:56 status triggers-pending python-support 1.0.10ubuntu3
2011-07-17 17:44:56 trigproc python-support 1.0.10ubuntu3 1.0.10ubuntu3
2011-07-17 17:44:56 status half-configured python-support 1.0.10ubuntu3
2011-07-17 17:44:56 status installed python-support 1.0.10ubuntu3
Any help is appreciated.

Thanks.

---

### Post by Frogs Hair on 2011-07-17
Take a look at this thread . [http://forums.boxee.tv/showthread.php?t=31960](http://forums.boxee.tv/showthread.php?t=31960)

---

### Post by sgy on 2011-07-17
Fantastic.  That was super helpful, and it worked perfectly.  Thank you very much.

---

