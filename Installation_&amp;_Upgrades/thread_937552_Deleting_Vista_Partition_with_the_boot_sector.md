---
title: "Deleting Vista Partition with the *boot sector"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by djdarkside on 2008-10-04
Hi All,
I need help on safely removing Vista on my system.  The problem is Vista (/dev/sda2) owns the rights to my boot sector as you can see at the bottom with the output of my fdisk -l command.  Any help would be appreciated on how to move the boot sector to my Ubuntu partition (/dev/sda6) in a safe and clean matter.  


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6309fc9b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1328    10667128+   7  HPFS/NTFS
/dev/sda2   *        1329        7855    52428127+   7  HPFS/NTFS
/dev/sda3            7856       18674    86903617+   5  Extended
/dev/sda4           18675       19457     6289447+   b  W95 FAT32
/dev/sda5           18414       18674     2096482+  82  Linux swap / Solaris
/dev/sda6            7856       18413    84807072   83  Linux

---

### Post by tigerstripedcat on 2008-10-04
I'm not totally familiar with the particulars of vista, but I'm not sure why you need to "move" your boot sector.  With modern OSs as far as I know the OS will write to your MBR.  So if vista was installed last it would have overwrote your MBR.  You'll need to boot into ubuntu (with a live cd if necessary) and reinstall/resetup grub.  Grub will take hold of the MBR and give your boot options.

If are trying to completely remove vista, you should just be able to use something like gparted to remove your vista partitions.

Hopefully someone else will chime in, but I think this is how it would work.

---

### Post by iponeverything on 2008-10-04
> I'm not totally familiar with the particulars of vista, but I'm not sure why you need to "move" your boot sector. With modern OSs as far as I know the OS will write to your MBR. So if vista was installed last it would have overwrote your MBR. You'll need to boot into ubuntu (with a live cd if necessary) and reinstall/resetup grub. Grub will take hold of the MBR and give your boot options.

If are trying to completely remove vista, you should just be able to use something like gparted to remove your vista partitions.

Hopefully someone else will chime in, but I think this is how it would work. 

If you install grub it will overwrite your mbr and add Vista to your boot menu. It is easy to copy your boot sector anywhere you want, most people do this to just back it up -- in case need to restore it later.  I have not needed to restore my boot sector quite a long time, nor have heard of anyone having to it in a long time.. - for me it was 1993, kernel 0.99.14 on my amd 386/40 and MFM 80 Meg hard drive that would shake the desk.

---

### Post by djdarkside on 2008-10-04
Thank you for your reply tigerstripedcat, I might be over-thinking this prosess, I just want to remove Vista (which was installed first) safely without messing up the boot process of my drive.  I guess I just wanted some confirmation from some people before I used GParted to wipe the Vista partition. Thank's..

---

### Post by caljohnsmith on 2008-10-04
> ```
/dev/sda1 1 1328 10667128+ 7 HPFS/NTFS
/dev/sda2 [COLOR="Red"]*[/COLOR] 1329 7855 52428127+ 7 HPFS/NTFS
/dev/sda3 7856 18674 86903617+ 5 Extended
/dev/sda4 18675 19457 6289447+ b W95 FAT32
/dev/sda5 18414 18674 2096482+ 82 Linux swap / Solaris
/dev/sda6 7856 18413 84807072 83 Linux
```
The asterisk * next to sda2 above means that your Vista partition sda2 is marked as the "active" partition, or has its boot flag set, and only one partition on a HDD is supposed to be marked as active. As far as Grub is concerned, Grub can boot any of your OSes regardless of whether they are the active partition. But if you replace your MBR with a Windows boot loader, all a Windows boot loader does is try and boot whichever partition on the HDD is marked as active, which is your Vista partition right now. 

So the bottom line is you can easily delete the Vista partition and not worry that it currently is marked as the active partition. But make sure that you then mark one of your other partitions as active (i.e. set the boot flag on for the partition), because some BIOSes will refuse to boot a drive that doesn't have one partition marked as active. You could arbitrarily make sda1 active for example; when you are in gparted, just right-click the partition and choose "manage flags", and there you can set the boot flag on. Let me know how it goes or if you have more questions.

---

### Post by djdarkside on 2008-10-04
Thank you caljohnsmith, thats what I needed to here and I removed Vista in a safe manner.  I knew all this stuff about the flags I just wasn't sure what my hard drive would do if I removed the OS that was currently flagged.

---

