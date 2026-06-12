---
title: "Installing Wubi with EasyBCD?"
date: 2011-06-04
forum: Installation &amp; Upgrades
---

### Post by Goosemonkey on 2011-06-04
I already installed Wubi, and I liked it so much, I decided to fully install Ubuntu in a dual-boot with Vista.

Well, that didn't go too well.. so I had to repair my computer with EasyBCD.

Now, I'm trying to reinstall Wubi, but when I install and then re-boot, Windows loads without asking me to go to Ubuntu.

I think there might be a problem here with EasyBCD.. when I install Wubi, then reboot and get back to Windows, EasyBCD doesn't show Ubuntu in the list of OS's. I tried adding it, which only brought me to a grub command line with some text, then an input that said

```
grub>
```

So, how might I go about getting Wubi installed?

(I'm not going back to the full install, that almost screwed my computer for good.)

---

### Post by Goosemonkey on 2011-06-05
bump

---

### Post by Rubi1200 on 2011-06-05
Here is a link that should help you achieve what you want:
[http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/](http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/)

---

### Post by ILoveYorkies on 2011-06-05
Hi, 
Or instead of using WUBI you could try to install to an external hard drive ( or a flash drive  like I have done ). You could either install just Grub2 bootloader to  the flash or get a 8 or 16 gb thumbdrive and partition it  with Gparted from a  livecd or liveusb. First  while in Windows change the thumbdrive from  removeable (to write cache so you have to always use shutdown safely like  when using an external hard drive). Then use a livecd choose try Ubuntu  not install. If it boots okay then go to apps and pick Gparted and  partition the drive giving 300mbs or less to Grub then you need a root  (/) partition then  a a swapfile and a /home partition. Then use disk  utility to double check which is the the dev names so you install to the  correct drive so you don't overwrite your Win partitions nor it's mbr.  Or you could install grub to a 4gb or less thumbdrive after partitioning  your main Win partition most likely c drive, shrinking it so you can  make another partition for Linux. If you do that, MAKE SURE YOU BACKUP  OR COPY ALL THE DATA YOU NEED TO KEEP! Shrinking your partition with  software for Win or using Gparted usually doesn't BUT IT CAN CORRUPT OR  ERASE DATA!  If you IMPROPERLY INSTALL GRUB YOU COULD MESS UP Windows  MBR BOOTLOADER! That's why I use flash drives and use the "other" check  box during install instead of allowing Ubuntu to choose everything. I can then choose  the devices to partition myself.  I just use the key to pause post so I  can choose which drive to boot from, In my case I press Esc then F9 and  it lists my Grub drive named Sandisk. I have to do that every time  I want to boot Natty but that's just the way I wanted it. If you don't then just go into your bios utility and move the Ubuntu drive to 1st place then Windows drive to 2nd place then every time you power on, it looks for your Grub drive to boot from. If it doesn't find it, it boots directly into Win again.So far this method has worked for  me. Post back to let me know if you need more details on it.
I hope this  helps you to dual boot if WUBI doesn't work for to anymore.

---

### Post by Goosemonkey on 2011-06-05
> **Rubi1200 said:**
> Here is a link that should help you achieve what you want:
[http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/](http://www.howtogeek.com/howto/20340/how-to-restore-the-wubi-ubuntu-bootloader/)

Thanks, I'll try that! It seems like exactly what I need.

---

