---
title: "Help with grub rescue"
date: 2010-07-28
forum: Installation &amp; Upgrades
---

### Post by woodfire on 2010-07-28
Hi everyone,
Very sad to post this thread here.
I have been satisfied with wubi/ubuntu 10.04 which was installed on my laptop, so I decided to also install that on my netbook (Acer Aspire One D250, no CD/DVD drive). 
After the installation was finished (successfully), it ran the update automatically. 
The error occurred after the restart, showing Error: no such device: xxxxxxxx-xxxxxxxx (I guess these letters and numbers vary). and grub rescue>
I tried to search on the internet and also in the forum and I see this error happened to many persons. There were a few solutions/instructions in some of the threads, but the problem now is neither windows nor ubuntu can start. The only thing I got is the Error. 
It's OK that all the data will be lost (no important data on this netbook), but I still prefer it can be fixed without reinstall the system.
Hope somebody can help me. Many thanks!

---

### Post by bcbc on 2010-07-28
This has been happening lately to some wubi users. During updates of grub, the grub bootloader is being installed to the drive MBR. With wubi installs you need the windows bootloader.

The repair is easy enough, but complicated by the lack of a cd/dvd drive. Did you create a windows repair USB or an Ubuntu live USB?
If the answer is yes, you can either use the windows repair to reinstall the windows bootloader, or boot the ubuntu live USB and install lilo as follows:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

If you don't have either you will have to create one on a different machine. I don't think there is any other way.

---

### Post by woodfire on 2010-07-28
> **bcbc said:**
> This has been happening lately to some wubi users. During updates of grub, the grub bootloader is being installed to the drive MBR. With wubi installs you need the windows bootloader.

The repair is easy enough, but complicated by the lack of a cd/dvd drive. Did you create a windows repair USB or an Ubuntu live USB?
If the answer is yes, you can either use the windows repair to reinstall the windows bootloader, or boot the ubuntu live USB and install lilo as follows:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```If you don't have either you will have to create one on a different machine. I don't think there is any other way.

Hi thanks for your help! I can make a live usb and try this when I get back home. :KS

---

### Post by bcbc on 2010-07-28
> **woodfire said:**
> Hi thanks for your help! I can make a live usb and try this when I get back home. :KS

OK... just make sure that when you boot from the USB that /dev/sda is still your internal drive. (It should be, but it's a good idea to double check). You can do this by running:
```
sudo fdisk -l
```
(that's a small L)

---

### Post by woodfire on 2010-07-28
> **bcbc said:**
> This has been happening lately to some wubi users. During updates of grub, the grub bootloader is being installed to the drive MBR. With wubi installs you need the windows bootloader.

The repair is easy enough, but complicated by the lack of a cd/dvd drive. Did you create a windows repair USB or an Ubuntu live USB?
If the answer is yes, you can either use the windows repair to reinstall the windows bootloader, or boot the ubuntu live USB and install lilo as follows:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```If you don't have either you will have to create one on a different machine. I don't think there is any other way.

Hi bcbc, thank you very much, it worked and now everything is back working.:p

---

