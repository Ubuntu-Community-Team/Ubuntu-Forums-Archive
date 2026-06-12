---
title: "Ubuntu 9.04 to 9.10 upgrade error: E:Error, pkgProblemResolver"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by iWarior on 2010-06-10
Hello!!!

I have server with Ubuntu Server 8.10.

Some time ago I needed to upgrade one package, in dependences there was newer version **libc6 2.11.1-0ubuntu7** - i get it from lucid repository, it was installed without problems. All worked well. But I have made it in vain...

Later I have noticed that if enter into consoles file name not existing in /bin/ -> **it does not display any error**, in general does not react in any way, some programs precisely also refuse to work - inform nothing, errors, anything.

I have decided to upgrade my Ubuntu consistently (8.10 -> 9.04 -> 9.10 -> 10.4).

Upgrade (over **do-release-upgrade**) has passed normally (uname: 2.6.28-19-server), but in **lsb_release** was data of the my old Ubuntu 8.10... I correct it to 9.04 and try to upgrade again (to 9.10), but upgrading was fail with error:

```
ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
```

Info from apt.log:

```
cat /var/log/dist-upgrade/apt.log | grep broken
```

```
Package upstart has broken dep on libc6
Package netbase has broken dep on upstart-job
Package module-init-tools has broken dep on upstart-job
Package libglib2.0-0 has broken dep on libc6
Package udev has broken dep on upstart-job
Package procps has broken dep on upstart-job
Package initscripts has broken dep on udev
Package mountall has broken dep on libc6
Package cron has broken dep on upstart-job
Package ifupdown has broken dep on upstart-job
Package x11-common has broken dep on upstart-job
Package proftpd-basic has broken dep on proftpd
Package rsyslog has broken dep on upstart-job
Package at has broken dep on upstart-job
Package libglib2.0-data has broken dep on libglib2.0-0
Package ubuntu-minimal has broken dep on rsyslog
Package aolserver4-daemon has broken dep on aolserver4
Package dbus has broken dep on upstart-job
Package ufw has broken dep on upstart-job
Package mysql-client-5.1 has broken dep on mysql-client-5.0
Package libpolkit-gobject-1-0 has broken dep on libglib2.0-0
Package mysql-server-core-5.1 has broken dep on mysql-server-core-5.0
Package mysql-client has broken dep on mysql-client-5.1
Package mysql-server-5.1 has broken dep on mysql-client-5.1
Package consolekit has broken dep on libpolkit-gobject-1-0
Package util-linux has broken dep on upstart-job
Package hostname has broken dep on upstart
Package initramfs-tools has broken dep on udev
Package sysv-rc has broken dep on initscripts
Package initscripts has broken dep on hostname
Package dmsetup has broken dep on util-linux
Package mysql-client-5.0 has broken dep on mysql-client
Package mysql-server has broken dep on mysql-server-5.1
Package grub has broken dep on util-linux
Package mdadm has broken dep on util-linux
Package mysql-server-5.0 has broken dep on mysql-server
Package sysv-rc has broken dep on initscripts
Package initscripts has broken dep on hostname
Package sysv-rc has broken dep on initscripts
Package initscripts has broken dep on hostname
Package sysv-rc has broken dep on initscripts
Package initscripts has broken dep on hostname
Package sysv-rc has broken dep on initscripts
Package initscripts has broken dep on hostname
Package sysv-rc has broken dep on initscripts
Package initscripts has broken dep on hostname
Package sysv-rc has broken dep on initscripts
Package initscripts has broken dep on hostname
Package sysv-rc has broken dep on initscripts
Package initscripts has broken dep on hostname
Package sysv-rc has broken dep on initscripts
Package initscripts has broken dep on hostname
```

As I understand - upgrade does not occur, because I have installed a package **libc6 2.11.1-0ubuntu7** ?

Then I'm try reinstall libc6 to **2.9-4ubuntu6.2** (it's version from repository for jaunty), but it has refused to be installed, now at start "sudo apt-get upgrade" permanently writes (it's translate from my lang., sorry for mistakes):

```
E: Package libc6 need reinstall, but find archive for it - was not possible
```

Command:

```
apt-get install -f
```

and

```
dpkg --configure -a
```

not helping...

I of course can't delete libc6 and install it again.

So.. Is it possible to somehow upgrade or may be downgrade libc6 to normal ver. ???

Many thanks for any help!!!

PS: "Mix repositories" - very bad idea...

---

### Post by iWarior on 2010-06-12
Solution - [here]("http://ubuntuforums.org/showpost.php?p=9463555&postcount=5")

---

