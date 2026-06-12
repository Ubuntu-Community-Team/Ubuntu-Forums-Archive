---
title: "MBR Confusion"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by gfinlay on 2010-04-07
I am using XP on drive 0-partition 1 and XP data on drive 0-partition 2 ,and Ubuntu 9.10 on drive 1-partition 1 with swap on drive1-partition 2.  This uses Grub2 which chainloads XP and uses initrd to load Ubuntu.  

I assume that Grub has overwritten the MBR on drive 0 to control booting, but I notice there is also an MBR on drive 1.

In booting to Ubuntu, does grub use the MBR on drive 1 at all or is it all done from initrd and the grub1 configuration files?

Many thanks.

---

### Post by gfinlay on 2010-04-07
Sorry, my question should have said


In booting to Ubuntu, does grub use the MBR on drive 1 at all or is it all done from initrd and the grub2 configuration files on drive 1?

---

### Post by Herman on 2010-04-07
Your BIOS checks the MBR of whichever hard drive is set as the first hard disk.
The GRUB code in the boot loader section of the MBR, (GRUB's stage_1), with help from code embedded in the first track of the hard disk, (GRUB's stage_2), can find the main body of GRUB even though it may be located in a different hard disk.

The main part of GRUB then gives you your boot menu and allows you to select which operating system you would like to boot. If you choose Ubuntu GRUB loads the Linux kernel into your computer's RAM and with the help of matching initrd.img the boot process is started.
If you choose Windows it chainloads the Windows boot sector, (the first sector of the Windows partition, back in your first hard disk).

The second hard disk's MBR has nothing to do with it but you can install GRUB there optionally so that if anything happens to your first hard disk, (if you remove it), your computer will still boot normally.

The BIOS usually numbers our disks by the way we have the drives plugged into the motherboard and jumper settings if you use IDE drives.
You can override the BIOS's opinion about which one should be the first hard drive by the hard disk order settings in the CMOS in most computers, or by pressing a key for a BIOS boot menu during boot up, often F8 or F12.

Some computers, especially computers that have some IDE drive and some SATA drives, have problems deciding whether the IDE or SATA drives should be counted first. I have one like that. It was stable for a long time until I started plugging in other hard disks for fixing other people's computers or doing file rescues. Right now it's a little bit mixed up and can change it's hard drive order seemingly at random, especially if a USB drive is thrown into the mix.
If you like adding and removing drives, it's probably a good idea to install GRUB to both or all of your hard disks MBRs so your computer will boot regardless of which one is first in the BIOS's hard disk order.

It's also easy to make your own GRUB2 emergency boot disk and that can sure come in handy once in a while, especially if you're the curious type like me and you feel the urge to try all kinds of experiments to find out how things work, [GRUB2 How To Boot From CLI Mode]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html") -  NEW!  Rescue your System

---

### Post by louieb on 2010-04-07
Could be in either or both MBRs to find out run the script.
[Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280")

---

### Post by gfinlay on 2010-04-07
This community is terrific.  I ask a question that could easily get a yes/no response, yet you give me some great background information and a pointer to a script.  Both of which have cleared my confusion.

A sincere thank you to Herman and louieb for making the effort and giving me your time and expertise, I appreciate it.
__

---

