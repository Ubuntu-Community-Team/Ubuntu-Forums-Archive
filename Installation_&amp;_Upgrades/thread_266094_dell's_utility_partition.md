---
title: "dell's utility partition"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by hvaughn on 2006-09-26
ok, i thinked i've figured out (to the best of my ability) what i've done wrong. i installed ubuntu and can get it to run. that is, only if i boot to the utility partition. evidently, dell's come with a utility partition and i think ubuntu has installed the boot record on this "utility partition" instead of the boot record on the hard drive (mbr). so when the system boots up, it doesn't see a boot record. do this make sense? i hope so, b/c i'm not sure if i'm explaining this properly. 

is there any way for me to either reinstall ubuntu and not have the boot record put on the utility partition or get rid of the utility partition??? also, are there any risks that deal with removing the utility partition (if i need to do this)???

thanks

---

### Post by whizbaby on 2006-09-26
If you didn't run it for long (seems like) just reinstall and erase the babylon-dell thingy from your hard drive during partitioning (anyway, I believe you got a dell cd with your computer so that you could reinstall it if you ever want to).

---

### Post by themusicwave on 2006-09-26
I don't know much about the boot partition stuff, but I also installed Ubuntu on a dell.

Dell ships with a few partitions, one is a backup and there are some small ones that I couldn't figure out the use of.

I simply wiped them all and everything on my laptop skill works.  The only thing I lost was the ability to use the "Media Direct" button.  So my guess is the smaller partitions enable that button.

I would suggest leaving the little dell partitions alone if you want that button to contiue working.

I hope this helps.

---

### Post by hvaughn on 2006-09-26
i replaced the hard drive with a new hard drive and have installed twice, erasing the drive both times. same results both times. would it be possible that the utility partition is somewhere other than the new hard drive i installed???

---

### Post by confused57 on 2006-09-27
I left a reply in your other thread which may help.
[http://www.ubuntuforums.org/showthread.php?t=265319](http://www.ubuntuforums.org/showthread.php?t=265319)

Here are  my Dell partitions:

> Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1           4       32098+   6  FAT16
/dev/hdb2   *           5       14589   117154012+   7  HPFS/NTFS

The Dell utility is on partition #1 (hdb1), so I think when you select to boot to it from the "Boot Menu"(F12?)...your system is booting into the first partition of your hard drive, which is where Ubuntu is installed...therefore it boots Ubuntu.  Do you see an option to enter the grub menu, e.g. press "esc" to enter grub...or does it boot directly to Ubuntu when you press the key to boot the Dell utility?
   You probably don't have a utility partition, but Dell bios has the option to boot into it for system troubleshooting, etc...

---

### Post by hvaughn on 2006-09-27
yes, i can esc into the grub menu. it gives me three options.
two are "kernel"s. one is a safe mode, i think. the third option is a memtest?
is there something that i can do from here to fix my problem?

---

### Post by confused57 on 2006-09-27
> **hvaughn said:**
> yes, i can esc into the grub menu. it gives me three options.
two are "kernel"s. one is a safe mode, i think. the third option is a memtest?
is there something that i can do from here to fix my problem?
Boot into Ubuntu, using the method you found to do so, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
The -l is a small "L".

You might want to post the output of:
```
cat /boot/grub/menu.lst
```
menu.lst is short for menu.list, not menu.first.

Also, did you happen to checkout the reply I gave in your other thread about checking in your bios?  Please ask if you don't quite understand anything.  You won't hurt anything just entering the bios setup, just be careful what settings you change...if nothing else, enter setup and familiarize yourself with the bios on your computer.  Pressing "Esc" should exit you from bios, just be sure to exit without saving changes...if you do change something(use discretion), write down what change(s) you made, so you can go back into bios and change back to your original settings, if you need to.

---

### Post by hvaughn on 2006-09-28
i went into the bios, and have all drive's off with the exception of the primary drive. it is recognizing my new hard drive.

when i try the "sudo fdisk l" command i get:
disk /dev/hda: 250.0gb, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
...

  device   boot    start  end blocks id system
/dev/hda1   *        1 30308  243448978+   83  linux
/dev/hda2         30309 30401   747022+     5  extended
/dev/hda5         30309 30401   746991     82  linux swap / solaris

when i enter "cat /boot/grub/menu.lst" i get:

# updatedefaultentry=false

## ## end default options ##

title  ubuntu, kernel 2.6.15-23-386
root   (hd0,0)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-386
savedefault
boot

title  ubuntu, kernel 2.6.15-23-386 (recovery mode)
root   (hd0,0)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd /boot/initrd.img-2.6.15-23-386
savedefault
boot

title  ubuntu, memtest86+
root   (hd0,0)
kernel /boot/memtest86+.bin
boot

### end debian automagic kernels list

----------------------------------------------------------------
also, if i go into the boot list and pick my hard drive. i get a boot record not found error message. just don't get it....

---

### Post by confused57 on 2006-09-28
Your output from sudo fdisk -l and /boot/grub/menu.lst look OK & should boot...I'm not sure what's going on with your system.

You could try reinstalling grub to the mbr, using the Dapper live cd:

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Hopefully, someone else will see your thread who might have another suggestion to try.

Edit: Since it's a new hard drive, is the jumper setting on the hard drive set to "master" or "cable select"?...most new hard drives are set to "cable select" by default.  Probably not the problem, just a thought...

---

### Post by hvaughn on 2006-09-28
yes i don't get it either. just my luck, i guess. thank you for your help

---

### Post by confused57 on 2006-09-28
You might want to try reinstalling Ubuntu(see you've already tried that), again selecting use entire disk...if reinstalling grub to mbr doesn't help.

Make sure your hard drive jumper is set to "master" or "cable select" and that the IDE cable is inserted securely &  correctly.

If all this fails & you can't find a solution to boot Ubuntu other than booting into the utility option and don't mind booting this way...you might want to try installing grub to the root partition using the live cd, you'd enter setup (hd0,0) rather than setup (hd0), as instructed in the link I gave you...if this works, you at least have the option to boot into recovery mode or memtest and newer kernels will be added to the grub menu that you can boot into, it's your option & may or may not work.  Wish I could help you more...good luck.

---

### Post by hvaughn on 2006-09-30
no luck with that other. hey, at least i can boot using the "utility partition". 
thanks again for you help

---

