---
title: "kworker hang at 100% due to nfs-server."
date: 2014-05-05
forum: Installation &amp; Upgrades
---

### Post by alfton on 2014-05-05
after Upgrade from xubuntu 12.04 to 14.04 I have a problem with kworker using 100% cpu constant at 1 cpu.
strange thing is that htop does not se the hang, but top does,

top say   
55 root      20   0       0      0      0 R  99,9  0,0   4021:26 kworker/6:0                                                                                                                                                                                                 

here is some printout from perf

+   0,68%      kworker/6:0  [kernel.kallsyms]                   [k] _raw_spin_lock_bh
+   0,63%      kworker/6:0  [kernel.kallsyms]                   [k] _raw_spin_unlock
+   0,55%      kworker/6:0  [kernel.kallsyms]                   [k] _raw_spin_lock
+   0,49%      kworker/6:0  [kernel.kallsyms]                   [k] _raw_spin_unlock_bh
+   0,37%      kworker/6:0  [kernel.kallsyms]                   [k] xs_sock_reset_connection_flags
+   0,36%      kworker/6:0  [kernel.kallsyms]                   [k] md5_transform
+   0,36%      kworker/6:0  [kernel.kallsyms]                   [k] __ip_route_output_key
+   0,34%      kworker/6:0  [kernel.kallsyms]                   [k] kfree
+   0,30%      kworker/6:0  [kernel.kallsyms]                   [k] kmem_cache_alloc_node
+   0,29%      kworker/6:0  [kernel.kallsyms]                   [k] _raw_spin_lock_irqsave
+   0,29%      kworker/6:0  [kernel.kallsyms]                   [k] fib_table_lookup
+   0,29%      kworker/6:0  [kernel.kallsyms]                   [k] process_one_work
+   0,28%      kworker/6:0  [kernel.kallsyms]                   [k] ip_finish_output
+   0,28%      kworker/6:0  [kernel.kallsyms]                   [k] _raw_spin_unlock_irqrestore
+   0,27%      kworker/6:0  [kernel.kallsyms]                   [k] kmem_cache_free
+   0,27%      kworker/6:0  [kernel.kallsyms]                   [k] __do_softirq
+   0,26%      kworker/6:0  [kernel.kallsyms]                   [k] local_bh_disable
+   0,25%      kworker/6:0  [kernel.kallsyms]                   [k] __netif_receive_skb_core
+   0,24%      kworker/6:0  [kernel.kallsyms]                   [k] dst_release
+   0,23%      kworker/6:0  [kernel.kallsyms]                   [k] insert_work
+   0,22%      kworker/6:0  [kernel.kallsyms]                   [k] __kmalloc_node_track_caller
+   0,22%      kworker/6:0  [kernel.kallsyms]                   [k] net_rx_action
+   0,22%      kworker/6:0  [kernel.kallsyms]                   [k] tcp_v4_rcv
+   0,22%      kworker/6:0  [kernel.kallsyms]                   [k] native_read_tsc
+   0,22%      kworker/6:0  [kernel.kallsyms]                   [k] __alloc_skb
+   0,21%      kworker/6:0  [kernel.kallsyms]                   [k] sock_def_error_report
+   0,21%      kworker/6:0  [kernel.kallsyms]                   [k] local_bh_enable
+   0,20%      kworker/6:0  [kernel.kallsyms]                   [k] tcp_transmit_skb
+   0,20%      kworker/6:0  [kernel.kallsyms]                   [k] __ip_dev_find

some last messages form dmsg
[   41.715919] type=1400 audit(1399033377.638:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1010 comm="apparmor_parser"
[   41.715925] type=1400 audit(1399033377.638:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=1010 comm="apparmor_parser"
[   41.716211] type=1400 audit(1399033377.638:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1010 comm="apparmor_parser"
[   41.805717] type=1400 audit(1399033377.726:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=1069 comm="apparmor_parser"
[   41.805724] type=1400 audit(1399033377.726:12): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1069 comm="apparmor_parser"
[   41.805729] type=1400 audit(1399033377.726:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1069 comm="apparmor_parser"
[   41.805827] type=1400 audit(1399033377.726:14): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=1072 comm="apparmor_parser"
[   41.806074] type=1400 audit(1399033377.730:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1069 comm="apparmor_parser"
[   41.806079] type=1400 audit(1399033377.730:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1069 comm="apparmor_parser"
[   41.806234] type=1400 audit(1399033377.730:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=1069 comm="apparmor_parser"
[   41.862345] init: cups main process (1019) killed by HUP signal
[   41.862356] init: cups main process ended, respawning
[   42.352325] init: Failed to spawn hybrid-gfx main process: unable to execute: No such file or directory

Is there anyone else that have this problem, and maybe could point me in the right directions to fix this?

best regards Alfton

---

### Post by alfton on 2014-05-06
after some digin I found the couse of the 100% cpu usage, its the nfs-kernel-server that causing abit problem, this was not a problem before the update. Is there anyone that maybe have a pointer on what I can do to fix this?

---

### Post by mörgæs on 2014-05-06
Does the same happen in a live boot of 14.04?

---

### Post by alfton on 2014-05-07
as long as the nfs-server-kernel is not enable the 100% cpu does not happend. 
its only when I activate nfs-kernel-server that 1 cpu constant is using 100%. I can try reinstall to if the problem goes away, but that is gonna be some work. Alot of setup to do.;)

strange thing is that the computer that use the nfs share does not have any problem playback content from the nfs share, so I dont se the as a big problem, and sins I have 7 more cores to pick from, does not the 1 core 100% hang affect anything on the system. It will one day be solved anyway I guess.

---

### Post by alfton on 2014-05-26
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1322406](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1322406)

finaly not only me that experience this bug

---

