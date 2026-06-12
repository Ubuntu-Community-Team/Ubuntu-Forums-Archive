---
title: "Cannot get to repositories"
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by Squrdel on 2006-12-10
For the last week I have not been able to  connect to the repos. I am posting my sources.list file and the error message from Synaptic. If anyone can help, please do. I should say that I did a clean reinstall of Dapper (4 times!) and can't install apps. by any method - Synaptic, terminal, apt, Automatix. Automatix error message says that there is an 'apt-based error'.

sources.list

# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


Error message

[http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out


What's with the 1.0.0.0 ? Can that be right?

A big thanks to anyone who can put me on the path to enlightenment!

---

### Post by louieb on 2006-12-10
"http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:"
For some reason the is a colon at the end of the first link you posted in the error section and that why the URL can't be found.  
Without the colon it brings up this:
```
-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.1 (GNU/Linux)

iD8DBQBEfegyQJdur0N9BbURAqolAJ9iJ/U2GV6O1s7/U4lA/ALCEMZ9OwCfXx1d
WaT9VElYazKOfHUydYtaoeg=
=Wwyu
-----END PGP SIGNATURE-----

```
Sorry don't know how to fix it.

---

### Post by arnieboy on 2006-12-10
you are probably behind a proxy. if yes, read the following:
[http://getautomatix.com/wiki/index.php?title=Proxy_configuration](http://getautomatix.com/wiki/index.php?title=Proxy_configuration)
also add your ftp and http proxies to ~/.bashrc

---

