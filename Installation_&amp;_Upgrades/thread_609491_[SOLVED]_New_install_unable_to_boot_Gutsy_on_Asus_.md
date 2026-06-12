---
title: "[SOLVED] New install: unable to boot Gutsy on Asus M2A-VM mobo with 64-bit Athlon"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by makeyre on 2007-11-11
I've read through all the other posts which try to get Ubuntu to boot with this motherboard, and despite trying many different options in grub (delete "quiet", ide_generic_all, acpi=off, pci=noacpi, noapic, nolapic, irqpoll), I've turned off HPET in BIOS.  I can't get it to boot normally - all I see when it boots up is a bunch of text then a black screen - I've waited 5-10 minutes and it doesn't change.

Rescue console works and I can "startx" from there to boot into GNOME from my root user just fine.  Applications seem to work, but things are very buggy: there is no network support for some reason, the hardware information/device manager tool crashes when I try to run it, and finally, if I click on the "Quit" button the machine becomes unresponsive and I have to CTRL-ALT-BKSP to kill X and get back to the rescue console.

I installed from the 7.10 alternate CD for 64-bit AMD machines with no problems, and chose a guided LVM/encrypted partition.  I can easily get into the machine via the rescue console so encryption seems to be fine.

Hardware list: BIOS revision 0302 for the motherboard, using onboard graphics, Seagate SATA II hard drive with NCQ and jumper pulled so as to allow up to 3 Gbps speed, SATA DVD+-RW drive, AMD Athlon X2 BE-2400 CPU.

Please help, especially if you've used an M2A-VM board successfully.  People seem to be having lots of issues with this board and I'm not sure why, as it's not particularly new - I believe it's been out for at least 9 months.

Links I've already visited and tried:
[http://ubuntuforums.org/showthread.php?t=435075](http://ubuntuforums.org/showthread.php?t=435075)
[http://ubuntuforums.org/showthread.php?t=584868](http://ubuntuforums.org/showthread.php?t=584868)
[http://ubuntuforums.org/showthread.php?t=552413](http://ubuntuforums.org/showthread.php?t=552413)
[https://bugs.launchpad.net/ubuntu/+bug/155349](https://bugs.launchpad.net/ubuntu/+bug/155349)
[http://ubuntuforums.org/showthread.php?t=398653&highlight=M2A-VM](http://ubuntuforums.org/showthread.php?t=398653&highlight=M2A-VM)
[http://ubuntuforums.org/showthread.php?t=592662&highlight=M2A-VM](http://ubuntuforums.org/showthread.php?t=592662&highlight=M2A-VM)

---

### Post by makeyre on 2007-11-15
No one has any suggestions?  I have Ubuntu on all my other machines but I've never had a hardware problem I can't even begin to diagnose...

---

### Post by benbelly on 2007-11-15
I have the identical symptoms on very different hardware.  I installed from the 64bit alternate CD.  I get a black screen unless I select recovery console.  I can startx as root, but get a permission denied if I su to another user.  I have no network access, even though the install CD seemed to find my network fine.

  I'm running a Asus P5N32-E SLI motherboard with an Intel E6600 Core 2 Duo.  Help!!

-Ben

---

### Post by benbelly on 2007-11-15
Well, this sounds silly, but I was able to get the LiveCD to work by removing the 'splash' command line option.  I reinstalled, removed the 'splash' option from the grub entry as I booted (hit 'e' at GRUB, then select your OS, hit 'e' again, delete 'splash', hit ENTER, hit 'b' to boot)

Everything seems fine.  Give it a try and see if it helps.  I know it sounds crazy.

-Ben

---

### Post by makeyre on 2007-11-16
> **benbelly said:**
> Well, this sounds silly, but I was able to get the LiveCD to work by removing the 'splash' command line option.  I reinstalled, removed the 'splash' option from the grub entry as I booted (hit 'e' at GRUB, then select your OS, hit 'e' again, delete 'splash', hit ENTER, hit 'b' to boot)

Everything seems fine.  Give it a try and see if it helps.  I know it sounds crazy.

-Ben

I don't believe it...that was the problem.  That was the last thing I was expecting to be an issue.  Someone should add this as a bug on launchpad - I still don't understand why it happened.  By the way, can you post your menu.lst so I can undo those changes I made to it in an attempt to fix things?

---

### Post by benbelly on 2007-11-16
I'm glad that fixed it.  I was a little embarrassed to post my solution, it seemed so nuts.  I'm at work, but I'll check my boot menu when I get home tonight.

---

### Post by benbelly on 2007-11-16
Here are my kernels and flags from /boot/grub/menu.lst.  Let me know if you need something else:


title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4688f2ad-0e3c-4fc0-9f32-7795d1713389 ro quiet
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=4688f2ad-0e3c-4fc0-9f32-7795d1713389 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

---

### Post by pk74 on 2007-11-17
I also just installed an M2A-VM, AMD 5000+, and an Nvidia 8600GT.  Same problem as you guys.  After much swearing, I decided to do an expert mode install off of the Alternate cd.  No idea why, but that installed just fine.  Normal install from alternate did not work, liveCD did not work.

---

