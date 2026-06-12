---
title: "Have to constantly restart mysql service"
date: 2012-05-12
forum: Installation &amp; Upgrades
---

### Post by nodetx on 2012-05-12
I'm running Ubuntu 12.04 on an EC2 Micro instance. I have a very small Joomla 1.5 site there. The server also has webmin, vsftp and awstats installed. Typically ram usage on the instance is around 40% in use, with about 20% average CPU use, and bursts to about 60% cpu usage so this is a very small system. It takes less than 1,000 hits per month.

I recently set this server up. It was running fantastic for a week straight without any crashes, and now it has suddenly started to crash. Simply restarting the mysql service solves the problem. When reviewing the syslog, there is 1 anomaly:
-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
```


May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736962] Out of memory: Kill process 707 (mysqld) score 131 or sacrifice child
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736980] Killed process 707 (mysqld) total-vm:889284kB, anon-rss:79356kB, file-rss:40kB
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.950933] init: mysql main process (707) killed by KILL signal
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.965710] init: mysql main process ended, respawning
May 12 10:43:02 ip-10-202-18-193 kernel: [46107.718122] type=1400 audit(1336819382.674:14): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7602 comm="apparmor_parser"
May 12 10:43:03 ip-10-202-18-193 kernel: [46108.361188] init: mysql main process (7606) terminated with status 1
May 12 10:43:03 ip-10-202-18-193 kernel: [46108.361224] init: mysql main process ended, respawning
May 12 10:43:04 ip-10-202-18-193 kernel: [46109.129996] init: mysql post-start process (7607) terminated with status 1
May 12 10:43:04 ip-10-202-18-193 kernel: [46109.147300] type=1400 audit(1336819384.102:15): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/mysqld" pid=7630 comm="apparmor_parser"
May 12 10:43:04 ip-10-202-18-193 kernel: [46109.244960] init: mysql main process (7634) terminated with status 1
May 12 10:43:04 ip-10-202-18-193 kernel: [46109.244996] init: mysql respawning too fast, stopped


```-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-

there is 1 other section of syslog prior to what is posted above. Maybe it doesn't matter, I'm sure. It might be junk so I'm putting it here instead of above. Anyway any ideas?

-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-

```

May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733505] oom_kill_process: 9 callbacks suppressed
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733511] apache2 invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0, oom_score_adj=0
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733515] apache2 cpuset=/ mems_allowed=0
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733519] Pid: 7562, comm: apache2 Not tainted 3.2.0-24-virtual #37-Ubuntu
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733522] Call Trace:
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733532]  [<ffffffff810bdabd>] ? cpuset_print_task_mems_allowed+0x9d/0xb0
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733539]  [<ffffffff81118131>] dump_header+0x91/0xe0
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733543]  [<ffffffff811184b5>] oom_kill_process+0x85/0xb0
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733546]  [<ffffffff8111885a>] out_of_memory+0xfa/0x220
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733550]  [<ffffffff8111e28a>] __alloc_pages_nodemask+0x7ea/0x800
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733556]  [<ffffffff816554ee>] ? _raw_spin_unlock_irqrestore+0x1e/0x30
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733562]  [<ffffffff81154c93>] alloc_pages_current+0xa3/0x110
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733566]  [<ffffffff81114e9f>] __page_cache_alloc+0x8f/0xa0
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733569]  [<ffffffff8111519e>] ? find_get_page+0x1e/0x90
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733573]  [<ffffffff81117022>] filemap_fault+0x212/0x3c0
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733577]  [<ffffffff81137242>] __do_fault+0x72/0x550
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733580]  [<ffffffff8113aada>] handle_pte_fault+0xfa/0x200
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733585]  [<ffffffff810067be>] ? xen_pmd_val+0xe/0x10
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733589]  [<ffffffff81005209>] ? __raw_callee_save_xen_pmd_val+0x11/0x1e
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733592]  [<ffffffff8113af98>] handle_mm_fault+0x1f8/0x350
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733597]  [<ffffffff81658ddb>] do_page_fault+0x14b/0x520
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733601]  [<ffffffff81174edd>] ? vfs_read+0x10d/0x180
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733605]  [<ffffffff81655a35>] page_fault+0x25/0x30
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733607] Mem-Info:
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733609] Node 0 DMA per-cpu:
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733612] CPU    0: hi:    0, btch:   1 usd:   0
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733614] Node 0 DMA32 per-cpu:
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733618] CPU    0: hi:  186, btch:  31 usd:  94
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733622] active_anon:135113 inactive_anon:31 isolated_anon:0
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733623]  active_file:263 inactive_file:268 isolated_file:0
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733624]  unevictable:0 dirty:0 writeback:0 unstable:0
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733625]  free:1369 slab_reclaimable:2289 slab_unreclaimable:2924
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733626]  mapped:265 shmem:66 pagetables:5275 bounce:0
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733628] Node 0 DMA free:2464kB min:72kB low:88kB high:108kB active_anon:11992kB inactive_anon:0kB active_file:0kB inactive_file:12kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:14524kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:52kB slab_unreclaimable:48kB kernel_stack:8kB pagetables:184kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:8 all_unreclaimable? yes
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733638] lowmem_reserve[]: 0 597 597 597
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733644] Node 0 DMA32 free:3012kB min:3088kB low:3860kB high:4632kB active_anon:528460kB inactive_anon:124kB active_file:1052kB inactive_file:1060kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:611856kB mlocked:0kB dirty:0kB writeback:0kB mapped:1060kB shmem:264kB slab_reclaimable:9104kB slab_unreclaimable:11648kB kernel_stack:1056kB pagetables:20916kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:3356 all_unreclaimable? yes
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733653] lowmem_reserve[]: 0 0 0 0
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733659] Node 0 DMA: 2*4kB 5*8kB 11*16kB 4*32kB 1*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 1*2048kB 0*4096kB = 2464kB
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733674] Node 0 DMA32: 239*4kB 5*8kB 0*16kB 1*32kB 1*64kB 1*128kB 1*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 3012kB
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733689] 613 total pagecache pages
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733691] 0 pages in swap cache
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733693] Swap cache stats: add 0, delete 0, find 0/0
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733695] Free swap  = 0kB
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.733696] Total swap = 0kB
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736717] 159472 pages RAM
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736719] 8381 pages reserved
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736721] 58665 pages shared
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736722] 147764 pages non-shared
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736724] [ pid ]   uid  tgid total_vm      rss cpu oom_adj oom_score_adj name
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736735] [  240]     0   240     4306       73   0       0             0 upstart-udev-br
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736739] [  247]     0   247     5395      167   0     -17         -1000 udevd
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736743] [  292]     0   292     5364      137   0     -17         -1000 udevd
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736746] [  293]     0   293     5364      137   0     -17         -1000 udevd
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736750] [  366]     0   366     3795       48   0       0             0 upstart-socket-
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736754] [  411]     0   411     1814      159   0       0             0 dhclient3
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736757] [  577]     0   577    12487      201   0     -17         -1000 sshd
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736761] [  587]   101   587    63427      117   0       0             0 rsyslogd
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736765] [  594]   102   594     5952      103   0       0             0 dbus-daemon
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736768] [  651]     0   651     3624       83   0       0             0 getty
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736772] [  660]     0   660     3624       82   0       0             0 getty
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736775] [  666]     0   666     3624       81   0       0             0 getty
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736778] [  668]     0   668     3624       84   0       0             0 getty
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736782] [  675]     0   675     3624       83   0       0             0 getty
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736785] [  687]     0   687     1080       69   0       0             0 acpid
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736789] [  688]     0   688     4776       91   0       0             0 cron
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736792] [  689]     0   689     4225       40   0       0             0 atd
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736796] [  707]   106   707   222321    19849   0       0             0 mysqld
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736800] [  728]   103   728    46895      327   0       0             0 whoopsie
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736803] [  753]     0   753    24391      392   0       0             0 proftpd
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736807] [  792]     0   792    74170     1563   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736811] [ 1198]     0  1198    20714     5015   0       0             0 miniserv.pl
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736815] [ 1208]     0  1208     3624       82   0       0             0 getty
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736818] [ 4398]    33  4398    79827     7016   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736822] [ 4866]    33  4866    77885     5088   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736825] [ 6269]    33  6269    80147     7221   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736829] [ 6527]    33  6527    79175     6351   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736833] [ 6604]    33  6604    80147     7348   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736836] [ 6605]    33  6605    79303     6479   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736840] [ 6843]    33  6843    80081     7190   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736843] [ 7184]    33  7184    79697     6857   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736847] [ 7187]    33  7187    79071     6230   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736850] [ 7212]    33  7212    78760     5944   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736854] [ 7555]    33  7555    76744     3911   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736857] [ 7556]    33  7556    76808     3968   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736860] [ 7557]    33  7557    76808     3973   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736864] [ 7558]    33  7558    77064     4150   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736867] [ 7559]    33  7559    76808     3973   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736871] [ 7560]    33  7560    76808     3974   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736874] [ 7561]    33  7561    76744     3911   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736878] [ 7562]    33  7562    76808     3844   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736881] [ 7563]    33  7563    76808     3853   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736885] [ 7564]    33  7564    76808     3858   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736888] [ 7565]    33  7565    76808     3858   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736892] [ 7566]    33  7566    76808     3858   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736895] [ 7567]    33  7567    76808     3858   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736899] [ 7568]    33  7568    76808     3858   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736902] [ 7569]    33  7569    76808     3858   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736906] [ 7581]    33  7581    76154     3097   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736909] [ 7582]    33  7582    76154     3097   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736913] [ 7583]    33  7583    76154     3097   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736916] [ 7584]    33  7584    75570     2866   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736920] [ 7585]    33  7585    75570     2866   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736923] [ 7586]    33  7586    75570     2866   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736927] [ 7587]    33  7587    75566     2917   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736930] [ 7588]    33  7588    75373     2695   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736934] [ 7589]    33  7589    75051     2381   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736937] [ 7590]    33  7590    74987     2320   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736941] [ 7591]    33  7591    74987     2308   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736944] [ 7592]    33  7592    74834     2178   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736948] [ 7593]    33  7593    74641     1993   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736952] [ 7594]    33  7594    74178     1414   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736955] [ 7595]    33  7595    74178     1414   0       0             0 apache2
May 12 10:43:01 ip-10-202-18-193 kernel: [46106.736958] [ 7596]    33  7596    74178     1414   0       0             0 apache2

```

---

### Post by SeijiSensei on 2012-05-12
Sure looks like you're running out of memory.  How big a virtual machine is this?  Anything less than 512M is probably too small these days.  Do you have swap enabled?  If not, you can add it to the system by [creating a swap file on disk]("http://www.cyberciti.biz/faq/linux-add-a-swap-file-howto/").

Some of the memory sizes in that log are absurdly large.  I've never used an EC2 instance, so I don't know what's  normal.  Try adding at least as much swap as physical memory and see if the problem disappears.  Also run "top" from the command prompt and see what it reports for memory usage.  On my VM at Linode with 768M running Apache, MailScanner (with two sendmail instances), and PostgreSQL, I have figures like this:

```

Mem:    768848k total,   655616k used,   113232k free,    35296k buffers
Swap:   262140k total,    75436k used,   186704k free,   282600k cached

```

That 282M constitutes disk cache, all of which can be reverted to program memory as needed.  So, in essence, I'm using about half the 768M of actual memory.

---

### Post by leon.nardella on 2012-05-12
Yes... Whatever you're doing there, it seems the micro instance is too small to handle it. You could probably try to decrease the amount of caching MySQL does and tweak Apache's configuration to spawn less processes (not sure if this applies here), but your best bet is to try a bigger EC2 instance and see if the problem goes away.

---

### Post by nodetx on 2012-05-12
It sounds like I need to adjust the mysql memory settings. Does anyone have any tips on where to start on that? I suppose I need to adjust stuff related to mysql memory usage, cache or buffers?

---

### Post by leon.nardella on 2012-05-12
Are you using innodb? I'd start with the innodb_buffer_pool_size setting.

---

### Post by nodetx on 2012-05-13
I'll try to tune my InnoDB settings. I've googled "ubuntu mysql innodb_buffer_pool_size" and found several interesting articles so I'll work with those.

---

### Post by nodetx on 2012-05-13
Oh I forgot to add that I also stopped the Proftpd and Webmin services and now the site hasn't crashed since. I found out of my admins had installed proftpd on the server and the crashes corresponded with when I installed that. I shut webmin down if it's not in use to save further memory.

---

### Post by nodetx on 2012-05-13
I looked and I guess I"m not using InnoDB even though it is enabled. I ran mysqltuner and I see my max possible memory size is 101% of my installed memory so I'm going to fine tune the my.cnf file

```

 >>  MySQLTuner 1.2.0 - Major Hayden <major@mhtx.net>
 >>  Bug reports, feature requests, and downloads at http://mysqltuner.com/
 >>  Run with '--help' for additional options and output filtering
Please enter your MySQL administrative login: root
Please enter your MySQL administrative password: 

-------- General Statistics --------------------------------------------------
[--] Skipped version check for MySQLTuner script
[OK] Currently running supported MySQL version 5.5.22-0ubuntu1
[OK] Operating on 64-bit architecture

-------- Storage Engine Statistics -------------------------------------------
[--] Status: +Archive -BDB -Federated +InnoDB -ISAM -NDBCluster 
[--] Data in MyISAM tables: 16M (Tables: 229)
[--] Data in InnoDB tables: 2M (Tables: 118)
[--] Data in PERFORMANCE_SCHEMA tables: 0B (Tables: 17)
[--] Data in MEMORY tables: 0B (Tables: 4)
[!!] Total fragmented tables: 127

-------- Security Recommendations  -------------------------------------------
(removed)

-------- Performance Metrics -------------------------------------------------
[--] Up for: 17h 2m 34s (131K q [2.140 qps], 2K conn, TX: 224M, RX: 19M)
[--] Reads / Writes: 80% / 20%
[--] Total buffers: 192.0M global + 2.7M per thread (151 max threads)
[!!] Maximum possible memory usage: 597.8M (101% of installed RAM)
[OK] Slow queries: 0% (0/131K)
[OK] Highest usage of available connections: 3% (6/151)
[OK] Key buffer size / total MyISAM indexes: 16.0M/5.9M
[OK] Key buffer hit rate: 99.5% (1M cached / 6K reads)
[OK] Query cache efficiency: 74.0% (84K cached / 114K selects)
[OK] Query cache prunes per day: 0
[OK] Sorts requiring temporary tables: 0% (0 temp sorts / 2K sorts)
[OK] Temporary tables created on disk: 3% (101 on disk / 2K total)
[OK] Thread cache hit rate: 99% (6 created / 2K connections)
[OK] Table cache hit rate: 25% (400 open / 1K opened)
[OK] Open file limit used: 50% (517/1K)
[OK] Table locks acquired immediately: 99% (61K immediate / 61K locks)
[OK] InnoDB data size / buffer pool: 2.8M/128.0M

-------- Recommendations -----------------------------------------------------
General recommendations:
    Run OPTIMIZE TABLE to defragment tables for better performance
    MySQL started within last 24 hours - recommendations may be inaccurate
    Reduce your overall MySQL memory footprint for system stability
    Enable the slow query log to troubleshoot bad queries

```

---

