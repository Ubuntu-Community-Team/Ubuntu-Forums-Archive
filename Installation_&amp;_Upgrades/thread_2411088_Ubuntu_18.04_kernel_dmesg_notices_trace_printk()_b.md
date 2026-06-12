---
title: "Ubuntu 18.04 kernel dmesg notices trace_printk() being used"
date: 2019-01-24
forum: Installation &amp; Upgrades
---

### Post by jzambon on 2019-01-24
Getting strange notices in my dmesg since upgrading to 18.04 Server...

```
[    7.608371] **********************************************************
[    7.608372] **   NOTICE NOTICE NOTICE NOTICE NOTICE NOTICE NOTICE   **
[    7.608372] **                                                      **
[    7.608373] ** trace_printk() being used. Allocating extra memory.  **
[    7.608373] **                                                      **
[    7.608374] ** This means that this is a DEBUG kernel and it is     **
[    7.608374] ** unsafe for production use.                           **
[    7.608375] **                                                      **
[    7.608375] ** If you see this message and you are not debugging    **
[    7.608375] ** the kernel, report this immediately to your vendor!  **
[    7.608376] **                                                      **
[    7.608376] **   NOTICE NOTICE NOTICE NOTICE NOTICE NOTICE NOTICE   **
[    7.608377] **********************************************************

```

After a while, network traffic causes a bunch more notices to pop up...

```
[  674.794021] IN=eno1 OUT=eno1 MAC=48:4d:7e:82:6c:91:48:4d:7e:82:6d:7f:08:00 SRC=192.168.2.22 DST=X.X.X.X LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=37484 DF PROTO=TCP SPT=37036 DPT=631 WINDOW=29200 RES=0x00 SYN URGP=0 
[  675.791987] IN=eno1 OUT=eno1 MAC=48:4d:7e:82:6c:91:48:4d:7e:82:6c:f9:08:00 SRC=192.168.2.23 DST=X.X.X.X LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=53369 DF PROTO=TCP SPT=45906 DPT=631 WINDOW=29200 RES=0x00 SYN URGP=0 
[  675.802363] IN=eno1 OUT=eno1 MAC=48:4d:7e:82:6c:91:48:4d:7e:82:6d:7f:08:00 SRC=192.168.2.22 DST=X.X.X.X LEN=60 TOS=0x00 PREC=0x00 TTL=63 ID=37485 DF PROTO=TCP SPT=37036 DPT=631 WINDOW=29200 RES=0x00 SYN URGP=0 

```

This server is the head node on a cluster and has 2 interfaces.  The one interface consistently references (eno1) is the internal ethernet adapter.  The other interface talks to the outside world and doesn't show any messages but is the DST in all the messages (redacted: X.X.X.X)

Any ideas?

Thanks!

---

### Post by Doug S on 2019-01-24
For the first one: Could you add which kernel version? i.e. the output from "uname -a". Example:

```
$ uname -a
Linux s17 4.15.0-43-generic #46-Ubuntu SMP Thu Dec 6 14:45:28 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```

For the second one: It looks like logging entries from an iptables rule set, just with no log prefix added. Try this command to show the rule set "sudo iptables -v -x -n -L" and "sudo iptables -t nat -v -x -n -L", although it might be difficult to correlate the rule set with the log entries without a unique log prefix, but the packet counters might help.

---

