---
title: "Unable to install linux-686-smp kernel in Dapper"
date: 2006-12-24
forum: Installation &amp; Upgrades
---

### Post by DarthPlageus on 2006-12-24
I have a laptop with an Intel dual core T2600 processor, which I installed XUbuntu (Dapper) on some time ago.  /proc/cpuinfo shows just one processor, so I tried implementing the SMP kernel by running:

sudo apt-get install linux-686-smp

then rebooting.  /proc/cpuinfo still shows just one processor.  I even ran 'sudo apt-get update' then the above command, but no-go.

I do have an ATI Radeon X1600 video card with the fglrx driver, which I had to do a manual install of sometime back.  Not sure if that makes a difference.

Thanks!

--john

---

### Post by fredj on 2006-12-26
Use the synaptics package manager and do a search for linux image. This should list
all the kernels and show which one you have installed.
The Dapper SMP kernel does detect and use both processors but it also breaks the
correct detection of Intel wireless chipsets and has reported troubles with certain
Nvidia video chips. I had to install the Edgy release which uses a SMP kernel by default
to solve all these problems.

---

