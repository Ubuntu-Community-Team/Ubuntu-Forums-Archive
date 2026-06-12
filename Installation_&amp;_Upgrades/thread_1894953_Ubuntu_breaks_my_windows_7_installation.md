---
title: "Ubuntu breaks my windows 7 installation"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by peyu on 2011-12-13
Hi everybody, I don't know if it's the right place to post so please move it to the correct section if it's not.
I have an ubuntu 11.10 installed in dual boot with windows 7 home premium.
The partitions are the following:

```
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    61442047    30617600    7  HPFS/NTFS/exFAT
/dev/sda3        61444094   625141759   281848833    5  Étendue
/dev/sda5        61444096    80973823     9764864   83  Linux
/dev/sda6        80975872    84879359     1951744   82  partition d'échange Linux / Solaris
/dev/sda7        84881408   625141759   270130176   83  Linux

```

The procedure was: first I deleted all the partitions, then I installed Win7 in a NTFS partition of 30Gb (sda2), Win7 asked me to create sda1 (I don't know why), and then, I installed Ubuntu in an extended partition, creating sda5 for /, sda6 for swap, sda7 for /home.
Grub is installed in the MBR of sda

Everything was working well, Grub recognized Win7, and I could launch both OS. But I discovered that if I tried to access /dev/sda2 from ubuntu, then I can not boot win7 in the next boot: I have the following error (in the win7 boot, after choosing win7 loader in grub): "the boot selection failed because a required device is inaccessible". And everytime I had this error, I have to restore sda2 with dd or reinstall win7.
So I just though that I should not access sda2 from ubuntu. But from time to time, I don't know why, I have this problem, and I can only resolve it reinstalling win7 or restoring partition with dd. I suppose that ubuntu access in some way sda2.

Questions:
- What's happening ?
- Is there any way to forbid ubuntu to access a partition ? (in theory, if you don't mount it, it should not access it, but it seems that it's not the case here)

Thanks a lot if you have any clue, because I was googling around and I haven't found anything...

---

### Post by dandnsmith on 2011-12-14
The extra partition (sda1) is created automatically by the Win7 install for it's own boot partition (yes, I was somewhat taken aback when this happened to me also).
I haven't had this corruption problem, so there may be something in the detail (win7, disk type ...) which is the root cause.
I suggest you look in /etc/fstab to see what is getting mounted, and comment out the line for sda2 if it is there (you may need to recognise it by UUID, in which case *blkid* can give you a list)

---

### Post by Mark Phelps on 2011-12-14
My guess would be that sda2 is your Win7 OS partition (since sda1 is the boot partition).  If your "access" is only reading files, that should not be causing a problem.

But, if your "access" includes writing or updating files -- then STOP doing that.  As you have discovered the hard way, tampering with the contents of a Win7 OS partition from outside runs the risk of filesystem corruption.

If there is stuff in your Win7 OS partition that you feel you need to change from Ubuntu, you would do better copying or moving those files to Ubuntu, or to a shared DATA NTFS partition.

---

### Post by peyu on 2011-12-14
Thanks for your replies.
Well, I never access sda1 or sda2 partition, and I don't have any information under win7 that I need under ubuntu (i'm using win7 only to play games ;) )

This is my fstab file:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=fee42613-a030-4566-a5ef-d92ad5b6c0ce /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=c9dccf43-ece8-40a8-b285-9fe6544c5e12 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
#UUID=4fba0c45-da71-495c-bc9c-525bb51b2a09 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

I don't understand it, since I never access it from ubuntu and either sda1 or sda2 are not included in the fstab.
Any idea?

Just for illustration, I restore yesterday night sda2 because win7 was not able to boot. Today, I turn on ubuntu and in nautilus I can't see sda2 partition (even if I don't mount it, it appears in nautilus), so I guess that win7 will not be available again...

EDIT: Actually, it's not available, I have to restore sda2 again with dd.

---

### Post by Mark Phelps on 2011-12-15
You said > **peyu said:**
> Thanks for your replies.
Well, I never access sda1 or sda2 partition, 

But, you earlier said > But I discovered that if I tried to access /dev/sda2 from ubuntu, then I can not boot win7 in the next boot:

So, I was responding to your earlier statement that clearly said you tried to access Win7 from inside Ubuntu.

But, there is nothing in your fstab indicating problems -- so the partitions are not being mounted automatically.

Is the problem only IF you access Win7 from inside Ubuntu? OR does the problem happen every time you access Ubuntu and then, later, try to boot into Win7?

---

### Post by peyu on 2011-12-15
Yes, you're right, I've tried 3 weeks ago to access from nautilus, which by the way didn't work.
Since yesterday, I want to try only booting in windows to see if it's the grub booting which is faulty or if it's windows by itself.
The problem is that I don't know what is the origin of the problem, because it happened yesterday and the day before, but it was running ok all the week before...

It seems that it's everytime ubuntu access the partition, because it happened also when I did the dd backup copy of sda2 2 weeks ago (and by the way it happened also with partimage).

So my opinion is that everytime ubuntu access sda2 (even if it's just reading), win7 can not boot anymore. I don't care about this behaviour since I will not try to access it with nautilus or other program, but it seems that ubuntu is accessing it by itself... I checked in the dmesg log and I haven't found anything, I will look further in other log files.
I was also thinking about trying to make a dd copy from a livecd, just to see if I have the same problem...

---

### Post by Mark Phelps on 2011-12-15
> **peyu said:**
> It seems that it's everytime ubuntu access the partition, because it happened also when I did the dd backup copy of sda2 2 weeks ago (and by the way it happened also with partimage).
When you "access" the partition through Nautilus, or use the Unity launcher "home" button to get a list of partitions and click on them, the default is to open that partition read-write -- even if all you want to do is browse its contents.

I had so much trouble with this in the past that modifed my fstab to mount the Windows partition read-only, and even then, from time to time, I would get a forced CHKDSK when I rebooted into Windows.

> So my opinion is that everytime ubuntu access sda2 (even if it's just reading), win7 can not boot anymore. I don't care about this behaviour since I will not try to access it with nautilus or other program, but it seems that ubuntu is accessing it by itself...

In principle, accessing Window partitions read-only should not present any problems, but it looks like something else is happening in your case.

What I would suggest, to see if this helps in any way, is that the next time you are in Windows, run a CHKDSK on each of the partitions.  You will have to reboot to do that on the OS partition.

With any luck, you won't have problems after the chkdsks complete -- but look at their results to see if there are any bad blocks found in the process.

---

### Post by peyu on 2011-12-18
Hi everybody, thank you so much for your support.

Let's resume what I did these days... first, I checked 2 times under windows the partition with chkdsk, everything was fine.
Yesterday, I booted ubuntu, the sda2 partition was still visible in nautilus (but I didn't mounted it), but today, it was not (I didn't boot windows between yesterday and today, and i didn't reboot ubuntu either).

I ran blkid and here the result:
```
/dev/sda1: UUID="ECE0533FE0530F68" TYPE="ntfs" 
/dev/sda5: UUID="fee42613-a030-4566-a5ef-d92ad5b6c0ce" TYPE="ext4" 
/dev/sda7: UUID="c9dccf43-ece8-40a8-b285-9fe6544c5e12" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="b9aadca6-5ffa-434e-ba02-a4be1def1341" TYPE="swap" 

```

blkid was not able to "see" the sda2 partition. I tried to use gnome-disk-utility but sda2 was shown as an unknown partition (sda1 as an ntfs partition).

So I tried ntfsfix to fix sda2, here was the result:
```
Mounting volume... ntfs_mst_post_read_fixup: magic: 0xf63ea6d8  size: 1024  usa_ofs: 12339  usa_count: 21347: Invalid argument
ntfs_mst_post_read_fixup: magic: 0x9af24613  size: 1024  usa_ofs: 2877  usa_count: 53601: Invalid argument
ntfs_mst_post_read_fixup: magic: 0xed81bcdc  size: 1024  usa_ofs: 36530  usa_count: 9115: Invalid argument
ntfs_mst_post_read_fixup: magic: 0x5977e1d7  size: 1024  usa_ofs: 19405  usa_count: 61425: Invalid argument
$MFTMirr does not match $MFT (record 0).
FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... ntfs_mst_post_read_fixup: magic: 0xf63ea6d8  size: 1024  usa_ofs: 12339  usa_count: 21347: Invalid argument
ntfs_mst_post_read_fixup: magic: 0x9af24613  size: 1024  usa_ofs: 2877  usa_count: 53601: Invalid argument
ntfs_mst_post_read_fixup: magic: 0xed81bcdc  size: 1024  usa_ofs: 36530  usa_count: 9115: Invalid argument
ntfs_mst_post_read_fixup: magic: 0x5977e1d7  size: 1024  usa_ofs: 19405  usa_count: 61425: Invalid argument
OK
Comparing $MFTMirr to $MFT... FAILED
Correcting differences in $MFTMirr record 0...OK
Correcting differences in $MFTMirr record 1...OK
Correcting differences in $MFTMirr record 2...OK
FAILED
$MFTMirr error: Invalid mft record for $Volume.

```
After that, even if it failed, it seemed to be an improvement since gnome-disk-utility and nautilus recognized sda2 as a ntfs partition, but windows was still not able to boot.

After this operation, blkid gave me this:
```
/dev/sda1: UUID="ECE0533FE0530F68" TYPE="ntfs" 
/dev/sda5: UUID="fee42613-a030-4566-a5ef-d92ad5b6c0ce" TYPE="ext4" 
/dev/sda7: UUID="c9dccf43-ece8-40a8-b285-9fe6544c5e12" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="b9aadca6-5ffa-434e-ba02-a4be1def1341" TYPE="swap" 
/dev/sda2: UUID="FA78B8B778B8744B" TYPE="ntfs" 

```

Since I was not able to boot windows, I restore sda2 using dd.
After this operation, the result of ntfsfix is:
```
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
NTFS volume version is 3.1.
NTFS partition /dev/sda2 was processed successfully.

```
And blkid:
```
/dev/sda1: UUID="ECE0533FE0530F68" TYPE="ntfs" 
/dev/sda2: UUID="FA78B8B778B8744B" TYPE="ntfs" 
/dev/sda5: UUID="fee42613-a030-4566-a5ef-d92ad5b6c0ce" TYPE="ext4" 
/dev/sda7: UUID="c9dccf43-ece8-40a8-b285-9fe6544c5e12" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="2c5a91c4-9f9a-4414-a89b-e3678ca18600" TYPE="swap" 

```

I don't understand why the second blkid attempt gave sda2 at the end and the third one showed sda2 in the right order.
So it seems that ubuntu is accessing sda2 somehow and mess up the partition.

Do you have any idea?

---

