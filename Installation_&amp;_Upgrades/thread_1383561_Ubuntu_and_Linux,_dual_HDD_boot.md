---
title: "Ubuntu and Linux, dual HDD boot"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by troembke on 2010-01-17
So, I've installed Ubuntu 9.10 on my external HDD and only want to boot to it when I plug it in via eSATA. However, I still want to only be able to boot to windows 7 when my external HDD is not plugged in. So, here is my issue, when I unplug my external HDD, my laptop boots up to "loading grub--error code 21" however, if my external is plugged in, I get my normal dual boot options. How do I go about fixing this?

---

### Post by bryanagee on 2010-01-18
It would be easier to use the BIOS boot device controls; that way you can restore your Winblows bootloader on the internal, and only have grub on the MBR of the external. Just change the boot priority to be 
1 - CDROM
2 - USB HDD
3 - IDE/SATA 0

---

### Post by troembke on 2010-01-18
Well, changing the BIOS doesn't affect the bootloader. I actually just fixed my issue. I ended up reinstalling Windows 7 on my internal, removed it, attached my eSATA drive and installed Ubuntu, and set up my BIOS to boot from external HDD first if present. 

*********

---

### Post by presence1960 on 2010-01-18
> **troembke said:**
> Well, changing the BIOS doesn't affect the bootloader. I actually just fixed my issue. I ended up reinstalling Windows 7 on my internal, removed it, attached my eSATA drive and installed Ubuntu, and set up my BIOS to boot from external HDD first if present. 

*********
it is a shame you did all that work. You could have restored the win 7 bootloader to the MBR of the internal disk. See [here]("http://ubuntuforums.org/showthread.php?t=1014708"). Scroll down to the part for Vista/Windows 7. All you needed to do is restore the windows bootloader because you put GRUB on MBR of the internal disk.

Then you could have reinstalled GRUB to MBR of the external disk like this depending on which GRUB you use:

Legacy GRUB:
```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

GRUB2:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

It is not necessary to remove internal disks to set up dual boot or multi-boot systems.

For future reference when installing Ubuntu you can choose where to install GRUB by clicking the Advanced button on the Ready to install window. See pic below.

---

