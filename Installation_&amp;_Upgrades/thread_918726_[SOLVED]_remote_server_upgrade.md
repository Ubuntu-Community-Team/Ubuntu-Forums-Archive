---
title: "[SOLVED] remote server upgrade"
date: 2008-09-13
forum: Installation &amp; Upgrades
---

### Post by el_baby on 2008-09-13
A quick one:

during a remote server upgrade, I hit ctrl-c when nothing happened after trying to see side-by-side differences between my modified php.ini and release php.ini.

everything went on with an error, but I guess the final steps of the "do-release-upgrade" are missing and I don't know how to run them.

At the end of the process I got:

```

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-server
Errors were encountered while processing:
 libapache2-mod-php5

Could not install the upgrades

The upgrade aborts now. Your system could be in an unusable state. A
recovery will run now (dpkg --configure -a).

Please report this bug against the 'update-manager' package and
include the files in /var/log/dist-upgrade/ in the bugreport.
E:Sub-process /usr/bin/dpkg returned an error code (1)

Setting up libapache2-mod-php5 (5.2.4-2ubuntu5.3) ...
Replacing config file /etc/php5/apache2/php.ini with new version
 * Reloading web server config apache2

Could not install the upgrades

The upgrade aborts now. Your system could be in an unusable state. A
recovery will run now (dpkg --configure -a).

Please report this bug against the 'update-manager' package and
include the files in /var/log/dist-upgrade/ in the bugreport.
installArchives() failed

```

I manually run [font=courier]dpkg --configure -a[/font] (which yelded no output).


Yesterday a did a similar upgrade on a similar server via console, but Murphy's Law seems to indicate that the errors would happen on the remote server and not on the local one. I recall that after finishing the "setting up blah-blah-blah" it did something else (apt-get autoremove maybe?). 	:confused:

I had to manually start apache and it's running OK, but I don't dare to reboot...

Full report is at [lpbug]269799[/lpbug].

Any help appreciated

---

### Post by el_baby on 2008-09-13
Well, apparantly everything went smoothly after
```

dpkg --configure -a
apt-get autoremove

```

---

### Post by el_baby on 2008-09-13
.

---

