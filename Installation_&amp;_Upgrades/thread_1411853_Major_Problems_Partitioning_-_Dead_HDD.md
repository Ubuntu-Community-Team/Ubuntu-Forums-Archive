---
title: "Major Problems Partitioning - Dead HDD?"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by ChildOfMana on 2010-02-20
Hi,

So, I've *finally* got round to installing Ubuntu 9.10. Before I started the install I replaced my old SATA-II 500GB HDD with a brand new Western Digital SATA-II 1.5TB HDD. Now, when I try to install Ubuntu (with a manual partition scheme with a seperate partition for '/' '/home' and 'swap') It throws up the following error message;

> The ext3 file system creation in partition #5 of SCSI3 (0,0,0) (sda) failed.

I tried again but this time opted for the guided ('whole disk') partitioning option (just to see if it would make a difference) but got the same error message again.

I then re-booted and tried a third time and got the following error message;

> Input/output error during read on /dev/sda

My BIOS seems to be detecting the HDD okay and I've tried burning another Ubuntu disk and still the same happens. I've also double-checked all the leads/connections inside the case.

Does this mean I've likely bought a dud HDD? Or could there be some other, fixable explanation for this?

Thanks.

---

### Post by darkod on 2010-02-20
HDD manufacturers usually on their website have tool(s) to check hdd integrity. That would give you more exact results than any windows/ubuntu tool I think.

I'm not sure whether BIOSes are limited to take new large hdds (like flashing to accept latest CPUs). I don't know if that can be an issue.

---

### Post by ChildOfMana on 2010-02-20
Thanks darkod I didn't think about that. I'll do a bit more research and see what I can find out.

I hope it's not a dead HDD - I *really* need that PC up and running :(

---

### Post by ChildOfMana on 2010-02-21
Nothing on the HD manufacturer's website. Nothing on the BIOS manufacturer's website about 1TB+ SATA drives either.

I'm stumped :(

Looks like I'll have to try to send it back (although it's outside the 10 day return policy now) and get a replacement. See if I fare better then.

---

### Post by darkod on 2010-02-21
This is just an example because I don't know your model:
[http://support.wdc.com/product/download.asp?groupid=606&sid=3&lang=en](http://support.wdc.com/product/download.asp?groupid=606&sid=3&lang=en)

Choose model/family here and then select Data Lifeguard Diagnostic for Windows:
[http://support.wdc.com/product/download.asp?level1=6&lang=en](http://support.wdc.com/product/download.asp?level1=6&lang=en)

---

### Post by ChildOfMana on 2010-02-21
Thanks darkod... but doesn't that require a) a Windows installation (or will it run in WINE?), and b) the HDD to actually be working in the first place?

Or am I missing something?

Do I not need a bootable disk image, as opposed to an executable?

I've tried the [Ultimate Boot CD]("http://www.ultimatebootcd.com/") but it hasn't got the tool specific to my drive model.

---

### Post by darkod on 2010-02-21
Ooops. Sorry, I thought you have windows running and you want to add ubuntu. Yes, that is windows software. They offer it for floppy too, if you have a floppy drive. Just select the one for floppy.
It will probably be a bootable floppy so it doesn't matter if the hdd is working at all. But as long as you have a floppy drive.

---

### Post by ChildOfMana on 2010-02-21
No Windows. I was just making the jump from 8.10 to 9.10. I haven't used Windows for about 3 or 4 years now :)

I've got a floppy drive. I haven't got any disks... but that's easy to solve at least!

Thanks darkod. I'll give it a try when I get my hands on a floppy disk.

---

