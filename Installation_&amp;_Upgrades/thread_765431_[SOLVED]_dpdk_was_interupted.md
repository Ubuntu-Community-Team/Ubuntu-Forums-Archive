---
title: "[SOLVED] dpdk was interupted"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by Chechakoo on 2008-04-24
when trying to install "ndisgtk" I recieve this message.
"E:dpdk was interrupted. You must  manually run `dpdk --configure -a` to correct.
E: _cache ->open() failed please report."


Will someone please instruct this chechakoo (tenderfoot) how
to accomplish this.

running ubuntu 7.10 (gutsy) on Dell laptop (CPxH)
pentium III - 498.5 MHz
L1 cache - 32K     4887MB/s
l2 cache - 256K    1873 MB/s
memory 383 Meg      256MB/s
chipset - intel i440BX
Bio Ver, A14 
40 gig HD with 1 partition.(KICKED WINDOWS OUT THE DOOR PERMANENTLY.)

Also would like info on where to get info concerning syntax and command
language for terminal. 

Big order but this chechakoo is willing and able to learn.

ANY and all help would be greatly appreciated.  THANX

---

### Post by xerosis on 2008-04-24
Hi, 

You just need to type the following in a terminal:

sudo dpkg --configure -a

---

