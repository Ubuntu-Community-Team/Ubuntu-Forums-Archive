---
title: "Cannot boot up after upgrade"
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by todd-armstrong on 2011-07-04
Hi,
 
After installing the upgrade package to 11.04, ubuntu cannot boot up and shows the following:
 
/sbin/init: /opt/NAI/LinuxShield/lib/libc.so.6: version 'GLIBC_2.10' not found required by /lib/libdbus-1.so.3)
 
[1.972459] Kernel panic - not synching: Attempted to kill init!
[1.972507] Pid:1, comm: init Not tainted 2.6.35*22-generic #35-Ubuntu
[1.972604] forget_original_parent+0x2e4/0x2f0
[1.972651] ? call_rcu+0xd/0x10
[1.972651] ? exit_notify+0x13/0170
 
Can someone help please?
 
Thanks.

---

### Post by lister171254 on 2011-08-16
Just performed an update on my laptop running 11.04 and am now unable to boot as I get the same error re. not finding libdbus-1.so.3

---

