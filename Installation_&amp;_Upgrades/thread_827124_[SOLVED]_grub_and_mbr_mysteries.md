---
title: "[SOLVED] grub and mbr mysteries"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by t.septekin on 2008-06-12
Hello you helpful boys and girls,

I was under the impression that during booting ubuntu looked at the MBR which pointed at the menu.lst which, in its turn, listed the kernel or the alternate OS to choose.

I was also under the impression that restoring the MBR, "/" and if any "/boot" from dd copies would return the device to its state when the backups were made.

I was wrong. And I would appreciate if any of you could throw some light on how the system is starting.

I have a Sony Vaio FZ21M with ubuntu 8.04 installed and it works fine. I have separate partitions for "/boot" (/dev/sda5), "/" (/dev/sda12), "/home" and "swap".

Now, to lead to my question: I installed ubuntu 7.10 in yet another partition (/dev/sda9). I configured it to include both the boot and root on the same partition, sharing my old home and swap partitions. Now when I start menu.lst gives the choice of selecting either 8.04 or 7.10, or their recovery modes; I've edited it so that 8.04 is the first choice which is selected after a short delay. All is well. However, the menu.lst is located in sda9 which means I cannot remove or change my second choice without upsetting the boot progress.

Here is what I attempted: I restored from their dd backups the MBR, "/boot" and "/" partitions to their state before the installation of 7.10. I thought that this would return my PC to its old state.

Yet when I Restart I get the 7.10 menu.lst which is in partition sda9. How come? The backups did not know about sda9's contents or 7.10; what is pointing at this location and how can I edit/modify it?

After starting ubuntu 8.04, I checked "df /" and "df /boot", they are returning the expected partitions, "/dev/sda12" and "/dev/sda", respectively.

I cannot consider this to be a problem, yet I would be grateful if anyone can tell me just what is happening.

PLEASE?

teoman

---

### Post by logos34 on 2008-06-12
> **t.septekin said:**
> I restored from their dd backups the MBR, "/boot" and "/" partitions to their state before the installation of 7.10. I thought that this would return my PC to its old state.

Yet when I Restart I get the 7.10 menu.lst which is in partition sda9. How come? The backups did not know about sda9's contents or 7.10; what is pointing at this location and how can I edit/modify it?

Maybe the restore didn't actually overwrite the mbr for some reason.  Hard to tell what happened, because grub stage1 on the MBR is still pointing to sda9.

Here an easy fix (I hope):

**sudo grub**

> **find /boot/grub/stage1**
(this looks for copies of stage1 in the above path on all partitions.  In your case it should output '(hd0,4)' and '(hd0,8)'--sda5 and sda9, respectively.)

**> root (hd0,4)**
(this is where you tell it which menu.lst to use. You want it to point to the one on /boot).
**> setup (hd0)**
(writes grub to the MBR.  You could also specify (hd0,4) or (hd0,8) if, say, you wanted to write grub to the bootsector of either partition instead)
**> quit**

---

### Post by meierfra. on 2008-06-12
logos34 method should work. 

I just want to explain why restoring the MBR did not work. The location of the files "stage2" and "menu.lst" is stored in the "stage1.5" files and not in the "stage1" files.  More precisely it is stored in  third sector of the  hard drive. So you need back-up at least your first three sectors.

But  reinstalling  grub  is in my opinion easier and safer than using your backup.

---

### Post by t.septekin on 2008-06-12
Thanks a lot logos34 and meierfra!

I had tried reinstalling grub before, without a change in performance. I now had a look at my notes and saw my error: I had put "setup (hd0,4)". I did it again with "setup (hd0)" and it worked, returning me to 8.04 menu. I shall now go ahead and tweak menu.lst to see if I can add good old Gutsy to my choices.

Thank both of you again for your quick and working suggestions. I raise a small glass to your good healths.

teoman

---

