---
title: "XPPro/Ubuntu dual boot install fails"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by pacman5 on 2009-12-21
Just tried to install Ubuntu 9.10 alongside Windows XP Pro. The re-partitioning and installation appeared to run normally but when I try to re-boot I get a black screen with the message:

GRUB loading.
Error: no such partition
grub rescue > (blinking cursor)

So I can boot neither Ubuntu nor Windows XP.

Can anyone tell me where to go from here ?

Paddy

---

### Post by darkod on 2009-12-21
Boot with the ubuntu cd, Try Ubuntu option.
Download the script from my signature, move it on desktop for example, and run it in terminal with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file. Copy the content here and wrap it in CODE tags (with the text selected hit the # button in the toolbar above).

---

### Post by pacman5 on 2009-12-21
Thanks for this, Darko.

Having watched the various threads over the last 18 hours I've come to the conclusion that there is some kind of systematic boot/GRUB problem with Ubuntu 9.10 and that for the time being it might be better to install an earlier version, e.g. the 8.04 LTS. So I've restored the original Windows XP Pro system to the laptop and will probably go for 8.04 (I'm still having a think about it; I'm an Ubuntu fan but I'm not sure of the advantages and disadvantages of the different releases).

Paddy

---

