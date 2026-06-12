---
title: "Can't boot LiveCD on Acer Aspire 5520-5912 laptop"
date: 2010-03-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by MCVenom on 2010-03-11
**Bug reported here: [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538310](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538310)**

Hey guys. I decided to try the Lucid Lynx daily build (March 10) and ran into some problems. I've doublechecked the MD5 and burned the CD twice at slowest speed. After choosing the 'Try without installing' option / letting it try to auto-boot into the LiveCD enviroment, I always get a CLI type interface which displays the following:

> [(process:355): GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)
                                   init: uread
ahead-other main process (1264) terminated with status 4
init: ureadahead-other main process (1265) terminated with status 4
init: ureadahead-other main process (1266) terminated with status 4
could not write bytes: Broken pipe
                                                            [  242.748086] INFO: task plymouthd:355 blocked for more than 120 seconds.
[  242.748127] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
](*,)
I am seemingly unable to input anything; also when I tried an Alpha 3 LiveCD it seemed to hang endlessly at the boot screen. I think from the last few lines that this has to do with the Plymouth bugs that have been turning up, but I can't say for sure. Is there a Launchpad bug filed or should I file the report myself? And what information should I include in the report?

---

### Post by MCVenom on 2010-03-12
I've checked Launchpad and didn't see any bugs reported similar to mine, so I'll just go ahead and report it.

---

### Post by MCVenom on 2010-03-12
Bug reported here: [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538310](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/538310)

---

### Post by wilee-nilee on 2010-03-12
I have found that the daily cd can be loaded to a thumb with unetbootin, when it doesn't seem to burn a bootable cd. unetbootin has a windows version and there is one in linux.

when using the thumb boot it runs a stock unetbootin boot screen hit enter I believe I never looked for a time out, then hit tab to access the boot info then enter.

---

