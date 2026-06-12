---
title: "Weird issues trying to boot Live CD - PLEASE HELP"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by mitch2k2 on 2008-04-11
Hey all. After switching back to Ubi on my laptop (an 8.04 installation that's working great), I decided it was time to try and initiate the kids into linux and want to install either 7.10 or 8.04 on an OOOOLLLDD Dell Dimension 4100. (512MB, 800MHZ PIII)

One problem. For the life of me, I cannot get the stupid machine to boot from a CD. Obviously, the BIOS is set to boot first from the CD, but that doesn't help. 

With either the Feisty, Gutsy, or Hardy Live CDs in the drive, the comp powers up, shows the Dell splash, starts to read from the first of two optical drives (a dvd  and a cd burner) and then reboots before loading anything. Without fail, every time. There is no way that I can see to get it to boot into the live cd environment.

I'm at my wits' end here. I opened the box, put a new cable in, changed the jumpers from CS to Master and Slave respectively, tried booting with only one connected (both drives), and nothing changes. I've tried a PCLinux OS live CD and the same thing happens. (and all of these CDs work on other machines).

The BIOS  in the Dell is the latest (and, I'd imagine, the last ever) version A11.

In my frustration, I installed Ubuntu last night using unetbootin, which worked, but I seemed to have made an error when choosing where to install GRUB, and the installation won't boot from GRUB, kicking out an error 17. Neither will XP (dual boot until I can get everyone acclimated). I'm pretty sure I can fix this simply by editing the menu.lst file, but trouble is, I can't boot into a Live CD to access the file or edit it.

SO my questions to you good, kind, helpful and knowledgeable folks are:

1. Does anyone have any ideas at all as to how I can get to the stupid box to actually boot from a CD?

2. Barring that, can anyone give me a heads up on how to get in some other way to edit the menu.lst file (I don't guess that can be done from the grub command line, can it)?

Note: the FDD on this machine works only intermittently, but it's the only floppy in the house, and so I wouldn't be able to write a floppy anyway. Also don't think the BIOS has the ability to boot from a USB drive/device.

Help?

---

### Post by Pumalite on 2008-04-11
Your problem might be memory. How much memory do you have?

---

### Post by mitch2k2 on 2008-04-11
512 MB, the max the machine is able to hold. I don't think it's a memory option. After all, XP (until I hosed the boot) was working fine. And honestly, this machine has been running for years and years.

---

### Post by Pumalite on 2008-04-11
Maybe some common boot parameters will do:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off irqpoll pci=noacpi pnpbios=off vga=0x317 vga=791

To be tried alone or in combinations.

---

### Post by mitch2k2 on 2008-04-11
I think what I really need is some way to edit the menu.lst file from the GRUB prompt. Is that possible?

---

### Post by Pumalite on 2008-04-11
See if you can boot a Knoppix Live CD. We can get your menu.lst from there:
[http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)

---

### Post by mitch2k2 on 2008-04-11
Never mind. Was able to boot by altering the grub commands in the menu ('e' to edit, changed Hd2,1 to HD0,1)

In now and will be making the changes to menu.lst

---

### Post by Pumalite on 2008-04-11
Glad my guide to edit the boot commands worked.

---

### Post by mitch2k2 on 2008-04-11
It did. Thank you very much. You don't happen to have a suggestion up your sleeve for the "failed to fetch" "could not resolve" anything when running update, do you?

---

### Post by Pumalite on 2008-04-11
Copy and paste the entire output here. Likely culprits: your sources.list needs to be enabled (your repos might be commented out). You might need to try  a different Server. You need to check your connection.

---

### Post by mitch2k2 on 2008-04-11
Checked sources.lst and everything checked out. But have now realized I don't have an internet connection which is the most likely culprit, I'd say!

---

