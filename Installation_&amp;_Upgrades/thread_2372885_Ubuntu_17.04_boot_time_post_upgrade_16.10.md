---
title: "Ubuntu 17.04 boot time post upgrade 16.10"
date: 2017-09-29
forum: Installation &amp; Upgrades
---

### Post by calabrache on 2017-09-29
Hello 
Ubuntu migrated from 16.10 to 17.04 and has been taking quite long to boot - here is the dmesg. Any orientation ?
[   56.252214] perf: interrupt took too long (2602 > 2500), lowering kernel.perf_event_max_sample_rate to 76750
[   64.431004] perf: interrupt took too long (3258 > 3252), lowering kernel.perf_event_max_sample_rate to 61250
[   89.123345] ISO 9660 Extensions: RRIP_1991A
[  122.154875] perf: interrupt took too long (4170 > 4072), lowering kernel.perf_event_max_sample_rate to 47750
[  141.284368] perf: interrupt took too long (5328 > 5212), lowering kernel.perf_event_max_sample_rate to 37500
[  171.641647] perf: interrupt took too long (6723 > 6660), lowering kernel.perf_event_max_sample_rate to 29750
[  396.484132] perf: interrupt took too long (8416 > 8403), lowering kernel.perf_event_max_sample_rate to 23750
[  501.625831] perf: interrupt took too long (10521 > 10520), lowering kernel.perf_event_max_sample_rate to 19000
[  510.299553] NET: Registered protocol family 40
[  511.010028] kauditd_printk_skb: 28 callbacks suppressed
[  511.010030] audit: type=1400 audit(1506717505.287:40): apparmor="DENIED" operation="capable" profile="/usr/sbin/cupsd" pid=9907 comm="serial" capability=21  capname="sys_admin"
[  664.856971] perf: interrupt took too long (13227 > 13151), lowering kernel.perf_event_max_sample_rate to 15000
tor@tor-virtual-machine:~$ lstB

---

