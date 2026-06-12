---
title: "How can I fix this Install Error?"
date: 2018-09-22
forum: Installation &amp; Upgrades
---

### Post by jisip on 2018-09-22
[COLOR=#242729][FONT=Arial]I'm trying to install Ubuntu 18.04.1 LTS Desktop with RUFUS on a computer with the following specs:[/FONT][/COLOR]

[LIST]
[*](CPU) AMD Ryzen 5 2600
[*](MOBO) ASUS Prime B450M-A/CSM
[*](RAM) G-Skill Ripjaws DDR4 F4-2400C15D-16GVB
[*](GPU) Nvidia GeForce GTX750
[*](PSU) Apexgaming AG-650M
[*](SSHD) Seagate Firecuda Compute
[*](mATX) Rosewill SCM-01
[/LIST]
[COLOR=#242729][FONT=Arial]Basically, it boots from the USB (FAT32) and brings up a black error screen with words and numbers. Then it transitions to the purple splash screen with "Ubuntu" and 5 dots. However, the screen shows various visual glitches depending on which USB port I plug into. The link below will show you what's going on with YouTube.

[https://youtu.be/1hMWySNdegg](https://youtu.be/1hMWySNdegg)

I appreciate any help you guys can offer. Thank you.[/FONT][/COLOR]

---

### Post by jisip on 2018-09-22
I posted the same question on another forum and got the answer. This will help someone.

[https://askubuntu.com/questions/1077486/how-can-i-fix-this-ubuntu-install-error/1077489#1077489](https://askubuntu.com/questions/1077486/how-can-i-fix-this-ubuntu-install-error/1077489#1077489)

---

### Post by oldfred on 2018-09-22
Those screens are for BIOS boot set of nomodeset.
All systems since Windows 8 released about 5 years ago are UEFI hardware and usually you want to install in the newer UEFI boot mode to a gpt partitioned drive, not the now 35 year old BIOS boot with MBR partitioning.

If you boot install media in UEFI mode, you get a grub menu. 

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

