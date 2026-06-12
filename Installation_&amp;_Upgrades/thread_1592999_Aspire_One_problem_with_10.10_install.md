---
title: "Aspire One problem with 10.10 install"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by Scotchpie on 2010-10-11
Hi

I've been using Ubuntu on my Acer Aspire One since buying it a couple of years ago. Never had any major problems until yesterday when I installed 10.10.

I downloaded the full desktop .iso and burnt it to a pen-drive.  Firstly I installed it on my main laptop and it runs flawlessly.

With the Aspire One however, though it boots into live mode and works well, after installing and rebooting all I am left with is a flashing prompt in the top left hand corner.  I left it for up to an hour thinking it may be slow to boot as its a fresh install but nothing.

So I booted again into the live distro and checked my hard drive.  As far as I can tell everything is there.  So Ubuntu installed which made me think the problem was with grub.  

From the live cd I installed grub using the commands:

>mount | tail -l 

>sudo grub-install --root-directory=/media/0d104aff-... /dev/sda

I rebooted but now I only have the grub prompt.  When I type boot I get a warning saying that the kernel needs to be installed first.

So why is 10.10 not booting?  What else can I do to fix this problem?  Any help much appreciated.

---

### Post by Scotchpie on 2010-10-11
For some reason the installer put half the OS on the SD card and half on the harddrive.  Don't know why.  As the card is none-bootable and grub was on the card that's why it didn't boot.

Just installed again without the card and everythings fine.

---

### Post by DeonStr on 2010-11-01
> **Scotchpie said:**
> For some reason the installer put half the OS on the SD card and half on the harddrive.  Don't know why.  As the card is none-bootable and grub was on the card that's why it didn't boot.

Just installed again without the card and everythings fine.

Thanks for this tip! :) It solved my problem as well!

Deon
Acer Aspire One

---

