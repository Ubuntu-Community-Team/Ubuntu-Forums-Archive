---
title: "Can't Boot 10.04: ata4: SATA link down"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by asuastrophysics on 2010-05-03
Dear all,

I seem to be unable to boot up my computer. After upgrading from 9.10 to 10.04, I get the following messages during boot up:
```
(lots of text is going by)...
write protect is off
write cache: enabled, read cache: enabled, doesn&#8217;t support DPO or FUA
sdb: sdb1 sdb2 < sdb5 > 
sd 2:0:0:0: [sdb] Attached SCSI disk
ata4: SATA link down (SStatus 0 SControl 300)

```
(this is the verbose output. the plymouth splash screen hangs, or hangs while showing: "the disc drive / is not ready or does not exist")

Does anyone know what's going on here? I appreciate the help! 
if you need me to post a log file, just let me know and I'd be more than happy to post it.

---

### Post by asuastrophysics on 2010-05-03
bump

please help me i'm really stuck here.

---

### Post by theviking10 on 2010-05-12
Same problem here. I also get a "Unable to find a medium containing a live file system" error after I'm dropped into busybox.

---

### Post by byStanderone on 2010-05-12
...could you run sudo upgrade-grub in a console?

---

### Post by asuastrophysics on 2010-05-12
> **byStanderone said:**
> ...could you run sudo upgrade-grub in a console?

I tried that about a dozen times. I also tried completely reinstalling grub2. Didn't fix it. I tried going back to grub legacy. Didn't fix it. 

Can you please help me??? I really need help here. I'm really about to just throw the whole computer away.

In "grub rescue" mode, I tried the following commands, as posted by ubuntu documentation:
"1. ls

2. set prefix=(hdX,Y)/boot/grub

3*. set root=(hdX,Y)

4. set

5. ls /boot

6. insmod /boot/grub/linux.mod

7*. linux /vmlinuz root=/dev/sdxY ro

8. initrd /initrd.img

9. boot "
However, on "insmod /boot/grub/linux.mod" I get:
```
error: the symbol 'grub_getcharwidth" not found.
```
What do I do???

---

### Post by byStanderone on 2010-05-13
...take a look at this thread, it's a nice one, hope it helps:

[http://ubuntuforums.org/showthread.php?t=1481841](http://ubuntuforums.org/showthread.php?t=1481841)

---

### Post by out-of-hand on 2010-07-28
hi there , i also have this problem, 

Pc is a foxconn intel 2 core.  i have tried with wubi... within windows ... and when it boots i get stuck when it counts down.
i then try reboot in safe graphics mode. and i get this same error i will attach a picture .


i have 3 hdd  the one has windows xp. and other 2 are empty, i tried to boot off a usb boot.. and it gets to the same position before even asking me where i wanna install ubuntu 

please help me anyone ... i really wanna get off windoze ...

[http://imagebin.org/107115]("http://imagebin.org/107115")

---

