---
title: "How to &quot;hide&quot; Ubuntu installation?"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by MustNotSleep on 2010-06-12
Hi,

I want to install Ubuntu on my family's PC, but don't want them to freak out when they see the Grub menu (they're used to Windows booting immediately after starting the machine). I will be the only one using Ubuntu, so I was looking for a way to:

- Install Ubuntu on the same HDD (there's plenty of space).
- Be able to boot Ubuntu only with a special "key", like upon setting the PC to boot from my USB drive that will have Grub, only then will I be able to boot into Ubuntu.

Sorry if this makes no sense. I basically want to install Grub on my USB drive, which will then serve as the "key" to boot Ubuntu on the machine.

Is there an easy way to accomplish this? I haven't installed Ubuntu in some time, so what settings should I check so it installs Grub on my USB drive, and **doesn't** overwrite my MBR (important!)?

Thanks for your help.

-MNS

---

### Post by darkod on 2010-06-12
It should be easy. First boot the ubuntu cd in live mode, and in terminal run:

sudo fdisk -l

to see all disks and partitions. Depending how many internal/external disks you might have, and the stick, it might show like:

/dev/sda int hdd1
/dev/sdb int hdd2
/dev/sdc ext hdd
/dev/sdd usb stick

This is just rough assumption, you won't get that layout. Note down the device name of your stick, like /dev/sdd.

Then click on the Install icon on desktop. Go trough the install, set where to install ubuntu. In the last screen of the installer, before clicking Install, click on Advanced and tell the bootloader to install on /dev/sdd (with no number in it, just the MBR of the stick, /dev/sdd).

That should be it.

---

### Post by DrMelon on 2010-06-12
Darkod's suggestion should do the trick. Remember to set your USB key to boot in the BIOS when you want to use it.

---

### Post by snowpine on 2010-06-12
Just install Ubuntu to your USB drive, you'll have a fully portable Ubuntu install that you can use on any computer without altering the HDD or leaving any trace. Secretly installing Ubuntu on your family's computer may seem like a good idea, but if something goes wrong, you'll have a lot of explaining to do. :)

---

### Post by MustNotSleep on 2010-06-12
Thanks for the explanation, darkod. :-) I thought it should be easy, just wasn't sure what the best procedure was.

> **snowpine said:**
> Just install Ubuntu to your USB drive, you'll have a fully portable Ubuntu install that you can use on any computer without altering the HDD or leaving any trace. Secretly installing Ubuntu on your family's computer may seem like a good idea, but if something goes wrong, you'll have a lot of explaining to do. :)

Heheh indeed, I agree with you there. The problem is that right now I don't have enough space on my external USB drive, and all my flash drives are too small. In the future when I get enough space, I might go with this option. Thanks!

Related question: how does Ubuntu deal with booting from several different machines? For example, if I install it on a USB drive on a multi-core machine with several devices, and then boot it on a single-core machine with a different set of devices, won't that mess up the configuration and/or leave unnecessary drivers/clutter on my drive?

Thanks for the help, guys. Really appreciate it. :-D

//EDIT: Oh, BTW, I'm going through several measures to insure that I can rollback in case something goes wrong with the installation. I'll be backing up all important files from the Windows install, as well as doing a full HDD clone. Hopefully, I won't be needing either. :-)

---

### Post by DrMelon on 2010-06-12
> **MustNotSleep said:**
> 

//EDIT: Oh, BTW, I'm going through several measures to insure that I can rollback in case something goes wrong with the installation. I'll be backing up all important files from the Windows install, as well as doing a full HDD clone. Hopefully, I won't be needing either. :-)

That's the way to do it! You've got your bases covered. Backups are invaluable during any slightly-risky process.

---

### Post by snowpine on 2010-06-12
> **MustNotSleep said:**
> Related question: how does Ubuntu deal with booting from several different machines? For example, if I install it on a USB drive on a multi-core machine with several devices, and then boot it on a single-core machine with a different set of devices, won't that mess up the configuration and/or leave unnecessary drivers/clutter on my drive?

Assuming you use Ubuntu's own "USB Startup Creator" you should be able to boot the USB drive on any computer with no hassles, just as you would with a Live CD. Ubuntu auto-detects your hardware during the boot process and loads the appropriate modules for the situation.

---

