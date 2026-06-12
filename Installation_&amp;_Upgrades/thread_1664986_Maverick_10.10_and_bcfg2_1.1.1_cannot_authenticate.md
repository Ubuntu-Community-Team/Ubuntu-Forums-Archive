---
title: "Maverick 10.10 and bcfg2 1.1.1 cannot authenticate client"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by revzalot on 2011-01-11
I've installed bcfg2 server 1.1.1 on ubuntu 10.10 and I cannot authenticate my ubuntu 10.10 bcfg2 client to the my bcfg2 server.  I redid my ca certs twice.  My ldap client webdev121 is in dns and can be resolvable.  10.04 bcfg2 server version worked fine by the way.

Here's the error from the client side:
```

root@webdev121:~# bcfg2 -q -v -n -d -p basic --ca-cert ./bcfg2.crt -S https://opsdev:6789 -x test
{'filelog': None, 'verbose': True, 'extra': False, 'ca': './bcfg2.crt', 'remove': False, 'file': False, 'help': False, 'password': 'test', 'omit-lock-check': False, 'certificate': None, 'paranoid': False, 'indep': False, 'decision': False, 'cache': False, 'servicemode': 'default', 'profile': 'basic', 'dryrun': True, 'kevlar': False, 'args': [], 'bundle': [], 'quick': True, 'user': 'root', 'key': None, 'lockfile': '/var/lock/bcfg2.run', 'retries': '3', 'setup': '/etc/bcfg2.conf', 'serverCN': None, 'server': 'https://opsdev.dot.ca.gov:6789', 'encoding': 'ascii', 'decision-list': False, 'debug': True, 'drivers': ['APT', 'Action', 'Blast', 'Chkconfig', 'DebInit', 'Encap', 'FreeBSDInit', 'FreeBSDPackage', 'IPS', 'MacPorts', 'POSIX', 'Portage', 'RPMng', 'RcUpdate', 'SMF', 'SYSV', 'Upstart', 'YUMng', 'launchd'], 'interactive': False}
Server failure: Protocol Error: 401 Unauthorized
Fatal error: Failed to set client profile

```Here's the server errors:
```

Jan 11 22:59:19 opsdev bcfg2-server[2616]: address resolution error for 10.112.18.156
Jan 11 22:59:19 opsdev bcfg2-server[2616]: Client 10.112.18.156 failed to resolve; metadata problem
Jan 11 22:59:19 opsdev bcfg2-server[2616]: Authentication Failure

```Here's my /etc/bcfg2.conf
```

root@opsdev:~# cat /etc/bcfg2.conf

[server]
repository = /var/lib/bcfg2
plugins = Base,Bundler,Cfg,Metadata,Packages,Rules,SSHbase

[statistics]
sendmailpath = /usr/lib/sendmail
database_engine = sqlite3
# 'postgresql', 'mysql', 'mysql_old', 'sqlite3' or 'ado_mssql'.
database_name =
# Or path to database file if using sqlite3.
#<repository>/etc/brpt.sqlite is default path if left empty
database_user =
# Not used with sqlite3.
database_port =
# Set to empty string for default. Not used with sqlite3.
web_debug = True

[communication]
protocol = xmlrpc/ssl
password = test 
certificate = /etc/bcfg2.crt
key = /etc/bcfg2.key
ca = /etc/bcfg2.crt

[components]
bcfg2 = https://opsdev:6789


```

---

### Post by revzalot on 2011-01-12
SOLVED!  The server couldn't do a reverse nslookup so I added the client to /etc/hosts.

---

