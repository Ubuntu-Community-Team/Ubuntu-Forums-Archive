---
title: "boot loader"
date: 2005-03-09
forum: Installation &amp; Upgrades
---

### Post by JMY1983 on 2005-03-09
I wanted to re-install Ubuntu on my primary SATA drive but there's no room to make a new partition. Or is there? Also, how do I get the boot choice screen on my primary drive while running Ubuntu on my secondary drive? Thanks.

---

### Post by KLineD on 2005-03-09
I don't know if there's space for another partition in your drive, but to install the boot loader in the bootable partition, tell the installer to overwrite the MBR. This will install grub in the bootable partition and present you with a list of possible choices. Also if you have another os in the first partition, you will get an entry to boot that other os.

Be careful with that though... you can get an unbootable system easily. Have rescue disks in hand.

---

### Post by JMY1983 on 2005-03-09
[QUOTE=KLineD]I don't know if there's space for another partition in your drive, but to install the boot loader in the bootable partition, tell the installer to overwrite the MBR. This will install grub in the bootable partition and present you with a list of possible choices. Also if you have another os in the first partition, you will get an entry to boot that other os.

Be careful with that though... you can get an unbootable system easily. Have rescue disks in hand.[/QUOTE]


Hmm, that sounds like an awful risk. Does everyone have to go through this?

---

### Post by maruchan on 2005-03-09
It's not really that big of a risk. Worst case scenario means you boot with a Live CD and rescue your data before doing a reinstall. Your master boot record is easy to change, it just sounds like a big deal ("ooohhh! Master!"). But yes, you do want to tell the bootloader to write to the MBR. I did it (had Vector Linux on the other partition) and GRUB found it just fine. I think it should work well for you.

> I wanted to re-install Ubuntu on my primary SATA drive but there's no room to make a new partition. Or is there?

I don't know how you want me to answer that question. Can you give more information?

---

### Post by JMY1983 on 2005-03-10
[QUOTE=maruchan]It's not really that big of a risk. Worst case scenario means you boot with a Live CD and rescue your data before doing a reinstall. Your master boot record is easy to change, it just sounds like a big deal ("ooohhh! Master!"). But yes, you do want to tell the bootloader to write to the MBR. I did it (had Vector Linux on the other partition) and GRUB found it just fine. I think it should work well for you.



I don't know how you want me to answer that question. Can you give more information?[/QUOTE]
 Alright so is it a live cd of Linux or Windows? And is there a link with instructions for this? Thank you.

---

### Post by lao_V on 2005-03-10
[QUOTE=JMY1983]Alright so is it a live cd of Linux or Windows? And is there a link with instructions for this? Thank you.[/QUOTE]

Didn't know Windows made Live CD??!!!!

---

### Post by JMY1983 on 2005-03-10
[QUOTE=lao_V]Didn't know Windows made Live CD??!!!![/QUOTE]
 I know windows makes a live cd, I just need to know whether I need to make a windows or linux live cd.

---

### Post by bored2k on 2005-03-10
It's not what he/she meant but, the 3rd party creators of Hirens Boot CD included a Live Windows 3.1 on the disc. Quite nostalgic I might add.

---

### Post by JMY1983 on 2005-03-10
[QUOTE=bored2k]It's not what he/she meant but, the 3rd party creators of Hirens Boot CD included a Live Windows 3.1 on the disc. Quite nostalgic I might add.[/QUOTE]
 I think I will use BartPE

Also, is there a link telling me how to instal grub to my MBR?

---

