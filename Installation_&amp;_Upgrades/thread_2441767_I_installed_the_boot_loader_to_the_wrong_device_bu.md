---
title: "I installed the boot loader to the wrong device but partially like the results"
date: 2020-04-26
forum: Installation &amp; Upgrades
---

### Post by ubuntone on 2020-04-26
I had a PC with 
 Wndows on /dev/sda
 Xubuntu 18.04 Desktop on /dev/sdb

I selected which to boot by switching between UEFI and Legacy boot.
 
I did not manage EFI boot becuase i could not get the Live 18.04 Xubuntu to  EFI boot (and I wanted to leave the Windows disk untouched). 

So just ran with that and used the boot mode to select the operating system.


I installed Ubuntu 20 Desktop  to a memory Stick while in EFI mode.

     and it booted.

What is more when booting from the memory stick in EFI mode: GRUB offered me the option Boot:
 1) Ubuntu -  20 from the memory stick
 2) Windows - from /dev/sda
 3) Xubuntu 18.04 from /dev/sdb

It would boot all three operating system  successfully via the GRUB menu on the Memory stick.

So I did a silly thing I reinstalled Ubuntu 20 to the stick BUT put the boot loader on /dev/sdb


So now I can EFI boot the second disk Xubuntu 18.04 form /dev/sdb but I must have the Memory stick present or the boot fails to the GRUB command line.

Can you help me get the it to boot EFI mode without the Memory stick present.

I want to keep the Xubuntu 18.04 on /dev/sdb and EFI boot.
I don't care about the Ubuntu 20 on the memory stick.

Thanks

---

### Post by ubuntone on 2020-04-27
I have reinstalled the Xubuntu on the second disk. 

So I am no longer looking for any other solution.

---

### Post by oldfred on 2020-04-27
Did you put an ESP - efi system partition on the Ubuntu drive?

In UEFI mode, the Ubiquity installer only puts grub into the ESP on first drive, usually inside the same ESP as Windows is using. That works fine, but often better or just as backup have the UEFI boot files on the Ubuntu drive.

---

