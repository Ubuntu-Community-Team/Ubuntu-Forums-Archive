---
title: "Problem with Grub menu and bootloader"
date: 2012-09-26
forum: Installation &amp; Upgrades
---

### Post by Michl on 2012-09-26
I have 12.04 on a SATA hard drive and 10.04 on a PATA drive that is controlled by a SATA/PATA PCI card.  When I boot-up, I get a grub2 menu that lists both operating systems, but if I try to boot into 10.04, I get
this message:

error:  no such device: [followed by the long uuid code for the drive on the PCI card.]
error:  hd1 cannot get C/H/S value
error:  you need to load kernel first

But if I then Ctl-Alt-Del, I get the GNU Grub menu from the PATA drive
with 10.04 and it also lists both OS's and I can boot into either without
a problem.  When I restart, I get into this grub menu, but if I shut down and boot-up, I get the grub2 menu on the drive with 12.04

I would like to clean this up so that I have only one grub menu at start-up and can choose to boot into either OS.

I have used grub optimizer from 12.04, and all the OSs show-up, but this
does not change things.  (There is an option Install to MBR, which I was afraid of using, so I just saved the new configuration file.)

I have also used boot-repair, but this created a huge mess and a grub rescue screen.  So I re-installed 12.04 and am back to the situation described above, which is at least workable, but not efficient.

Thank you!!!!
Michael

---

### Post by darkod on 2012-09-26
It doesn't look like a grub issue directly. It seems to have some issues reading the values for your PATA disk.

You can try booting the 12.04 and in terminal run:
sudo update-grub

but I doubt that will solve it. Try it anyway. After it updates, reboot and see if that changed anything.

If not, try googling for that exact error message about the chs values.

Once that gets solved, I'm sure the 12.04 grub will boot 10.04 just fine and you will never see the second grub menu. It only shows up if you boot from the other disk.

---

### Post by Michl on 2012-09-27
Thank you so much.  grub-update didn't fix anything.  I also googled the error messages exactly and got two relevant hits, and one was this thread and another one with exactly the same problem (with Fedora and Ubuntu on
two disks), but no solution.

I checked the grubs on both disks, and I can't find a mistake.

Somehow the PATA drive can;t be found when booting from the
SATA drive with 12.04, but both drives can be found and booted
into from the grub menu on the 10.04 drive.

Michael

---

### Post by darkod on 2012-09-27
You might have a board that gives some sort of issues in SATA/PATA combination, or it favors one interface over the other.

Obvious quick solution would be to use grub2 from the PATA disk. If you want to use the grub2 from 12.04 just install it there by booting once and executing:
sudo grub-install /dev/sdb (assuming the PATA disk is /dev/sdb)

After that booting from the PATA will give you the same grub2 from 12.04.

---

### Post by YannBuntu on 2012-09-27
**@Michl:** please could you indicate the URL provided by Boot-Repair? if you don't remember, please follow [this tutorial]("https://help.ubuntu.com/community/Boot-Info") (it won't change your boot).

---

### Post by Michl on 2012-09-28
Here it is:

[http://paste.ubuntu.com/1247204/](http://paste.ubuntu.com/1247204/)

Merci!

---

### Post by YannBuntu on 2012-09-28
ok
Currently you have GRUB 12.04 (the one with 12.04 by default) in sda (80GB), and GRUB 10.04 (the one with 10.04 by default) in sdb (120GB).

Your BIOS should allow you to choose the boot order priority.

- in the BIOS, you can choose to place the 80GB disk first, so that you will access the GRUB 12.04 when rebooting the PC. From this GRUB 12.04 menu, do the first entry ('Ubuntu, with Linux 3.2.0-31-generic') allow you to boot Ubuntu12.04?
Do the "Ubuntu, with Linux 2.6.32-43-generic (on /dev/sdb1)" entry allow you to boot Ubuntu10.04 ?

- in the BIOS, you can choose to place the 120GB disk first, so that you will access the GRUB 10.04 when rebooting the PC.
From this GRUB 10.04 menu, do the first entry ('Ubuntu, with Linux 2.6.32-43-generic') allow you to boot Ubuntu10.04?
Do the "Ubuntu, with Linux 3.2.0-31-generic (on /dev/sda1)" entry allow you to boot Ubuntu12.04 ?

---

### Post by Michl on 2012-09-28
> **YannBuntu said:**
> ok
Currently you have GRUB 12.04 (the one with 12.04 by default) in sda (80GB), and GRUB 10.04 (the one with 10.04 by default) in sdb (120GB).

Yes.  also, sdb is on a PCI controller, while sda is on a motherboard controller.

> **YannBuntu said:**
> Your BIOS should allow you to choose the boot order priority.

- in the BIOS, you can choose to place the 80GB disk first, so that you will access the GRUB 12.04 when rebooting the PC. From this GRUB 12.04 menu, do the first entry ('Ubuntu, with Linux 3.2.0-31-generic') allow you to boot Ubuntu12.04?

Yes, no problem.

> **YannBuntu said:**
> Do the "Ubuntu, with Linux 2.6.32-43-generic (on /dev/sdb1)" entry allow you to boot Ubuntu10.04 ?

No.  Here I get the error message quoted in my first message.


> **YannBuntu said:**
> - in the BIOS, you can choose to place the 120GB disk first, so that you will access the GRUB 10.04 when rebooting the PC.
From this GRUB 10.04 menu, do the first entry ('Ubuntu, with Linux 2.6.32-43-generic') allow you to boot Ubuntu10.04?

Yes, from the sdb grub I can boot successfully into 10.04 or 12.04.
Also, I do not need to go into BIOS and change the boot order.  If
in the 12.04 grub menu I ctr-alt-del (or simply reboot forcible with the
on/off switch, I will automatically boot into the sdb grub.  So this is
workable, but not proper.


> **YannBuntu said:**
> Do the "Ubuntu, with Linux 3.2.0-31-generic (on /dev/sda1)" entry allow you to boot Ubuntu12.04 ?

Yes.

I hope you can solve the mystery.  Darkod recommends I try to load
the sdb grub onto sda1.  I'll try that if this path runs out, but
I couldn't find a relevant difference.  I am thinking that maybe
I need to have the very same grub file in both MBRs?

Dunno,
Michael

---

### Post by YannBuntu on 2012-09-28
ok.
Please could you check in your BIOS if it's possible for you to put the 120GB in first place in the boot order?  (so that the GRUB10.04 appears directly without needing Ctrl+Alt+Del)

---

### Post by darkod on 2012-09-28
I never said to load any grub2 to sda1. That's a partition, and usually you don't install the bootloader to partitions.

I suggested to install the grub2 from 12.04 onto /dev/sdb since grub from that disk seems to load fine.

---

### Post by Michl on 2012-09-28
> **darkod said:**
> I never said to load any grub2 to sda1. That's a partition, and usually you don't install the bootloader to partitions.

I suggested to install the grub2 from 12.04 onto /dev/sdb since grub from that disk seems to load fine.

Darko,
Super sorry!  Just to double-check my understanding here.
In both drives, I have 3 partitions:  /, /home, and swap.
/ is bootable, the others aren't.  / is sda1 in the
case of the SATA drive and sdb1 in the case of the PATA
drive.  I've always had (and on all my other computers,
laptops and netbookd) the system files in / and that partition
is sd*1.

The grub that works is the one on sdb (the PATA drive) and the
one that doesn't is on sda.

I'll get all this straight one of these days!!!!  Thank you.
Michael

---

### Post by darkod on 2012-09-28
You are correct. My idea is this:
Right now the situation is, the bootloader on sda boots only sda and not sdb.
The bootloader on sdb boots both disks.

In case sda has some issues with the bootloader seeing sdb correctly, regardless to which OS that bootloader belongs, lets put the 12.04 grub2 on sdb, for a test.

For this, you only need to boot 12.04 (regardless whether from sda or sdb), open terminal and do:
sudo grub-install /dev/sdb

That will put it on the MBR of sdb (notice how there are no numbers in /dev/sdb).

If by any chance that makes 10.04 unbootable, don't panic since it's easy to return the 10.04 grub on sdb.

---

### Post by Michl on 2012-09-28
> **darkod said:**
> You are correct. My idea is this:
Right now the situation is, the bootloader on sda boots only sda and not sdb.
The bootloader on sdb boots both disks.

In case sda has some issues with the bootloader seeing sdb correctly, regardless to which OS that bootloader belongs, lets put the 12.04 grub2 on sdb, for a test.

For this, you only need to boot 12.04 (regardless whether from sda or sdb), open terminal and do:
sudo grub-install /dev/sdb

That will put it on the MBR of sdb (notice how there are no numbers in /dev/sdb).

If by any chance that makes 10.04 unbootable, don't panic since it's easy to return the 10.04 grub on sdb.


Got it!!

---

### Post by Michl on 2012-09-28
> **YannBuntu said:**
> ok.
Please could you check in your BIOS if it's possible for you to put the 120GB in first place in the boot order?  (so that the GRUB10.04 appears directly without needing Ctrl+Alt+Del)

Yes, the 120GB is ahead of the 80GB drive.  WHat is strange, though, is that it seems to ignore this and boot into the 80GB drive.  This might
be getting close.  Bios recognizes both drives, it recognizes the controller, but when booting first, it ignores the 120 drive.

---

