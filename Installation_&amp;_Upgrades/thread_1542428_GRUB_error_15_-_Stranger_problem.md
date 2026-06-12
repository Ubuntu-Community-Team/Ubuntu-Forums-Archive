---
title: "GRUB error 15 - Stranger problem"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by Grozzy on 2010-07-30
Hi!

I was trying to remove a Kubuntu usplash image from my dads laptop with "StartUp manager" when I accidently clicked "Restore to default settings". Now I get a "Error 15 blabla" after selecting what to boot from GRUB.

/boot is on a separated partition. "find /grub/stage1" return hd(0,4) so i ran "root (hd0,4)" and "setup (hd0)". The thing is that GRUB is set up fine and it works as it should (the list of OS'es shows up etc..), but when i choose something to boot it gives me the error 15.

I think it links something wrong but I don't know really what. Please ask for what "the output of..." is and thanks in advance for helping!

---

### Post by Rubi1200 on 2010-07-30
I think it is likely you will need to reinstall GRUB2 (I am assuming you are using Karmic or Lucid).
 
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling)
 
But, post the output of this so we can see for sure:
 
```
 
sudo fdisk -l

```

---

### Post by Grozzy on 2010-07-30
I've tried to reinstall GRUB several times now, it seems like everything is fine. Some other guy said that it was wrong with the menu items, and most likely it's the problem. But I don't know how to fix that.

The output of "sudo fdisk -l":

```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9896d864

   Device     Boot       Start                   End              Blocks            Id         System
/dev/sda1     *               1               18346       147364213+            7         HPFS/NTFS
/dev/sda2               37594               38913        10599424               7         HPFS/NTFS
/dev/sda3               18347               37593       154601527+            5         Extended
/dev/sda5               18347               18537          1534176             83         Linux
/dev/sda6               18538               18792          2048256             82         Linux swap
/dev/sda7               18793               27741        71882811             83         Linux
/dev/sda8               27742               37593        79136158+           83         Linux

Partition table entries are not in disk order

```

---

### Post by Rubi1200 on 2010-07-31
I am not sure why you would be having issues reinstalling GRUB, but just to make sure please boot the laptop with a LiveCD, choosing to try in live mode not install.
 
Then, click on the link at the bottom of my post and follow the instructions there.
 
Post the results back here please and we will see what can be done to sort this out.

---

### Post by Grozzy on 2010-07-31
Okey, I managed to fix the problem by reinstall Ubuntu and GRUB :)
I found that it was the best solution because the computer was mixed with some Kubuntu and a pretty much messed settings.. I also merged the partitions into just root and swap. Ofcourse I took a backup of the home folder.

Thank you anyway **Rubi1200 **for trying to help me! :)

---

