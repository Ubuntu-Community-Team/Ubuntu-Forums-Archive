---
title: "ubuntu dapper secority repo errors"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by giohappy on 2006-11-28
I've been all the day trying to install some packages with apt I need to compile some software. In most tha cases I have apt errors like this:

"Unable to get [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8a-7ubuntu0.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl-dev_0.9.8a-7ubuntu0.3_i386.deb)  MD5 sum mismatching"

(error translated from italian, maybe not corrisponding to the english errors...)

These errors are always raised with security repo, alsa when updating the system... 
This is my source.list:


    # Ubuntu supported packages (packages, GPG key: 437D05B5)
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

    # Ubuntu community supported packages (packages, GPG key: 437D05B5)
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
    deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

    # Ubuntu backports project (packages, GPG key: 437D05B5)
    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

Can anyone help me?!!!
Giovanni

---

### Post by giohappy on 2006-11-28
up

---

