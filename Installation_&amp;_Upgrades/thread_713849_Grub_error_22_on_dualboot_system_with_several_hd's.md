---
title: "Grub error 22 on dualboot system with several hd's"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by Trondern on 2008-03-03
Firstly i would like to mention that i have searched this forum and the internet for grub error 22 posts to help me. I have followed the guides and they dont work for me. I have done the find /boot/grub/stage1 and found it on hd1,6 and then the root and setup and it worked great but did not solve my problem. I still get the error when rebooting. 

I have one IDE disk and 3 SATA disks in this computer. Windows are on the IDE and use all of it. On the first SATA i have a small NTFS partition but i use (or rather try to use) the rest for Ubuntu. It seems to me that the problem are that Ubunta or Grub have trouble "counting" these different disk and thues give some wrong info about which disk is which... Are there anyone who have any experience from this? I read that advanced user have edited the device.map in /boot/grub for example.. Can this be a solution for me?

---

### Post by xRaVagEx on 2008-03-03
> **Trondern said:**
> Firstly i would like to mention that i have searched this forum and the internet for grub error 22 posts to help me. I have followed the guides and they dont work for me. I have done the find /boot/grub/stage1 and found it on hd1,6 and then the root and setup and it worked great but did not solve my problem. I still get the error when rebooting. 

A little confused here.  Did you say that when you editted the root and hit 'b', it booted up fine, but after rebooting, it gave you the same error?

If it worked editting the root, you need to make it permanment on your menu.lst when you boot into ubuntu.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Trondern on 2008-03-04
> **xRaVagEx said:**
> A little confused here.  Did you say that when you editted the root and hit 'b', it booted up fine, but after rebooting, it gave you the same error?

If it worked editting the root, you need to make it permanment on your menu.lst when you boot into ubuntu.

```
gksudo gedit /boot/grub/menu.lst
```

Sorry for being unclear. I have worked on it a bit and reinstalled and put grub bootloader on hd1. I also changed the root partition so it became primary. I think maybe that was part of the problem to begin with. Now Ubuntu root is on hd1,0. Now when booting hd1 i get into grub but now i get a error 17 when trying to load Ubuntu. I edit root from 1,0 to 0,0 and press b and it starts fine.. I changed root in menu.lst to 0,0 after but this doesnt solve it tho..what should i put in menu.lst now to get it to boot fine?

---

