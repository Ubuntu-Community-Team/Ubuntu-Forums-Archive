---
title: "Grub.cfg Windows Chainloader Help Needed"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by gwilson on 2012-02-09
I'm usually pretty good at sorting out grub.cfg issues, but I'm stumped here. I have a multi-boot system with two hard drives. I boot from the first hard drive (sda) and have installed grub there. When I run update-grub, it gives me the two Windows entries pasted below. When I select XP from the grub menu, it loads properly. When I select Win7 from the grub menu, it also starts XP. As you can see, XP is on the first partition of sda, and Win7 is on the first partition of sdb. 

Can anyone suggest a text correction that will get things running without changing anything else (such as which hard drive I boot from)?

Thanks for your help!

Grub.cfg text:

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 16B815A0B8158003
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sdb1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd1,msdos1)'
	search --no-floppy --fs-uuid --set=root 16B815A0B8158003
	chainloader +1

---

### Post by oldfred on 2012-02-09
Normally Windows sees other Windows installs and moves all boot files to the first bootable partition. So does your install of 7 have all of its boot files?

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Then the NTFS partition boot sector - PBR has to have the correct NTFS boot signature.

You may just need to run Windows fixes to each Windows install separately to make each Windows independent. 
To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Just noted:
Your search line has the same UUID.
```
search --no-floppy --fs-uuid --set=root 16B815A0B8158003
```
The search overrides the set root, so UUID is more important.

---

### Post by gwilson on 2012-02-09
Thanks for responding, OLDFRED. I'll look into these things. I can tell you that I installed XP onto its drive as the solo hard drive in the system as a normal install. I did the same with Win7. It's been working for a couple of years that way with no problems until the other day when Grub-pc was installed as part of a new installation on a separate partition. Somehow, update-grub isn't seeing things as it did up until now.

Thanks for the help, and I'll keep plugging away!

---

### Post by bcarlowise on 2012-02-09
As oldfred pointed out, the issue is is the following line for the Windows 7 menuentry:

search --no-floppy --fs-uuid --set=root 16B815A0B8158003

the hex value listed is for the Windows XP Partition. One way to get the hex value for the Windows 7 partition is to mount the Windows 7 partition via Nautilus. Once the partition is mounted,the hex value of the partition will display in the title bar. Screenshot is attached. Just change the value and then try booting into Windows 7 again.

---

### Post by oldfred on 2012-02-09
From Ubuntu you can also list all UUIDs:

sudo blkid

then you can update your 40_custom with the correct UUID for Windows 7.

---

### Post by gwilson on 2012-02-11
Thank you, everyone. I deleted the line with the incorrect UUID and things work fine. I may update and correct the Win7 UUID, but I'm not sure it's worth the effort. It is odd that the system has the incorrect UUID for that one, though.

---

### Post by gwilson on 2012-02-11
I ran sudo blkid, andthe two Windows partitions STILL have the identical UUID even though they are on two separate physical hard drives.

I like to be tidy, but I'm not going to lose any sleep over it in the near furture.

---

### Post by oldfred on 2012-02-11
If you have identical UUIDs you must have done an image copy to create the new drive or partition.

Not sure if this works on NTFS or not.

Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX

---

