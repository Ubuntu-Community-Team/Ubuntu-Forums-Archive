---
title: "Bootloader Installation Question"
date: 2006-04-20
forum: Installation &amp; Upgrades
---

### Post by Karm on 2006-04-20
Greetings,

I have 2 SATA drives. The first drive has Windows XP on it and I would like to install Ubuntu on the second drive. When I install Ubuntu, I wish to have the bootloader in the MBR of the second drive. So, when I want to boot Linux, I can change the BIOS setting to boot from the second drive. I'm trying to obtain complete OS separation because there are other people that use the computer.

Is it possible to accomplish the above? If so, can I specify this somehow during the installation?

If not, is it possible to put the boot loader on a floppy and just boot from there when I want to run Linux?

Thanks in advance for any comments/suggestions you may have.

Cheers,
Kerry

---

### Post by cleverselfreferentialname on 2006-04-20
It is possible to put grub on a floppy, but it's not an easy task. Grub being installed to the MBR of the first drive will not remotely affect Windows. In fact, I think that upon choosing Windows XP as the OS to be booted, the Windows bootloader takes over.

---

### Post by cotcot on 2006-04-21
During ubuntu install you get the question if the bootloader is to be installed in the MBR. Reply "no". Then you get the question where the bootloader should be installed. You can reply "/dev/hdb" to have it on your second HDD or "/dev/fd0" to have it on a floppy. In the latter floppy inserted will give you the Grub menu; floppy removed will boot windows directly. (do not forget to make the partition with the MBR active again after ubuntu install.

You do not need to put grub fully on the floppy; only the bootloader. Stage 1 and 2 can reside in the ubuntu partition (/boot/grub)

---

### Post by DDAAXX on 2006-04-21
With a Mandriva installation, I do somethings like this: I installed LILO on the boot partition of linux, than with a command from the shell I created a file like bootsect.lnx on drive C:.
After this I added a line in boot.ini and finally I have the normal bootloader of windows with also the line "Linux" that use the bootsect.lnx to boot linux.

Now I've installed Kubuntu 5.10 because I think it's bether than Mandriva, I installed the GRUB on floppy and I start with it.

Do you think it's possible to create the same scenary I had before?
What kind of command I have to send in shell to install GRUB on boot partition of linux (hdb2), than to create the bootsect.lnx for to place on drive C: ?

Thanks a lot for your help
DDAAXX

---

### Post by Karm on 2006-04-21
[QUOTE=cotcot]During ubuntu install you get the question if the bootloader is to be installed in the MBR. Reply "no". Then you get the question where the bootloader should be installed. You can reply "/dev/hdb" to have it on your second HDD or "/dev/fd0" to have it on a floppy. In the latter floppy inserted will give you the Grub menu; floppy removed will boot windows directly. (do not forget to make the partition with the MBR active again after ubuntu install.

You do not need to put grub fully on the floppy; only the bootloader. Stage 1 and 2 can reside in the ubuntu partition (/boot/grub)[/QUOTE]
Thanks very much for the information. So, during the installation I can put the bootloader on my second drive or on a floppy. If I specify /dev/sdb for my second drive, does the bootloader go to the MBR of that drive or just the first part of the /boot partition?

---

### Post by cotcot on 2006-04-21
It will go to the MBR of your second drive.

---

### Post by Karm on 2006-04-21
That is exactly what I want to happen. Thank you!

---

