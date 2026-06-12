---
title: "Grub _"
date: 2005-03-20
forum: Installation &amp; Upgrades
---

### Post by Frayed on 2005-03-20
I have a strange problem with grub. I've seen other posts with a similar problem but there doesn't seem to be a clean solution.

I successfully installed Ubuntu, but when I boot my comp (Toshiba M30 Laptop), all I get is
```
GRUB _
```
and the cursor blinks. I thought i was screwed, so I popped in my winxppro disc to repair my mbr but I missed the "Press any key to boot from CD..." message and lo and behold, grub loaded with all the options.  So there is something that is skipped when I attempt to boot from CD. Needless to say, this isn't how I want to boot everytime.

Any suggestions?

---

### Post by Buffalo Soldier on 2005-03-20
Mind sharing the usual info of */boot/grub/menu.lst* file and the output of **sudo fdisk -l** command?

---

### Post by gnutux on 2005-03-20
I think when you can't boot from your HDD, (s)he can't use that command. Pretty obvious. Try getting a Live CD and then look into your hard drive like KNOPPIX or UltimateBootCD.

gnutux

---

### Post by Buffalo Soldier on 2005-03-20
[QUOTE=gnutux]I think when you can't boot from your HDD, (s)he can't use that command. Pretty obvious. Try getting a Live CD and then look into your hard drive like KNOPPIX or UltimateBootCD.

gnutux[/QUOTE]
 duhghghh!! My mistake.

---

### Post by Frayed on 2005-03-22
Actually I can boot, but it just requires me putting in a cd to boot from and then skipping the "Press any key to boot from cd..." option....after which, the grub menu appears.  I can get into both ubuntu and windows, it's just a pain to do so.

---

### Post by Frayed on 2005-03-22
Actually I can boot, but it just requires me putting in a cd to boot from and then skipping the "Press any key to boot from cd..." option
after which, the grub menu appears.  I can get into both ubuntu and windows, it's just a pain to do so.  This makes me think it's not a problem with menu.lst.

---

### Post by Frayed on 2005-03-22
Here's the relevant stuff:

#sudo fdisk -l
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        7785    42050137+   f  W95 Ext'd (LBA)
/dev/hda3            7786        9729    15615180   83  Linux
/dev/hda5            2551        3825    10241406    7  HPFS/NTFS
/dev/hda6            3826        7698    31109841    b  W95 FAT32
/dev/hda7            7699        7785      698796   82  Linux swap / Solaris

```
/boot/grub/menu.lst
```
title           Ubuntu, kernel 2.6.10-5-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel 2.6.10-4-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.10-4-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.10-4-386
savedefault
boot

title           Ubuntu, kernel 2.6.10-4-386 (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.10-4-386 root=/dev/hda3 ro single
initrd          /boot/initrd.img-2.6.10-4-386
savedefault
boot

title           Ubuntu, kernel memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by Buffalo Soldier on 2005-03-22
Sorry for the late reply. Was trying to get the full picture in my mind. Let me double check with on some item.

You said when you pop in your WinXP installation CD, the GRUB menu loads. Please correct me if I'm wrong.

Were you able to succesfully boot into WinXP and Ubuntu with this menu?

So far after reading your fdisk output and fstab file, I don't find anything wrong. But then again I could be missing something.

Hhmmm.. one last thing. After installing Ubuntu, did you change back your boot setting to boot to harddisk? Or is it still set to boot to CD? Usually this wouldn't create a problem, but we could give it a try.

---

### Post by Pse on 2005-03-22
I take your WindowsXP installation is on the first partition...
BTW, what HD do you have? Brand/model?

---

### Post by Frayed on 2005-03-22
> You said when you pop in your WinXP installation CD, the GRUB menu loads.
That's correct. The WinXP CD give me the option to boot from CD by pressing any key. But if I don't hit a key, I suppose it reverts to trying to boot from the HD. And this is when I actually see the GRUB boot menu. If I don't do this, I just get "GRUB _"; no error message, just that line.

Regarding changing back to booting from HD, I never changed it to boot from CD *permanently* anyhow. The bios allows me to press F12 when powering up to choose a different boot device. If I choose CD, that's when I can get to the GRUB menu (provided the WinXP install disc is in the drive), otherwise it just locks up.

My HD is:```
hda: TOSHIBA MK8025GAS, ATA DISK drive
```

---

### Post by Frayed on 2005-03-22
Hmmm, found this:> 
the problem is that grub can aonly address the first 2GB of a hdd so if the windows parition is > 2GB and at the front of the dsisk grub wont work

to fix make a /boot partition at the start of the drive

Is that what you were hinting at Pse?

---

### Post by CAPTAIN RON FL on 2005-03-22
I have a Toshiba Satallite M35X-S109  so I am watching this thread also.  The reason is I had trouble with warty doing the same thing on a new desktop I had. Took a long time to fix it. I had to wipe the drive clean and start all over. Check my other threads on it. I am almost bald now. :cry: 

I sure do not want to hose my new laptop. [-o< 

I know it has to do with grub and the boatloader they are using. I was hoping it would be clean up by now.

Thanks, Ron

---

### Post by Frayed on 2005-03-23
Issue resolved.  :-D 

Ok, since I had installed grub into my mbr during ubuntu's installation, I thought maybe I'd try creating a new boot partition and use that instead. So I used partition magic to create a new 50 mb partition at the beginning of the drive.
Long story short, I messed up grub completely. (Error 15). I probably could've messed around more and got it sorted out, but I'm impatient and I hadn't done much with ubuntu anyway. 

I just booted the ubuntu installation CD and reinstalled, HOWEVER, this time I did not install grub to the mbr, I installed it to my new 50mb partition....

and it works.

_**Summary**_
During installation you're asked if you want to install grub to the MBR: **Say NO**
Then choose a partition to install GRUB onto. Note that you'll have to set this partition up earlier in the installation. It helped having Partition Magic to make this partition beforehand, but I'm sure there's lot's of info out there on moving/resizing partitions.
That's all it took.

As an aside, I think the installation could be more helpful on that initial GRUB/MBR screen since it says, "If all operating systems installed are listed above, it should be safe to install GRUB to the MBR" (I'm paraphrasing).  Maybe it should note, "It's also perfectly safe to install to a partition elsewhere on your HD".

=====================
Here is my new HD partition layout:```
Disk /dev/hda: 79.9 GB, 79916820992 bytes
255 heads, 63 sectors/track, 9716 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               8        2550    20426616    7  HPFS/NTFS
/dev/hda2            2551        7785    42050137+   f  W95 Ext'd (LBA)
/dev/hda3            7786        9729    15615180   83  Linux
/dev/hda4   *           1           7       56196   83  Linux
/dev/hda5            2551        3825    10241406    7  HPFS/NTFS
/dev/hda6            3826        7698    31109841    b  W95 FAT32
/dev/hda7            7699        7785      698796   82  Linux swap / Solaris
```

And my new /boot/grub/menu.lst
```
title           Ubuntu, kernel 2.6.10-4-386
root            (hd0,3)
kernel          /vmlinuz-2.6.10-4-386 root=/dev/hda3 ro quiet splash
initrd          /initrd.img-2.6.10-4-386
savedefault
boot

title           Ubuntu, kernel 2.6.10-4-386 (recovery mode)
root            (hd0,3)
kernel          /vmlinuz-2.6.10-4-386 root=/dev/hda3 ro single
initrd          /initrd.img-2.6.10-4-386
savedefault
boot

title           Ubuntu, kernel memtest86+
root            (hd0,3)
kernel          /memtest86+.bin
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
chainloader     +1
```

Thanks for your thoughts...

---

