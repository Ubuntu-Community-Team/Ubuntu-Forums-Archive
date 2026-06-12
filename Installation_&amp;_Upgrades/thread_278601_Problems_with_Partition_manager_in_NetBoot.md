---
title: "Problems with Partition manager in NetBoot"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by swimin on 2006-10-16
I am installing ubuntu onto a dell inspiron 1000 laptop, and am doing a netboot install due to a bad cdrom (intermittingly fails cd checks) drive. 

Whenever either I manually start the partition manager(in an expert install), or when the partition manager starts, the screen turns blue, with a gray line on it. I am able to switch to a shell at this point, and see what is going on. There is the sort-of-working cd rom drive  as /dev/hdc, and /dev/hda, my already partitioned hard drive. There are no /dev entries with any of the names of the partitions, and when I run: parted /dev/hda, it immediatly exits.

Any Ideas on how to complete this install?

---

### Post by swimin on 2006-10-16
I just noticed that the last line in the F4 console is
kernel: [long number] cdrom: open failed.

---

### Post by swimin on 2006-10-18
I found some relevant output in syslog:> Apr  1 22:05:13 kernel: [13739.547749] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
Apr  1 22:05:14 lvmcfg: File descriptor 3 left open
Apr  1 22:05:14 lvmcfg: File descriptor 4 left open
Apr  1 22:05:14 lvmcfg: File descriptor 5 left open
Apr  1 22:05:14 lvmcfg: File descriptor 6 left open
Apr  1 22:05:14 lvmcfg:   No matching physical volumes found
Apr  1 22:05:14 lvmcfg: File descriptor 3 left open
Apr  1 22:05:14 lvmcfg: File descriptor 4 left open
Apr  1 22:05:14 lvmcfg: File descriptor 5 left open
Apr  1 22:05:14 lvmcfg: File descriptor 6 left open
Apr  1 22:05:14 lvmcfg:   
Apr  1 22:05:14 lvmcfg: No volume groups found
Apr  1 22:05:14 lvmcfg: 
Apr  1 22:05:14 lvmcfg:   Reading all physical volumes.  This may take a while...
Apr  1 22:05:21 main-menu[31088]: (process:31140): File descriptor 3 left open 
Apr  1 22:05:21 main-menu[31088]: (process:31140): File descriptor 4 left open 
Apr  1 22:05:21 main-menu[31088]: (process:31140): File descriptor 5 left open 
Apr  1 22:05:21 main-menu[31088]: (process:31140): File descriptor 6 left open 
Apr  1 22:05:21 main-menu[31088]: (process:31140):    
Apr  1 22:05:21 main-menu[31088]: (process:31140):    
Apr  1 22:05:21 main-menu[31088]: (process:31140): Finding all volume groups 
Apr  1 22:05:21 main-menu[31088]: (process:31140):  
Apr  1 22:05:21 main-menu[31088]: (process:31140):    
Apr  1 22:05:21 main-menu[31088]: (process:31140): No volume groups found 
Apr  1 22:05:21 main-menu[31088]: (process:31140):  
Apr  1 22:05:21 main-menu[31088]: (process:31140): File descriptor 3 left open 
Apr  1 22:05:21 main-menu[31088]: (process:31140): File descriptor 4 left open 
Apr  1 22:05:21 main-menu[31088]: (process:31140): File descriptor 5 left open 
Apr  1 22:05:21 main-menu[31088]: (process:31140): File descriptor 6 left open 
Apr  1 22:05:21 main-menu[31088]: (process:31140):    
Apr  1 22:05:21 main-menu[31088]: (process:31140):    
Apr  1 22:05:21 main-menu[31088]: (process:31140): Finding all volume groups 
Apr  1 22:05:21 main-menu[31088]: (process:31140):  
Apr  1 22:05:21 main-menu[31088]: (process:31140):    
Apr  1 22:05:21 main-menu[31088]: (process:31140): No volume groups found 
Apr  1 22:05:21 main-menu[31088]: (process:31140):  

and from lspci:
> lspci -v: 0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
lspci -v: 	Subsystem: Dell: Unknown device 0195
lspci -v: 	Flags: bus master, medium devsel, latency 128, IRQ 137
lspci -v: 	I/O ports at 2800 [size=16]

---

