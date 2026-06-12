---
title: "kubuntu hogs boot: installed ku 1st xu 2nd grub only boots ku"
date: 2021-04-28
forum: Installation &amp; Upgrades
---

### Post by devrin_gubler on 2021-04-28
dual boot installed kubuntu 1st, xubuntu 2nd, but grub shows ubuntu (and windows) and that (choosing ubuntu) only boots to kubuntu. please tell me what is up with these installs? is it possibly the fact that in order to see the thumb drive for xubuntu i had to switch bios to both legacy and uefi where it was uefi only for kubuntu? i may have had an old ubuntu installed before i dont remember.

---

### Post by oldfred on 2021-04-28
UEFI & BIOS are not compatible.
Once you start to boot in one mode, you cannot switch. Or grub can only boot other installs that are in the same boot mode.

Sound like you installed Windows & Kubuntu in UEFI mode, but installed Xubuntu in BIOS boot mode.
How you boot install media, UEFI or BIOS is then how it installs.

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Normally last install, becomes the default boot. But if different boot modes then that will change how you boot.

---

### Post by devrin_gubler on 2021-04-28
whatever i used didnt allow to choose it just wrote the iso as mbr, think it was etcher. will use rufus since it gives you choice of uefi. this will solve it right?

---

### Post by oldfred on 2021-04-28
As long as you use the UEFI/gpt mode & boot installer in UEFI mode.
I think with Rufus, it then only boots in mode you select to create installer.
Most installers allow you to choose  which way to boot in UEFI one time boot menu.

---

