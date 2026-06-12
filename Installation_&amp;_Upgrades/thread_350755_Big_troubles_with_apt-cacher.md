---
title: "Big troubles with apt-cacher"
date: 2007-02-01
forum: Installation &amp; Upgrades
---

### Post by copacule on 2007-02-01
Hello all!

This is my first post so be careful what you reply because it will be very important to my first impression regarding this forum. Just kidding!:)

Now, I've followed [THIS]("http://ubuntu-tutorials.com/2007/01/08/save-bandwidth-during-updates-with-apt-cacher-ubuntu-610/") url exactly. I now have sources.list on every client machine:

```

#ubuntu archive
#deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
deb http://10.0.0.1:3124/archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
#deb-src http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
deb-src http://10.0.0.1:3124/archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse


# ubuntu updates
#deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://10.0.0.1:3124/archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
#deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://10.0.0.1:3124/archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse

#ubuntu security
#deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://10.0.0.1:3124/security.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse
#deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://10.0.0.1:3124/security.ubuntu.com/ubuntu/ dapper-security main restricted universe multiverse

```

But on the client machines, once I run **sudo apt-get update**, I get these errors:

```

Ign http://10.0.0.1 dapper-security/main Sources
Ign http://10.0.0.1 dapper-security/restricted Sources
Ign http://10.0.0.1 dapper-security/universe Sources
Ign http://10.0.0.1 dapper-security/multiverse Sources
Err http://10.0.0.1 dapper/universe Packages
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper/main Packages
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper/restricted Packages
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper/multiverse Packages
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper/universe Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper/main Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper/restricted Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper/multiverse Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper-updates/main Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper-updates/restricted Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper-updates/universe Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper-updates/multiverse Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper-updates/main Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper-updates/restricted Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper-updates/universe Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper-updates/multiverse Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper-security/main Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper-security/restricted Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper-security/universe Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper-security/multiverse Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper-security/main Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper-security/restricted Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper-security/universe Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Err http://10.0.0.1 dapper-security/multiverse Sources
  500 (Internal Server Error) Can't connect to http::80 (Bad hostname 'http:')
Fetched 27.0kB in 28s (961B/s)

```

However, if i wget  [http://10.0.0.1/archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://10.0.0.1/archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz) , everything is fine but not through apt-cacher.

What can I do? thank you!

---

### Post by guheka on 2007-10-24
try to change the line at your /etc/host.conf.

from  : [COLOR="DarkRed"]multi on [/COLOR] 
to       : [COLOR="DarkRed"]multi off[/COLOR]

It's fix that problem in my apt-cacher.

---

