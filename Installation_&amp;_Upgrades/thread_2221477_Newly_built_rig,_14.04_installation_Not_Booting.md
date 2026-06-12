---
title: "Newly built rig, 14.04 installation Not Booting"
date: 2014-05-02
forum: Installation &amp; Upgrades
---

### Post by mike_blogg on 2014-05-02
Hi, 
i have a built a new rig (not too expensive):
8GB ram
AMD 8 core 
Mobo 970A-g43
gfx gtx 750

The bios sees all the HDDs, and the 14.04 live usb installs without issues. But when it comes to boot from HDD, the screen is black with a blinking cursor. (changing to consoles does not work, it seems that the kernel is not loaded)
I have tried repairing the installation with Boot-Rpepair ([http://paste.ubuntu.com/7379085/](http://paste.ubuntu.com/7379085/)) but no joy.

I am pretty sure that it is something to do with the UEFI/secure boot thingie (i have tried with secure boot off too), but last I installed Ubuntu from scratch  was on a 12.04 old banger PC, and that gave me on problems.

I am a little lost, as i want to play with the new rig.... can anyone help?

Thanks.
Mike

---

### Post by AllenGG on 2014-05-02
Using a Flash Drive?  Correct?  Do you have access to a large SD card, ie a fast one?
What ports available?  Externañ DVD  reader?  You might have a conflict with an older Flash.

---

### Post by mike_blogg on 2014-05-02
> **AllenGG said:**
> Using a Flash Drive?  Correct?  Do you have access to a large SD card, ie a fast one?
What ports available?  Externañ DVD  reader?  You might have a conflict with an older Flash.


the installation was done with a 2GB  USB stick, and the OS is installed on a 320GB Hard Disk, conventional platter one. No SSD inside the PC, i am reusing some HDDs I had in my pile of stuff (sata disks).

during the installation everything was successful. But then, when booting off the HDD the screen stays black and nothing happens, as if nothing is in the MBR

there is no CD/DVD on the machine

---

### Post by mike_blogg on 2014-05-02
the curious thing is that the HDD light up as i turn the PC on, then a quick splash screen off the bios comes up, then.... as it should be reading off the HDD, nothing happens.....

---

### Post by oldfred on 2014-05-02
It is a nVidia thing.

I have an old nVidia and both installer and first boot require nomodeset. Screen always goes black.
And screen defaulted to very large in default mode and made it difficult for me to get to system settings, software & updates and tab to add drivers.
And your 750 may need some other updates as it is very new.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If you only have one install, you do not get grub menu by default. If BIOS mode then hold shift key until menu appears should work. If UEFI often shift does not work and you have to use escape key.

 Maxwell 750 
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1)

---

### Post by mike_blogg on 2014-05-02
> **oldfred said:**
> It is a nVidia thing.

I have an old nVidia and both installer and first boot require nomodeset. Screen always goes black.
And screen defaulted to very large in default mode and made it difficult for me to get to system settings, software & updates and tab to add drivers.
And your 750 may need some other updates as it is very new.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If you only have one install, you do not get grub menu by default. If BIOS mode then hold shift key until menu appears should work. If UEFI often shift does not work and you have to use escape key.

 Maxwell 750 
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1)


Thx for the info,  I will try it asap and let you know.

---

### Post by mike_blogg on 2014-05-03
Thanks  oldfred
it was the Nvidia issue, the system is now booting fine..
will mark this thread as solved..

---

