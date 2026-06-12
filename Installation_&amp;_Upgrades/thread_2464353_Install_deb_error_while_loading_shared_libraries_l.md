---
title: "Install deb: error while loading shared libraries: libc.so.6"
date: 2021-06-30
forum: Installation &amp; Upgrades
---

### Post by pilot8 on 2021-06-30
I built libc6-2.28 from source code. Then I created deb file. I used the control file and post/pre scripts from the standard libc6_2.28-0ubuntu1_armhf.deb. I also have the same files and folder structure as that of the official deb file.


But when I install it, I got errors:
```
$ sudo dpkg --debug=72200 -i libc6_2.28-0ubuntu1_armhf.deb
(Reading database ... 19303 files and directories currently installed.)
Preparing to unpack libc6_2.28-0ubuntu1_armhf.deb ...
D020000: trigproc_activate_packageprocessing pkg=libc6:armhf
D010000: trigproc_enqueue_deferred pend=libc-bin:armhf
D000200: process_archive conffile '/etc/ld.so.conf.d/arm-linux-gnueabihf.conf' in package libc6:armhf - conff ?
D000200: pkg_conffiles_mark_old '/etc/ld.so.conf.d/arm-linux-gnueabihf.conf' namenode '/etc/ld.so.conf.d/arm-linux-gnueabihf.conf' flags 5
D020000: post_script_tasks - ensure_diversions
D020000: post_script_tasks - trig_incorporate
Unpacking libc6:armhf (2.28-0ubuntu1) over (2.28-0ubuntu1) ...
D000200: conffderef in='/etc/ld.so.conf.d/arm-linux-gnueabihf.conf' current working='/etc/ld.so.conf.d/arm-linux-gnueabihf.conf'
D000200: tarobject conffile extracted
/bin/sh: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dpkg: warning: old libc6:armhf package post-removal script subprocess returned error exit status 127
dpkg: trying script from the new package instead ...
/bin/sh: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dpkg: error processing archive libc6_2.28-0ubuntu1_armhf.deb (--install):
 new libc6:armhf package post-removal script subprocess returned error exit status 127
D020000: post_script_tasks - ensure_diversions
D020000: post_script_tasks - trig_incorporate
/bin/sh: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dpkg: error while cleaning up:
 installed libc6:armhf package pre-installation script subprocess returned error exit status 127
D020000: post_script_tasks - ensure_diversions
D020000: post_script_tasks - trig_incorporate
D010000: trigproc_run_deferred
D010000: trigproc libc-bin:armhf
Errors were encountered while processing:
 libc6_2.28-0ubuntu1_armhf.deb



```Could you tell me what exactly is wrong? 


By installing the official libc6_2.28-0ubuntu1_armhf.deb. There is no such problem.


Thanks in advance!

---

