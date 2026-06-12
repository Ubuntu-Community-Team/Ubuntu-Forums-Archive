---
title: "Live CD fails to boot"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by horizon981 on 2006-12-29
A month before, everything worked like a charm.
Now, I recently had no Linux and got myself an NVIDIA FX 5200 AGP card.
And now, no Linux boots up.

Here are the errors I get with Ubuntu 6.06:
[B]
Loading hardware drivers.....
hw_random not detected
...............................
............................... //many error messages scroll

[17179631.480000] [<f887e01f7>] agp_intel_int+0x1f/0x22[intel_agp]

......................
...................... //more such errors

[17179631.480000] Code: 00 00 00 0f ba 35 ..........

.......................
.......................

[17179631.480000] <0> Kernel panic: not syncing.
Fatal exception in interrupt .......

[/B]

etc etc.

With Knoppix 5.01:
[B]
starting udev-hotplug hardware detection...
udev_event[1387]: run_program: '/sbin/modprobe] abnormal exit.
[/B]

Now, giving up Linux for my AGP card is the last thing I want to do, but I seem to be out of options.

[SIZE="7"]HELP!!![/SIZE]

](*,) ](*,) ](*,) ](*,) ](*,)

---

