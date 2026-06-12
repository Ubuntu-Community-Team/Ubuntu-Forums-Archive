---
title: "Xubuntu does not load after upgrade to kernel 2.6.22.14"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by todoporron on 2008-01-14
Hi all.

First of all, I have already searched the forums and the net for 2 days now about this and nothing has come helpful.

After upgrading to xubuntu 7.10 and therefore to kernel 2.6.22.14-generic and 2.6.22.14-i386, the sistem just does not load. (grub does load ok)

It worked like a charm with previous kernels. (In fact, I'm writing this with 2.6.20.16 .kernel)

When I tell to boot with 2.6.22.14 (generic or i386)  in recovery mode, it says "starting the files needed to boot" and after all  I get is this kind of repeating messages (every 30 seconds aprox):

[511.646545] ata1: soft resetting port
[511.689548] ata1.00: configured for UDMA/25
[511]986532] ata1: EH complete
[511.689547] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[511.689574] ata1.00: cmd c8/00:00:0f:b0:04:00:00: tag 0 cdb 0x0 data 131072 in
[511.523678] res 40/00:00:00:00:00:00/00:00:00  .... Emask 0x4 (timeout)

and so on, the only thing that changes are the numbers in []

System is an old pentium II with 128 Mb RAM and 8.5 GB hard drive, onboard SIS graphics. 

I already tried the acpi=off option but nothing happens. And I don't think the problem is due to graphics drivers. I've been using Ubuntu for more than 2 years on the 3 PC's at my office so I'm not so noob.

Any hint??

Thanks a lot
:confused:

---

### Post by Foxray on 2008-01-14
You may want to replace your hard drive with another one and see if it happens again, it might be a sign that the drive is dying. This happened to my other ubuntu rig as well and after i replaced the hard drive no more error messages. Do you have another hard drive lying around?

---

### Post by todoporron on 2008-01-15
Hi, thanks for the answer.

I hardly think it's a hdd problem. Anyway, I'm trying to get another hdd to test. In the meantime, I just commented the lines which refer to kernel 2.6.22.14 on /boot/grub/menu.lst so I can boot with kernel 2.6.20.16 at once.

---

