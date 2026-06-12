---
title: "installation of 20.04 failed on grub installation"
date: 2022-05-13
forum: Installation &amp; Upgrades
---

### Post by martinvanek on 2022-05-13
Good evening,
I tried to install a Ubuntu 20.04 LTS on Acer Spin One instead of w10. It repeatedly ends with "fatal error" as "grub install failed".
Using Boot-Repair I got this boot info summary: [https://paste.ubuntu.com/p/5Pqqxf5zYg/](https://paste.ubuntu.com/p/5Pqqxf5zYg/)
I already tried the recommended repair option, but with error saying:
" /target detected. Please close the Ubuntu installer, then retry. "

Well, this error makes some sense as the only option now to run Ubuntu on this laptop is using the live session from usb stick.
But how should I end this session and run Boot-repair when I cannot run Ubuntu directly on that laptop? 
Could anyone help me?
Thanks in advance.
M

---

### Post by oldfred on 2022-05-13
Many Acer systems have needed UEFI update.
Did you close installer so /target (for installer) not mounted.
Boot-Repair may then work?

And then setting "trust" on "unknown" as Ubuntu entry in UEFI.
Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

### Post by ubfan1 on 2022-05-13
Looks like you have the unfortunate allocation of your install media to sda, which may have the installer trying to write grub back to it (see launchpad bug 1396379).  You should be able to run grub from the install media ("try" option) and install grub to /dev/mmcblk1 where it belongs (looks like you already have an EFI partition assigned on that device). Do add yourself to the bug's "Does this affect me?" list if that's the case.

---

### Post by martinvanek on 2022-05-14
So, I closed the installer.
I get the black screen with GNU GRUB version 2.04, using ls command to find grub on usb stick and then set this location for root (or what is it doing, you guys will know more than me as I am a Linux begginer)(commands found on [https://askubuntu.com/questions/883992/stuck-at-grub-command-line](https://askubuntu.com/questions/883992/stuck-at-grub-command-line))
set prefix=(hd0,1)/grub
set root=(hd0,1)
insmod linux
insmod normal
normal(note: I cannot reach the EFI/UEFI menu - and this was problem also prior ubuntu installation - this Acer laptop (second and the last Acer I will ever have) doesn't react on any F2, F12, Del,.... any key to enter the bios. To start ubuntu installation, I needed (when in windows10) to click on "restart" while holding Shift key) 

So after hitting enter on last command it directly booted to usb stick, I started "Try Ubuntu" virtual session, downloaded the Boot-Repair, run the recommended repair - and it is o.k. now!

So everything needed was run away from the installation session (as oldfred proposed) during which the fail occurred and somehow start the "Try Ubuntu" session to do the repair. 

(note2: when you boot using USB stick, you may probably also want to try another attempt to install, but it did not worked for me in this case, I've tried twice...)

Thank you for the support!

---

