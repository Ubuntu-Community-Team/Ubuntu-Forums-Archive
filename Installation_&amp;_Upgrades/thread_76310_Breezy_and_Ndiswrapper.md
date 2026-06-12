---
title: "Breezy and Ndiswrapper"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by Wmknox on 2005-10-14
I just upgraded to breezy, which totally killed ndiswrapper, and my nvidia drivers. Because I upgraded using apt-get, I have no access to any cds to reinstall anything, which has proven to be a bit of a problem. I had originally compiled ndiswrapper (1.3rc1) from source, and it worked perfectly until the upgrade. However, now whenever ndiswrapper is modprobed, it gives me the following error:

```
[4295895.182000] ndiswrapper (wrapper_init:1534): loadndiswrapper failed (1536); check system log for messages from 'loadndisdriver'
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
```

Until this is fixed, I can't reinstall my nvidia drivers, which makes starting X impossible. Any help would be greatly appreciated.

Edit: I've noticed that Ndiswrapper only refuses to work on the new kernel option that appears on grub. If I select the old one, it works fine.

---

### Post by justbrian on 2005-10-14
Hey Wmknox,

ndiswrapper is indeed a kernel-specific piece of software. You will need to rebuild the kernel module for the new kernel you received after upgrading to Breezy by booting into your new kernel and re-executing the make->make install process you used to build ndiswrapper initially. This will rebuild the ndiswrapper modules for your new kernel.

As you might suspect, this process will need to be repeated for your nvidia drivers as well.

Hope this helps, I had to do it too on this Dell laptop, keep the thread going if you have any more questions.

Thanks,

Brian

---

### Post by Wmknox on 2005-10-15
The problem is, I am completely unaware as to how it is I do this. I had done it once, but I am now unable to remember how it was I did it.

Edit: Following the steps from [https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28ndiswrapper%29), the make deb command works, until I get this error: ```
Can't find kernel sources in /lib/modules/2.6.12-9-386/build;
     give the path to kernel sources with KSEC=<path> argument to make
```
Edit 2: Apparently I don't have the proper headers for breezy, apt-get states that they are not installed. Is there any way I could aquire them?

---

