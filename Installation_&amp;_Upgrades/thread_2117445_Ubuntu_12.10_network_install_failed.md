---
title: "Ubuntu 12.10 network install failed"
date: 2013-02-18
forum: Installation &amp; Upgrades
---

### Post by axbyczdv on 2013-02-18
I am doing Ubuntu 12.10 Auto install, where am using preseed file passed via network (http), and a install repository available on local web server. ([http://192.168.1.100/image/ubuntu1210_x86_64-dvd/repository](http://192.168.1.100/image/ubuntu1210_x86_64-dvd/repository))

Installation failed saying "Installation step failed"
On the console i can see following messages

Mar 20 19:18:49 anna-install: Queueing udeb apt-mirror-setup for later installation
Mar 20 19:18:49 choose-mirror[3575]: DEBUG: command: wget -q [http://192.168.1.100/image/ubuntu1210_x86_64-dvd/repository/dists/quantal/Release](http://192.168.1.100/image/ubuntu1210_x86_64-dvd/repository/dists/quantal/Release) -O - | grep -E '^(Suite|Codename):'
Mar 20 19:18:49 choose-mirror[3575]: INFO: suite/codename set to: quantal/quantal
Mar 20 19:18:49 choose-mirror[3575]: DEBUG: command: wget -q [http://192.168.1.100/image/ubuntu1210_x86_64-dvd/repository/dists/quantal/main/binary-amd64/Release](http://192.168.1.100/image/ubuntu1210_x86_64-dvd/repository/dists/quantal/main/binary-amd64/Release) -O - | grep ^Architecture:
Mar 20 19:18:49 anna-install: Queueing udeb quantal-support for later installation
Mar 20 19:18:49 main-menu[390]: DEBUG: resolver (libc6-udeb): package doesn't exist (ignored)
Mar 20 19:18:49 main-menu[390]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Mar 20 19:18:49 main-menu[390]: INFO: Menu item 'download-installer' selected
Mar 20 19:18:49 net-retriever: Not verifying Release signature: unauthenticated mode enabled
Mar 20 19:18:49 anna[3600]: wget: server returned error: HTTP/1.1 403 Forbidden
Mar 20 19:18:54 anna[3600]: wget: bad address 'security.ubuntu.com'


Mar 20 19:19:27 main-menu[390]: INFO: Menu item 'live-installer' selected
Mar 20 19:19:27 base-installer: error: Could not find any live images
Mar 20 19:19:27 main-menu[390]: WARNING **: Configuring 'live-installer' failed with error code 1
Mar 20 19:19:27 main-menu[390]: WARNING **: Menu item 'live-installer' failed.
Mar 20 19:19:29 main-menu[390]: INFO: Modifying debconf priority limit from 'critical' to 'high'
Mar 20 19:19:29 debconf: Setting debconf/priority to high
Mar 20 19:19:30 main-menu[390]: DEBUG: resolver (libnewt0.52): package doesn't exist (ignored)
Mar 20 19:19:30 main-menu[390]: DEBUG: resolver (ext2-modules): package doesn't exist (ignored)
Mar 20 19:19:30 main-menu[390]: INFO: Menu item 'live-installer' selected
Mar 20 19:19:30 base-installer: error: Could not find any live images
Mar 20 19:19:30 main-menu[390]: WARNING **: Configuring 'live-installer' failed with error code 1
Mar 20 19:19:30 main-menu[390]: WARNING **: Menu item 'live-installer' failed.

Am wondering why installer is trying to download any live-installer from 'security.ubuntu.com', where as am using a local repository ( [http://192.168.1.100/image/ubuntu1210_x86_64-dvd/repository/](http://192.168.1.100/image/ubuntu1210_x86_64-dvd/repository/)). :confused:

---

### Post by schragge on 2013-02-18
Do you preseed *apt-setup/security_host*? If not, I guess debconf uses default value for it.
```

# Select which update services to use; define the mirrors to be used.
# Values shown below are the normal defaults.
#d-i apt-setup/services-select multiselect security, volatile
#d-i apt-setup/security_host string security.debian.org
#d-i apt-setup/volatile_host string volatile.debian.org

```
Try to set
```

d-i apt-setup/services-select select none

```

---

### Post by axbyczdv on 2013-02-18
Thank you for the reply,

I tried your suggestion, but the same failure :(

---

### Post by schragge on 2013-02-18
I don't know the exact syntax. Maybe this will work better
```

d-i apt-setup/services-select multiselect none

```
But I'm afraid that making d-i use your local repository instead of security.ubuntu.com is not enough. See [this post](https://lists.fedorahosted.org/pipermail/cobbler/2012-November/008396.html).

---

