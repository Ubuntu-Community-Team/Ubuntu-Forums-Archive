---
title: "USB install always wants to install"
date: 2013-03-29
forum: Installation &amp; Upgrades
---

### Post by stew1411 on 2013-03-29
So I wanted a USB install of Ubuntu, as I already have a desktop, this is so I can take my college programs with me to school on their computers. I followed the instructions, but every time i boot, I get the option to install or try it. I don't have a problem clicking try it. But none of my settings or documents or downloaded apps never remain after reboot. What should I do?

---

### Post by sudodus on 2013-03-29
Welcome to the Ubuntu Forums :-)

You can either make a persistent live USB drive or make a regular installed system on your USB drive. I mean installed as if it were installed to an internal hard disk drive. This is actually the best method, at least if you have 8GB or more. You can manage the system as usual, update and upgrade it etc. And the best thing is that it is portable to most computers as long as you don't install any proprietary drivers.

---

### Post by fantab on 2013-03-29
> **stew1411 said:**
> So I wanted a USB install of Ubuntu, as I already have a desktop, this is so I can take my college programs with me to school on their computers. I followed the instructions, but every time i boot, I get the option to install or try it. I don't have a problem clicking try it. But none of my settings or documents or downloaded apps never remain after reboot. What should I do?

That is because what you have on your USB is Ubuntu installer, its not a proper installation. If you have 8gb or more USB you can install Ubuntu on it. Also, a proper Ubuntu install on USB will be faster than the Ubuntu installer version.

---

### Post by stew1411 on 2013-03-29
OK, its a 32 GB usb stick. So should I mount the ISO in windows, and then try the install from windows to the usb stick itself? Also, if I do it this way, can I still access my windows drive to access files when booted into the usb install? Also, I don't think I need any proprietary drivers, as the PCs are stock builds from Dell.

---

### Post by sudodus on 2013-03-29
> **stew1411 said:**
> OK, its a 32 GB usb stick. So should I mount the ISO in windows, and then try the install from windows to the usb stick itself? Also, if I do it this way, can I still access my windows drive to access files when booted into the usb install? Also, I don't think I need any proprietary drivers, as the PCs are stock builds from Dell.

1. You should make one install CD/DVD/USB drive (use the one you have or another one, a USB drive need be only 1 GB for a CD iso image).

2. Boot from this drive and install to a (another) USB drive, for example the 32 MB drive you have. Consider getting a USB 3 drive! The flash is much faster and improves the speed even when used with a USB 2 port. Recently Sandisk Extreme was a good choice (but the market changes quickly, so check what is available and compare speed and price).

---

### Post by stew1411 on 2013-04-01
So I used 2 usb drives for the usb install. It took forever to install, but I got it. Now, when I boot from the usb stick, it takes FOREVER. It will boot into Ubuntu, it just takes freaking forever. Why is this? BTW, I installed as ext2, because everytime I tried to install as FAT, I kept getting an error saying that usb doesn't support FAT.

---

### Post by fantab on 2013-04-01
Ext2 is the old version of EXT4. We use EXT4 to install Ubuntu/Linux. Linux, AFAIK, does not install on FAT, thought it can read and write to it. 

The speed of the USB Drive also matters. Generally it will NOT take "forever". So I guess there is something wrong with the install or with the USB drive. 

By the way, do you have SWAP partition, either on the machine's internal HDD or on the USB? If not, then create atleast 1GB SWAP partition on your USB. These days, this is not an absolute must, given the huge RAM available on computers. However, in my experience, ubuntu works faster with a SWAP partition. Since you will be carrying this USB around and will probably boot on different comps. then I suggest you create one.

To surmise, create a SWAP partition and reinstall.

Good Luck.

---

### Post by stew1411 on 2013-04-01
OK. Yes, I did create a swap partition of 1.2 GB, and installed to ext2. I will do a reinstall to ext4. When I did the install, it took it around 3 hours to install, so if I install to ext4, will the install also go faster?

---

### Post by sudodus on 2013-04-01
It will be faster with a USB 3 drive. It is really worthwhile to get good hardware to avoid such slow performance. Ext 4 is known to be faster than ext2, but I don't know how much. What is really slow via USB 2 is writing many small files (and there are really many to be installed).

---

