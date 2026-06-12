---
title: "missing operating system woes"
date: 2006-12-04
forum: Installation &amp; Upgrades
---

### Post by latro666 on 2006-12-04
Ok, thought i'd get into linux, I have been using knoppix for a while on my laptop using the live cd. 

was recogmended ubuntu as it is 'easy' to get installed and running.

So. 

I loaded the cd, fine
installed to step 6 fine (no partitions whatso ever and selected the erase all option)
step 5 said it would create 2 partitions one swap and another one.. ok. 

so it chugged along for an hour or so installing. Then the cd drive pops open and in blue text it said remove the cd close the tray and press enter. I did this and the laptop shut down. 

I loaded the laptop back up and selected boot from hard drive. 

'Missing operating system'

what am i doing wrong? I'm not really all that impressed whatever you say about XP, at least it installs.

laptop is an oldish (2001/2) Toshiba Satellite 

i'm thinking its on there just not booting propperly? any help apreciated before i go back to M$

---

### Post by Sef on 2006-12-04
> i'm thinking its on there just not booting propperly?

To [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub").

If that does not do it, download the alternate cd, and install from that.  It is text-based, but easy to follow directions.

> laptop is an oldish (2001/2) Toshiba Satellite


How much ram do you have?

---

### Post by Delta_Farce on 2006-12-04
When the system loads, do you see the Grub boot menu? This should be the first thing that comes up.

If that fails, can you remember if you set the first partition on your hard drive to be bootable (should be called / from the sounds of your system)? This should be an automatic thing, but it's worth checking.

---

