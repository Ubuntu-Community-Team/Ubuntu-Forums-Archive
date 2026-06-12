---
title: "Simple 11.04 ubuntu dual windows install"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by freeallforever on 2011-07-25
Hi, I will be installing windows due to the fact that my graphics card is very "special" and won't properly work with Linux. I am a gamer and have a gaming laptop.

I will be installing windows over my current ubuntu install and there will be an attempt at not deleting all the saved files :popcorn:. Afterwards I would like to recover it but a guide I found on google for doing so assumes I get the results it says I should have when double checking and then gives no troubleshoot option.

I have an 11.04 livecd. Is there a simple guide specifically for using grub 2 to recover ubuntu 11.04 and have the option to boot either linux or windows? An important question is, should I create a partition for NTFS before starting the windows installation or will that be done as a first step anyway?

Thank you.

---

### Post by ppv on 2011-07-25
You may not need to install over Ubuntu if you want to dual boot. If you have an extra partition you can use that to install Windows. If you have free space you can shrink existing partition, create a new partiotion and then install windows in the newly created partition. You would need to update grub after installing windows and then grub would show you both the OSs to choose from.

---

### Post by Tea4all on 2011-07-25
What video card is it?

---

### Post by freeallforever on 2011-07-25
> **Tea4all said:**
> What video card is it?
*nVidia GT 540M 1024MB PCI-Express GDDR3 DX11 *

---

### Post by Tea4all on 2011-07-25
Boot from the livecd, go to System > Administration > GParted. Resize the ubuntu partition to whatever you want. Install Windows in the free space. Go in the livecd again and open up a terminal. Type ```
sudo grub-install /dev/sda
``` for the first drive.

---

