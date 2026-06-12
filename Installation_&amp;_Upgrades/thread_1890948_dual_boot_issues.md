---
title: "dual boot issues"
date: 2011-12-04
forum: Installation &amp; Upgrades
---

### Post by tripdagoat on 2011-12-04
Ok, so Im new to Ubuntu and all the how tos so far have been newb friendly, but I am having real issues with Grub2...I think.   My last linux machine was dedicated, but due to some new needs, i've decided to have a dual boot machine.  I have a fresh computer with win7 and have done a fresh install of 11.04 and made the choice in the install menu to install alongside windows. install went fine, rebooted, went straight into windows.  The only way i can get into Ubuntu is by using the boot disk.  I have messed around with easybcd.exe in windows.  i have managed to get grub2 to come up from the boot menu, but it is nothing but a command prompt and i haven't the slightest idea what to do from there. here are the specifics

sda1 ntfs pqservice 20gb flagged as diag
sda2 ntfs system reserved 100mb flagged as boot
sda3 ntfs emachines 230gb
sda4 extended 215Gb
sda5 ext4 214Gb
sda6 linux-swap 1.5Gb

can someone put me in the right direction with a step by step on how to set up this dual boot.  Thanks

---

### Post by bluexrider on 2011-12-04
This should help.

installing windows after ubuntu and 

installing ubuntu after windows

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) 

fairly simple to follow

---

### Post by darkod on 2011-12-04
I would:
1. Undo all changes done by easybcd (if any).
2. Boot with the ubuntu cd in live mode and try to reinstall grub2 to the MBR in terminal with:
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

3. If that doesn't work there is option to try with more complex commands, lets try the simple way first.

Reboot and see if it worked.

---

