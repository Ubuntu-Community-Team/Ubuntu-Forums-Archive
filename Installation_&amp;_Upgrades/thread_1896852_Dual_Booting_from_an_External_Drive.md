---
title: "Dual Booting from an External Drive"
date: 2011-12-17
forum: Installation &amp; Upgrades
---

### Post by rfbeck on 2011-12-17
I recently (and sadly) had to delete my Ubuntu partition from my notebook's main HDD. I was running out of room for Windows7.
However, what I'd like to do is install Ubuntu to my exteral drive (eSATA) and dual boot that way.
I just need to make sure that if my external is not connected (it usually is) I can still boot into Win7.
Will I have to decide where the GRUB2 bootloader is placed, or any other arcane details?
I miss Ubuntu very much and am trying to think of any solution that will allow me to dual boot again.
Thanks for and guidance on this issue.
______
Robert

---

### Post by 2F4U on 2011-12-18
Make sure to not install Ubuntu's boot loader Grub into the MBR of the Windows hard disk.

[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)

---

### Post by fantab on 2011-12-18
Can you make adjustments in BIOS to boot External Drive First? If you can then its easy.

When installing Ubuntu, Install GRUB on EXTERNAL DRIVE ONLY... when it is not plugged in Windows will boot. 

If you can't adjust the BIOS then you will have a problem. You will be forced to install GRUB to Internal Drive and this will erase your Windows MBR. IMO that not big issue because GRUB will handle Windows with ease.

---

### Post by BC59 on 2011-12-18
> **rfbeck said:**
> I recently (and sadly) had to delete my Ubuntu partition from my notebook's main HDD. I was running out of room for Windows7.
However, what I'd like to do is install Ubuntu to my exteral drive (eSATA) and dual boot that way.
I just need to make sure that if my external is not connected (it usually is) I can still boot into Win7.
Will I have to decide where the GRUB2 bootloader is placed, or any other arcane details?
I miss Ubuntu very much and am trying to think of any solution that will allow me to dual boot again.
Thanks for and guidance on this issue.
______
Robert

I really don't understand what you like to do. Why you need Grub? If you like to use Ubuntu, just plug the external bootable drive and boot. If you like to use Windows, unplug the external drive and that's it.

---

### Post by hansdown on 2011-12-18
Hi, rfbeck.

Reply # 2 & 3 are good.

BC59, Grub needs to be installed to the proper place.

---

