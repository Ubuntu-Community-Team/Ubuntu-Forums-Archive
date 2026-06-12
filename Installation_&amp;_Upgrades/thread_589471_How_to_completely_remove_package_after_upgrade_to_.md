---
title: "How to completely remove package after upgrade to Gutsy"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by Gus_T_Reer on 2007-10-24
After a successful upgrade from Feisty to Gutsy I had a lot of packages residing in the residual config state.
I have completely removed these packages except for netkit-inetd which I had installed under Feisty but was removed during the upgrade. No matter what I do I can't seem to get this package completely removed.
Synaptic gives an error of: E: netkit-inetd: subprocess post-removal script returned error exit status 1

In terminal, sudo dpkg --purge netkit-inetd gives:
Removing netkit-inetd ...
Purging configuration files for netkit-inetd ...
update-rc.d: /etc/init.d/inetd exists during rc.d purge (use -f to force)
dpkg: error processing netkit-inetd (--purge):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 netkit-inetd

And also in terminal, sudo apt-get --purge remove netkit-inetd gives:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package netkit-inetd is not installed, so not removed

I've also tried reinstalling the package but it no longer exists in any of the Gutsy repositories.

Any advice on how to completely remove this package would be appreciated.

Thanks

---

### Post by bapoumba on 2007-10-24
[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg312088.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg312088.html)
Looks like a bug..
There is also a very old 2005 bug:
[https://bugs.launchpad.net/ubuntu/+source/xinetd/+bug/12995](https://bugs.launchpad.net/ubuntu/+source/xinetd/+bug/12995)

You could try the following:
```
sudo dpkg --remove --force-remove-reinstreq netkit-inetd
```

[QUOTE=man dpkg] 
remove-reinstreq:  Remove  a package, even if it’s broken
              and marked to require reinstallation. This may, for exam&#8208;
              ple,  cause parts of the package to remain on the system,
              which will then be forgotten by dpkg.

[/QUOTE]

---

### Post by Gus_T_Reer on 2007-10-24
Thank you bapoumba, nice avatar by the way, I tried your suggestion but unfortunately it didn't work. There's some (small) comfort in knowing it's not just me though.

sudo dpkg --remove --force-remove-reinstreq netkit-inetd
dpkg - warning: ignoring request to remove netkit-inetd, only the config
 files of which are on the system. Use --purge to remove them too.

---

### Post by bapoumba on 2007-10-24
> **Gus_T_Reer said:**
> Thank you bapoumba, nice avatar by the way, I tried your suggestion but unfortunately it didn't work. There's some (small) comfort in knowing it's not just me though.
Eheh, [Complexnumber]("http://ubuntuforums.org/member.php?u=76421") has found it for me for the Halloween Costume party (please see my sig).
> **Gus_T_Reer said:**
> 
sudo dpkg --remove --force-remove-reinstreq netkit-inetd
dpkg - warning: ignoring request to remove netkit-inetd, only the config
 files of which are on the system. Use --purge to remove them too.
Well, never used it with purge, but if dpkg says so, try:
```
sudo dpkg --purge --force-remove-reinstreq netkit-inetd
```

---

### Post by Gus_T_Reer on 2007-10-24
> **bapoumba said:**
> Eheh, [Complexnumber]("http://ubuntuforums.org/member.php?u=76421") has found it for me for the Halloween Costume party (please see my sig).

Aha, I see and I understand, neat.

> **bapoumba said:**
> Well, never used it with purge, but if dpkg says so, try:
```
sudo dpkg --purge --force-remove-reinstreq netkit-inetd
```

I had the same thought process, so tried it but got the usual purge fail message:
Removing netkit-inetd ...
Purging configuration files for netkit-inetd ...
update-rc.d: /etc/init.d/inetd exists during rc.d purge (use -f to force)
dpkg: error processing netkit-inetd (--purge):
subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
netkit-inetd

---

### Post by bapoumba on 2007-10-24
/etc/init.d/inetd --> Could you please have a look and see what is in it? I'm not sure if renaming the faulty file would be of any help.. (so that dpkg does not see it any longer, as the package is not installed any longer.)

You should probably comment in the Launchpad bug, to reactivate the issue.

---

### Post by Gus_T_Reer on 2007-10-24
/etc/init.d/inetd reads:
#!/bin/sh

# /etc/init.d/inetd has been diverted by the xinetd package.
# The inetd service is provided by xinetd, which means inetd
# doesn't need to be run.
#
# See /etc/init.d/xinetd, or /etc/init.d/inetd.real.

exit 0
-------------------
There isn't a /etc/init.d/inetd.real file but there are xinetd and  inetd.real.dpkg-new files.

The xinetd file doesn't make reference to /etc/init.d/inetd but the inetd.real.dpkg-new file does:
------------------------------------
/etc/init.d/xinetd:
#!/bin/sh
#
# /etc/init.d/xinetd  --  script to start and stop xinetd.

if test -f /etc/default/xinetd; then
	. /etc/default/xinetd
fi


test -x /usr/sbin/xinetd || exit 0

checkportmap () {
  if grep "^[^ *#]" /etc/xinetd.conf | grep -q 'rpc/'; then
    if ! rpcinfo -u localhost portmapper >/dev/null 2>&1; then
      echo
      echo "WARNING: portmapper inactive - RPC services unavailable!"
      echo "    Commenting out or removing the RPC services from"
      echo "    the /etc/xinetd.conf file will remove this message."
      echo
    fi
  fi
} 

case "$1" in
    start)
        checkportmap
	echo -n "Starting internet superserver: xinetd"
	start-stop-daemon --start --quiet --background --exec /usr/sbin/xinetd -- -pidfile /var/run/xinetd.pid $XINETD_OPTS
	echo "."
	;;
    stop)
	echo -n "Stopping internet superserver: xinetd"
	start-stop-daemon --stop --signal 3 --quiet --oknodo --exec /usr/sbin/xinetd
	echo "."
	;;
    reload)
	echo -n "Reloading internet superserver configuration: xinetd"
	start-stop-daemon --stop --signal 1 --quiet --oknodo --exec /usr/sbin/xinetd
	echo "."
	;;
    force-reload)
	echo "$0 force-reload: Force Reload is deprecated"
	echo -n "Forcefully reloading internet superserver configuration: xinetd"
	start-stop-daemon --stop --signal 1 --quiet --oknodo --exec /usr/sbin/xinetd
	echo "."
	;;
    restart)
	$0 stop
	$0 start
	;;
    *)
	echo "Usage: /etc/init.d/xinetd {start|stop|reload|force-reload|restart}"
	exit 1
	;;
esac

exit 0
-------------------------------------------
/etc/init.d/inetd.real.dpkg-new:
#!/bin/sh
#
# start/stop inetd super server.

if ! [ -x /usr/sbin/inetd ]; then
	exit 0
fi

. /lib/lsb/init-functions

checkportmap () {
    if grep -v "^ *#" /etc/inetd.conf | grep 'rpc/' >/dev/null; then
        if ! [ -x /usr/bin/rpcinfo ]
        then
            echo
            log_warning_msg "WARNING: rpcinfo not available - RPC services may be unavailable!"
            log_warning_msg "         (Commenting out the rpc services in inetd.conf will"
	    log_warning_msg "         disable this message)"
            echo
        elif ! /usr/bin/rpcinfo -u localhost portmapper >/dev/null 2>/dev/null
        then
            echo
            log_warning_msg "WARNING: portmapper inactive - RPC services unavailable!"
            log_warning_msg "         (Commenting out the rpc services in inetd.conf will"
	    log_warning_msg "         disable this message)"
            echo
        fi
    fi
} 

case "$1" in
    start)
        checkportmap
	log_begin_msg "Starting internet superserver..."
	start-stop-daemon --start --quiet --pidfile /var/run/inetd.pid --exec /usr/sbin/inetd
	log_end_msg $?
	;;
    stop)
	log_begin_msg "Stopping internet superserver..."
	start-stop-daemon --stop --quiet --oknodo --pidfile /var/run/inetd.pid --exec /usr/sbin/inetd
	log_end_msg $?
	;;
    reload)
	log_begin_msg "Reloading internet superserver..."
	start-stop-daemon --stop --quiet --oknodo --pidfile /var/run/inetd.pid --signal 1
	log_end_msg $?
	;;
    force-reload)
	$0 reload
	;;
    restart)
	log_begin_msg "Restarting internet superserver..."
	start-stop-daemon --stop --quiet --oknodo --pidfile /var/run/inetd.pid
	checkportmap
	start-stop-daemon --start --quiet --pidfile /var/run/inetd.pid --exec /usr/sbin/inetd
	log_end_msg $?
	;;
    *)
	log_success_msg "Usage: /etc/init.d/inetd {start|stop|reload|restart}"
	exit 1
	;;
esac

exit 0
-------------------------

I'm all confused but I'll register with launchpad and do as you suggest.

Thanks for your help.

---

### Post by bapoumba on 2007-10-24
Please look in /var/lib/dpkg/info/ if you have a file related to netkit-inetd or intetd with a .postrm extension. If so, please paste the file in here.

---

### Post by Gus_T_Reer on 2007-10-24
Hi bapoumba,

I've made an entry in launchpad as you suggested. I'm not sure if it will be accepted as that bug refers to xinetd but it's been made so we'll see how it goes.

I have no netkit-inetd or inetd file with a .postrm extension in /var/lib/dpkg/info/, the only file anywhere close is a netkit-inetd.list file which contains:
/etc
/etc/init.d
/etc/init.d/inetd
/etc/cron.daily
/etc/cron.daily/netkit-inetd

Regards

---

### Post by bapoumba on 2007-10-24
Hmm. I've reached what I understand and know.
To me, the package is removed, but some script files are still there, making dpkg unhappy.
If we find which file is sending the error during the --purge process, you can edit it so that dpkg thinks everything is fine.

But for now, I have no idea where to look, and indeed this package is not on gutsy any longer:
```
isabella@yeti:~ $ aptitude show netkit-inetd
No current or candidate version found for netkit-inetd
Package: netkit-inetd
State: not a real package
Provided by: inetutils-inetd, openbsd-inetd

```

Sorry :(

---

### Post by Gus_T_Reer on 2007-10-24
bapoumba,

Regardless of the outcome, I appreciate your efforts. Thanks and take care.

---

### Post by bapoumba on 2007-10-24
> **Gus_T_Reer said:**
> bapoumba,

Regardless of the outcome, I appreciate your efforts. Thanks and take care.
You're very welcome. I'll keep looking and post here is I find something (but I think I searched google with every line from the error messages..). The package scripts have been reported to cause problems long before you ran into them. The upgrade should have been able to handle the package removal.

---

### Post by Gus_T_Reer on 2007-10-24
> **bapoumba said:**
> The upgrade should have been able to handle the package removal.

C'est la vie.  :tongue:

---

### Post by bapoumba on 2007-10-24
> **Gus_T_Reer said:**
> C'est la vie.  :tongue:
Ahah, yes ^^

May be someone around here will come up with a smart idea :)

---

