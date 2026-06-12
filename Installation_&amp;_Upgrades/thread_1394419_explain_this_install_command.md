---
title: "explain this install command"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by dd1313 on 2010-01-30
Hi Guys

I picked up this code from here [http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4](http://www.howtoforge.com/perfect_setup_ubuntu_6.06_p4)

```
apt-get install binutils cpp cpp-4.0 fetchmail flex gcc gcc-4.0 libarchive-zip-perl libc6-dev libcompress-zlib-perl libdb4.3-dev libpcre3 libpopt-dev linux-kernel-headers lynx m4 make ncftp nmap openssl perl perl-modules unzip zip zlib1g-dev autoconf automake1.9 libtool bison autotools-dev g++

```

I then get the following response

```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ncftp
```

What does that mean please ?

I am using 6.06 LTS server

can someone help me with a line feed after each install above so I know the names of the packages.

THanks
Dev

---

### Post by falconindy on 2010-01-30
Pretty straightforward. You've got the package 'ncftp' listed in your install command and its not being found by apt. Remove it from the string and try running it again.

---

### Post by dd1313 on 2010-01-30
> **falconindy said:**
> Pretty straightforward. You've got the package 'ncftp' listed in your install command and its not being found by apt. Remove it from the string and try running it again.

thanks

what is ncftp and how can I get it please ?

THanks
Dev

---

### Post by howefield on 2010-01-30
[http://packages.ubuntu.com/dapper/ncftp](http://packages.ubuntu.com/dapper/ncftp)

---

### Post by dd1313 on 2010-01-30
> **howefield said:**
> [http://packages.ubuntu.com/dapper/ncftp](http://packages.ubuntu.com/dapper/ncftp)

thank you

---

