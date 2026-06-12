---
title: "HP Pavilion a706n installation 12.04"
date: 2012-07-25
forum: Installation &amp; Upgrades
---

### Post by flores65 on 2012-07-25
I'm trying to install Ubuntu 12.04 on my dad's old HP Pavilion a706n. I get an error during the installation process. I've tried installing through a CD, and through Windows, with no success. Of course this is where I should be posting what the screen is saying but the computer reboots or freezes to a black screen before I can take a good look at it.

It's an AMD Athlon XP processor with 1gb of RAM. Any suggestions where to start? I'm new to Ubuntu giving problems so I'm not exactly sure how to troubleshoot.

---

### Post by dino99 on 2012-07-26
you probably need to use some boot option, like nomodeset or noacpi

google around "ubuntu boot option"

---

### Post by flores65 on 2012-07-26
I tried to install Kubuntu 12.04 thinking the computer may not be able to handle Ubuntu.  Also had an error but the screen froze on this one.

So I'm going to try and type this as best as possible...

```

64.551862 - Kernel panic - not syncing: Attempted to kill init!
64.551880 - Pid: 1, comm: run-init Not tainted 3.2.0-23-generic-pae #36-Ubuntu
64 ............. - Call Trace:
? printl+0x2d/0x2f
panic+0x5c/0x161
forget_oringinal_parent+0x1e4/0x1f0
? perf_cgroup_attach_task+0x11/0x20
? perf_cgroup_attach_task+0x20/0x20
exit_notify+0x14/0x140
do_exit+0x1ac/0x390
? tyy_write+0x220/0x220
sys_exit+0x18/0x20
syscalll_call+0x7/0xb

```

I don't have a clue what any of this means. I've burned 2 Ubuntu CDs and one Kubuntu CD. Any suggestions?

---

