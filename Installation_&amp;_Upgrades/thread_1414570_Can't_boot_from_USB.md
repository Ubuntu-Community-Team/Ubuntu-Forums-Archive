---
title: "Can't boot from USB"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by sharp11 on 2010-02-23
SOLUTION: At boot, go into the BIOS. As you exit the BIOS, hit the Esc key. This brings up the Unetbootin boot menu. Stupid but it works.

#############

I am trying to install Ubuntu on my netbook (Eee PC 1000HE) with a brand new hard drive. I created a bootable thumb drive using Unetbootin to write ubuntu-9.10-desktop-i386.iso (checksums are fine).

But when I try to boot off the thumb drive, I immediately get the error: "Reboot and Select proper Boot device". Apparently it's not recognizing the drive as bootable. The BIOS is configured to boot from removable storage.

I have looked at the thumb drive in Gparted and the boot flag is on. I have tried using usb-creator instead of Unetbootin. I've reformatted the thumb drive and done it all over again. I've tried making the secret handsign and shouting "Ubuntu" three times. Even that didn't work.

The odd thing - one last clue? - is that I used the same thumb drive to install UNR (netbook remix) on this machine yesterday. It worked fine. Then I realized I wanted Ubuntu not UNR, and that's when my problems began.

Added: I meant to include this odd fact. When I look at my thumb drive with fdisk, it gives weird output for the partition table: 

```
Disk /dev/sdc1: 4003 MB, 4003140608 bytes
124 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Disk identifier: 0x8ef631df

This doesn't look like a partition table
Probably you selected the wrong device.

     Device Boot      Start         End      Blocks   Id  System
/dev/sdc1p1   ?      274784      529564   979374166   66  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(734, 123, 14) logical=(274783, 70, 21)
Partition 1 has different physical/logical endings:
     phys=(120, 143, 6) logical=(529563, 65, 22)
Partition 1 does not end on cylinder boundary.
/dev/sdc1p2   ?      448668      961719  1972168331    7  HPFS/NTFS
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(187, 180, 14) logical=(448667, 16, 52)
Partition 2 has different physical/logical endings:
     phys=(784, 0, 13) logical=(403059, 76, 1)
Partition 2 does not end on cylinder boundary.
/dev/sdc1p3   ?      426615      680707   976730017   7d  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(252, 59, 46) logical=(426614, 84, 39)
Partition 3 has different physical/logical endings:
     phys=(139, 118, 4) logical=(122048, 22, 28)
Partition 3 does not end on cylinder boundary.
/dev/sdc1p4   ?       42708       43791     4161547   6f  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(370, 101, 50) logical=(42707, 63, 39)
Partition 4 has different physical/logical endings:
     phys=(10, 114, 13) logical=(43790, 15, 4)
Partition 4 does not end on cylinder boundary.

```

---

### Post by Old_Grey_Wolf on 2010-02-23
I think there are two options in the eee PC BIOS for booting. Check to see if there is one for boot priority order, and one for boot device. Set both to USB.

---

### Post by sharp11 on 2010-02-23
> **Old_Gray_Wolf said:**
> I think there are two options in the eee PC BIOS for booting. Check to see if there is one for boot priority order, and one for boot device. Set both to USB.

Thanks for the suggestion. You're right about the two options. They are both set and still get the error.

---

### Post by Old_Grey_Wolf on 2010-02-23
I am guessing at this point.

I had problems, at one time, getting my wife's eeePC to boot if I had a card in the SD memory slot. After removing it, it booted properly.

---

### Post by sharp11 on 2010-02-23
> **Old_Gray_Wolf said:**
> I had problems, at one time, getting my wife's eeePC to boot if I had a card in the SD memory slot. After removing it, it booted properly.

Thanks, but I don't use the SD slot.

---

### Post by Old_Grey_Wolf on 2010-02-23
I am sorry and embarrassed for replying to your thread without having a solution. 

Have you tried to reformat the USB as FAT32 then using Unetbutin or USB Startup Dick Creator to reinstall the live Ubuntu boot OS?

---

### Post by sharp11 on 2010-02-24
> **Old_Gray_Wolf said:**
> I am sorry and embarrassed for replying to your thread without having a solution. 

Have you tried to reformat the USB as FAT32 then using Unetbutin or USB Startup Dick Creator to reinstall the live Ubuntu boot OS?

It's kind of you to try!

I think that FAT32 is the default for thumb drives (for compatibility), but in any case, that's what I've been using. Since this is linux to linux, maybe I should try formatting it as ext4? I don't know if that would affect the boot record - kind of doubt it. But I'm grasping at straws at this point.

Also, I updated my original post with output of fdisk. Weird, but I don't know ...

---

