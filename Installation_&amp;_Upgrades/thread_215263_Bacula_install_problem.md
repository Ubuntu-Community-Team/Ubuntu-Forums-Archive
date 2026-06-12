---
title: "Bacula install problem"
date: 2006-07-13
forum: Installation &amp; Upgrades
---

### Post by ProspectorPete on 2006-07-13
Hi

I've installed Ubuntu Dapper as a server.  It works ok as a server and Windows clients can access it thru Samba.  I added Gnome so it can be started manually when required to do admin stuff.

I installed bacula from bacula-1.38.11.tar.gz, but when I start bacula, then bconsole I get:

 "connecting to <hostname>:9101"
then after a timeout delay:
 "bconsole: Fatal error: bnet.c:859 Unable to connect to Director daemon on <hostname>:9101. ERR=Connection refused":confused: 

Also the bacula icon is not available in Gnome

Any advice welcomed

Peter

---

### Post by baastie on 2006-08-01
Hi Peter,

Sorry for the late ( very ) late reply, if you are still trying to get bacula working... you can try to solve the errors below with making sure the server and clients can resolve eachother by dns or hosts file.

And that the passwords used in al the conf files ( dir, sd and fd ) match eachother.

Cheers,

---

### Post by Lundin on 2007-03-07
I've got the same problem

I've used synaptic to install bacula and its dependencies, and without touching any of the .conf files I get the connection refused message. Trying the password matching didn't help either.
Some other thread talked about hanging deamons, so I've restarted the director, sd and fd deamons as well.

The brief Bacula tutorial doesn't really help either, but it talks about installing from source and not debs....

Anyone who could point me into the right direction?

---

### Post by dkrysmann on 2007-05-13
Installed with synaptic and also does not work. When I start the -sd daemon I can hear tape starts zooming to stop after a 15-30 sec.

---

### Post by jkp on 2007-05-25
Hi

I found that Bacula gets configured as being bound to 127.0.0.1 by default on Ubuntu.  This means that you will be able to contact the daemons on the loopback, but not on the external network IP.  You need to change this in the three config files for it to respond properly.

Now if someone would only run up some deb's for version 2...

Jamie

---

### Post by informatica on 2007-11-21
Woa

That localhost suggestion goes against all suggestions inside the .conf files.

My problem is that i can't start the director through webmin. I'm using the same versions mentioned earlier in this post but all changes I've tried were useless. There no way that webmin can control the bacula director.

On the command line though I can start and stop it without any error message coming up, i have even tried a backup job but it does seem that console and director are not communicating. Passwords are OK as far as documentation goes and also everything else.

This is the message I get on webmin everytime I try to start all bacula daemons:
> "Failed to start Bacula : No init script found for bacula-dir"

Even this localhost trick is not OK?

Will someone help me if I post y .conf files along with the init scripts.?

Thanks in advance,
Pax

---

### Post by IntuitiveNipple on 2007-12-10
The reason for this is explained in the error message reported by Webmin:
```
Failed to start Bacula : No init script found for bacula-dir

```
There is no **/etc/init.d/bacula-dir**. At some point the Debian or Ubuntu packages appear to have changed the init script name to **bacula-director**.

The fix is to create a symlink:
```
sudo ln -s /etc/init.d/bacula-director /etc/init.d/bacula-dir
```

Now the bacula service will start in Webmin.

---

