---
title: "How to resolve GRUB conflict with external drive"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by deusdiabolus on 2010-10-05
A little while back I did a complete reinstall of 10.04.  I have an external USB drive that I use for storage that I had previously installed Ubuntu on, before I realized that it would be easier to use the drive for storage and have the OS on the original internal drive of the machine, which would mean that I could upgrade/reinstall without destroying my end-created content...but anyway.  Ever since I did the reinstall, GRUB2 will not allow the system to boot with the external plugged in due to the drive having the old GRUB bootloader on it (I get an Error 15).  I have to wait for the OS to boot and then plug the drive in.  I tried unmounting it and then using the drive manager utility to make the drive non-bootable (which I thought would remove the GRUB bootloader and resolve the problem), but it persists.  

What I would like to know is this:

1.  Is there a way to fix the bootsector/bootloader so that I can leave the drive connected during reboots?  I don't plan to boot from the external, I just don't want to have to keep plugging and unplugging it.
2.  Can I fix this without lobotomizing the contents of the drive?  Losing 500GB of data is not an experience I wish to repeat anytime soon.

Thanks in advance...

---

### Post by Herman on 2010-10-05
:) Well done for moving your Ubuntu installation to an 'internal' drive. 
While it doesn't really matter if a drive is 'internal' or 'external', the inteface your operating system has to work through does matter. 
A SATA or even a plain old fashioned IDE interface is way faster than USB2 and you should notice an improvement in  performance. 

Your problem sounds to me like more of an issue with your BIOS settings and probably does not have anything to do with GRUB.
Check your BIOS boot order and try to set your USB disk if one is plugged in, further down in the boot list.

You should be able to boot with any boot loader in a hard disk perfectly well with any other hard disk or flash memory stick plugged in, regardless of the presence of another boot loader. 
If not, I will be very interested because we might be discovering something new. :smile:

Grub Error 15 is an error message from Legacy GRUB.

---

### Post by deusdiabolus on 2010-10-06
...and that is what it was.  Due to problems installing from CD-ROM this last go-round, I had to install from a USB flash drive, and I hadn't changed the boot order in the BIOS menu back to boot from the local drive first.  Once I changed the order, the system continued booting without a fuss.  Thank you, Herman!

---

### Post by Herman on 2010-10-06
:cool: Cool!  I'm glad you got it sorted and thanks for the feedback.  :)

---

