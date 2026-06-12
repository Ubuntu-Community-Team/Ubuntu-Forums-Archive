---
title: "Trouble Installing Ubutu; Will not Boot"
date: 2013-06-04
forum: Installation &amp; Upgrades
---

### Post by sayofethos on 2013-06-04
Hi,

I have been trying to install the latest Ubuntu on my Lenovo Thinkpad X230 to no avail. Once powered on, it does not even take me up to the Ubuntu logo in the installation process, but instead presents this;

[I][B]Intel(R) Boot Agent GE v1.3.81
Copyright (C) 1997-2011, Intel Corp.[/B][/I]

[B][I]PXE-E61: Media test failure, check cable
PXE-MOF: Exiting Intel Boot Agent.[/I][/B]

This text will appear even when the computer is powering on and starting up Windows 7, which is the current OS installed on it, but also when attempting to install Ubuntu 13.04. I have just got this laptop and it was formatted and refurbished by its previous owner. Any ideas?

Specs; 
Intel Core i5-3320M CPU 2.60GHz
8Gb RAM
Intel HD4000 Graphics

All advice appreciated!

---

### Post by ahallubuntu on 2013-06-04
~

---

### Post by sayofethos on 2013-06-05
It seems like the problem was with the boot order settings in the BIOS. Now that the Intel and PXE are not there to confuse things it booted fine and installed in a very smooth fashion. So much easier than my last episode with Lubuntu on another machine!

Thanks a lot for the tip, really appreciate it!

---

