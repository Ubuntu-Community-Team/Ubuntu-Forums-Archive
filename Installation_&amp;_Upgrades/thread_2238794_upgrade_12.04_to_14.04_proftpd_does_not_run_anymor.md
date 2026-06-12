---
title: "upgrade 12.04 to 14.04 proftpd does not run anymore"
date: 2014-08-10
forum: Installation &amp; Upgrades
---

### Post by elroy2 on 2014-08-10
I recently upgraded from 12.04 to 14.04. So far so good, but proftpd , which did run under 12.04 flewlessly, does not run anymore. Of course I use the same config files etc.
Seems to be a problem with my authfile (ftpd.passwd). I see this msgs on the screen:

```

 * Starting ftp server proftpd
2014-08-10 12:58:40,977 shuttle proftpd[8330]: mod_auth_file/1.0: unable to use world-readable AuthUserFile '/etc/proftpd/ftpd.passwd': Operation not permitted
2014-08-10 12:58:40,977 shuttle proftpd[8330]: Fatal: AuthUserFile: unable to use /etc/proftpd/ftpd.passwd: Operation not permitted on line 37 of '/etc/proftpd/proftpd.conf'      [fail]
```
Any idea why this is not working anymore...?

---

### Post by nuller2 on 2014-08-13
Hi! I got the same problem... This happens, cause proftp cannot work with world readable password file....
(this is described in error message "mod_auth_file/1.0: unable to use world-readable AuthUserFile '/etc/proftpd/ftpd.passwd': Operation not permitted" )

All you have to do is change permissions of password file.

sudo chmod o-rwx /etc/proftpd/ftpd.passwd

sudo service proftpd start   

(alternative way: sudo /etc/init.d/proftpd start)

---

### Post by elroy2 on 2014-08-13
thanks for replying. proftpd starts again now, so that helped. However it does not read my ftpd.passwd file. In log I see this error:
```
error: unable to open passwd file '/etc/proftpd/ftpd.passwd': Permission denied
```

Any idea?

Terrible an upgrade with such bugs....

---

### Post by elroy2 on 2014-08-15
Fixed and thus working after entering:
```
sudo chmod 440 /etc/proftpd/ftpd.passwd && sudo chown proftpd.root /etc/proftpd/ftpd.passwd 
```

---

