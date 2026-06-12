---
title: "Upgrade failing from 11.10 to 12.04 with &quot;Failed to fetch *** Hash Sum mismatch&quot;"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by RoboJ1M on 2012-04-28
Hi,

I'm trying to upgrade my 11.10 box to 12.04 using the update manager

I'm also use apt-cacher-ng, which is set up and working fine for caching updates.

It might just be because the servers are overloaded but I'm getting lots of:

```
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libcamel-1.2-29_3.2.3-0ubuntu6_i386.deb Hash Sum mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/b/brltty/libbrlapi0.5_4.3-1ubuntu5_i386.deb Hash Sum mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/libq/libqtdee/libqtdee2_0.2.4-0ubuntu1_i386.deb Hash Sum mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/a/aptdaemon/aptdaemon_0.43+bzr805-0ubuntu1_all.deb Hash Sum mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/t/telepathy-mission-control-5/telepathy-mission-control-5_5.12.0-0ubuntu2_i386.deb Hash Sum mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/l/launchpad-integration/launchpad-integration_0.1.56_all.deb Hash Sum mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/libs/libsocket6-perl/libsocket6-perl_0.23-1build2_i386.deb Hash Sum mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system-core4.0-cil_2.10.8.1-1ubuntu2_all.deb Hash Sum mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/t/totem/totem-common_3.0.1-0ubuntu21_all.deb Hash Sum mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/strigi/libstreams0_0.7.7-1.1ubuntu3_i386.deb Hash Sum mismatch
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/r/rhythmbox/rhythmbox_2.96-0ubuntu4_i386.deb Hash Sum mismatch
```

Any ideas?

Thanks,

James.

---

### Post by RoboJ1M on 2012-04-29
Well, this is either going to fix it or break it but I changed the sources.list content to:

```
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
deb-src http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse

###### Ubuntu Update Repos
deb http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
deb http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse
deb http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb-src http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
deb-src http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/ precise-proposed main restricted universe multiverse
deb-src http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

```

But at least I'm getting no errors and 500KB/s instead of 20KB/s!

(Generated using [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) and reading about the Ubuntu auto mirror choosing URL [http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/))

J.

---

### Post by RoboJ1M on 2012-05-01
Solved it.

When you use apt-cacher-ng, it's default configuration it to silently redirect all of your package requests to the URL in:
```

/etc/apt-cacher-ng/backends_ubuntu
```

which on my install had defaulted to:

```
http://gb.archive.ubuntu.com/ubuntu/
```

Which is not only slow (20K/s) but broken

I just added the following line to the top of that file:

```
/etc/apt-cacher-ng$ cat backends_ubuntu
http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu/
http://gb.archive.ubuntu.com/ubuntu/

```

Now it goes fast. Shame I figured it out after upgrading both machines, no caching goodness... :(

Now I'm not sure, but I *think* if you just comment out the remap lines in acng.conf, it will just merge and cache requests by the path in their URL!

---

