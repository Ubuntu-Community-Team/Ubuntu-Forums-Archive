---
title: "Kernel Panic On Startup After Building Kernel"
date: 2010-04-01
forum: Installation &amp; Upgrades
---

### Post by danben on 2010-04-01
I've got the Lucid Beta installed and running on an HP Envy, and my next venture is to apply the Synaptics Clickpad patch (since the mouse is currently unusable).  I was told this would require a rebuild of the kernel, so I followed the steps at [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild), applying the patch as necessary.

I did this for versions 2.6.34-rc3 and 2.6.33.1 (2.6.33 is the oldest version I'd want to use as it has some patches that the Envy needs), and trying to start either one gives me error messages roughly like the following:

```

VFS: Cannot open root device "mapper/isw_cigaehddaa_RAID-04" or unknown-block(0,0)
Please append a correct "root=" boot option; here are the available partitions:
pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
Kernel panic - not syncing: VFS:Unable to mount root fs on unknown-block(0,0)
Pid: 1, comm: swapper Tained: G      W 2.6.34-rc3-custom #1
Call Trace:
  panic
  mount_block_root
  ? trace_kmalloc
  mount_root
  prepare_namespace
  kernel_init
  kernel_thread_helper

```I have 2 SSD drives with "fake RAID", and the root device listed is the one that contains the partition with my Ubuntu install.  I'm unclear as to what the problem might be; a Google search on this error turned up a fair number of results but none was very clear on a solution.  None of the other solutions mentioned RAID, but other than that I don't have any specific reason to believe that that doesn't have anything to do with it.  Booting the kernel that came with the Lucid ISO (2.6.32-17) still works fine.

---

