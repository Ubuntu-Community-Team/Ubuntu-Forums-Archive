---
title: "Ubuntu 10.4 and Win 7 with TrueCrypt"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by azureice55 on 2010-06-11
Hi.  So I really want to have a dual boot system with my Win 7 partition encrypted with TrueCrypt.  I don't need Ubuntu 10.4 encrypted.

I started by installing Win 7 and encrypting the partition (not entire drive) with TrueCrypt.  This puts the TrueCrypt boot loader in the MBR.  Next, I installed Ubuntu 10.4 on another partition, which puts Grub2 on the MBR.  I restored TrueCrypt bootloader to the MBR using the TC recovery CD.

So now I had the problem of getting both to boot.  I read about keeping Grub2 in the MBR and chainloading TC into it, but apparently that doesn't work with Grub2.  So the other option is to install Grub2 on to the linux partition and just have TC find it when you hit escape.  I did this by booting from the Ubuntu live CD and doing the following:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt --force /dev/sda5

(where sda5 is my ubuntu partition)

Now the weirdness happens.  It works once.  I reboot the machine, hit escape at the TC bootloader, and I can choose to boot to Grub, which loads my Ubuntu install just fine.  However, when I restart the computer, I can't boot to Grub anymore.  I have to restore it by using the above commands again.  What gives?

Here's a layout of my drive (just one disk):
sda1: windows 7 loader (boot)
sda2: encrypted windows 7
sda3: extended partition
--sda5: ubuntu
--sda6: swap

Does anyone know why this is happening?

---

### Post by azureice55 on 2010-06-13
Nobody has any ideas? :(

---

### Post by Malexan on 2010-07-15
TrueCrypt bootloader has to be installed in MBR. GRUB2 works unstable when it's installed in a partition but not in MBR. I've [downgraded to GRUB Legacy]("https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy") and now it works.

---

### Post by robwicks on 2010-07-15
I did a grub install to my Linux boot partition. I had to force it, since that is not the recommended, but it has worked fine. I have Truecrypt on Windows 7 in the first partition on the drive, the Grub2 MBR installed on the second partition, and encrypted LVM on the third partition.

---

