---
title: "Replace Windows 8 with Ubuntu?"
date: 2013-01-18
forum: Installation &amp; Upgrades
---

### Post by Justplainwyrd on 2013-01-18
Searched the forums, but haven't found this. I am considering buying an HP Pavillion G6-2240nr Notebook at CostCo, pre-installed with Windows 8.

I would like to erase Windows 8, and install Ubuntu instead. I assumed it would be no problem installing with the Ubuntu DVD, but now I see all these posts about Windows 8 problems. They seem to only talk about dual booting problems, but I don't want to assume.

Should I expect problems? Or will I be given the option to simply "Replace Windows 8 with Ubuntu"?

Thanks,
Mike

---

### Post by darkod on 2013-01-18
There shouldn't be any problems. But I would do two things before starting to install (even better, check if you can do this before buying it if possible):

1. Go into BIOS and disable Secure Boot, if enabled.
2. If you can select the boot mode between UEFI and Legacy, set it to Legacy only.

Much better.

Also, it will probably come installed on a gpt table. Make a new msdos table first from live mode, and then start the install. You can use gpt if you prefer, but in that case you will need to make a small bios_grub partition. I think the installer can create it for you, not sure. I always create it myself.

---

### Post by Justplainwyrd on 2013-01-19
Your suggestions helped, thanks!

---

### Post by Thee on 2013-01-19
I would suggest that, if you are buying a new laptop and planning to install Ubuntu on it without Windows, then buy a laptop without Windows to begin with. That way you will save some money by not paying for Windows 8 license.

---

### Post by Sachil on 2013-04-07
Darko,

Kindly explain in layman's terms what you mean the following as well as how to make an msdos table.

 *"Also, it will probably come installed on a gpt table. Make a new msdos  table first from live mode, and then start the install. You can use gpt  if you prefer, but in that case you will need to make a small bios_grub  partition"*

Thanks!

---

### Post by oldfred on 2013-04-07
If it is a new computer I suggest staying with gpt. It has some improvements over BIOS, but is newer and not as well known. Windows will only boot from gpt with UEFI. So I would leave space or leave the efi partition at the beginning of the drive as it is difficult to add that later if you do want to convert to UEFI boot.

Ubuntu will boot from gpt drives in BIOS or UEFI mode. I have been using gpt for a couple of years with BIOS and once configured have not noticed any difference. You have to use gpt if a drive is over 2TB and it really is recommended for SSDs unless you are booting Windows and do not have UEFI.

       GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)


 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

If totally erasing drive, it belive you can just repartition with gparted. The default is MBR(msdos) partitioning. Windows does not erase backup gpt partition table (one of its advantages) and then you need fix parts to repair it.

---

### Post by darkod on 2013-04-08
As oldfred mentioned, you have plenty of options especially if not planning to dual boot.

If you want to dual boot (now or in future), using gpt table will limit you to using uefi boot, since windows can work on gpt only with uefi. But uefi dual boot is still much more complicated than legacy dual boot, which is easier to do.
But you can do legacy dual boot on single disk only with msdos table.

If you plan to install only ubuntu, you can make the disk with gpt table and still use legacy boot if that's easier for you. You only have to make sure you create the small bios_grub partition with no filesystem. Grub2 needs it to install correctly.

As for writing new tables, you can do it in terminal very fast, for example if the disk is /dev/sda you do:
```
sudo parted /dev/sda
mklabel msdos/gpt
quit
```

That's it, that will create new blank msdos or gpt table, depending what you use.

If you prefer GUI tools like Gparted, in the menu there is option Create Partition Table which usually by default is msdos. For gpt you need to open the Advanced options and select another type of table. Then click the green button to execute the change at the end.

---

