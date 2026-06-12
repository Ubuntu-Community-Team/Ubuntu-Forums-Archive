---
title: "How to install TorquePBS on Ubuntu 17.10?"
date: 2018-01-23
forum: Installation &amp; Upgrades
---

### Post by nimble2005 on 2018-01-23
Hi all, 

I recently installed Ubuntu 17.10 on my new PC with AMD Ryzen platform. Now I want to install Torque PBS (version: torque-4.2.6) on 17.10 but failed. 
The configure procedure went well while error continues to show up during the make process, as

```
job_attr_def.c:1239:3: error: invalid conversion from &#8216;char&#8217; to &#8216;int (*)(pbs_attribute*, void*, int)&#8217; [-fpermissive]
};

Makefile:643: recipe for target 'job_attr_def.o' failed

```

I used to successfully installed Torque on 16.04LTS through apt-get packages according to this [guide]("https://jabriffa.wordpress.com/2015/02/11/installing-torquepbs-job-scheduler-on-ubuntu-14-04-lts/"). But unfortrunately, I cannot find torque packages in the current source. It seems like the error relates to the gcc compilation and my current gcc complier version is 7.2.0. I do not know if I should use an older version of gcc? So, has anyone successfully installed Torque on 17.10 so far? I need some help and thanks in advance!

Bo-Yuan

---

### Post by yoyobrain on 2018-02-13
Hi Bo-Yuan.  I ran into similar problems with Torque after upgrading to the latest gcc.

I was able to build Torque 6.0.3 from source with gcc-7.2.0 by setting the environment variable 'CFLAGS=-fpermissive'

Hope this helps.

---

