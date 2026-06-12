---
title: "Is this an upgrade problem or hardware issues?"
date: 2013-08-29
forum: Installation &amp; Upgrades
---

### Post by owkaye on 2013-08-29
Running 12.04 and MATE 1.6, after a recent upgrade I seem to have lots of processes running that were never running before, the system is slow, and my web development system is misbehaving.  I'm not sure if a recent upgrade broke things, or if it's a hardware issue, or something else ...  

When I open the MATE System Monitor the Memory column shows lots of "N/A" values.  Here are the Waiting Channel values for the corresponding processes:

bdi_forker_thread
bdi_sync_supers
bdi_writeback_thread
cpu_stopper_thread
devtmpfsd
encryptfs_threadfn
fs_notify_mark_destroy
hub_thread
irq_thread
khugepaged_loop
kjournaled2
ksm_scan_thread
kswapd_try_to_sleep
ktthreadd
rescuer_thread (lots of these)
rfcomm_run
run_ksoftirqd
scsi_error_handler
watchdog
worker_thread

I also have LOTS of processes that list specific memory allocations but that have Waiting Channel values of "poll_schedule_timeout" which I have never seen before.

Can anyone shed some light on this for me?

---

