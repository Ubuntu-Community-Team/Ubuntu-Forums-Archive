---
title: "WIndows to 8.04 Hard Drive Boot Issue"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by mary900 on 2008-10-30
Just made the leap from xp to 8.04. I have 2 hard drives installed, one for data the other for OS. Every time I boot, I have to go into the bios and re-select the correct hard drive to boot from. 

I make the selection to save, and computer boots. Shut down, same thing happens again. What am I missing??

Any insight will be appreciated.

---

### Post by martrn on 2008-10-30
Are you sure you have to enter the BIOS to select the correct hard disk to boot from.  Usually when entering the BIOS you have to hold down the <DEL> key or hold down the <F*> or <F6> key or simular.  Grub can look like the BIOS update sometimes.  The BIOS will load everytime a computer is started regardless of you holding down any screens although normaly you will not have to enter it.  If your BIOS is not remembering your settings when you save and exit the BIOS enter program then you may have a flat CMOS batter in your motherboard.

If you motherboard will not boot any disk other than the first hard disk in your computer system then you may need to install grub to the other hard disk on the computer system.  Goto [https://help.ubuntu.com/community/GrubHowto]("https://help.ubuntu.com/community/GrubHowto") to find out how to do this.  Normally you don't need to do this you can play around with the BIOS to make sure it boots the correct disk.

Sometimes it can be difficult to work out whats going on, the BIOS will bootstrap load the MBR on the hard disk specified in the BIOS, but the MBR could be installed to either the first hard disk or the second hard disk in your computer system.  The MBR on the disk the BIOS points to should contain grub, which will boot stage2 of grub if you need to boot ubuntu.

---

### Post by mary900 on 2008-10-30
I have to hold down the DEL key. Once in the Bios I have to change the order of the hard disk boot drive, press F10 to save, and select [OK]. The drive I change to is the drive with Ubuntu loaded. The other drive has no OS; contains only my data files. 

Thanks for the link. I will give it a try. :)

---

### Post by martrn on 2008-10-30
Grub is only a boot strap loader.  An operating system would load in several stages, the first part would be to load, the BIOS, which would load the first part of grub.  The part contained in the MBR.   The second stage of grub would be on a partition where your operating system is stored which is the part where your kernel (or operating system) is stored.

The first part of grub, which is the boot strap will only contain instructions to load the second part.   It wouldn't matter which disk (or MBR) the first part of grub would be placed upon as long as the BIOS is pointing to it.

As before you have two options:

1.  Get the BIOS to point to the MBR with grub on.  Check your motherboard manual for an howto.
2.  Put grub on the MBR of the disk that the BIOS is pointing toward.  See [https://help.ubuntu.com/community/GrubHowto]("https://help.ubuntu.com/community/GrubHowto") for the how to on that.

---

### Post by mary900 on 2008-10-30
Thanks for the info martrn. I will try the instructions of the link you provided. I'll do that tomorrow night...this has wore me out today!!!

---

### Post by mary900 on 2008-10-31
After reading the link you provided, my kopt=root has the following setting:

# kopt=root=UUID=138a7cfd-6cb7-47c9-89e8-b903740b8a59 ro

I'm thinking it should be: "kopt=root=/dev/sdb1 ro" because when I "df /" I get sdb1. Will I crash anything by changing the value of my current kopt=root line?

Once again, thanks.

---

### Post by caljohnsmith on 2008-10-31
Mary900, are you sure you can't go into BIOS and simply change the boot order permanently so you don't have to change it each time on start up? If you install Grub to the MBR (Master Boot Record) of your data drive, then your two drives become dependent on each other for booting, meaning that if you have problems with either of them you may not be able to boot Ubuntu. It is much more ideal to boot directly from the Ubuntu drive on start up like you are doing now, but you should be able to make the boot order change permanent in BIOS so you don't have to do it manually every time on start up. :)

If it's not too much trouble, it would help if you could also post:
```
sudo fdisk -lu
```
You can do that from a terminal (applications > accessories > terminal).

---

### Post by mary900 on 2008-10-31
Something odd I just discovered. If I just "restart" computer the Bios doesn't retain settings that I just changed in the Bios to bring up the computer. However, if I do "Shut Down" and re-boot, the computer boots from the correct drive.

The 40.9 GB drive is just my data drive.
 
Disk /dev/sda: 40.9 GB, 40982151168 bytes
255 heads, 63 sectors/track, 4982 cylinders, total 80043264 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xea1aa9c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    78108029    39053983+   7  HPFS/NTFS

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x96b196b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   237103334   118551636   83  Linux
/dev/sdb2       237103335   240107489     1502077+   5  Extended
/dev/sdb5       237103398   240107489     1502046   82  Linux swap / Solaris

---

### Post by caljohnsmith on 2008-10-31
One thing I notice is that none of your partitions on your sdb Ubuntu drive are marked as bootable, and some BIOSes will refuse to boot a drive that doesn't have one partition marked as bootable. That's not quite your case since you can obviously boot the Ubuntu, but I think it would be wise to at least mark one partition active in case that has any effect on how your BIOS treats the boot order on start up. In other words, it can only help, not hurt. 

If that sounds OK with you, then just do:
```
sudo fdisk /dev/sdb
```
Press "a", "1", then "w". fdisk should quit, and then do:
```
sudo fdisk -l
```
And make sure sdb1 has an asterisk * next to it showing that it is bootable. See if that makes any difference about booting the Ubuntu drive when doing a shutdown vs. restart. Let me know how it goes.

---

### Post by mary900 on 2008-10-31
caljohnsmith -- I now have * beside sdb1 but now I get "cannot find operating system" error if I just do a restart. Before I was getting "cannot find array" error. Still boots fine from a shut down.

But your method cured another ill I was having (either that or the stars are aligned correctly)... I could not get correct monitor or resolution to show up. Now, presto, I have correct monitor and all corresponding screen resolutions -- go figure!!

Well...I spoke too soon...did another shut down and got the same monitor and resolution problem back. I'm wondering if I should re-install ubuntu...??

---

### Post by caljohnsmith on 2008-10-31
OK, I think at this point it would be helpful to clarify which drive(s) have Grub in their MBR (Master Boot Record), so please post the following:
```
sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump
```

---

### Post by mary900 on 2008-10-31
Thanks for your patience!

~$ sudo dd if=/dev/sda count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 

~$ sudo dd if=/dev/sdb count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
Missing operating system

~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 8100                                   
0000002

~$ sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 0000                                   
0000002

---

### Post by caljohnsmith on 2008-10-31
OK, that definitely clears things up quite a bit; your sda drive has Grub in the MBR, while your sdb drive still has a Windows MBR that is probably left over from some other time. That means you must be booting the sda drive on start up to get Grub. The disadvantage of this is that your two drives are dependent on each other for booting; if anything happens to either drive, you most likely won't be able to boot either Windows or Ubuntu. A more ideal solution is if we install Grub to the MBR of your sdb drive, and if you can successfully set your BIOS to boot your sdb drive, then both drives will be independent; for instance if your Ubuntu install/HDD has any problems, you will still be able to boot into Windows (assuming we restore the Windows MBR to sda of course). 

If that sounds OK with you, then first post the output of:
```
sudo grub
grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
Reboot, set your BIOS to boot the sdb drive, and if you successfully boot the sdb drive, you will get the Grub menu; but booting any of the OSes should give you a Grub error 17 (or other grub error). So to temporarily fix your Grub menu, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. That should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent. See if you can get this far and we can work from here. :)

---

### Post by mary900 on 2008-10-31
I don't have windows installed on either drive. I reformatted the drive that did have xp on it with ubuntu and left my data drive as-is.

I followed your instructions....the only way I could do it was by the restart method. I changed (hd1,0) to (hd0,0). Here's the output of code:

sudo grub 

[ Minimal BASH-like line editing is supported.   For

         the   first   word,  TAB  lists  possible  command

         completions.  Anywhere else TAB lists the possible

         completions of a device/filename. ]

grub> root (hd1,0)

grub> setup (hd1)

 Checking if "/boot/grub/stage1" exists... yes

 Checking if "/boot/grub/stage2" exists... yes

 Checking if "/boot/grub/e2fs_stage1_5" exists... yes

 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.

succeeded

 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,0)/boot/grub/stage2

/boot/grub/menu.lst"... succeeded

Done.

grub>quit

---

### Post by caljohnsmith on 2008-10-31
> **mary900 said:**
> 
I followed your instructions....the only way I could do it was by the restart method. I changed (hd1,0) to (hd0,0). 
OK, great, since you had to change the Ubuntu entry to use (hd0,0), that means you successfully booted from your sdb drive. But if you are still getting inconsistent booting bahavior between doing a restart vs. a shutdown, that's not something we can correct with Grub; I think that sounds entirely like a BIOS issue. Maybe if you check the manufacturer's website for you motherboard, you could get a BIOS update that might cure the problem. Or it still could simply be one of your BIOS settings, I don't know. 

But as long as you have Ubuntu booting from the sdb drive on start up, you might as well go ahead and change your Grub's menu.lst so you don't have to use the menu editing technique every time on start up:
```
gksudo gedit /boot/grub/menu.lst 
```
That should bring up your menu.lst, so just change all the Ubuntu entries to use (hd0,0) rather than (hd1,0). Also, to prevent problems when you get kernel upgrades, you would want to change the "# groot=(hd1,0)" line to "# groot=(hd0,0)". Sorry I can't help with your restart vs. shutdown issue, but let me know if you find a solution. :)

---

### Post by mary900 on 2008-10-31
well...now when I do a restart and get the array error, it actually goes ahead and boots. 

Now, I'm back to trying to get my monitor and it's corresponding resolutions on track.

Thanks for all of your help, it is much appreciated!!

---

