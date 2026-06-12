---
title: "Dual booting with Win 7"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by shahgols on 2010-04-02
Hi everyone,

The last time I tried installing a dual boot system, I messed everything up.  So here I am asking for some help please.

I have Win 7 installed on /dev/sdb.  /dev/sdb1 is 100MB, which Win 7 reserves for something, and /dev/sdb2 is where my C: drive is.  

I am installing Ubuntu to /dev/sda.  Where should I tell it to install the boot loader?  The options are:

(hd0)
/dev/sda
/dev/sda1  (root partition)
/dev/sda2  (home partition)
/dev/sdb
/dev/sdb1
/dev/sdb2

Any help would be greatly appreciated!

---

### Post by Herman on 2010-04-02
1. You should install GRUB to /dev/sda, which will most times be the MBR of your first hard disk. That's what most people do and that usually results in the simplest and most convenient arrangement.
2. It would also be okay to install GRUB to /dev/sdb, which should normally be the MBR of your second hard disk drive, but if you do that you will need to press a key on your keyboard for a BIOS boot menu in order to select your second hard disk to boot GRUB.
3. You could install GRUB to /dev/sda and then later, after the installation also install GRUB to /dev/sdb so GRUB will be in both hard disks MBRs so if the hard disk order gets accidentally swiched around in the BIOS, (by someone unplugging and replugging hard disks perhaps), you will still be able to boot with GRUB.

4.  It's also possible to install GRUB to /dev/sda1 the boot sector of your Ubuntu partition, but if you do that then you will need some other boot manager to chainload it or you won't be able to boot Ubuntu.


What NOT to do: 
(x) You should never install GRUB to the boot sector of your Windows partition, which would be /dev/sdb1 for your Windows 7 /boot partition and /dev/sdb2 for your Windows 7 / (or 'root'). Do not install GRUB to either of those locations under any circumstances.
(xx) You should not install GRUB to  the MBR of a hard disk when you have installed certain kinds of drive encryption for use with the other operating system. You should know if you did because probably you would have paid extra money for that.
BitLocker Drive Encryption, available only in the Enterprise and Ultimate editions of Windows Vista and Windows 7 is a prime example of what I'm talking about here. Third Party alternative drive encryption softwares available for Windows include McAfee endpoint Encryption and Symantec Endpoint Encryption and there may be others.

---

### Post by shahgols on 2010-04-02
Wow, excellent reply!!  Thx so much!

---

