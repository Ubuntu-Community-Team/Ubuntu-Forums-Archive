---
title: "Installing Windows 7"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by donkey56 on 2009-12-28
A few weeks ago, I installed Ubuntu 9.10 on my laptop. I did that and at the same time got rid of Windows Vista, as i was not happy with Vista. Now, my wife is asking me to install Windows 7 on the laptop as a dual-boot option. I'm at a loss as to where to begin. Should i uninstall Ubuntu 9.10 first, then install Windows 7, and finally reinstall Ubuntu 9.10 using Wubi? Or can I just install windows 7 and keep my present Ububtu 9.10 and all my files and software with it?

Novice needs advice,

Thanks.

---

### Post by presence1960 on 2009-12-28
> **donkey56 said:**
> A few weeks ago, I installed Ubuntu 9.10 on my laptop. I did that and at the same time got rid of Windows Vista, as i was not happy with Vista. Now, my wife is asking me to install Windows 7 on the laptop as a dual-boot option. I'm at a loss as to where to begin. Should i uninstall Ubuntu 9.10 first, then install Windows 7, and finally reinstall Ubuntu 9.10 using Wubi? Or can I just install windows 7 and keep my present Ububtu 9.10 and all my files and software with it?

Novice needs advice,

Thanks.

You do not have to uninstall Ubuntu to install windows. Make an NTFS partition or some unallocated space for windows by booting the Ubuntu Live CD/USB. Choose "try ubuntu without any changes...", when the desktop loads open a terminal (Applications > Accessories > Terminal) and run ```
gksu gparted
```

This will open gparted. If you have no unallocated space or a partition that you want to convert to windows then you will have to shrink Ubuntu's partition to create space for windows. You can leave that space as unallocated or create an NTFS partition from that space. Then boot the Windows 7 DVD and install to that unallocated space or NTFS partition as the case may be.

You will have to restore GRUB after the windows installation because windows will overwrite GRUB on the MBR. Once you have windows installed and checked to see that it indeed does boot post back and we'll get you instructions to restore GRUB to MBR.

The above is for a single hard disk. If you have multiple hard disks in your machine post back because you have multiple options at your disposal.

**_I would back up all data you do not want to lose!!_** This is best practice prior to any partitioning/OS installation operations, usually nothing happens but remember Murphy's Law! Don't be the one caught with your pants down without a backup  of your data on here whining about it.

---

### Post by donkey56 on 2009-12-29
Thanks for the swift reply. One problem: I installed Ubuntu 9.10 by downloading and not by CD/USB. So i don't have CD/USB you mention here.

< Make an NTFS partition or some unallocated space for windows by booting the Ubuntu Live CD/USB.>

---

### Post by zey on 2009-12-29
> **donkey56 said:**
> Thanks for the swift reply. One problem: I installed Ubuntu 9.10 by downloading and not by CD/USB. So i don't have CD/USB you mention here.

< Make an NTFS partition or some unallocated space for windows by booting the Ubuntu Live CD/USB.>


download the CD and burn it then..

---

### Post by donkey56 on 2009-12-30
Windows 7 up and running. Many thanks for the help. Could you now tell me how to restore GRUB?

---

### Post by presence1960 on 2009-12-30
You need to download the 9.10 iso and make a bootable CD/USB. You are going to boot from that to restore GRUB. But first you need the CD/USB and I need info. So Make the bootable CD/USB, boot from it and choose "try Ubuntu without any changes...", when the desktop loads open a terminal (Applications > Accessories >Terminal) and run this command ```
sudo fdisk -l
```
That is a lowercase L in -l. Post the output of the command here so I can see your partition table. I will then give you the commands to install GRUB2

Here is a link to install GRUB2 for your reference: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

