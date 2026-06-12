---
title: "apt-get update lucid-security GPG error"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by agnawt on 2011-06-11
Hi,

I get this error when running apt-get update on Ubuntu 10.04.1 Server.  Never got it before today, apt-get update is always error-free, unless there are connection issues.

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release)

W: Some index files failed to download, they have been ignored, or old ones used instead.

Any advice would be appreciated.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **agnawt said:**
> Hi,

I get this error when running apt-get update on Ubuntu 10.04.1 Server.  Never got it before today, apt-get update is always error-free, unless there are connection issues.



Any advice would be appreciated.

You added a repository without adding the PGP key?

Which PPA or Repository were you trying to add? 

:popcorn:

---

### Post by agnawt on 2011-06-11
I did not add any repo (manually) without adding a corresponing PGP key.  These are "built-in" repo(s) AFAIK.  I can see it fail on
> Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
during apt-get update

Specifically from my /etc/apt/sources.list:
```
deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
```

Commenting out those lines removed the error.

Okay, that is weird, I un-commented them one-by-one and even with them all un-commented there is still no error now.  What happened here?  Some little cache get flushed?

Still all working.  Weird.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **agnawt said:**
> I did not add any repo (manually) without adding a corresponing PGP key.  These are "built-in" repo(s) AFAIK.  I can see it fail on

during apt-get update

Specifically from my /etc/apt/sources.list:
```
deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
```Commenting out those lines removed the error.

Okay, that is weird, I un-commented them one-by-one and even with them all un-commented there is still no error now.  What happened here?  Some little cache get flushed?

Still all working.  Weird.

You could re-enable them and try this:
```

sudo rm -rf /var/lib/apt/lists/* 
sudo apt-get update

```

You are going to want to have those available for security reasons, just saying. :)

---

### Post by agnawt on 2011-06-11
Yeah, it still works after that "flush" so something probably was broken, maybe in /var/lib/apt/lists/ maybe I'll never know unless it happens again and I empty that dir again.  Thanks for the tip.

---

