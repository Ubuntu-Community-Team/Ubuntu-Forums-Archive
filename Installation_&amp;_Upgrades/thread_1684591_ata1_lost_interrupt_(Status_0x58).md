---
title: "ata1: lost interrupt (Status 0x58)"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by adi. on 2011-02-09
Hi,
I have Ubuntu 10.04 installed on my machine. It takes too much time to boot. When I took a look at dmesg after startup, I found that, it is something to do with the hard disk. I am getting following o/p from dmesg. 


```

--snip--
[    **1.528334**] usb 3-1: configuration #1 chosen from 1 choice
[   **21.816019**] ata1: lost interrupt (Status 0x58)
[   21.816045] ata1: drained 1 bytes to clear DRQ.
[   21.816054] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   21.816061] scsi 0:0:0:0: CDB: Inquiry: 12 00 00 00 60 00
[   21.816080] ata1.00: cmd a0/01:00:00:60:00/00:00:00:00:00/a0 tag 0 dma 96 in
[   21.816083]          res 40/00:02:00:24:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   21.816088] ata1.00: status: { DRDY }
[   26.856027] ata1: link is slow to respond, please be patient (ready=0)
[  ** 30.552028**] ata1: soft resetting link
[   30.732345] ata1.00: configured for UDMA/66
[   30.733498] ata1: EH complete
[   **51.816019**] ata1: lost interrupt (Status 0x58)
[   51.816044] ata1: drained 1 bytes to clear DRQ.
[   51.816050] ata1.00: limiting speed to UDMA/44:PIO4
[   51.816056] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   51.816061] scsi 0:0:0:0: CDB: Inquiry: 12 00 00 00 60 00
[   51.816079] ata1.00: cmd a0/01:00:00:60:00/00:00:00:00:00/a0 tag 0 dma 96 in
[   51.816081]          res 40/00:02:00:24:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   51.816086] ata1.00: status: { DRDY }
[   56.856026] ata1: link is slow to respond, please be patient (ready=0)
[   60.664039] ata1: soft resetting link
[   60.844344] ata1.00: configured for UDMA/44
[   60.845500] ata1: EH complete
--snip--

```


a 20 second delay gets introduced before these "ata1" error messages. it happens 4 times at regular intervals : 21,51,81,111 seconds.
What could be the problem?
I have dual boot on the system with Win XP and it has 5 drives. Is that the cause?
please help!

---

### Post by dino99 on 2011-02-09
Interrupt, Emacs errors: that let me think about irq conflicts

check the bios settings about irq preferences, maybe tweak the actual ones. Look hdd settings; ide/ahci/compatible ?

into a terminal, watch the output of:

dmesg | grep irq

other possible reason: how are hdd jump set (master, slave, compatible) and how its plugged (order if several hdds) on the motherboard.

i remember ages ago with an ancient kernel, some users had to add irqpoll before "quiet splash" on the boot line (/etc/default/grub, then sudo update-grub)

---

### Post by adi. on 2011-02-10
Thanks dino99 for the reply, changing bios settings helped me to reduce boot time by 20 sec.

However, I found a solution here:
[http://ubuntuforums.org/showthread.php?t=1549579](http://ubuntuforums.org/showthread.php?t=1549579)

Now my computer boots in 17 seconds :D

---

