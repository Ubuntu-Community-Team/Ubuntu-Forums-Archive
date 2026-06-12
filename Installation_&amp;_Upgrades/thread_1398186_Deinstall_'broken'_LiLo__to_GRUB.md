---
title: "Deinstall 'broken' LiLo  to GRUB"
date: 2010-02-04
forum: Installation &amp; Upgrades
---

### Post by Ubnoob2 on 2010-02-04
I tried installing LiLo because GRUB **2.0** didn't want to add my Windows 7 to the chainlist. So basicly the only two things I did where two commands to install and then I rebooted. Which resulted in me not having any bootloaders on my partition. 

I know there are a lot of topics about this but I am pretty noob so I guess I am just failing. :P 

Here's a [picture from Disk Utitily]("http://img97.imageshack.us/img97/6108/pars.png"). My partition with the Ubuntu I am normally on is already mounted. So now my question is how the h do I get in there and deinstall LiLo? 

Thanks and sorry with spamming you with more of the same stuff.

---

### Post by Leppie on 2010-02-04
i would re-install grub2.
follow these instructions:
```
sudo -i
umount /dev/sda5
mkdir /mnt/temp/
mount /dev/sda5 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
apt-get purge grub grub-pc grub-common lilo
mv /boot/grub /boot/grub.old
apt-get install grub-pc grub-common
exit
```don't worry if you are prompted that some packages are not installed during this process, just continue. dpkg should launch the configuration scripts for grub-pc and grub-common after installation. when all is complete you should also have a 7 menu entry.

---

### Post by Ubnoob2 on 2010-02-04
I tried that, but it doesn't seem to work. Btw this is the error I get when I boot: 'No boot signature found on partition.'

---

### Post by Leppie on 2010-02-04
> **Ubnoob2 said:**
> I tried that, but it doesn't seem to work. Btw this is the error I get when I boot: 'No boot signature found on partition.'
did you install grub2 into a partition or intot he mbr? for grub-install /dev/sda points to the mbr whereas /dev/sda5 points to the first partition in the extended partition.

---

### Post by Ubnoob2 on 2010-02-04
No GRUB is just installed in /boot. I am now on my Ubuntu on the HD again by using a different version of Ubuntu with a different GRUB list. Deinstalling GRUB doesn't work and it says LiLo is already uninstalled. 

Could it harm my system when I just copy all files from my GRUB that works to my not working version of GRUB?

---

### Post by Ubnoob2 on 2010-02-04
> **Ubnoob2 said:**
> No GRUB is just installed in /boot. I am now on my Ubuntu on the HD again by using a different version of Ubuntu with a different GRUB list. Deinstalling GRUB doesn't work and it says LiLo is already uninstalled. 

Could it harm my system when I just copy all files from my GRUB that works to my not working version of GRUB?

[B]Just solved it. I tried a lot of stuff, but what I tried last was use Synaptic Package Manager and chose for complete removal of anything containing GRUB. Then I chose to install 'grub-pc', 'grub-common' and 'grubutil-win32' again. And everything seems to be fixed. 
Except for Windows 7 which still isn't in the list but I'll figure that soon I hope. :p
[/B]

---

### Post by Leppie on 2010-02-04
> **Ubnoob2 said:**
> [B]Just solved it. I tried a lot of stuff, but what I tried last was use Synaptic Package Manager and chose for complete removal of anything containing GRUB. Then I chose to install 'grub-pc', 'grub-common' and 'grubutil-win32' again. And everything seems to be fixed. 
Except for Windows 7 which still isn't in the list but I'll figure that soon I hope. :p
[/B]
did you do a wubi install?
what you're saying doesn't really make sense. "completely remove" in synaptic is "purge" with apt-get, so if apt-get purge didn't work "completely remove" in synaptic wasn't the solution either. that leaves as only difference the "grubutil-win32" which sounds something like a wubi thing (i don't have any experience with wubi though).

---

