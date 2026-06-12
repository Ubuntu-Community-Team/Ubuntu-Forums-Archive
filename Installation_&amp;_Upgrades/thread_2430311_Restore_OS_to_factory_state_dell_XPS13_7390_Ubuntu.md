---
title: "Restore OS to factory state dell XPS13 7390 Ubuntu 18.04.3 Preinstalled"
date: 2019-10-30
forum: Installation &amp; Upgrades
---

### Post by egeror on 2019-10-30
Hi There,

I recently bought an dell xps 13 7390, within a few days the wifi adapter went.

I had little installed on the machine (android, spotify, notepad++) so i decided to restore to factory settings through the bios.

Like a numpty, i didnt create a recovery disc on set up ... So now when the machine tries to boot from grub2:

I chose the option "**ubuntu**" and it ends up at a black screen with "(initramfs)"

If i try to boot and with "**Restore OS to factory state**" i get a black screen with "(initramfs) unable to find a medium containing a live file system"

I have went back to the supplier so i will see what they say ... But I am just wondering if there is something I could do to restore it OR will I have to wipe the harddrive and install it fresh? Has anyone else had this experience and overcame it?

---

### Post by CatKiller on 2019-10-30
A fresh install takes, like, 20 minutes, and you can browse the Internet while it's doing its thing.

Dell have been really good about upstreaming all their drivers and whatnot, so you won't be missing out on any special sauce.

If they come back to you in the future with an answer you like better, you'll have had a functioning machine in the meantime.

---

### Post by oldfred on 2019-10-30
The one or two pre-installed versions of grub I have seen with Dell  were very customized to boot the recovery partition. Do not remember details.

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

Ubuntu 19.10 Provides Good Out-Of-The-Box Support For The Dell XPS 7390 Icelake Laptop
[https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1](https://www.phoronix.com/scan.php?page=article&item=dell-xps7390-ubuntu1910&num=1)
probably similar:
Dell XPS 15 Series 7590 (2019)
[https://askubuntu.com/questions/1161456/how-to-run-ubuntu-on-new-dell-xps-15-7000-series-7590](https://askubuntu.com/questions/1161456/how-to-run-ubuntu-on-new-dell-xps-15-7000-series-7590)
[https://github.com/TillmannBerg/Ubuntu-Dell-XPS-15-2019](https://github.com/TillmannBerg/Ubuntu-Dell-XPS-15-2019)

---

### Post by Alex_Marcus on 2019-11-07
Sorry to hear about your difficulty on the XPS 13.  I have the exact same machine, and during my days of trying out different Linux OS's I experienced the same dreaded `(initramfs)` screen.  It's a bad feeling.

I tend to agree with CatKiller here - my solution was to obtain a USB drive and create a bootable Ubuntu installer on it.  Once you've booted to the USB installer, wiping the broken OS remnants and installing a fresh cup of Ubuntu is fairly trivial.

These instructions may prove useful: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows)

Good luck!

---

