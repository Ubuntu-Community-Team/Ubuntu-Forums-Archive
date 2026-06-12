---
title: "recent updates make a vmware guest go crazy"
date: 2021-08-18
forum: Installation &amp; Upgrades
---

### Post by russellr on 2021-08-18
I have a laptop with 6 cores (12 CPUs) and 64GB RAM, along with 2 NVME drives.

I've been using Ubuntu 20.04.1 as host OS for many months (previous Ubuntu versions for years).

My main guest OS (VM) has been 18.04 and an update in early August made it go completely crazy.

The guest VM has 12 CPUs and 32GB RAM.

It would work fine for about 23 hours, and then behave like either it was swapping like mad or was running a squillion processes (it was so slow top was useless).

Upgrading to 20.04.2 didn't fix the problem in the guest.

I then created a new guest with 20.04.2 and a similar problem occurred.  After 23 hours it showed 50 jobs active.  Of course, that wasn't what I was actually doing - it was basically idle.

I suspect the kernel versions 5.11.0-25-generic and 5.11.0-27-generic are to blame.

My host OS is 5.11.0-25-generic on 20.04.1 does not seem to exhibit this problem.

Kernel  5.4.0-80-generic in 18.04 has been stable since I installed it some time ago.

I've now reverted (thanks to snapshots and/or backups) back to my pre-update 18.04 and will write back in a few days with more information.

---

### Post by russellr on 2021-08-25
As promised, here's the answer...

The nVidia driver on the host was causing the problem in the VMWare guest.  The host itself was unaffected.

The problem nVidia driver was version 460.x.x.  Version 470.x.x resolved it.

---

### Post by russellr on 2021-08-25
As promised, here's the answer...

The nVidia driver on the host was causing the problem in the VMWare guest.  The host itself was unaffected.

The problem nVidia driver was version 460.x.x.  Version 470.x.x resolved it.

---

