---
title: "Memory errors in logs"
date: 2010-04-12
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dusdus on 2010-04-12
Hi there,

I've noticed some weird messages in my logs. At that moment I was installing Office in Windows XP in Virtualbox, downloading at highspeed, browsing, listening to music...the ordinary multi-tasking.

I'm using a dual core 2.4 ghz processor with 2gb ram. I've given WinXP about 800 Mb of RAM. 

Before using lucid, I've been using karmic and have never seen messages like this. 
According to system monitor I'm using 1.3 Gb of my total 2 Gb RAM, and 250 Mb of swap. 
The errormessages:
```


Apr 12 14:16:13 laptux kernel: [22374.014516] __ratelimit: 92 callbacks suppressed
Apr 12 14:16:18 laptux kernel: [22374.014522] swapper: page allocation failure. order:1, mode:0x4020
Apr 12 14:16:18 laptux kernel: [22374.014527] Pid: 0, comm: swapper Tainted: G        W  2.6.32-20-generic #29-Ubuntu
Apr 12 14:16:18 laptux kernel: [22374.014531] Call Trace:
Apr 12 14:16:18 laptux kernel: [22374.014534]  <IRQ>  [<ffffffff810f9d7e>] __alloc_pages_slowpath+0x56e/0x580
Apr 12 14:16:18 laptux kernel: [22374.014553]  [<ffffffff810f9eee>] __alloc_pages_nodemask+0x15e/0x1a0
Apr 12 14:16:18 laptux kernel: [22374.014561]  [<ffffffff8112ca97>] alloc_pages_current+0x87/0xd0
Apr 12 14:16:18 laptux kernel: [22374.014567]  [<ffffffff81132977>] new_slab+0x2f7/0x310
Apr 12 14:16:18 laptux kernel: [22374.014573]  [<ffffffff811351f1>] __slab_alloc+0x201/0x2d0
Apr 12 14:16:18 laptux kernel: [22374.014593]  [<ffffffffa00e8035>] ? ath_rxbuf_alloc+0x35/0xb0 [ath]
Apr 12 14:16:18 laptux kernel: [22374.014600]  [<ffffffff81136238>] __kmalloc_node_track_caller+0xb8/0x180
Apr 12 14:16:18 laptux kernel: [22374.014608]  [<ffffffffa00e8035>] ? ath_rxbuf_alloc+0x35/0xb0 [ath]
Apr 12 14:16:18 laptux kernel: [22374.014614]  [<ffffffff81452cd0>] __alloc_skb+0x80/0x190
Apr 12 14:16:18 laptux kernel: [22374.014622]  [<ffffffffa00e8035>] ath_rxbuf_alloc+0x35/0xb0 [ath]
Apr 12 14:16:18 laptux kernel: [22374.014637]  [<ffffffffa01879df>] ath_rx_tasklet+0x20f/0x6c0 [ath9k]
Apr 12 14:16:18 laptux kernel: [22374.014645]  [<ffffffff81088f40>] ? hrtimer_interrupt+0x130/0x220
Apr 12 14:16:18 laptux kernel: [22374.014658]  [<ffffffffa0184fa9>] ath9k_tasklet+0x109/0x140 [ath9k]
Apr 12 14:16:18 laptux kernel: [22374.014666]  [<ffffffff8106c985>] tasklet_action+0xd5/0xe0
Apr 12 14:16:18 laptux kernel: [22374.014672]  [<ffffffff8106e3a7>] __do_softirq+0xb7/0x1e0
Apr 12 14:16:18 laptux kernel: [22374.014679]  [<ffffffff81031b52>] ? ack_apic_level+0x82/0x1f0
Apr 12 14:16:18 laptux kernel: [22374.014685]  [<ffffffff810142ec>] call_softirq+0x1c/0x30
Apr 12 14:16:18 laptux kernel: [22374.014690]  [<ffffffff81015cb5>] do_softirq+0x65/0xa0
Apr 12 14:16:18 laptux kernel: [22374.014695]  [<ffffffff8106e245>] irq_exit+0x85/0x90
Apr 12 14:16:18 laptux kernel: [22374.014701]  [<ffffffff81545fd5>] do_IRQ+0x75/0xf0
Apr 12 14:16:18 laptux kernel: [22374.014706]  [<ffffffff81013b13>] ret_from_intr+0x0/0x11
Apr 12 14:16:18 laptux kernel: [22374.014709]  <EOI>  [<ffffffff8130d203>] ? acpi_idle_enter_bm+0x28a/0x2be
Apr 12 14:16:18 laptux kernel: [22374.014720]  [<ffffffff8130d1fc>] ? acpi_idle_enter_bm+0x283/0x2be
Apr 12 14:16:18 laptux kernel: [22374.014728]  [<ffffffff81437617>] ? cpuidle_idle_call+0xa7/0x140
Apr 12 14:16:18 laptux kernel: [22374.014735]  [<ffffffff81011e73>] ? cpu_idle+0xb3/0x110
Apr 12 14:16:18 laptux kernel: [22374.014741]  [<ffffffff8153ae7b>] ? start_secondary+0xa8/0xaa
Apr 12 14:16:18 laptux kernel: [22374.014744] Mem-Info:
Apr 12 14:16:18 laptux kernel: [22374.014747] Node 0 DMA per-cpu:
Apr 12 14:16:18 laptux kernel: [22374.014752] CPU    0: hi:    0, btch:   1 usd:   0
Apr 12 14:16:18 laptux kernel: [22374.014756] CPU    1: hi:    0, btch:   1 usd:   0
Apr 12 14:16:18 laptux kernel: [22374.014758] Node 0 DMA32 per-cpu:
Apr 12 14:16:18 laptux kernel: [22374.014763] CPU    0: hi:  186, btch:  31 usd: 181
Apr 12 14:16:18 laptux kernel: [22374.014767] CPU    1: hi:  186, btch:  31 usd: 154
Apr 12 14:16:18 laptux kernel: [22374.014775] active_anon:242221 inactive_anon:82255 isolated_anon:183
Apr 12 14:16:18 laptux kernel: [22374.014777]  active_file:27065 inactive_file:42187 isolated_file:77
Apr 12 14:16:18 laptux kernel: [22374.014778]  unevictable:30231 dirty:19179 writeback:3713 unstable:0
Apr 12 14:16:18 laptux kernel: [22374.014780]  free:3187 slab_reclaimable:5343 slab_unreclaimable:9200
Apr 12 14:16:18 laptux kernel: [22374.014781]  mapped:43376 shmem:22931 pagetables:10070 bounce:0
Apr 12 14:16:18 laptux kernel: [22374.014785] Node 0 DMA free:7748kB min:40kB low:48kB high:60kB active_anon:208kB inactive_anon:488kB active_file:2260kB inactive_file:3844kB unevictable:132kB isolated(anon):0kB isolated(file):0kB present:15352kB mlocked:132kB dirty:180kB writeback:16kB mapped:460kB shmem:56kB slab_reclaimable:172kB slab_unreclaimable:1048kB kernel_stack:16kB pagetables:8kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Apr 12 14:16:18 laptux kernel: [22374.014803] lowmem_reserve[]: 0 1934 1934 1934
Apr 12 14:16:18 laptux kernel: [22374.014809] Node 0 DMA32 free:5000kB min:5604kB low:7004kB high:8404kB active_anon:968676kB inactive_anon:328532kB active_file:106000kB inactive_file:164904kB unevictable:120792kB isolated(anon):732kB isolated(file):308kB present:1980892kB mlocked:120792kB dirty:76536kB writeback:14836kB mapped:173044kB shmem:91668kB slab_reclaimable:21200kB slab_unreclaimable:35752kB kernel_stack:2984kB pagetables:40272kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:256 all_unreclaimable? no
Apr 12 14:16:18 laptux kernel: [22374.014827] lowmem_reserve[]: 0 0 0 0
Apr 12 14:16:18 laptux kernel: [22374.014833] Node 0 DMA: 7*4kB 2*8kB 3*16kB 25*32kB 19*64kB 6*128kB 7*256kB 2*512kB 0*1024kB 1*2048kB 0*4096kB = 7740kB
Apr 12 14:16:18 laptux kernel: [22374.014850] Node 0 DMA32: 986*4kB 1*8kB 2*16kB 0*32kB 11*64kB 2*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 4944kB
Apr 12 14:16:18 laptux kernel: [22374.014867] 99546 total pagecache pages
Apr 12 14:16:18 laptux kernel: [22374.014870] 7298 pages in swap cache
Apr 12 14:16:18 laptux kernel: [22374.014874] Swap cache stats: add 476148, delete 468850, find 61175/104811
Apr 12 14:16:18 laptux kernel: [22374.014877] Free swap  = 2318408kB
Apr 12 14:16:18 laptux kernel: [22374.014880] Total swap = 2490064kB
Apr 12 14:16:18 laptux kernel: [22374.024475] 506880 pages RAM
Apr 12 14:16:18 laptux kernel: [22374.024475] 32989 pages reserved
Apr 12 14:16:18 laptux kernel: [22374.024475] 292098 pages shared
Apr 12 14:16:18 laptux kernel: [22374.024475] 241140 pages non-shared
Apr 12 14:16:18 laptux kernel: [22374.024475] SLUB: Unable to allocate memory on node -1 (gfp=0x20)
Apr 12 14:16:18 laptux kernel: [22374.024475]   cache: kmalloc-8192, object size: 8192, buffer size: 8192, default order: 3, min order: 1
Apr 12 14:16:18 laptux kernel: [22374.024475]   node 0: slabs: 166, objs: 640, free: 0
Apr 12 14:16:18 laptux kernel: [22374.028140] swapper: page allocation failure. order:1, mode:0x4020
Apr 12 14:16:18 laptux kernel: [22374.028147] Pid: 0, comm: swapper Tainted: G        W  2.6.32-20-generic #29-Ubuntu
Apr 12 14:16:18 laptux kernel: [22374.028152] Call Trace:
Apr 12 14:16:18 laptux kernel: [22374.028155]  <IRQ>  [<ffffffff810f9d7e>] __alloc_pages_slowpath+0x56e/0x580
Apr 12 14:16:18 laptux kernel: [22374.028175]  [<ffffffff810f9eee>] __alloc_pages_nodemask+0x15e/0x1a0
Apr 12 14:16:18 laptux kernel: [22374.028184]  [<ffffffff8112ca97>] alloc_pages_current+0x87/0xd0
Apr 12 14:16:18 laptux kernel: [22374.028192]  [<ffffffff81132977>] new_slab+0x2f7/0x310
Apr 12 14:16:18 laptux kernel: [22374.028199]  [<ffffffff811351f1>] __slab_alloc+0x201/0x2d0
Apr 12 14:16:18 laptux kernel: [22374.028216]  [<ffffffffa00e8035>] ? ath_rxbuf_alloc+0x35/0xb0 [ath]
Apr 12 14:16:18 laptux kernel: [22374.028224]  [<ffffffff81136238>] __kmalloc_node_track_caller+0xb8/0x180
Apr 12 14:16:18 laptux kernel: [22374.028233]  [<ffffffffa00e8035>] ? ath_rxbuf_alloc+0x35/0xb0 [ath]
Apr 12 14:16:18 laptux kernel: [22374.028241]  [<ffffffff81452cd0>] __alloc_skb+0x80/0x190
Apr 12 14:16:18 laptux kernel: [22374.028250]  [<ffffffffa00e8035>] ath_rxbuf_alloc+0x35/0xb0 [ath]
Apr 12 14:16:18 laptux kernel: [22374.028267]  [<ffffffffa01879df>] ath_rx_tasklet+0x20f/0x6c0 [ath9k]
Apr 12 14:16:18 laptux kernel: [22374.028282]  [<ffffffffa0184fa9>] ath9k_tasklet+0x109/0x140 [ath9k]
Apr 12 14:16:18 laptux kernel: [22374.028292]  [<ffffffff8106c985>] tasklet_action+0xd5/0xe0
Apr 12 14:16:18 laptux kernel: [22374.028299]  [<ffffffff8106e3a7>] __do_softirq+0xb7/0x1e0
Apr 12 14:16:18 laptux kernel: [22374.028307]  [<ffffffff81031b52>] ? ack_apic_level+0x82/0x1f0
Apr 12 14:16:18 laptux kernel: [22374.028315]  [<ffffffff810142ec>] call_softirq+0x1c/0x30
Apr 12 14:16:18 laptux kernel: [22374.028321]  [<ffffffff81015cb5>] do_softirq+0x65/0xa0
Apr 12 14:16:18 laptux kernel: [22374.028327]  [<ffffffff8106e245>] irq_exit+0x85/0x90
Apr 12 14:16:18 laptux kernel: [22374.028334]  [<ffffffff81545fd5>] do_IRQ+0x75/0xf0
Apr 12 14:16:18 laptux kernel: [22374.028341]  [<ffffffff81013b13>] ret_from_intr+0x0/0x11
Apr 12 14:16:18 laptux kernel: [22374.028345]  <EOI>  [<ffffffff8130d203>] ? acpi_idle_enter_bm+0x28a/0x2be
Apr 12 14:16:18 laptux kernel: [22374.028359]  [<ffffffff8130d1fc>] ? acpi_idle_enter_bm+0x283/0x2be
Apr 12 14:16:18 laptux kernel: [22374.028367]  [<ffffffff81437617>] ? cpuidle_idle_call+0xa7/0x140
Apr 12 14:16:18 laptux kernel: [22374.028375]  [<ffffffff81011e73>] ? cpu_idle+0xb3/0x110
Apr 12 14:16:18 laptux kernel: [22374.028382]  [<ffffffff8153ae7b>] ? start_secondary+0xa8/0xaa
Apr 12 14:16:18 laptux kernel: [22374.028387] Mem-Info:
Apr 12 14:16:18 laptux kernel: [22374.028391] Node 0 DMA per-cpu:
Apr 12 14:16:18 laptux kernel: [22374.028397] CPU    0: hi:    0, btch:   1 usd:   0
Apr 12 14:16:18 laptux kernel: [22374.028402] CPU    1: hi:    0, btch:   1 usd:   0
Apr 12 14:16:18 laptux kernel: [22374.028406] Node 0 DMA32 per-cpu:
Apr 12 14:16:18 laptux kernel: [22374.028412] CPU    0: hi:  186, btch:  31 usd: 182
Apr 12 14:16:18 laptux kernel: [22374.028417] CPU    1: hi:  186, btch:  31 usd: 154
Apr 12 14:16:18 laptux kernel: [22374.028426] active_anon:242221 inactive_anon:82223 isolated_anon:215
Apr 12 14:16:18 laptux kernel: [22374.028429]  active_file:27065 inactive_file:42187 isolated_file:77
Apr 12 14:16:18 laptux kernel: [22374.028431]  unevictable:30231 dirty:19179 writeback:3713 unstable:0
Apr 12 14:16:18 laptux kernel: [22374.028434]  free:3187 slab_reclaimable:5343 slab_unreclaimable:9200
Apr 12 14:16:18 laptux kernel: [22374.028436]  mapped:43376 shmem:22931 pagetables:10070 bounce:0
Apr 12 14:16:18 laptux kernel: [22374.028442] Node 0 DMA free:7748kB min:40kB low:48kB high:60kB active_anon:208kB inactive_anon:488kB active_file:2260kB inactive_file:3844kB unevictable:132kB isolated(anon):0kB isolated(file):0kB present:15352kB mlocked:132kB dirty:180kB writeback:16kB mapped:460kB shmem:56kB slab_reclaimable:172kB slab_unreclaimable:1048kB kernel_stack:16kB pagetables:8kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? no
Apr 12 14:16:18 laptux kernel: [22374.028464] lowmem_reserve[]: 0 1934 1934 1934
Apr 12 14:16:18 laptux kernel: [22374.028475] Node 0 DMA32 free:5000kB min:5604kB low:7004kB high:8404kB active_anon:968676kB inactive_anon:328404kB active_file:106000kB inactive_file:164904kB unevictable:120792kB isolated(anon):860kB isolated(file):308kB present:1980892kB mlocked:120792kB dirty:76536kB writeback:14836kB mapped:173044kB shmem:91668kB slab_reclaimable:21200kB slab_unreclaimable:35752kB kernel_stack:2984kB pagetables:40272kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:288 all_unreclaimable? no
Apr 12 14:16:18 laptux kernel: [22374.028499] lowmem_reserve[]: 0 0 0 0
Apr 12 14:16:18 laptux kernel: [22374.028509] Node 0 DMA: 7*4kB 2*8kB 3*16kB 25*32kB 19*64kB 6*128kB 7*256kB 2*512kB 0*1024kB 1*2048kB 0*4096kB = 7740kB
Apr 12 14:16:18 laptux kernel: [22374.028536] Node 0 DMA32: 986*4kB 1*8kB 2*16kB 0*32kB 11*64kB 2*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 4944kB
Apr 12 14:16:18 laptux kernel: [22374.028562] 99546 total pagecache pages
Apr 12 14:16:18 laptux kernel: [22374.028566] 7299 pages in swap cache
Apr 12 14:16:18 laptux kernel: [22374.028570] Swap cache stats: add 476149, delete 468850, find 61175/104811
Apr 12 14:16:18 laptux kernel: [22374.028575] Free swap  = 2318404kB
Apr 12 14:16:18 laptux kernel: [22374.028579] Total swap = 2490064kB
Apr 12 14:16:18 laptux kernel: [22374.042266] 506880 pages RAM
Apr 12 14:16:18 laptux kernel: [22374.042266] 32989 pages reserved
Apr 12 14:16:18 laptux kernel: [22374.042266] 292002 pages shared
Apr 12 14:16:18 laptux kernel: [22374.042266] 241175 pages non-shared
Apr 12 14:16:18 laptux kernel: [22374.042266] SLUB: Unable to allocate memory on node -1 (gfp=0x20)
Apr 12 14:16:18 laptux kernel: [22374.042266]   cache: kmalloc-8192, object size: 8192, buffer size: 8192, default order: 3, min order: 1
Apr 12 14:16:18 laptux kernel: [22374.042266]   node 0: slabs: 166, objs: 640, free: 0

```

Could anyone tell me please what is going on?

---

