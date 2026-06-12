---
title: "Cannot ID LDAP User On LDAP Client"
date: 2010-12-02
forum: Installation &amp; Upgrades
---

### Post by revzalot on 2010-12-02
I've setup an Ubuntu 10.10 LDAP Client to authenticate off my LDAP server.  I've install the following:

sudo apt-get install libpam-ldap libnss-ldap nss-updatedb libnss-db nscd ldap-utils pam_ccreds


Here's my /etc/nsswitch.conf:[INDENT] passwd: files ldap [NOTFOUND=return] db
 
 group: files ldap [NOTFOUND=return] db
 
 shadow: files ldap

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
[/INDENT]I can nss_updatedb ldap succssfully:
# nss_updatedb ldap
passwd... done.
group... done.

I can getent passwd, getent passwd shadow, getent group just fine and they all show all my ldap users.


However, I cannot do an id ldapuser

ex:
$ id tony
id: tony: No such user

Here's my auth.log:[INDENT] Dec  1 21:08:17 webdev120 sshd[14765]: pam_unix(sshd:auth): check pass; user unknown
[/INDENT]Here's my syslog:[INDENT] sshd[14648]: Libgcrypt warning: missing initialization - please fix the application
[/INDENT]Here's my /etc/pam.d/commoun-auth:[INDENT][INDENT] auth    [success=4 default=ignore]      pam_unix.so nullok_secure
auth    [success=3 default=ignore]      pam_ldap.so use_first_pass
auth    [success=2 default=ignore]      pam_ccreds.so minimum_uid=1000 action=validate use_first_pass
auth    [default=ignore]                pam_ccreds.so minimum_uid=1000 action=update
# here's the fallback if no module succeeds
#auth   requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
#auth   required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth    optional                        pam_ccreds.so minimum_uid=1000 action=store
# end of pam-auth-update config
[/INDENT][/INDENT]Here's my /etc/pam.d/common-account:[INDENT] # here are the per-package modules (the "Primary" block)
account [success=2 new_authtok_reqd=done default=ignore]        pam_unix.so
account [success=1 default=ignore]      pam_ldap.so
# here's the fallback if no module succeeds
account requisite                       pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
account required                        pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config
[/INDENT]ID works just fine with my local users on my local machine so somehow it's not able to read the ldap users.  


Any insights appreciated.

Here's my test on my ldap user 'tony'
root@webtest111:/etc/pam.d# id tony
id: tony: No such user
root@webtest111:/etc/pam.d# getent passwd tony
root@webtest111:/etc/pam.d# getent passwd |grep tony
tony:x:1005:10000:Tony Montana:/home/tony:/bin/bash
root@webtest111:/etc/pam.d# /etc/init.d/nscd stop
 * Stopping Name Service Cache Daemon nscd                               [ OK ] 
root@webtest111:/etc/pam.d# getent passwd |grep tony
tony:x:1005:10000:Tony Montana:/home/tony:/bin/bash
root@webtest111:/etc/pam.d# getent passwd tony
root@webtest111:/etc/pam.d# id tony
id: tony: No such user

SOLVED:  I added ldapns.schema to enable host based authentication and  the users before the schema upgrade caused this caching to stop.  I  added a new after the schema upgrade and all is well.

---

### Post by TSJason on 2010-12-02
Do you have nscd running? What does your /etc/ldap.conf (or /etc/ldap/ldap.conf) look like?

---

### Post by revzalot on 2010-12-02
Yes I have ncsd running and then disabled but still id does not work.  

Here's my /etc/ldap.conf:
```
cat /etc/ldap.conf | grep -v ^# | grep -v ^$
base dc=example,dc=com
uri ldapi:///10.112.18.2
ldap_version 3
rootbinddn cn=admin,dc=example,dc=com
bind_policy soft 
pam_check_host_attr yes
pam_password md5
```

---

### Post by TSJason on 2010-12-02
You might try defining nss_base_passwd, nss_base_shadow, and nss_base_group in your ldap.conf. And keep nscd running :-)

---

### Post by revzalot on 2010-12-02
Ok I turned ncsd back on but id still doesn't work.  

```
cat /etc/ldap.conf | grep -v ^# | grep -v ^$
base dc=example,dc=com
uri ldap://10.112.18.2
ldap_version 3
bindpw secret
rootbinddn cn=admin,dc=example,dc=com
bind_policy soft 
pam_check_host_attr yes
pam_password md5
nss_base_passwd        ou=People,dc=example,dc=com
nss_base_shadow        ou=People,dc=example,dc=com?one
nss_base_group        ou=Groups,dc=example,dc=com?one
```
On another machine, tried this howto after purging the above above packages.

[http://www.opinsys.fi/en/setting-up-openldap-on-ubuntu-10-04-alpha2](http://www.opinsys.fi/en/setting-up-openldap-on-ubuntu-10-04-alpha2)

sudo apt-get install libnss-ldapd libpam-ldapd

Still the same outcome.  I can ldapsearch, getent, etc. but id cannot show the ldap users.

---

### Post by TSJason on 2010-12-02
well comparing your setup to mine (I'm using 10.04), I also setup the pam session file as well. My config file looks like this:

```
[open_ldap]
nss_passwd=passwd: files ldap
nss_group=group: files ldap
nss_shadow=shadow: files ldap
nss_netgroup=netgroup: ldap files 
nss_sudoers=sudoers: ldap files
pam_auth=auth       required     pam_env.so
        auth       sufficient   pam_unix.so likeauth nullok
        auth       required     pam_group.so use_first_pass
        auth       sufficient   pam_ldap.so use_first_pass
        auth       required     pam_deny.so
pam_account=account    sufficient   pam_unix.so
        account    sufficient   pam_ldap.so
        account    required     pam_deny.so
pam_password=password   sufficient   pam_unix.so nullok md5 shadow
        password   sufficient   pam_ldap.so use_first_pass
        password   required     pam_deny.so
pam_session=session    required     pam_limits.so
        session    required     pam_mkhomedir.so skel=/etc/skel/
        session    required     pam_unix.so
        session    optional     pam_ldap.so
```

I apply it with:

```
auth-client-config -a -p open_ldap
```

---

### Post by revzalot on 2010-12-02
Tried it but didn't budge.

```
root@webtest111:/etc/auth-client-config/profile.d# auth-client-config -a -p open_ldap
root@webtest111:/etc/auth-client-config/profile.d# id tony
id: tony: No such user
root@webtest111:/etc/auth-client-config/profile.d# nss_updatedb ldap
passwd... done.
group... done.
root@webtest111:/etc/auth-client-config/profile.d# getent passwd | grep tony
tony:x:1005:10000:Tony Montana:/home/tony:/bin/bash
root@webtest111:/etc/auth-client-config/profile.d# id tony
id: tony: No such user
root@webtest111:/etc/auth-client-config/profile.d# 
```

---

### Post by revzalot on 2010-12-02
NSCD daemon is the culprit.  Here's the error when I do id tony:

```
 nscd -d
Thu 02 Dec 2010 02:18:18 PM PST - 14248: handle_request: request received (Version = 2) from PID 14257
Thu 02 Dec 2010 02:18:18 PM PST - 14248:     GETFDPW
Thu 02 Dec 2010 02:18:18 PM PST - 14248: provide access to FD 5, for passwd
Thu 02 Dec 2010 02:18:18 PM PST - 14248: handle_request: request received (Version = 2) from PID 14257
Thu 02 Dec 2010 02:18:18 PM PST - 14248:     GETPWBYNAME (tony)
Thu 02 Dec 2010 02:18:18 PM PST - 14248: Haven't found "tony" in password cache!
Thu 02 Dec 2010 02:18:24 PM PST - 14248: Reloading "nslcd" in password cache!
Thu 02 Dec 2010 02:18:39 PM PST - 14248: remove GETPWBYNAME entry "tony"
Thu 02 Dec 2010 02:18:50 PM PST - 14248: handle_request: request received (Version = 2) from PID 14258
```

Here's my nscd.conf file:

```

cat /etc/nscd.conf | grep -v ^# | grep -v ^$
    debug-level        0
    paranoia        no
    enable-cache        passwd        yes
    positive-time-to-live    passwd        600
    negative-time-to-live    passwd        20
    suggested-size        passwd        211
    check-files        passwd        yes
    persistent        passwd        yes
    shared            passwd        yes
    max-db-size        passwd        33554432
    auto-propagate        passwd        yes
    enable-cache        group        yes
    positive-time-to-live    group        3600
    negative-time-to-live    group        60
    suggested-size        group        211
    check-files        group        yes
    persistent        group        yes
    shared            group        yes
    max-db-size        group        33554432
    auto-propagate        group        yes
    enable-cache        hosts        no
    positive-time-to-live    hosts        3600
    negative-time-to-live    hosts        20
    suggested-size        hosts        211
    check-files        hosts        yes
    persistent        hosts        yes
    shared            hosts        yes
    max-db-size        hosts        33554432
    enable-cache        services    yes
    positive-time-to-live    services    28800
    negative-time-to-live    services    20
    suggested-size        services    211
    check-files        services    yes
    persistent        services    yes
    shared            services    yes
    max-db-size        services    33554432


```

---

### Post by luvshines on 2010-12-04
But when nscd was off, still id command didn't work, right ?

So that can't be a possible culprit :)

Since you have rootbinddn mentioned in /etc/ldap.conf file, did you also put in the root bind passwd in /etc/ldap.secret ?

---

### Post by revzalot on 2010-12-07
> **luvshines said:**
> But when nscd was off, still id command didn't work, right ?

So that can't be a possible culprit :)

Since you have rootbinddn mentioned in /etc/ldap.conf file, did you also put in the root bind passwd in /etc/ldap.secret ?

Yes to all the above.  After making a new user id worked on that ldap user.  Somehow the schema install prevent id from working with my old users. :)

---

