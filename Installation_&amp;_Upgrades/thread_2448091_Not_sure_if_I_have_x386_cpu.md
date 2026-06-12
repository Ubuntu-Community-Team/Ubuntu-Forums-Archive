---
title: "Not sure if I have x386 cpu"
date: 2020-08-01
forum: Installation &amp; Upgrades
---

### Post by cgoes on 2020-08-01
I am currently running server edition of 18.04 on dual cpu Intel Xeon CPU E3110 @ 3.00 GHz, 64bit. There is a caution about upgrading to 20.04. Don't want to do anything before I'm sure I will be ok, since this is a production machine. Thanks.

---

### Post by deadflowr on 2020-08-01
```
uname -a
```
will tell you if running 32-bit or 64-bit.

32-bit will show as i686
64-bit will show as x86_64

---

### Post by zebra2 on 2020-08-01
This should ID your processor.

```
 cat /sys/devices/cpu/caps/pmu_name    
```

---

### Post by crip720 on 2020-08-01
Might running 32b version of 18.04, 20.04 does not have 32b, which is why the warning.  Have at least three years before needing to upgrade, which might need a new install to 64 bit version.

---

### Post by grahammechanical on 2020-08-01
According to the ISO bug tracker Ubuntu 18.04 Server edition does not have a 32 bit version. The Flavours of Ubuntu have 32 bit versions but not Ubuntu Desktop or Ubuntu server.

[http://iso.qa.ubuntu.com/qatracker/milestones/389/builds](http://iso.qa.ubuntu.com/qatracker/milestones/389/builds)

And according to Intel the Xenon E3110 is 64bit

[https://ark.intel.com/content/www/us/en/ark/products/34694/intel-xeon-processor-e3110-6m-cache-3-00-ghz-1333-mhz-fsb.html](https://ark.intel.com/content/www/us/en/ark/products/34694/intel-xeon-processor-e3110-6m-cache-3-00-ghz-1333-mhz-fsb.html)

>                             Instruction Set                                                                                                                                          64-bit                                         

Regards

---

### Post by ActionParsnip on 2020-08-02
OK, what is the output of
```

uname -a

```

Thanks

---

### Post by cgoes on 2020-08-03
Linux richese 4.15.0-112-generic #113-Ubuntu SMP Thu Jul 9 23:41:06 UTC 2020 i68   6 i686 i686 GNU/Linux

---

### Post by deadflowr on 2020-08-03
Yep.
i686,i386 is 32-bit no longer supported going forward,
except for a select few applications:
See
[https://ubuntu.com/blog/statement-on-32-bit-i386-packages-for-ubuntu-19-10-and-20-04-lts]("https://ubuntu.com/blog/statement-on-32-bit-i386-packages-for-ubuntu-19-10-and-20-04-lts")
[https://discourse.ubuntu.com/t/community-process-for-32-bit-compatibility/12598]("https://discourse.ubuntu.com/t/community-process-for-32-bit-compatibility/12598")

Basically this means there is no upgrade path.
Any upgrades offered will be crippled.
So do not take them if offered.
Were you actually offered an upgrade?

Your choices are to continue on with 18.04 for the foreseeable future.
Or figure out the best time to do a fresh install of 20.04 64-bit (amd64 is 64-bit for all cpus; intel and amd)

---

