---
title: "Dual Ubuntu booting"
date: 2015-01-30
forum: Installation &amp; Upgrades
---

### Post by Riback on 2015-01-30
I have 12.04 64 bit installed on my server. I would like to see what 14.04 is like to use - is it possible to dual boot the 2 systems.
Would run a bootable USB drive with 14.04 on.

---

### Post by Bucky Ball on 2015-01-30
If you mean run a USB Live installer and 'Try Ubuntu', sure, go for it. You can run it from the USB and try it out. If you want to dual-boot two Ubuntus, that is easy, too. Just install one on another partition (but that depends on if you have installed in BIOS or UEFI mode). BIOS mode will only handle four partitions per drive, but you can overcome that limitation by using extended partitions.

I have about three Ubuntus installed in an extended partition at last count (although I only really use one and haven't looked for awhile).

Try 14.04 LTS from the install media and take it from there would be my advice. Good luck. ;)

---

### Post by Bashing-om on 2015-01-30
Riback; Sure !

I multi-boot; for reference:
```

sysop@1404mini:~$ sudo blkid
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdc1: LABEL="1404std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdc2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 

```
Just keep in mind that the last system installed has control of booting, until you change it .

[INDENT]it's 'buntu
[INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-01-30
> **Bashing-om said:**
> 
Just keep in mind that the last system installed has control of booting, until you change it .

Exactly what I thought to say, but omitted saying! ;)

Last one in has control. It installs grub over the previous. You can change which one has the final say later, of course.

---

