---
title: "Ubuntu 16.04 LTS and Windows 10 Pro BitLocker dual boot loop"
date: 2017-08-03
forum: Installation &amp; Upgrades
---

### Post by Parth_Maniar on 2017-08-03
[COLOR=#111111][FONT=Ubuntu]Greeting's, following is my laptop configuration including OS installation:[/FONT][/COLOR]

[LIST=1]
[*]SSD - 180 GB - Windows 10 Pro with systemroot drive (C:) - **Encrypted - BitLocker ON.**
[*]HDD - 1 TB - 5 partitions: A. 50 GB - Ubuntu 16.04 LTS - ext4 file system. B. 10 GB - SWAP space for Ubuntu C, D and E - are NTFS partition - **PLAINTEXT (BitLocker off).** which I use only in windows.
[/LIST]
[COLOR=#111111][FONT=Ubuntu]When the system boots GRUB 2.02 beta takes over. I see Ubuntu 16.04 LTS with few options related to it and Windows 10 as DEV/SDA1/.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Here is the issue:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]At times when I select windows, it boots normally and goes to BitLocker screen for password. However, **more often than not it shows redraws the blank background (color resembling that of ubuntu grub screen earlier and just stay there.** Only way for me to come out of this is to reboot the system.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Both the systems are fully patched as of this writing.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]What can I do ensure a smooth boot cycle and not a hit or miss.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thank you in advance![/FONT][/COLOR]

---

### Post by Parth_Maniar on 2017-08-03
Following is the solution I've found, tested and currently using without any further problems.


As I click on "Windows" option, everything should be transferred to windows (boot sequence, POST, etc.). This concludes that the problem is before Windows bootloader and hence I edited following file to disable graphics for GRUB.


Boot into Ubuntu, open terminal and type:


sudo gedit /etc/default/grub


Uncomment to disable graphical terminal (grub-pc only) (remove the # before GRUB_TERMINAL line)


GRUB_TERMINAL=console


Update GRUB settings using:


sudo update-grub


and you're done!

---

