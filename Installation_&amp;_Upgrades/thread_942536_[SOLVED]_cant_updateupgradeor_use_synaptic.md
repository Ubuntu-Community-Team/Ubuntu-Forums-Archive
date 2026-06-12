---
title: "[SOLVED] cant update/upgrade/or use synaptic"
date: 2008-10-09
forum: Installation &amp; Upgrades
---

### Post by SteveNorman on 2008-10-09
I get this

```
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/universe/x/xgalaga/xgalaga_2.1.0-1-1ubuntu1_i386.deb
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
```

when I try and download anything. I tried to update my system via apt-get update and get this lengthy message:

```
$ sudo apt-get update
Err http://us.archive.ubuntu.com hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://us.archive.ubuntu.com hardy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://us.archive.ubuntu.com hardy/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://us.archive.ubuntu.com hardy/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://us.archive.ubuntu.com hardy-updates Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://us.archive.ubuntu.com hardy-backports Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://us.archive.ubuntu.com hardy-backports/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://us.archive.ubuntu.com hardy-backports/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://us.archive.ubuntu.com hardy-backports/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://us.archive.ubuntu.com hardy-backports/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://archive.canonical.com hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://archive.canonical.com hardy/partner Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://security.ubuntu.com hardy-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://security.ubuntu.com hardy-security/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://security.ubuntu.com hardy-security/restricted Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://security.ubuntu.com hardy-security/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://security.ubuntu.com hardy-security/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://ppa.launchpad.net hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://ppa.launchpad.net hardy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://ppa.launchpad.net gutsy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://ppa.launchpad.net gutsy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://playonlinux.botux.net hardy Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://playonlinux.botux.net hardy/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://wine.budgetdedicated.com etch Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Err http://wine.budgetdedicated.com etch/main Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)
Reading package lists... Done
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/partner/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). -connect (111 Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://ppa.launchpad.net/compiz/ubuntu/dists/hardy/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://ppa.launchpad.net/compiz/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). -connect (111 Connection refused)

W: Failed to fetch http://ppa.launchpad.net/corenominal/ubuntu/dists/gutsy/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://ppa.launchpad.net/corenominal/ubuntu/dists/gutsy/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://playonlinux.botux.net/dists/hardy/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://playonlinux.botux.net/dists/hardy/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/etch/Release.gpg  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connectionrefused)

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/etch/main/i18n/Translation-en_US.bz2  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
```


any ideas? I can get online ok, I am posting on the same computer now. I did try and install Debian Lenny to another Hard drive, but the install failed so I wiped it. Shouldn't have affected this HD though.

---

### Post by rishabh on 2008-10-09
Looks like a proxy problem.
Type 
```
$http_proxy
```
(with the $ symbol)
or try 
```
set | grep proxy
```
and post the result.

---

### Post by SteveNorman on 2008-10-09
heres the results, I did try and download jap proxy

```
$ $http_proxy
bash: http://localhost:4001: No such file or directory
```

```
~$ set | grep proxy
http_proxy='http://localhost:4001 '
                                -http-proxy -ftp-proxy -download-dir \
```

---

### Post by rishabh on 2008-10-09
Yes! You are proxied!
Is this absolutely necessary for you? I think the problem will go away if you purge the package.

---

### Post by SteveNorman on 2008-10-09
weird though,when i do an ip look up it shows that I am not anonymous. I like my privacy,,but I like my updates also.

---

### Post by rishabh on 2008-10-09
Have you tried Tor and Privoxy?

---

### Post by SteveNorman on 2008-10-09
no I have Tor and anon-proxy. I was hoping to get anon-proxy to work like it does on a windows system,,with the little gui security meter.

---

### Post by SteveNorman on 2008-10-09
That worked,,Thanks a bunch!

---

### Post by rishabh on 2008-10-09
> **SteveNorman said:**
> That worked,,Thanks a bunch!
Any time :)

---

