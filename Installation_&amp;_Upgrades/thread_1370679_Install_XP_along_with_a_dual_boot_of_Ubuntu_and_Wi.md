---
title: "Install XP along with a dual boot of Ubuntu and Windows 7"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by ath007 on 2010-01-02
I have a dual boot running on an Acer Aspire 5930G; Windows 7 32 bit and Ubuntu 9.10 64 bit. I recently got some softwares that work only with XP. Since it is important for my work, i will have to install XP. Is it possible to install along with this already existing dual boot structure? I had installed Win7 first after which i installed Ubuntu. 

Please help me here as i am in a tight spot. I dont want to run VirtualBox or VMware or those sort of programs cuz if i have to work with XP, it has to be XP alone (because of many performance dependencies)

Is a triple boot in this sequence possible?

Thanks for your time :)

---

### Post by starcraft.man on 2010-01-02
> **ath007 said:**
> I have a dual boot running on an Acer Aspire 5930G; Windows 7 32 bit and Ubuntu 9.10 64 bit. I recently got some softwares that work only with XP. Since it is important for my work, i will have to install XP. Is it possible to install along with this already existing dual boot structure? I had installed Win7 first after which i installed Ubuntu. 

Please help me here as i am in a tight spot. I dont want to run VirtualBox or VMware or those sort of programs cuz if i have to work with XP, it has to be XP alone (because of many performance dependencies)

Is a triple boot in this sequence possible?

Thanks for your time :)

I triple boot just fine. It's possible. Though I started by installing XP then 7 then reinstalling grub to the MBR (ubuntu was there already).

I advise you to look at resizing your partitions and make space for XP. Then install it to made partition, it will overwrite your MBR unfortunately. Then see about restoring [grub2]("https://help.ubuntu.com/community/Grub2"). See grub1 documentation if not karmic (article called HowtoGrub I believe). It shouldn't be too hard, restoring grub the only finicky part. Also, you may need to write custom entries for windows if it doesn't detect right.

If you need more specific advice reply with questions.

---

### Post by oldfred on 2010-01-02
Windows default install finds the existing install with the boot flag and combines the boot moving some files. As such each is not directly bootable from grub but from the one windows with the boot flag. There is a work around if you want to directly boot each windows install directly from grub.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Vista copies boot manager to one
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
[]("http://members.iinet.net/%7Eherman546/...MGR_is_missing")
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

---

### Post by ajgreeny on 2010-01-02
Alternatively, you could just use a VM, eg VirtualBox (the version direct from Sun for best user experience) and install your XP software in that, if it will still do what you need it to do in a VM.

---

### Post by Cheesemill on 2010-01-02
If you have Windows 7 Professional or higher it comes with a built-in virtualized copy of XP making it able to run all XP programs.

---

