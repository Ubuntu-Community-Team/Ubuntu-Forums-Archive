---
title: "invalid windows 7 EFI boot path after boot repair ubuntu 12.04.03"
date: 2014-01-10
forum: Installation &amp; Upgrades
---

### Post by johndoesmithers on 2014-01-10
Hello, I have an Asus x401u with factory windows 7 and I have installed Ubuntu 12.04 LTS for a dual boot machine.  when I attempt to load windows from the grub screen, I see an invalid path message.  I can change the BIOS EFI boot order to boot windows or Ubuntu, but neither recognizes the other.  I don't want to go to BIOS every time I need to switch OS's.  Ubuntu boots fine from grub.

I used the boot repair iso from usb - [http://paste.ubuntu.com/6730021](http://paste.ubuntu.com/6730021)

I am hoping for help to resolve this.  Thank you.

---

### Post by tfrue on 2014-01-10
You probably have Win 7 installed with EFI, and probably also tried to install Ubuntu without EFI, which causes problems.

Read through these articles and see if it helps:
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

You will have to reinstall Ubuntu probably and make sure that it boot's with EFI and you should be ok.

Good luck, 
Chris

---

### Post by fantab on 2014-01-10
[QUOTE=http://paste.ubuntu.com/6730021/]Adding custom /mnt/boot-sav/sda4/boot/efi/EFI/Microsoft/Boot/**bkpbootmgfw.efi**
Adding custom /mnt/boot-sav/sda4/boot/efi/EFI/Boot/**bkpbootx64.efi**
sda1//mnt/boot-sav/sda4/boot/efi/EFI/Boot/**bkpbootx64.efi** already added
sda1//mnt/boot-sav/sda4/boot/efi/EFI/Microsoft/Boot/**bkpbootmgfw.efi** already added[/QUOTE]

You had installed Ubuntu in "non-UEFI" mode. Boot-Repair corrected the problem by removing 'grub-pc' and installing 'grub-efi'. So far so good.

Boot-Repair has renamed your Windows EFI boot files as it is evident from the quote above.

Run Boot-Repair again and make sure to select the option "***Restore EFI Backups***". That should solve the Windows boot issue.

If the issue isn't solved then post the new LINK to 'BootInfo Summary', here.

Good Luck.

---

### Post by johndoesmithers on 2014-01-11
Well, I ran boot repair again and checked only Restore EFI Backups and nothing changed... oops!  So, I ran boot repair again choosing Recommended Repairs and it fixed the problem.

Thank you for the help, I appreciate it.

---

### Post by tfrue on 2014-01-11
Don't forget to mark this thread as SOLVED from the thread options

Thanks,
Chris

---

