---
title: "Multiple issues with OpenLDAP slapd"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by luvshines on 2010-10-20
I am trying to setup LDAP server on Ubuntu 10.04 and am sticking to the old /etc/ldap/slapd.conf file configuration.

I had to comment ldapi:/// from /etc/default/slapd since it was giving 'Address already in use error'. Also had to juggle with pid directory and file issues :)

After that I was able to start the slapd daemon (service slapd start) but now I am running into multiple issues:

1. **Can't stop the service with service slapd sto**p
```

## Service stop returns 0, maybe because start-stop-daemon is not giving error
#service slapd stop
Stopping OpenLDAP: slapd.
# echo $?
0

## ps says that slapd is running
# ps aux | grep slapd
openldap 16312  0.0  0.2  29140  4152 ?        Ssl  03:19   0:00 /usr/sbin/slapd -h ldap:/// -g openldap -u openldap -f /etc/ldap/slapd.conf

## This says no such process
# start-stop-daemon --stop --oknodo --retry TERM/10 --pidfile /var/run/slapd/ldap/slapd.pid --exec /usr/sbin/slapd
No /usr/sbin/slapd found running; none killed.
```

2. **Can't slapcat it**. I think it is running the HDB database. I have always worked with BDB database so don't know if that can be issue
```
## As root user
#slapcat 
Available database(s) do not allow slapcat

## As non-root user
#slapcat 
ldif_read_file: Permission denied for "/etc/ldap/slapd.d/cn=config.ldif"
slapcat: bad configuration file!
```

Will switching to BDB database resolve this ??
Also can't I slapcat at non-root user ??

---

### Post by luvshines on 2010-10-20
[COLOR="Blue"]Some success on the first issue.[/COLOR]

Just found something interesting (for me atleast)

I changed pid file location to /var/run/slapd/slapd.pid which is default in cn=config.ldif

But the thing is, if I don't speficy the --pidfile in start-stop-daemon it is able to stop the service
```
start-stop-daemon --stop --oknodo --retry TERM/10 --exec /usr/sbin/slapd -vvv
Stopped /usr/sbin/slapd (pid 18108)
```

Now the interesting part is:
a) For starting the service it uses
```
start-stop-daemon --start --quiet --oknodo --pidfile /var/run/slapd/slapd.pid --exec /usr/sbin/slapd -- -h ldap:/// -g openldap -u openldap -f /etc/ldap/slapd.conf
```

Here since it will not get any process with that pid and slapd running it will start the service

**[COLOR="Red"]But, noone creates the PID file[/COLOR]**

b) For stopping the service if it uses
```
start-stop-daemon --stop --oknodo --retry TERM/10 --pidfile /var/run/slapd/ldap/slapd.pid --exec /usr/sbin/slapd
```

Since it finds no pid file it won't kill the service

**[COLOR="red"]So, the question now is who creates the PID file. Since there is not code for that in /etc/init.d/slapd[/COLOR]**

This failure of PID file creation also results in service being reported as not running, even when it is

---

### Post by luvshines on 2010-10-21
As always, had to resolve the issue myself :(, **[COLOR="Red"]no response here[/COLOR]**

1. Added at the end of start_slapd functino in /etc/init.d/slapd ```
pidof /usr/sbin/slapd > "$SLAPD_PIDFILE"
```

This now creates the required pid file with correct pid file and start/stop/status/restart now works perfect

2. Instead of slapcat, have to use
```
slapcat -f /etc/ldap/slapd.conf
```

**And this command only runs as sudo, not as any other user**

---

