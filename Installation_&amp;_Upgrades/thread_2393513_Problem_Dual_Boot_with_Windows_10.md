---
title: "Problem: Dual Boot with Windows 10"
date: 2018-06-04
forum: Installation &amp; Upgrades
---

### Post by BrianV on 2018-06-04
I have a problem that may be related to this question. For several days I've tried to get a dual boot operation, putting lubuntu 18.04 onto an Acer Aspire ES 15 which has Win 10 installed. I have created various versions of the install USB, most recently with rufus while running under the Win OS on the laptop. I have turned off secure boot and rapid start/hibernate. I can run lubuntu from the USB with no difficulties, though I had to turn on the F12 boot selection option in order to see the USB boot option. When trying to install lubuntu on the laptop with lubuntu running on the USB the installation hangs at "installing the 'grub 2' package", but I got past this by adding "acpi=off" to the boot options. Once the install is (apparently) complete a re-boot immediately goes to Win 10 start-up with no indication lubuntu is installed.

I think I have run out of suggestions from the various forums. Can you suggest any other avenues to pursue? Should I be opening a new thread?

---

### Post by QIII on 2018-06-04
Moved to its own thread from [here]("https://ubuntuforums.org/showthread.php?t=2393415").

---

### Post by mohicann on 2018-06-04
Have you tried restarting from another device directly from your Windows session? 

Restart -> choose another device -> lubuntu

If Windows recognize Lubuntu then it's been installed, otherwise... May someone have another idea?

---

### Post by oldfred on 2018-06-04
All Acer require you to set "trust" on Ubuntu/grub .efi boot files.
And you need to update UEFI from Acer.

       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

---

