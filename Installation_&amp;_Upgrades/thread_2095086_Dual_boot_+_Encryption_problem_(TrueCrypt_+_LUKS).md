---
title: "Dual boot + Encryption problem (TrueCrypt + LUKS)"
date: 2012-12-15
forum: Installation &amp; Upgrades
---

### Post by abadr on 2012-12-15
Hi,

Just got a new Lenovo Ideapad Z580 that has Windows 7 64-bit Home Premium installed. I would like to Encrypt it with TrueCrypt as well as install Kubuntu also encrypted.

According to:
[https://aprescott.com/posts/dual-booting-windows-and-linux-with-encryption](https://aprescott.com/posts/dual-booting-windows-and-linux-with-encryption)
[http://www.ices.utexas.edu/sysdocs/encryption/winlinux.html](http://www.ices.utexas.edu/sysdocs/encryption/winlinux.html)

I resized windows and installed kubuntu encrypted and all works well.
I ended up with 4 primary partitions: windows boot, windows system, ubuntu boot, ubuntu system (LVM/LUKS)

Now I'm supposed to, from windows, encrypt the windows system partion and let TrueCrypt overwrite grub with it's own loader. TrueCrypt gives me the oportunity to test it's new boot loader without actually encrypting the drive. Doing that the boot loader loads up, accepts my password but gives me the following error:
```
Error: No Boootable Partition Found
```

Any ideas? 
Thank you.

---

### Post by oldfred on 2012-12-16
That error is often from BIOS usually Intel motherboard when there is no boot flag on a primary partition. Windows has to have a boot flag, grub does not use boot flag.

I do not use encryption, but from some other users it seems truecrypt has to control MBR so you cannot get to grub. One user just installed grub to a USB flash drive and used that when he wanted to boot Ubuntu.

Also you need to change the default reinstall location of grub or it will overwrite the MBR on a major update and erase your truecrypt in the MBR. Best to have a truecrypt repair disk as that will let you boot.

       #To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

    #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by abadr on 2012-12-16
> **oldfred said:**
> That error is often from BIOS usually Intel motherboard when there is no boot flag on a primary partition. Windows has to have a boot flag, grub does not use boot flag.

That's it :) The boot flag was off for the windows boot partition, I set it up and the computer booted as normal. Encrypting for real as we speak.

Thanks a lot for your help :)
Best Regards

---

