---
title: "Ubuntu rejects Vista HDD"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by Scynet on 2008-05-18
Hello, here's the wacky scenario:

1. I installed Vista on "Vista HDD"(140GB) and it works fine. I then unplugged this HDD.

2. I installed Ubuntu on "Ubuntu HDD"(80GB) and it works fine. I then unplugged this HDD.

3. I plugged in both HDDs and I can chooce which OS to boot to by setting the HDD boot priority from BIOS: if I chooce the Vista HDD as first boot HDD, Vista loads and works fine.

However, if I chooce Ubuntu HDD as first boot HDD, Ubuntu starts loading but comes up with this:

[http://img229.imageshack.us/my.php?image=img0519pb4.jpg](http://img229.imageshack.us/my.php?image=img0519pb4.jpg)

That is the same error I got if I tried to use Live CD or install from Live CD with Vista HDD and Ubuntu HDD both plugged in (which is the reason for this whole hassle).


In a nutshell, both OSes work fine with just their own HDD plugged in, and Vista works with both plugged in, but Ubuntu fails if Vista HDD is plugged in. 

Both HDDs are SATA drives, the Ubuntu one is from a laptop (2,5" size), Vista HDD is normal desktop drive.

I use Abit IP35 Pro motherboard, Intel Q6600, Nvidia GF 8800GT and 2GB of DDR2.

Is there any way to make Ubuntu boot up with Vista HDD plugged in? If I could do that, I could easily modify GRUB boot menu so I can select which OS to boot to without needing to use BIOS.

---

### Post by Pumalite on 2008-05-18
You have to install with both drives plugged in and let Grub install to Vista's MBR. Or install Grub to it's own partition and later change the order of booting in BIOS or boot Ubuntu with Super Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
If you cannot install with the Live CD; use the Alternate CD

---

### Post by damis648 on 2008-05-18
Quote from his post:

> **Scynet said:**
> That is the same error I got if I tried to use Live CD or install from Live CD with Vista HDD and Ubuntu HDD both plugged in (which is the reason for this whole hassle).

---

### Post by tamoneya on 2008-05-18
I agree that the problem is probably to do with the fact that you unplugged the harddrives for the installs.  It is best if you let ubuntu know about vista existance.  Unlike vista it is smart enough to play nicely with vista and will configure GRUB(the bootloader) to allow you to pick which OS to boot.  A menu will be displayed after the bios loads that lets you select.  This may actually be easier than switching the boot preferences in your BIOS.

On a side note.  What are the specs on your RAM.  I have the same motherboard and am having trouble with some patriot memory sticks.

---

### Post by Scynet on 2008-05-18
> **tamoneya said:**
> I agree that the problem is probably to do with the fact that you unplugged the harddrives for the installs.  It is best if you let ubuntu know about vista existance.  Unlike vista it is smart enough to play nicely with vista and will configure GRUB(the bootloader) to allow you to pick which OS to boot.  A menu will be displayed after the bios loads that lets you select.  This may actually be easier than switching the boot preferences in your BIOS.

On a side note.  What are the specs on your RAM.  I have the same motherboard and am having trouble with some patriot memory sticks.

But I can't install Ubuntu with Vista HDD plugged in, that's when I get the error message I posted :(

About your memory: I had problems with memory too (bluescreens). Check the memory manufacturer's site for the voltage, and use BIOS uGuru tool to make sure it's giving the DDR sticks enough power. I use OCZ Platinum which needs 1.9V minimum, and the motherboard was only giving 1.6V. I raised it to the recommended settings and it's worked like a charm since then!

> You have to install with both drives plugged in and let Grub install to Vista's MBR. Or install Grub to it's own partition and later change the order of booting in BIOS or boot Ubuntu with Super Grub:
[http://users.bigpond.net.au/hermanzo...bdiskpage.html](http://users.bigpond.net.au/hermanzo...bdiskpage.html)
If you cannot install with the Live CD; use the Alternate CD

As was pointed out, that doesn't work, since having both HDDs plugged in causes ubuntu installation, and in fact even the Live CD Demo, to fail. I tried several live CDs: 7.04, 8.04 and 8.04 64-bit Alternative. The alternative got the same messages but seemed to ignore them. However, partitioning didn't work as it didn't recognize any HDDs, so that was a dead end.

---

### Post by Pumalite on 2008-05-18
Try changing the ports.

---

### Post by Scynet on 2008-05-19
I solved this by enabling AHCI mode in the BIOS safely, by following these instructions:

[http://support.microsoft.com/kb/922976](http://support.microsoft.com/kb/922976)

Ubuntu boots up fine now. All I have to do is come up with a boot loader that has entries for both operating systems. Thanks for the help, folks! :)

PS. To anyone else who has this problem: you can't enable AHCI from BIOS without modifying the Vista registry first, or you'll get BSOD during the loading period if Vista.

---

