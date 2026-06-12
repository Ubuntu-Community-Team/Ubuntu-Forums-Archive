---
title: "Compaq EVO D510 e-pc and GRUB (Solved)"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by Soarer on 2007-07-27
About a year ago I did my first Ubuntu install on the aforementioned PC. I couldn't get GRUB to work - it just hung at stage 1.5. Fortunately I had another machine handy, and it installed on that first time. So I persevered and after much reading I managed to install LILO instead, which has worked just fine. Thing was, I didn't like it not recognising kernel upgrades.

Recently I read the manual on the Compaq, and discovered that there were switches on the mobo, one of which, as default,  prevents overwriting the MBR. After flicking this switch, I was able to install GRUB and boot using it. Works fine now.

One small thing was fstab, which needed it's entries changed from /dev/hda? to /dev/sda?. No idea why :)

---

### Post by flyboy_2003 on 2007-11-10
> **Soarer said:**
> About a year ago I did my first Ubuntu install on the aforementioned PC. I couldn't get GRUB to work - it just hung at stage 1.5. Fortunately I had another machine handy, and it installed on that first time. So I persevered and after much reading I managed to install LILO instead, which has worked just fine. Thing was, I didn't like it not recognising kernel upgrades.

Recently I read the manual on the Compaq, and discovered that there were switches on the mobo, one of which, as default,  prevents overwriting the MBR. After flicking this switch, I was able to install GRUB and boot using it. Works fine now.

One small thing was fstab, which needed it's entries changed from /dev/hda? to /dev/sda?. No idea why :)

I don't have a manual for this machine, nor can I find one. Can you please tell me which switches on the motherboard you are referring to? I am having the same problems here with Linux. I tried to install Untangle gateway (Knoppix based), and it's confused as well. Some Linux distros show the partitions as /dev/hda, but once installed, the partitions show up as /dev/sda. And in any event, GRUB will not install properly.

Mine, by the way, is the EVO D510 e-pc SFF. 

Thanks

---

### Post by Soarer on 2007-11-11
I have this manual:

technical reference manual
Evo D510 e-pc
Document Part Number: 305511-001
August 2002

which I downloaded from hp.com. I couldn't find it again just now, though. I'd be happy to send it to you if you PM me your email address.

It refers to a bank of switches on the motherboard. This is a small, blue block near the processor on the edge of the board. There are 3 white switches. No 1 switch in the 'On' position, prevents the overwriting of the bootblock. No 2, in the 'On' position resets the CMOS, including passwords. No 3 doesn't do anything

Switch Switch Position Function
1      ON              Bootblock protected (default)
       OFF             Bootblock not protected
2      ON              Clear CMOS and reload default values in
                       Computer Setup. Clear all passwords.
       OFF             CMOS locked (default)
3      ON              Reserved
       OFF             Reserved (default)

---

