---
title: "apt-get claims Apache is not installed"
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by girasquid on 2007-06-25
Hello, all.

I am working on installing proFTP using apt-get. The command that I am using is this:
```

apt-get install proftpd

```
This works, and the installation begins, but then breaks when apt-get claims that I don't have Apache installed. 

I am running on Ubuntu 7 Server, with Apache 2 - could it be that apt-get is looking for some version of Apache other than 2? 

Does anyone know what I need to fix for apt-get to understand that Apache **is** installed?

Thanks,
Girasquid

---

### Post by bapoumba on 2007-06-25
Disclaimer: I'm not familiar with servers and such things.

<snip>
So could you please post the error message you get when installing proftpd? (for other members to chime in ^^).

As far as the install process, apache (or apache2) is not a dependency for proftpd, so I _guess_ the error you get is during the post-install set up ?

---

### Post by Swab on 2007-06-25
Apparently Apache is not a dependency....

Dependencies: 
1.3.0-21ubuntu1 - netbase (2 4.13) perl (0 (null)) libacl1 (2 2.2.11-1) libattr1 (2 2.4.4-1) libc6 (2 2.5-0ubuntu1) libldap2 (2 2.1.17-1) libmysqlclient15off (2 5.0.24-2) libncurses5 (2 5.4-5) libpam0g (2 0.76) libpq5 (0 (null)) libssl0.9.8 (2 0.9.8c-1) libwrap0 (0 (null)) zlib1g (2 1:1.2.1) debconf (2 0.5.00) adduser (0 (null)) ucf (2 0.30) debianutils (2 1.21.0) libpam-runtime (2 0.76-13.1) update-inetd (0 (null)) proftpd-doc (0 (null)) wu-ftpd (0 (null)) wu-ftpd-academ (0 (null)) ftp-server (0 (null)) proftpd-common (0 (null)) proftpd-common (0 (null)

---

### Post by girasquid on 2007-06-25
Here's what happens:
```

# apt-get install proftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
proftpd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.

```
And then after this, messages which(I believe) apply to installing Apache are showing up:
```

1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up apache (1.3.34-4.1) ...
Error: apache appears not to be installed
dpkg: error processing apache (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 apache
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
I think that these messages mean apt-get is attempting to install an older version of Apache; how can I tell it not to?

---

### Post by az on 2007-06-25
First, run 

sudo apt-get remove apache


Then run

sudo apt-get -f install

To install Apache (or LAMP) on Ubuntu, use the Ubuntu documentation at help.ubuntu.com:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

The "perfect setup" tutorials often install non-essential packages and don't really tell you why.  As well, you can install the whole LAMP stack from main (and nothing else) which has better security support than universe,

---

### Post by bapoumba on 2007-06-26
> **az said:**
> 
The "perfect setup" tutorials often install non-essential packages and don't really tell you why.  As well, you can install the whole LAMP stack from main (and nothing else) which has better security support than universe,
Thanks for adding this, az. I will remove the link in my post. As this did not seem a dependecy issue to me, I looked around to find the link between the two.

---

