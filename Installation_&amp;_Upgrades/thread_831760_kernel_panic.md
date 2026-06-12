---
title: "kernel panic"
date: 2008-06-17
forum: Installation &amp; Upgrades
---

### Post by Nama_2008 on 2008-06-17
Hii all!
I want to boot kernel-2.6.14 under ubuntu 7.10 on HP-dv2601.I have configured and successfully complied kernel-2.6.14 but at boot got kernel panic 

modprobe: FATAL: could not load /lib/modules.dep " NO such file or directory
mount:unknown filesystem type 'devfs'
FATAL : could not load /lib/modules/2.6.14/modules.dep:No such file or
directory
umount: devfs: not mounted
/scripts/ext3-add-journal.sh:27:arith:syntax error : "0X"
modprobe:FATAL : could not load /lib/modules/2.6.14/modules.dep:No such
file or directory
mount: unknown filesystem type 'devfs'
/sbin/init:426:arith:syntax error : "0X"
kernel panic - not syncing:Attempted to kill init!

I have tried many possible solutions like enable ext2 ext3 fs support, modification in grub menu.lst but still getting same error.Please tell me what is the reson behind this error and how to solve it.It;s urgent.
Thank u in advance.

---

### Post by Nama_2008 on 2008-06-17
I have also tried ubuntu method of compiling kernel. [www.howtoforge.com/kernel_compilation_ubuntu](www.howtoforge.com/kernel_compilation_ubuntu).
And got BUG:soft lockup detected on CPU#0!
Please tell me possible solution for this problem.

---

