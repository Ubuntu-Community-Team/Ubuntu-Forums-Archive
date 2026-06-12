---
title: "grub rescue  error :no such partition"
date: 2011-09-09
forum: Installation &amp; Upgrades
---

### Post by skiet078 on 2011-09-09
hi i have installed windows 7 & ubuntu 
But ubuntu is not working properly

I delete the ubuntu partition 
then I m getting this error

grub rescue  error :no such partition

I tried to boot from cd 
It doesnot boot from cd

Pls  guide me 
I shall be thankful to u

---

### Post by raja.genupula on 2011-09-09
[http://superuser.com/questions/74017/why-do-i-get-a-grub-error-after-deleting-the-linux-partition](http://superuser.com/questions/74017/why-do-i-get-a-grub-error-after-deleting-the-linux-partition)



go with this, its gonna help you to solve this issue

---

### Post by raja.genupula on 2011-09-09
my suggestion is , if you have any problem with your ubuntu just dont try to remove it . ask here . we are here to solve(i mean experts not me , may be i can solve if i know ) . removing ubuntu is gonna give a new problem to you . so please never do this again .

---

### Post by coffeecat on 2011-09-09
> **skiet078 said:**
> 
I tried to boot from cd 
It doesnot boot from cd


You are going to have to be able to boot from a CD of some sort to be able to fix this. You need to reinstall the Windows mbr. At the moment you have grub installed to the mbr and it is looking for the rest of itself in the Ubuntu root partition - which you deleted.

Method 1:

Boot from a Windows 7 repair disc or Mirosoft Windows 7 installation DVD. An OEM manufacturers restore disc will not do. Go to the command prompt and run:

```
bootrec /FixMbr
```

You did create a Windows 7 repair disc from within Windows while you were still able to boot into it, didn't you? If you didn't and you need one and you have access to another working Windows 7 system, then follow this guide to create one:

[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

Unfortunately, you need Windows and Silverlight to be able to watch that.

Method 2:

Boot from an Ubuntu live CD and make sure you are connected to the internet. Try one of these three methods:

[http://ubuntuforums.org/showpost.php?p=8950739&postcount=7](http://ubuntuforums.org/showpost.php?p=8950739&postcount=7)

The lilo method works well, but check that your boot drive is sda before you run that code.

---

