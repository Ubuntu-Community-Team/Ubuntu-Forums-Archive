---
title: "ubuntu live CD &amp; USB not working."
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by empyrec on 2011-04-30
Still new to the forums. Sorry if i'm doing something wrong.
Okay i tried to install ubuntu 11.04 from a live usb and when i get to the installation process ubuntu will not recognize my main and only HDD. The only thing it want's to install on is on the USB which is a 2gig and won't work. I got tired of trying. so i made a live CD when it goes to boot up i get the try ubuntu, install ubuntu grub when i go to try ubuntu it seems as if it's booting up correctly then bam it says that no medium was found and won't boot anymore. I am not using a VB and the live CD isn't damaged or corrupted in anyway.
:(

---

### Post by darkod on 2011-11-08
> **empyrec said:**
> Still new to the forums. Sorry if i'm doing something wrong.
Okay i tried to install ubuntu 11.04 from a live usb and when i get to the installation process ubuntu will not recognize my main and only HDD. The only thing it want's to install on is on the USB which is a 2gig and won't work. I got tired of trying. so i made a live CD when it goes to boot up i get the try ubuntu, install ubuntu grub when i go to try ubuntu it seems as if it's booting up correctly then bam it says that no medium was found and won't boot anymore. I am not using a VB and the live CD isn't damaged or corrupted in anyway.
:(

Not finding the hdd looks like there is raid meta data present. Has the drive been used in motherboard raid?

If you are not using raid (you said it's only drive), boot into ubuntu live mode, open a terminal and execute:

sudo dmraid -E -r /dev/sda

That should ask you if you want to remove raid data. Confirm and after that the installer should be able to see the disk.

---

