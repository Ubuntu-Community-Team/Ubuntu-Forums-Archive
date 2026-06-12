---
title: "compiling problems with high point sata 1740 6.06.1 LTS Server"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by krischeu on 2007-05-02
Dear Newsgroup,

please give me a helping hand.

I am running a HP xw 6000 workstation with ubuntu 6.06.1 LTS server. Kernel version is 2.6.15-28-server #1 SMP.
The machine is running. Everything without the raid-controller is fine.

This is what i have done:
Downloaded the source code
created a directory and changed into it --> /usr/src/highpoint_1740_sata_rr174x-linux-src-1.02/product/rr174x/linux

i typed "make" and 2 errors occured:
   root@carhs1:/usr/src/highpoint_1740_sata_rr174x-linux-src-1.02/product/rr174x/linux# make
   make[1]: Entering directory `/usr/src/linux-headers-2.6.15-28-server'
     CC [M]  /usr/src/highpoint_1740_sata_rr174x-linux-src-1.02/osm/linux/os_linux.o
   /usr/src/highpoint_1740_sata_rr174x-linux-src-1.02/osm/linux/os_linux.c: In function ‘refresh_sd_flags’:
   /usr/src/highpoint_1740_sata_rr174x-linux-src-1.02/osm/linux/os_linux.c:261: warning: implicit declaration of function ‘mutex_lock’
   /usr/src/highpoint_1740_sata_rr174x-linux-src-1.02/osm/linux/os_linux.c:261: error: ‘struct inode’ has no member named ‘i_mutex’
   /usr/src/highpoint_1740_sata_rr174x-linux-src-1.02/osm/linux/os_linux.c:267: warning: implicit declaration of function ‘mutex_unlock’
   /usr/src/highpoint_1740_sata_rr174x-linux-src-1.02/osm/linux/os_linux.c:267: error: ‘struct inode’ has no member named ‘i_mutex’
   make[2]: *** [/usr/src/highpoint_1740_sata_rr174x-linux-src-1.02/osm/linux/os_linux.o] Error 1
   make[1]: *** [_module_/usr/src/highpoint_1740_sata_rr174x-linux-src-1.02/product/rr174x/linux/.build] Error 2
   make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-28-server'
   make: *** [rr174x.ko] Error 2
root@carhs1:/usr/src/highpoint_1740_sata_rr174x-linux-src-1.02/product/rr174x/linux#


Does anybody can give me a hint?

---

### Post by krischeu on 2007-05-02
can't anyone figure out my problem?

This should not be a really big thing.

---

### Post by krischeu on 2007-05-02
Could the problem be located, that only the headers are installed?
There are no linux-source-files at the moment at /usr/src, only the linux.headers for the matching kernel.

---

### Post by krischeu on 2007-05-02
There seems to be a problem in the file "/rr174x-linux-src-1.02/osm/linux/os_linux.c"
I changed both entrys 

#if LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,15)

to

#if LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,16)



I market it as usual and it could be compiled.
make 

make install

I can load the compiled driver with: 

modprobe sd_mod
insmod rr1740.ko

---

### Post by krischeu on 2007-05-02
Dear all,

with dmesg i see the following:
[42949649.980000] rr1740: disagrees about version of symbol struct_module
[42950261.930000] Driver 'sd' needs updating - please use bus_type methods
[42950271.380000] rr174x: module license 'Proprietary' taints kernel.
[42950271.380000] rr174x:0: RocketRAID 174x controller driver v1.02 (May  2 2007 15:17:27)
[42950271.380000] ACPI: PCI Interrupt 0000:05:0e.0[A] -> GSI 16 (level, low) -> IRQ 193
[42950271.380000] rr174x:0: adapter at PCI 5:14:0, IRQ 193
[42950271.960000] rr174x:0: start channel [0,1]
[42950271.960000] rr174x:0: start channel [0,3]
[42950272.280000] rr174x:0: channel [0,1] started successfully
[42950272.280000] rr174x:0: channel [0,3] started successfully
[42950272.530000] scsi2 : rr174x
[42950272.530000]   Vendor: HPT       Model: DISK_2_0          Rev: 4.00
[42950272.530000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[42950272.530000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[42950272.530000] SCSI device sda: drive cache: write through
[42950272.530000] SCSI device sda: 312581808 512-byte hdwr sectors (160042 MB)
[42950272.530000] SCSI device sda: drive cache: write through
[42950272.530000]  sda: sda1
[42950272.540000] sd 2:0:0:0: Attached scsi disk sda
[42950272.590000] sd 2:0:0:0: Attached scsi generic sg0 type 0



This is a 4 channel controller. But i have 2 harddisks connected. How can i connect the second one?

---

### Post by krischeu on 2007-05-02
Dear NG,

one step forward 2 steps back.

after discommenting some lines from "/rr174x-linux-src-1.02/osm/linux/os_linux.c" (Line 260 --> 265)
compiling was succesfull.

I can test after compiling with hdparm the speed ( hdparm -tT /dev/sda) 68MB/s.
Unfortunately i only see one harddisc --> reboot could help? No, after reboot no harddisks anymore availiable.

modprobe sd_mod
insmod rr1740.ko 
depmod

Don't help anymore.
If i do this:

modprobe sd_mod --> no error
insmod rr1740.ko  --> insmod: can't read 'rr1740.ko': No such file or directory
depmod --> no error

dmesg give this:
--snip---
[42949423.080000] matrox_w1 0000:01:00.0: Matrox G400 GPIO transport layer for 1-wire.
[42949423.210000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 209
[42949423.210000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[42949423.330000] rr174x: module license 'Proprietary' taints kernel.
[42949423.330000] rr174x:0: RocketRAID 174x controller driver v1.02 (May  2 2007 15:17:27)
[42949423.330000] ACPI: PCI Interrupt 0000:05:0e.0[A] -> GSI 16 (level, low) -> IRQ 193
[42949423.330000] rr174x:0: adapter at PCI 5:14:0, IRQ 193
[42949423.910000] rr174x:0: start channel [0,0]
[42949423.910000] rr174x:0: start channel [0,1]
--snip---


I can see rr174x - the harddisks are connected at 0.0 and 0.1 --> i know this, because i tested it before. 
How can i go on?

---

### Post by krischeu on 2007-05-03
Dear NG,

one step forward 2 steps back.

after discommenting some lines from "/rr174x-linux-src-1.02/osm/linux/os_linux.c" (Line 260 --> 265)
compiling was succesfull.

I can test after compiling with hdparm the speed ( hdparm -tT /dev/sda) 68MB/s.
Unfortunately i only see one harddisc --> reboot could help? No, after reboot no harddisks anymore availiable.

modprobe sd_mod
insmod rr1740.ko
depmod

Don't help anymore.
If i do this:

modprobe sd_mod --> no error
insmod rr1740.ko --> insmod: can't read 'rr1740.ko': No such file or directory
depmod --> no error

dmesg give this:
--snip---
[42949423.080000] matrox_w1 0000:01:00.0: Matrox G400 GPIO transport layer for 1-wire.
[42949423.210000] ACPI: PCI Interrupt 0000:00:1f.5[b] -> GSI 17 (level, low) -> IRQ 209
[42949423.210000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[42949423.330000] rr174x: module license 'Proprietary' taints kernel.
[42949423.330000] rr174x:0: RocketRAID 174x controller driver v1.02 (May 2 2007 15:17:27)
[42949423.330000] ACPI: PCI Interrupt 0000:05:0e.0[A] -> GSI 16 (level, low) -> IRQ 193
[42949423.330000] rr174x:0: adapter at PCI 5:14:0, IRQ 193
[42949423.910000] rr174x:0: start channel [0,0]
[42949423.910000] rr174x:0: start channel [0,1]
--snip---


I can see rr174x - the harddisks are connected at 0.0 and 0.1 --> i know this, because i tested it before.
How can i go on?:lolflag:

---

### Post by krischeu on 2007-05-03
Dear NG,

one step forward 2 steps back.

after discommenting some lines from "/rr174x-linux-src-1.02/osm/linux/os_linux.c" (Line 260 --> 265)
compiling was succesfull.

I can test after compiling with hdparm the speed ( hdparm -tT /dev/sda) 68MB/s.
Unfortunately i only see one harddisc --> reboot could help? No, after reboot no harddisks anymore availiable.

modprobe sd_mod
insmod rr1740.ko
depmod

Don't help anymore.
If i do this:

modprobe sd_mod --> no error
insmod rr1740.ko --> insmod: can't read 'rr1740.ko': No such file or directory
depmod --> no error

dmesg give this:
--snip---
[42949423.080000] matrox_w1 0000:01:00.0: Matrox G400 GPIO transport layer for 1-wire.
[42949423.210000] ACPI: PCI Interrupt 0000:00:1f.5[b] -> GSI 17 (level, low) -> IRQ 209
[42949423.210000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[42949423.330000] rr174x: module license 'Proprietary' taints kernel.
[42949423.330000] rr174x:0: RocketRAID 174x controller driver v1.02 (May 2 2007 15:17:27)
[42949423.330000] ACPI: PCI Interrupt 0000:05:0e.0[A] -> GSI 16 (level, low) -> IRQ 193
[42949423.330000] rr174x:0: adapter at PCI 5:14:0, IRQ 193
[42949423.910000] rr174x:0: start channel [0,0]
[42949423.910000] rr174x:0: start channel [0,1]
--snip---


I can see rr174x - the harddisks are connected at 0.0 and 0.1 --> i know this, because i tested it before.
How can i go on?

---

### Post by glenndavy on 2007-05-21
hi  krischeu
i feel your pain - i've got same card and had no luck - though you've been more persistnent than me - I think I'm going to stick my card on ebay - wish I could offer you some help

just thought id let you know you're not the only one

glenn

---

