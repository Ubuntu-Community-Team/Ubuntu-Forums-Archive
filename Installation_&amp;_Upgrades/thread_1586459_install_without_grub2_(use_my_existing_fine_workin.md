---
title: "install without grub2 (use my existing fine working grub legacy)"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by nico23 on 2010-10-02
[FONT="Verdana"]I have a dual boot config with

sda1 /boot
sda2 Win7
sda3 /
sda4 Truecrypt Partition

i have grub1 working and chaonloading truecrypt loader if i choose "win7" in grub1 menu

I want to install a new kubuntu (no upgrade)

I have read that that there are problems with grub2 and truecrypt actually [a bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/484102") that grub2 dont chainloads truecrypt boot loader
many ppl seem to have problems with grub2

then i read somewhere that ubuntu install is not asking for grub2 to be installed and just installing it. is this right?

i think at least for the alternative install cd its wrong. i installed it on another pc and it asked me! it works for win7 and **U**buntu and i guess its grub2 but there is no truecrypt installed

anyway, i wanted to ask is the live cd installer asks me for grub2 and what is the best and easiest way to stay with my grub and just change the menu.lst to the new kernel (i guess there will be one)[/FONT]

---

### Post by garvinrick4 on 2010-10-02
In just the opposite scenerio I will choose not to install any grub when I install a linux
version with grub legacy so as not to mess with grub2. I have never looked but I imagine there is a way not to install grub2 at all. Then go into your legacy install and update-grub and it will put the new install in its menu.

---

