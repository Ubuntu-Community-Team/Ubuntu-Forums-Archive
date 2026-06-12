---
title: "partition/grub/multi boot help"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by jmcc2950 on 2009-12-10
Had Fedora 12 & win xp dual booting using grub in F12.  Wanted to try Ubuntu 8.04 so loaded on 3rd drive sdc. Now when I reboot only shows Ubuntu & XP to boot into F12 disappeared.  Can boot into rescue mode of F12 & looked at grub.conf but didn't see anything unusual.  I guess my question is what did Ubuntu overwrite in F12 & is there something similar in Ubuntu taht I could modify to boot F12 located on hd1 (sdb)?
   Thanks

---

### Post by louieb on 2009-12-10
Take a look at the setup [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280")

Put the results.txt file in your next post - it will help in figuring it out.

---

### Post by raymondh on 2009-12-10
> **jmcc2950 said:**
> Had Fedora 12 & win xp dual booting using grub in F12.  Wanted to try Ubuntu 8.04 so loaded on 3rd drive sdc. Now when I reboot only shows Ubuntu & XP to boot into F12 disappeared.  Can boot into rescue mode of F12 & looked at grub.conf but didn't see anything unusual.  I guess my question is what did Ubuntu overwrite in F12 & is there something similar in Ubuntu taht I could modify to boot F12 located on hd1 (sdb)?
   Thanks

When you installed hardy, GRUB was re-installed in the MBR of the 1st HD to boot in BIOS ..... unless you decided otherwise in step 7.  I don't know why it failed to pick-up the fedora install.

You may try to chainload F12 in Ubuntu's boot/grub/menu.lst.

In ubuntu and thru the Terminal ... 

```
cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```  
This creates a back-up of your current menu.lst should anything go wrong whilst you edit.

```
gksudo gedit /boot/grub/menu.lst
```
To edit the menu.lst

The gyst of it will be

title Fedora
root (hdx,y)
chainloader +1

where X is the HD and y is the partition in said HD.

EDIT : the bootinfoscript will be of great help.

Regards,

---

### Post by jmcc2950 on 2009-12-10
Thanks for the quick response, I did try to edit the menu.lst but I must of screwed up which partition to point to, I will mess around with that later.  However went back to F12 rescue & went into grub & repaired grub.conf, so now I have F12 & XP back.  Will try to add 3rd drive with Ubuntu later & try to mess around with F12 grub.conf to see if I can get all 3 OS's to work.  Thanks again for your help.

---

