---
title: "How to upgrade perl 5.10 to 5.15 in ubuntu 10.04LTS"
date: 2012-01-30
forum: Installation &amp; Upgrades
---

### Post by AnuragSatish on 2012-01-30
:KSHi,


Can anyone tell me how to upgrade perl 5.10 version in ubuntu 10.04LTS to the latest version available now i.e. 5.15?


Regards,
Anurag Satish.P

---

### Post by markp_2000 on 2012-01-31
Yes, I would like to know as well.  I ran 

```
perl -MCPAN -e 'upgrade'
```

But is crashed and burned.


```
Running install for module 'vmsish'
The most recent version "1.03" of the module "vmsish"
is part of the perl-5.15.4 distribution. To install that, you need to run
  force install vmsish   --or--
  install F/FL/FLORA/perl-5.15.4.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'warnings'
The most recent version "1.12" of the module "warnings"
is part of the perl-5.15.4 distribution. To install that, you need to run
  force install warnings   --or--
  install F/FL/FLORA/perl-5.15.4.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
Running install for module 'warnings::register'
The most recent version "1.02" of the module "warnings::register"
is part of the perl-5.15.4 distribution. To install that, you need to run
  force install warnings::register   --or--
  install F/FL/FLORA/perl-5.15.4.tar.gz
Running make test
  Can't test without successful make
Running make install
  Make had returned bad status, install seems impossible
```

I ran the suggestions but they did not work as well.

Any help would be appreciated.

Mark

---

### Post by pmuniz on 2012-05-03
You need install make before.
sudo apt-get install make then you run perl -MCPAN -e 'upgrade'

install make is necessary but does not resolve.

---

