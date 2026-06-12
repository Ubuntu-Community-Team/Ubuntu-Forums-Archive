---
title: "Laptop does not boot after installing Ubuntu"
date: 2020-09-04
forum: Installation &amp; Upgrades
---

### Post by lamarcheb2 on 2020-09-04
I have an older HP Pro X2 612 G1 laptop with an i5-4302Y. I installed Ubuntu by booting from a thumb drive and following the default prompts. The machine was previously running Windows 10 Pro.

I seems I cannot select the default boot partition from the machine's firmware that will allow the machine to boot into Ubuntu when it is turned on. I tried everyone setting combinations in the UEFI settings.

When the machine is powered on it flashes very briefly "System BootOrder not found. Initializing defaults." and then right below "Reset System".

The only way the machine boots is by pressing F9 when turning it on and selecting Ubuntu from the boot menu.

Otherwise it works wonderfully well. Overall, it's much more pleasant than Windows.

---

### Post by oldfred on 2020-09-05
Did you install in UEFI boot mode?

Many with HP, found efibootmgr (which grub uses to set order) does not work and only have an UEFI update and then changes in UEFI boot order in UEFI would work. Not sure about your model.

HP UEFI menus
[https://ubuntuforums.org/showthread.php?t=2448563&p=13979237#post13979237](https://ubuntuforums.org/showthread.php?t=2448563&p=13979237#post13979237)

---

### Post by geckojames on 2020-09-06
Try putting ubuntu above windows in your firmware boot sequence. :P

---

