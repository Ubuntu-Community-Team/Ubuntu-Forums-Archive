---
title: "Installation problem,partitionar stuck at 52%...."
date: 2006-03-04
forum: Installation &amp; Upgrades
---

### Post by soni456 on 2006-03-04
Hello,
I am new member of ubuntu forum, I got around 50 cd's of 
ubuntu 5.10 for me as well as friends and classmates. 
Now problem is this that i'm not able to install ubuntu 5.10 on my system. Apart from this i'm also  using RedHat 7.2 , It is working perfectly on my system. 
         [B]My System specification is as follows,
            *    Intel P-III 667 MHz.
            *    RAM : 64 MB SDRAM
            *    HDD : 20 GB IDE drive from Seagate.
            *    CDROM : LG CDROM 52x
[/B]
      Now when I tried to install ubuntu on my system it goes all well till the partitionar, but when the partitionar start it ones complete 100% mark then screen goes blank for few(3-4) seconds and partitionar again starts and goes upto 52% mark and stuck there. I can't understand what is the problem. please some one help me I'm eagrly waiting to use ubuntu on my system.
        I'm also including few last lines of "messages" , "syslog" & "partman" files from /var/log directory.

**_ messages_**
.....
.....
insmod /lib/modules/2.6.12-9-386/kernel/drivers/ide/ide-generic.ko 
insmod /lib/modules/2.6.12-9-386/kernel/drivers/ide/ide-floppy.ko 
insmod /lib/modules/2.6.12-9-386/kernel/drivers/ide/ide-disk.ko 
insmod /lib/modules/2.6.12-9-386/kernel/drivers/cdrom/cdrom.ko 
insmod /lib/modules/2.6.12-9-386/kernel/drivers/ide/ide-cd.ko 
insmod /lib/modules/2.6.12-9-386/kernel/fs/isofs/isofs.ko 
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
  No matching physical volumes found
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
  No volume groups found
  Reading all physical volumes.  This may take a while...

**_syslog_**
.....
.....
Feb  3 13:50:22 main-menu[15864]: DEBUG: Menu item 'partman-base' selected 
Feb  3 13:50:22 main-menu[15864]: DEBUG: configure partman-base, status: 2  
Feb  3 13:50:22 main-menu[15864]: DEBUG: configure libc6, status: 0  
Feb  3 13:50:22 main-menu[15864]: DEBUG: virtual package libc6  
Feb  3 13:50:22 main-menu[15864]: DEBUG: configure libparted1.6-12, status: 0  
Feb  3 13:50:22 main-menu[15864]: DEBUG: virtual package libparted1.6-12  
Feb  3 13:50:22 main-menu[15864]: DEBUG: configure harddrive-detection, status: 0  
Feb  3 13:50:22 main-menu[15864]: DEBUG: virtual package harddrive-detection  

**_partman_**
.....
.....
parted_server: Closing infifo and outfifo
parted_server: main_loop: iteration 34
parted_server: Opening infifo
/lib/partman/automatically_partition/10resize_use_free/choices: 1 primary partitions, 1 logical partitions
/lib/partman/automatically_partition/10resize_use_free/choices: filtered partition list:
/lib/partman/automatically_partition/10resize_use_free/choices: 1 32256-5009195519 5009163264 primary fat32 /dev/ide/host0/bus0/target0/lun0/part1 
-1 5009195520-15060487679 10051292160 pri/log free /dev/ide/host0/bus0/target0/lun0/part-1 
5 15060519936-20020331519 4959811584 logical fat32 /dev/ide/host0/bus0/target0/lun0/part5 
/lib/partman/automatically_partition/10resize_use_free/choices: IN: GET_RESIZE_RANGE =dev=ide=host0=bus0=target0=lun0=disc 32256-5009195519
parted_server: Read command: GET_RESIZE_RANGE
parted_server: command_get_resize_range()
parted_server: Opening outfifo
parted_server: partition_with_id(32256-5009195519)
parted_server: named_partition_is_virtual(=dev=ide=host0=bus0=target0=lun0=disc,63,9783584)
parted_server: no
/bin/partman: *******************************************************
/lib/partman/init.d/30parted: *******************************************************
/lib/partman/init.d/31md-devices: *******************************************************
/lib/partman/init.d/35dump: *******************************************************

Please someone help me.

---

