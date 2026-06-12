---
title: "Freeze on Ubuntu CD boot : cd is good"
date: 2005-07-11
forum: Installation &amp; Upgrades
---

### Post by boutros on 2005-07-11
hello,

 i am trying to install ubuntu on my new laptop. As on all my systems i use bootitNG as a partition/boot tool. Here is my disk config

40 gig drive :
bootitNG is on its own 8mb partition
hda1:winxp
hda2:linux install
hda3:linux swap
hda4:fat32 data partition.

i have 2 boot options. WinXP or Linux. Win XP is setup to "see" only itself and the data part, and linux is set to "see" itself, swap, data. Basically to install linux, i boot up to bootitNG, i set the boot option for the particular linux partition to boot from the cd, i boot, install no problem. I have installed mepis, debian, slack, vector, fedora, among many others using this method w/no problem. But with 2 different ubuntu cd's, as well as kubuntu that i have used to install ubuntu to other systems the cd will not boot, it pops up saying isolinux etc (no ubuntu splash/boot screen), and freezes. No other boot cd has ever done this. I even used a smart boot floppy or something similar that i found mentioned on the forums, boot to this floppy, choose cdrom, it now boots to the splash screen, i type "expert" it begins loading "vmlinuz" i believe, then freezes.

Any ideas why this will not boot under these circumstances. Please note if i boot from the cd before the bootit partition boots then the cd boots ok. But installing in this fashion is not an option. And as mentioned i have never had a problem with this using any other distro cd.

I really would appreciate any ideas related to this problem, as i would love to try ubuntu on my laptop (dell inspiron 2200).

thanks alot,
boutros

---

