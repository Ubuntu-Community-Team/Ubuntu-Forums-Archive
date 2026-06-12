---
title: "HDIO_GET_IDENTITY failed"
date: 2010-04-12
forum: Installation &amp; Upgrades
---

### Post by rudyard12 on 2010-04-12
Hi,

I installed ubuntu 9.10 (64 bit) on a new lenovo thinkstation D20 with Intel Xeon processors. I installed ubuntu one week ago. after running fine for a couple of days, the screen froze and I had to reboot. The startup then stalled following choosing the Ubuntu version to load in GRUB and showing me an error message something like: 
HDIO_GET_IDENTITY failed for...

I then re-installed ubuntu and it ran fine until a couple of hours ago when the same thing happened again. Now, the error message says:

ata_id[461]: HDIO_GET_IDENTITY failed for '/dev/.tmp-block-8:16'

Could anyone help please? I don't know what that means and couldn't find infos online.

Thank you very much in advance!!!

R

---

### Post by drreed on 2010-04-12
> **rudyard12 said:**
> Hi,


ata_id[461]: HDIO_GET_IDENTITY failed for '/dev/.tmp-block-8:16'


R


I'll offer my 2 cents if that's ok?

Are you using a scsi drive? sata? how about RAID? I dropped that in google and found a lot of stuff about RAID.

Actually, I'm finding some other stuff too, and this sounds like an interesting problem. I'd like to see the startup log. Maybe that big Xeon desktop has some cutting-edge stuff going on with it, and some things need tweaking.

---

