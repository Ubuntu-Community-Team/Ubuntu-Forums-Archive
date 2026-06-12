---
title: "question on dual booting"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by JustinJAH on 2007-07-05
i recently installed ubuntu 7.04 on my spare backup HD. iam using EasyBCD to boot but cant seem to configure it correctly. here is my configuration.

i have a raid 0 setup for windows Vista 2x36gb WD10k RPM
and for my media and backup is on a 500gb Samsung
i partitioned 18gb for /root and 2gb for a swap.
so for the 500gb here is the order of the partitions
partition 0 = Media and backup files
partition 1 =18GB Linux 
partition 2 = 2GB Swap

vista would see my 500GB as HD1 cause of the raid iam guess. since grub isnt installed on my MBR i used the Neo Grub install. iam lost on how to configure Neo grub to boot to ubuntu. any help would be great thanks guys

---

### Post by destructchaos on 2007-07-05
out of curiosity, why didn't you install grub?  a default install of ubuntu should have set all that up for you.

---

### Post by JustinJAH on 2007-07-05
when i was installing ubuntu it didnt give me the option to install to my free partition space on my 500gb. it kept wanting to overwrite my 500gb. so i had to manualy select the partition and make a 18gb and a 2gb. i had a 20gb already made so i just split it and i think it made a 512kb partition for the boot which would be grub. but since grub is installed on the 500gb hd it isnt gonna work.

---

### Post by Computer Guru on 2007-07-06
Hey Justin,

First, uninstall NeoGrub. Then download EasyBCD 1.61 BETA and add a "grubless" entry:
[http://neosmart.net/forums/showthread.php?t=642](http://neosmart.net/forums/showthread.php?t=642)

Just go to Add/Remove -> Linux/BSD and check the "I don't have GRUB installed" box, then click "Add Entry"

---

