---
title: "Upgrade to Fiesty - VMWare Server Issue"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by Raedwald on 2007-04-20
This problem has now been resolved.


I've just upgraded (using update manager) to 7.04 from 6.10.

Under 6.10 I had VMWare Server installed, and it ran fine (use it to run MS Publisher as I can't find anything else that will work with .pub files).

Following the upgrade, attempting to reinstall VMWare gives the following error:


Using 2.6.x kernel build system.

make: Entering directory `/tmp/vmware-config0/vmmon-only'

make -C /lib/modules/2.6.20-15-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules

make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'

  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o

In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:

/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;compat_exit&#8217;

/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;exit_code&#8217;

/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_syscall1&#8217;

make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1

make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2

make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'

make: *** [vmmon.ko] Error 2

make: Leaving directory `/tmp/vmware-config0/vmmon-only'

Unable to build the vmmon module.



Anyone got any ideas as to what/why and what I can do to sort it?

---

### Post by tatster on 2007-04-20
Hi, 

Not any ideas yet but just want to add that I am having the same problem.
Off to carry on searching....

Tat.

---

### Post by tatster on 2007-04-20
Hi,

I've got mine working on Feisty.

I had to install g++ with a quick ```
sudo apt-get install g++
```

And then I re-ran vmware-config.pl and hew presto Vmware compiled for the new Feisty kernel and I'm happily in Vm-land!!

Hope this helps,

Tat.

---

### Post by Raedwald on 2007-04-20
Just gave that a try, but I get exactly the same error result :(

---

### Post by tatster on 2007-04-20
Ok
 - the other thing I did was to use the vmware any-any patch as mentioned in [http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0]("http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0")

Tat.

---

### Post by Raedwald on 2007-04-20
That's got it.

Thankyou :)

---

### Post by ampop on 2007-04-20
It solved my problem too. Thank you very much.

---

### Post by tatster on 2007-04-21
Excellent news guys.

Raedwald - perhaps you'd like to go back and edit your first post to change it to resolved so others know it's fixed.

Tat.

---

### Post by kraz on 2007-04-22
Thnaks a lot...took some time for me to find this tip, and that did the trick for me too!:guitar:

---

### Post by dro0g on 2007-04-22
> **tatster said:**
> Ok
 - the other thing I did was to use the vmware any-any patch as mentioned in [http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0]("http://www.vmware.com/community/thread.jspa?messageID=76957&tstart=0")

Tat.

Thanks! that worked for me as well.

---

### Post by reality_hunter on 2007-04-23
also thanks , how do I istall that any any patch????

---

### Post by reality_hunter on 2007-04-23
thank i git it

---

### Post by leep on 2007-04-23
It worked for me too. I have only a problem: I would like to add the vmware consolle to the application menu. How do i do?
Thank u in advance,
S.

---

