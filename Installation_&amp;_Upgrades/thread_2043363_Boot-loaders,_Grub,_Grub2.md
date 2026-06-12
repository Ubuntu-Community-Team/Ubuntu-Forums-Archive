---
title: "Boot-loaders, Grub, Grub2"
date: 2012-08-16
forum: Installation &amp; Upgrades
---

### Post by WindsOfChange on 2012-08-16
Hi

Sorry to have to ask such an "over-asked" question but I'm not familiar  with boot loaders, Grub or Grub2 which I keep reading about in regards  to dual booting Ubuntu with an additional OS installed (win2k in my  case).

Are these boot loaders automatically installed and configured when I install Ubuntu 12.04 from the Live Cd?

I am installing Ubuntu on a second drive and would like to know if everything is installed automatically from the Ubuntu Live Cd including the boot loader that will recognize my windows 2000 OS on the Master Drive and allow me to dual boot?

In other words, do I have to code anything or jump thru any hoops to get Ubuntu to recognize my windows 2000 OS?

Thank you very much.

---

### Post by darkod on 2012-08-16
The grub2 bootloader that comes with 12.04 installs automatically and detects windows and creates entry for it in the boot menu.

What you have to watch out for when having more than one disk, is that grub2 might get installed on the ubuntu disk and if you have your BIOS set to boot the windows disk first, you might see your computer booting windows directly as if ubuntu doesn't exist.

You will have to have the disk where grub2 is as first option to boot in BIOS.

---

### Post by drs305 on 2012-08-16
As to Grub and Grub 2, Grub 2 replaced Grub several years ago and brought some significant improvements. When first introduced, users were fairly diligent of making the distinction between Grub (0.97) and Grub 2 (1.96 and later). 

As Grub 2 became the standard over time, the "2" in Grub 2 was often dropped and today I think most users who read "Grub" in these forums assume the user is referring to Grub2 unless there is something in the post to indicate the older bootloader.

For you, the main concern would be if you are looking at posts older than a few years. If they mention menu.lst in the commands they are referring to the older version and it won't apply to you.

---

