---
title: "Ubuntu 11.10 install on old Toshiba Satellite (ca 1999)"
date: 2012-04-01
forum: Installation &amp; Upgrades
---

### Post by TheQMann on 2012-04-01
So I have an old Toshiba Satellite laptop from 1999-2000 that I ran a fresh install of Ubuntu 11.10 on.  Everything seems to run fine from the Live CD, and the install process went without a hitch.  However, after rebooting after the install, I get the error message:

NTLDR is missing
Press any key to restart

I tried the boot-repair-disk LiveCD, and had no luck there.  It did generate this useful log:

[http://paste.ubuntu.com/910859/]("http://paste.ubuntu.com/910859/")

The ubuntu installer was told to wipe the existing disk before installing, and there is only the one hard drive installed.  No version of windows is present or needed (not dual boot).

---

### Post by RJARRRPCGP on 2012-04-01
> **TheQMann said:**
> 

NTLDR is missing
Press any key to restart



That error message is from the Microsoft bootloader. GRUB wasn't installed to the MBR. 
You must have GRUB in the MBR!

When most people delete stuff before giving a computer to someone else, Microsoft bootcode still gets left on the HDD. :(

---

### Post by TheQMann on 2012-04-01
So how do I get GRUB into the MBR?

---

### Post by RJARRRPCGP on 2012-04-01
> **TheQMann said:**
> So how do I get GRUB into the MBR?

The installer should have done it already.

---

### Post by YannBuntu on 2012-04-02
Hello
As said above, NTLDR is a Windows boot file, required to boot Windows.
The "NTLDR is missing" usually comes when the bootloader tries to boot a Windows partition.

But,according to your BootInfo Summary, your bootloader (GRUB2) is correctly installed in your disk's MBR, and looks for partition 1 (where Ubuntu is), so it should not search for any Windows boot file.

I see 2 possibilities:

1) Your sda1 bootsector has remains of Windows (although they are not detected by BootInfo). You can try to repair your sda1 bootsector by following the following tutorial: [http://ubuntuforums.org/showpost.php?p=11693662&postcount=1](http://ubuntuforums.org/showpost.php?p=11693662&postcount=1)

2) Your computer is MBR or BIOS-locked. This is very rare, so i'm not sure how it exactly works. In this case, i think you will need to use the OEM Windows CD, until you reinstall and have access to Windows. Then try to create a dual-boot via EasyBCD or else.

---

### Post by TheQMann on 2012-04-02
Couple of updates:

1) I tried the steps outlined in #1, but testdisk didn't find any errors.  I had it wipe the MBR and re-ran boot-repair, with the same no NTLDR results.

2) This machine had an older version of ubuntu (probably 2007ish) prior to my effort this week to wipe and install 11.10 on it.  Booting worked fine with GRUB1.

3) By using the ubuntu LiveCD and selecting Boot from hard disk, I can get past the MBR issue and run the OS from my local drive (which is how I ran #1 above).

---

### Post by YannBuntu on 2012-04-03
When you used GRUB1, was it installed normally (in the MBR) ? (if it was installed automatically via the Ubuntu installer, answer is yes)

Since you stopped using GRUB1, did you change something in your BIOS setup ?

Please could take pictures (with a camera) of your BIOS setup screens, and show them to us ?

---

### Post by RJARRRPCGP on 2012-04-04
You still have left over Microsoft bootcode.

---

