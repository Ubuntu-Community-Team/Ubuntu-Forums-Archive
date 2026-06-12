---
title: "recently updated ubuntu kernel question"
date: 2013-01-07
forum: Installation &amp; Upgrades
---

### Post by nepalnt21 on 2013-01-07
so i had ubuntu , probably lucid lynx or another right around there, and had added the ubuntu studio audio packages. the other day, i updated to the latest ubuntu, and it also updated to the latest version of the us-audio packages. 

my question is, will the update have given me the ubuntu studio low latency kernel? how do i find out if it is so? and if not, how might i go about getting it ? (never compiled a kernel before :oops:)

thanks for any help

):P

---

### Post by ibjsb4 on 2013-01-07
In terminal

```
uname -a
```

Will tell you what kernel your running.

The low lat kernel is 3.2.0-29.46

---

### Post by nepalnt21 on 2013-01-07
im getting 

3.2.0-35-generic-pae

shall i follow a tutorial on compiling a new linux kernel? 

where is the best place to get the low latency kernel?

or, would that be unnecessary if i am using jackd with the realtime box checked, and am running all of my audio programs through it???

---

