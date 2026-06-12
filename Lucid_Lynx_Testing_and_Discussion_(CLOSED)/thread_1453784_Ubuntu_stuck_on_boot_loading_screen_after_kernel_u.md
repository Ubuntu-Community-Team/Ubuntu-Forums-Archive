---
title: "Ubuntu stuck on boot loading screen after kernel update"
date: 2010-04-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by atlee on 2010-04-13
the new kernel that was in updates just yesterday for me, 2.6.32-20. Rebooted fine but now cannot boot it goes to the Ubuntu loading screen with the 5 red dots and keeps going through the red dots over and over, tried booting 2.6.32-19 too but same issue? Can anyone help me with this one?

---

### Post by ronparent on 2010-04-13
I have the same problem. The dots stop changing and the picture remains frozen. I have no idea what is causing it except that the system will boot if I remove splash from the boot line parameters. I had thought that plymoth was fixed, but, you can't tell it by me. lol

I incidently am using the new 2.6.32.20 kernel.

---

### Post by atlee on 2010-04-13
> **ronparent said:**
> I have the same problem. The dots stop changing and the picture remains frozen. I have no idea what is causing it except that the system will boot if I remove splash from the boot line parameters. I had thought that plymoth was fixed, but, you can't tell it by me. lol

Can i remove the splash inside recovery mode? And how do I do this using terminal? Thanks

---

### Post by ronparent on 2010-04-13
If the problem is that the grub menu does't show, hold the left shift key immediately after the bios load on boot. Otherwise just hit **e** at on the grub menu line (to edit). move the cursor down to the beginning of the line for loading the kernel, hit end to move the cursor to the end of the line and backspace to erase splash. Then hit **<ctrl>x** to boot. This is only a temporary change and will will beignored on the next boot, but, if the freeze is cause by the splash screen you will know immediately. You can remove the splash parameter by then editing it out from the file **/default/grub**.

---

### Post by atlee on 2010-04-13
> **ronparent said:**
> If the problem is that the grub menu does't show, hold the left shift key immediately after the bios load on boot. Otherwise just hit **e** at on the grub menu line (to edit). move the cursor down to the beginning of the line for loading the kernel, hit end to move the cursor to the end of the line and backspace to erase splash. Then hit **<ctrl>x** to boot. This is only a temporary change and will will beignored on the next boot, but, if the freeze is cause by the splash screen you will know immediately. You can remove the splash parameter by then editing it out from the file **/default/grub**.

The splash does not freeze, the dots keep scrolling, thinking, continuous thinking. I removed the splash from the boot and i get really fast amount of scrolling text that continuously fills mu screen but this is the error message that i could see.

"UNEXPECTED INCONSISTENCY RUN fsck MANUALLY" and this scrolls through all my linux partions with this message.

---

### Post by atlee on 2010-04-14
anyone able to help me stop it from doing this and to boot to the desktop?

---

### Post by dino99 on 2010-04-14
try to boot with recovery mode:

- you can boot without "quiet splash" and see if that help
- add on that boot line "nomodeset" or "yourchipsetname.modeset=0"
- maybe you can test with acpi=off and/or lapic=off and/or noapic=off

e.g. to edit the boot line: when you choose recovery mode from grub menu, at the bottom line you can see "press E" for edit, then "press X" to validate.

yourchipsetname depend on your hardware, can be i915 or radeon or else for example, so you write i915.modeset=0 for example

If you can boot, its what i hope, first goto synaptic and remove/purge gdm & plymouth, then reinstall them ( that will erase old/wrong settings on their sides)

---

### Post by atlee on 2010-04-17
> **dino99 said:**
> try to boot with recovery mode:

- you can boot without "quiet splash" and see if that help
- add on that boot line "nomodeset" or "yourchipsetname.modeset=0"
- maybe you can test with acpi=off and/or lapic=off and/or noapic=off

e.g. to edit the boot line: when you choose recovery mode from grub menu, at the bottom line you can see "press E" for edit, then "press X" to validate.

yourchipsetname depend on your hardware, can be i915 or radeon or else for example, so you write i915.modeset=0 for example

If you can boot, its what i hope, first goto synaptic and remove/purge gdm & plymouth, then reinstall them ( that will erase old/wrong settings on their sides)

I have X58 chipset, I tried removing quiet boot nothing, tryed boot recovery but got stuck on same sort of messages, rebooted and it decided to boot after 4 days. i will update and see if i can login.

---

### Post by cariboo on 2010-04-18
What graphics chipset are you using?

---

