---
title: "K3b: /usr/bin/wodim: A write error occured."
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2011-06-13
I am trying to burn a new DVD with k3b but I am getting this errors.
I am googling but any help is welcomed.
Here is the debug
Debug:
Track 02:  144 of 3815 MB written (fifo  99%) [buf 100%]   3.5x.
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
CDB:  2A 00 00 01 21 4B 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 71 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, deferred error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.025s timeout 200s

/usr/bin/wodim: A write error occured.

/usr/bin/wodim: Please properly read the error message above.
write track data: error after 151672832 bytes
Writing  time:   34.976s
Average write speed  82.9x.
Min drive buffer fill was 100%
Fixating...
Fixating time:    0.001s
/usr/bin/wodim: fifo had 2580 puts and 2390 gets.
/usr/bin/wodim: fifo was 0 times empty and 1205 times full, min fill was 94%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=4 -sao driveropts=burnfree -data -tsize=1953312s -

---

