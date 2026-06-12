---
title: "No bootloader"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by dotancohen on 2006-06-19
When I installed Ubuntu, no boot loader was installed. This is the message I got during install:
"You will need to boot manually with the /vmlinuz kernel on partition /dev/hda1 and root=/dev/hda1 passed as a kernel argument"

When I booted up I got to a prompt that asked for a user name. I gave root and got a prompt with no password. What must I do now to get grub installed and to have a gui? The install disk does not have an option of just installing a boot loader. And I had many freezes during the install (took me two days), so reinstalling the whole system is out of the question.

---

### Post by Winblowz on 2006-06-19
I think if it is just GRUB you need to install you could boot the Ubuntu live-cd and open a command prompt (terminal). Then, do "grub-install /dev/hda1", and then "update-grub". You could also try manually installing GRUB, but the above should be easier. I'm not 100% though.

---

### Post by dotancohen on 2006-06-19
Turns out that it's more than just grub... so i'm doing a full reinstall anyway. And it's locking up in the install again...

---

### Post by Winblowz on 2006-06-19
Have you tried using the "alternate install cd." It uses text-mode and may work better. You can get it from the Ubuntu downloads page.

---

### Post by dotancohen on 2006-06-19
I am using the alternate install cd.

---

### Post by Winblowz on 2006-06-19
Are you sure you are using the right architecture on the install cd  for your system?

---

### Post by sethmahoney on 2006-06-19
I'm having the same issue (also with the alternate install CD) - everything goes fine until it gets to the grub install, and then grub fails to install and says that same nonsense.  I'm installing to an AMD64 machine, but using the 32 bit desktop installer, with one SATA drive and one IDE drive, if that helps - if any other hardware specs will help, let me know and I'll dig them up.

---

### Post by dotancohen on 2006-06-19
[QUOTE=Winblowz]Are you sure you are using the right architecture on the install cd  for your system?[/QUOTE]

I'm on a P4 and using the x86 alternative disc. I also tried Fedora Core 5 and it too it locking up during the install. FC3 and 4 and Kubuntu 5.10 all installed fine. I suspect a hardware problem, but memtest86+ ran all night and found nothing. I also tried witha different harddrive, and also with a different power supply. I don't know how to test the m/b or the processor, but I have Hiron's Boot Disk if that could help diagnose the problem.

---

