---
title: "[SOLVED] Dual boot installation results in &amp;quot;missing operating system&amp;quot;"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by egbertsl on 2008-01-24
Hi,

I just installed Ubuntu 7.10 from the life DVD into my pc in a dual boot config with Vista. The installation ended without problemes but when I reboot I receive a "missing operating system"  message. This is my hd configuration: 

/dev/sda1        HPFS/NTFS
/dev/sda2        Linux
/dev/sda3 *     Linux
/dev/sda4        Extended
/dev/sda5        Linux Swap/Solaris

I already found out that there is no grub directory in /boot  ..so somehow grub isnt installed....I was told that with the command "grub" I can start the grub programm (that worked good) but then that I should give the command "root (sda0,2) " but this results in the next error: Error 23: error while parsing the number   Can someone give me some advice? I cant use either OS now but it seems to me that this just a small error ....

thx!

---

### Post by PmDematagoda on 2008-01-24
Could you please post your menu.lst file.

---

### Post by egbertsl on 2008-01-24
well...actually there is no /boot/grub directory..so also no menu.lst file...

---

### Post by egbertsl on 2008-03-03
I replaced my old IDE dis with a new Sata one and reinstalled grub...now it works good...it looked like the combination of ide versus sata and Vista versus Ubuntu is not a great combi!

thx for te hhulp!

---

