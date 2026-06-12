---
title: "Lucid without touching MBR ?"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by spandey on 2010-05-02
Hi,
I have 9.04 running without problems. I want install Lucid without touching my MBR. While installing Lucid, I selected advanced option in the end. When I uncheck install boot loader option OK button is greyed out. IT only accepts /dev/sda which will change the MBR. 

In Koala it was possible to do this. How to do it in LUCID???

---

### Post by ottosykora on 2010-05-02
also I found this and some other users.

Apparently one has to not install it and then install it later 'by hand' from live cd again, this seems to me a big bug rather then a feature.
I prevets me from using lucid on most of my installations.

there was a thread on that, some parts useful, manual installation needed, --force switch needed apparently in the installation etc.

[http://ubuntuforums.org/showthread.php?t=1466033](http://ubuntuforums.org/showthread.php?t=1466033)

---

### Post by dryder on 2010-05-02
If I understand you correctly, you don want the MBR on another disk to be changed?

Then power down, open up your box and unplug the power to all drives except the cdrom and the hdd you wan to install to. Then grub will only write grub on that drive and the mbr on other drives will not be affected.

The (minor) downside is you won´t get a menu letting you choose which OS you want - you will have to use F12 (on my system) to choose which disk to boot from.

David

---

### Post by spandey on 2010-05-02
Thanks for info Dryder but I have only one Hardisk and I don't want to touch MBR as my old XP starts it's tantrums. I don't have backup CD to reinstall XP.

---

### Post by dryder on 2010-05-04
Is this any use [here]("http://www.ehow.com/how_2138434_ubuntu-boot-disk.html")?

---

### Post by spandey on 2010-05-04
Hi Dryder,
I don't have problem booting m PC. I just want to install LUCID without touching MBR of harddisk.

---

### Post by oldfred on 2010-05-04
I have had no problem booting XP from grub.

You can install any non-Vista/7 boot loader to the MBR to boot XP even win98. Linux has a windows boot loader you can install also.

Restore basic windows boot loader 
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

---

### Post by louieb on 2010-05-04
I did a couple of fresh Lucid installs in the last week using the 32-bit alternate CD. 

Both times I installed GRUB to the boot sector of the  / (root) partition. - Not a problem at all - chain loading works and they both boot right up.

Just wondering what boot loader do you want to use when the PC starts.

---

