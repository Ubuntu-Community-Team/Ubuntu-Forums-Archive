---
title: "100% CPU usage on one core by kworker/0:0-pm"
date: 2020-12-11
forum: Installation &amp; Upgrades
---

### Post by joiseystud on 2020-12-11
*note - process is actually kworker/0:3-pm but I don't know how to change the thread title here.  Sorry

New installation of ubuntu or pop os has kworker pm process running 100% of one core non stop.   Googled the problem, found some old solutions, but my system doesn't seem to have the same issue.

Computer is an HP elitedesktop mini G5 800.  

Here is the output of dmesg.  I see some errors in there, but not sure which may be the culprit.  Let me know if there are further troubleshooting steps I can take to help narrow this down.


[ATTACH]287528[/ATTACH][ATTACH]287528[/ATTACH]

here is the result of 
cat /proc/2434/status

Name:    kworker/0:3+pm
Umask:    0000
State:    R (running)
Tgid:    2434
Ngid:    0
Pid:    2434
PPid:    2
TracerPid:    0
Uid:    0    0    0    0
Gid:    0    0    0    0
FDSize:    64
Groups:     
NStgid:    2434
NSpid:    2434
NSpgid:    0
NSsid:    0
Threads:    1
SigQ:    0/30578
SigPnd:    0000000000000000
ShdPnd:    0000000000000000
SigBlk:    0000000000000000
SigIgn:    ffffffffffffffff
SigCgt:    0000000000000000
CapInh:    0000000000000000
CapPrm:    000000ffffffffff
CapEff:    000000ffffffffff
CapBnd:    000000ffffffffff
CapAmb:    0000000000000000
NoNewPrivs:    0
Seccomp:    0
Speculation_Store_Bypass:    thread vulnerable
Cpus_allowed:    1
Cpus_allowed_list:    0
Mems_allowed:    00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000001
Mems_allowed_list:    0
voluntary_ctxt_switches:    29635
nonvoluntary_ctxt_switches:    951232483

---

### Post by norobro on 2020-12-11
Did you see this thread on the kernel mailing list? [https://lkml.org/lkml/2020/7/20/278](https://lkml.org/lkml/2020/7/20/278)

---

