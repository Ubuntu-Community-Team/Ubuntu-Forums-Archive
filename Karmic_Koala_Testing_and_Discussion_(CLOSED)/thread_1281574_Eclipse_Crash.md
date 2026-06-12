---
title: "Eclipse Crash"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jlward4th on 2009-10-03
A recent change in Karmic is causing my eclipse-jee-galileo with Sun Java 6.0_15-b03 to crash.  Here is the crash report:
```
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGBUS (0x7) at pc=0x04f4bc0d, pid=19815, tid=54913904
#
# JRE version: 6.0_15-b03
# Java VM: Java HotSpot(TM) Client VM (14.1-b02 mixed mode, sharing linux-x86 )
# Problematic frame:
# V  [libjvm.so+0x2fcc0d]
#
# An error report file with more information is saved as:
# /home/jamesw/hs_err_pid19815.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
#
Aborted (core dumped)
```

Switching to the Open JDK allows Eclipse to run but causes other issues in Eclipse.

Any ideas?  Thanks.

---

### Post by Copernicus1234 on 2009-10-03
> **jlward4th said:**
> 
Any ideas?

Yes.

Check the log file mentioned in the error message. :)

---

### Post by jlward4th on 2009-10-03
Log is attached.  Nothing in there that makes any sense to me about the potential cause of the error.

---

### Post by jlward4th on 2009-10-03
Actually looking through that log did help a bit...  The cause is:
```
Error accessing class data sharing archive. Mapped file inaccessible during execution,  possible disk/network problem.
```

And now looking in my dmesg I see:
```
Oct  3 12:06:23 dos kernel: [50830.017220] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Oct  3 12:06:23 dos kernel: [50830.017223] ata1.00: irq_stat 0x40000008
Oct  3 12:06:23 dos kernel: [50830.017228] ata1.00: cmd 60/08:00:19:34:73/00:00:07:00:00/40 tag 0 ncq 4096 in
Oct  3 12:06:23 dos kernel: [50830.017229]          res 41/40:08:19:34:73/8b:00:07:00:00/40 Emask 0x409 (media error) <F>
Oct  3 12:06:23 dos kernel: [50830.017231] ata1.00: status: { DRDY ERR }
Oct  3 12:06:23 dos kernel: [50830.017232] ata1.00: error: { UNC }
Oct  3 12:06:23 dos kernel: [50830.017914] ata1.00: configured for UDMA/133
Oct  3 12:06:23 dos kernel: [50830.017923] ata1: EH complete
Oct  3 12:06:23 dos kernel: [50830.019667] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Oct  3 12:06:23 dos kernel: [50830.019670] ata1.00: irq_stat 0x40000008
Oct  3 12:06:23 dos kernel: [50830.019677] ata1.00: cmd 60/08:00:19:34:73/00:00:07:00:00/40 tag 0 ncq 4096 in
Oct  3 12:06:23 dos kernel: [50830.019679]          res 41/40:08:19:34:73/8b:00:07:00:00/40 Emask 0x409 (media error) <F>
Oct  3 12:06:23 dos kernel: [50830.019682] ata1.00: status: { DRDY ERR }
Oct  3 12:06:23 dos kernel: [50830.019685] ata1.00: error: { UNC }
Oct  3 12:06:23 dos kernel: [50830.020224] ata1.00: configured for UDMA/133
Oct  3 12:06:23 dos kernel: [50830.020231] ata1: EH complete
Oct  3 12:06:23 dos kernel: [50830.023071] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Oct  3 12:06:23 dos kernel: [50830.023074] ata1.00: irq_stat 0x40000008
Oct  3 12:06:23 dos kernel: [50830.023082] ata1.00: cmd 60/08:00:19:34:73/00:00:07:00:00/40 tag 0 ncq 4096 in
Oct  3 12:06:23 dos kernel: [50830.023084]          res 41/40:08:19:34:73/8b:00:07:00:00/40 Emask 0x409 (media error) <F>
Oct  3 12:06:23 dos kernel: [50830.023088] ata1.00: status: { DRDY ERR }
Oct  3 12:06:23 dos kernel: [50830.023090] ata1.00: error: { UNC }
Oct  3 12:06:23 dos kernel: [50830.023799] ata1.00: configured for UDMA/133
Oct  3 12:06:23 dos kernel: [50830.023810] ata1: EH complete
Oct  3 12:06:23 dos kernel: [50830.025550] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Oct  3 12:06:23 dos kernel: [50830.025554] ata1.00: irq_stat 0x40000008
Oct  3 12:06:23 dos kernel: [50830.025561] ata1.00: cmd 60/08:00:19:34:73/00:00:07:00:00/40 tag 0 ncq 4096 in
Oct  3 12:06:23 dos kernel: [50830.025563]          res 41/40:08:19:34:73/8b:00:07:00:00/40 Emask 0x409 (media error) <F>
Oct  3 12:06:23 dos kernel: [50830.025566] ata1.00: status: { DRDY ERR }
Oct  3 12:06:23 dos kernel: [50830.025569] ata1.00: error: { UNC }
Oct  3 12:06:23 dos kernel: [50830.026150] ata1.00: configured for UDMA/133
Oct  3 12:06:23 dos kernel: [50830.026156] ata1: EH complete
Oct  3 12:06:23 dos kernel: [50830.027875] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Oct  3 12:06:23 dos kernel: [50830.027879] ata1.00: irq_stat 0x40000008
Oct  3 12:06:23 dos kernel: [50830.027886] ata1.00: cmd 60/08:00:19:34:73/00:00:07:00:00/40 tag 0 ncq 4096 in
Oct  3 12:06:23 dos kernel: [50830.027888]          res 41/40:08:19:34:73/8b:00:07:00:00/40 Emask 0x409 (media error) <F>
Oct  3 12:06:23 dos kernel: [50830.027892] ata1.00: status: { DRDY ERR }
Oct  3 12:06:23 dos kernel: [50830.027894] ata1.00: error: { UNC }
Oct  3 12:06:23 dos kernel: [50830.028555] ata1.00: configured for UDMA/133
Oct  3 12:06:23 dos kernel: [50830.028561] ata1: EH complete
Oct  3 12:06:23 dos kernel: [50830.030892] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
Oct  3 12:06:23 dos kernel: [50830.030895] ata1.00: irq_stat 0x40000008
Oct  3 12:06:23 dos kernel: [50830.030903] ata1.00: cmd 60/08:00:19:34:73/00:00:07:00:00/40 tag 0 ncq 4096 in
Oct  3 12:06:23 dos kernel: [50830.030904]          res 41/40:08:19:34:73/8b:00:07:00:00/40 Emask 0x409 (media error) <F>
Oct  3 12:06:23 dos kernel: [50830.030908] ata1.00: status: { DRDY ERR }
Oct  3 12:06:23 dos kernel: [50830.030910] ata1.00: error: { UNC }
Oct  3 12:06:23 dos kernel: [50830.031514] ata1.00: configured for UDMA/133
Oct  3 12:06:23 dos kernel: [50830.031520] sd 0:0:0:0: [sda] Unhandled sense code
Oct  3 12:06:23 dos kernel: [50830.031522] sd 0:0:0:0: [sda] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
Oct  3 12:06:23 dos kernel: [50830.031525] sd 0:0:0:0: [sda] Sense Key : Medium Error [current] [descriptor]
Oct  3 12:06:23 dos kernel: [50830.031528] Descriptor sense data with sense descriptors (in hex):
Oct  3 12:06:23 dos kernel: [50830.031530]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
Oct  3 12:06:23 dos kernel: [50830.031537]         07 73 34 19 
Oct  3 12:06:23 dos kernel: [50830.031540] sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
Oct  3 12:06:23 dos kernel: [50830.031544] end_request: I/O error, dev sda, sector 124990489
Oct  3 12:06:23 dos kernel: [50830.031551] ata1: EH complete
```

So I have a corrupt file!  Now I just need to find out what file it is.

Any ideas?

---

### Post by jlward4th on 2009-10-03
Took a shot in the dark - reinstalled the Sun JDK.  Error went away!  So there must have been something wrong with part of my drive.

---

### Post by Copernicus1234 on 2009-10-03
> **jlward4th said:**
> Took a shot in the dark - reinstalled the Sun JDK.  Error went away!  So there must have been something wrong with part of my drive.

Yes, I did some googling on that error and it seems people agree its caused by some kind of problem with the hardware. Hopefully your disk is not about to fail. :)

---

