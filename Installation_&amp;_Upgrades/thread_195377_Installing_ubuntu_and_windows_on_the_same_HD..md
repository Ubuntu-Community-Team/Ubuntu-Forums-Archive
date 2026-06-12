---
title: "Installing ubuntu and windows on the same HD."
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by sidy on 2006-06-12
Hi there.

First of all, I installed ubuntu 5.10 on partition of 40gb, then I installed windows on the other partition of 40gb been a total of 80gb.(I should have done the other way around).

But when I switch the cp on, it boot only to windows and don't give me option to also boot on ubuntu.

So, I've tryed to reinstall ubuntu again, but I can't find the partition to reinstall ubuntu.

So, WHAT CAN I DO TO BE ABLE TO BOOT IN BOTH (be able to choose ubuntu or windows)?

Can u give me same directions or commands in full?

rgds

---

### Post by az on 2006-06-12
Hmmmm..    If you made windows install on it's own partition, you can still get back Ubuntu - it's a question of reinstalling the bootloader.

If windows ate your ubuntu partition and it is no longer there, you have to start over again.

What do you mean when you say that your ubuntu partition is no longer there?  You looked with the partitioning tool of the ubuntu installer?

To give you exact commands to reinstall the bootloader (grub) I would have to know the specifics of your system.  IN general, you would boot the live cd and the chroot into the ubuntu partition from a terminal

sudo chroot /media/hda3
sudo grub-install /dev/hda
exit


and then reboot.

If you totaly erased your ubuntu partition with windows, just re-reun the installer and pick the default option which is to resie your windows partition and install on the freed space.

---

### Post by sidy on 2006-06-13
When I first installed ubuntu I left free space for windows. Then I installed windows on that free space, but when I booted, I didn't have ubuntu as option. Windows just started. Inside windows, on properties, windows was using 40gb. So I dicided to reinstall ubuntu. But I couldn't identify what was the partition for windows or ubuntu. The only option I had for instalation was the entire disc, 82gb.

I've dropped the commands u gave me:
# sudo chroot /media/hda3
' chroot change roote directory to /media/hda3: No such file or directory '
(I also tryed hda2 and 1, with same reply)

# sudo grub-install /dev/hda
' Probing devices to guess BIOS drives. This way take a long time.
/dev/mapper/casper-snapshot does not have any corresponding BIOS drive. '

What does it means?

And when I rebooted, came up at the bottom of the screen.

' Error loading operating system_ '

From there it doesn't go anywhere.

About my system I'm not sure.
Processor is AMD, the one before 754.
256 Ram
HD 80
Motherboard MS 6787 ver:2.

What do you think should I do now?
I can reinstall erery thing again if it is going to be complicated.

Thank you for now.

---

