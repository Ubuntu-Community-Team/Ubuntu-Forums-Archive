---
title: "Install 10.04 without CD or USB"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by Batfrog on 2010-05-31
I’m trying to install Ubuntu 10.04 on my Toshiba Portege M200 tablet PC. 

This is made exceedingly difficult by the fact that the m200 has no CD drive, and furthermore, does not allow booting from any USB device :icon_frown:

**What we do have:**
[LIST]
[*]The option to boot from SD (I have tried this using the same method used for USB, but to no avail)
[*]The option to boot from Network (I do have a wireless\wired network available, and other PCs on the network)
[*]An external hard drive case I could temporarily transplant the m200’s HDD into.
[*]A desktop PC running Windows 7 (it can be used, but it should be completely unaltered by the end of the process)
[/LIST]

keep in mind, that after i install Ubuntu i plan to install Windows XP and Snow Leopard (Hackintosh) on different partitions on the same HDD.

Hope you can help [-o<
-Batfrog

---

### Post by ronnielsen1 on 2010-05-31
Ultimate boot cd will allow you to boot from usb. I've used it on an old laptop

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

It also fixes grub or grub2 errors

---

### Post by ronnielsen1 on 2010-05-31
Sorry forgot no cd

---

### Post by C.S.Cameron on 2010-05-31
It is probably best to install XP before Ubuntu.
There are several methods you can use.
1) disable the desktop internal HDD plug in the m200 HD with external enclosure. Install Ubuntu to it using the Live CD. (a Ubuntu HDD is usually portable between machines).
2) Download the Ubuntu iso to the m200 and use Unetbootin to install Diskimage to Hard disk Drive C:\. This should give you the opportunity to install Ubuntu the next time you boot the m200.
3) Clone an Ubuntu installation from another machine to the m200 over the network using dd.

---

### Post by azertyh on 2010-05-31
unetbootin has the option to install an OS from network or from an image iso ont the hard disk.

---

### Post by Batfrog on 2010-05-31
> **C.S.Cameron said:**
> 2) Download the Ubuntu iso to the m200 and use Unetbootin to install Diskimage to Hard disk Drive C:\. This should give you the opportunity to install Ubuntu the next time you boot the m200.

This sounds like the best option to me. Would it be possible to install XP and Snow leopard using the same method? (keep in mind that Snow leopard would need to be put on a HFS+ partition)

> **C.S.Cameron said:**
> It is probably best to install XP before Ubuntu.

How would you recommend i do this?

Thanks!

---

### Post by C.S.Cameron on 2010-05-31
The attached link looks interesting but I have not tried it yet:

[http://www.techtroupe.com/os/windows-xp/how-to-install-windows-xp-on-a-laptop-with-no-cd-drive/](http://www.techtroupe.com/os/windows-xp/how-to-install-windows-xp-on-a-laptop-with-no-cd-drive/)

I have not heard of anyone being able to make UNetbootin work with XP.

---

### Post by MrMintanet on 2010-12-01
Your M200 is capable to boot from USB.  You need to check your BIOS settings.  The laptop "has" to be able to boot from USB being it doesn't have an optical drive.  You may need to flash BIOS.

I'm sure this issue is probably already closed though.

---

### Post by davegaunt on 2011-07-28
[QUOTE=MrMintanet;10186027]The laptop "has" to be able to boot from USB being it doesn't have an optical drive.

No, actually it will NOT boot from USB unless it is a Toshiba floppy or CD/DVD, or some select Targus CD/DVDs. I've tried four different external CDs and DVDs and none will boot. The Toshiba website lists 6 drives that will boot and that's it. No flash drives or ext. HDs.

Is that true that installs are transferable from computer to computer? If I were to do that, would it be better to install 11.04 right off the bat, or an earlier version and then upgrade?

Thanks!

---

