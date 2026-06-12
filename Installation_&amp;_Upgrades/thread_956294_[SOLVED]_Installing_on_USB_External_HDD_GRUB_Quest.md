---
title: "[SOLVED] Installing on USB External HDD: GRUB Questions Too"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by DrMelon on 2008-10-23
Hello there, everyone. 

I've got a 250 GB External USB HDD. I would like to partition 50GB and use that as an Ubuntu installation. I would also like to boot from this partition. Easy enough, eh?

However, I don't know how to set up GRUB so that Windows boots normally instead of Ubuntu (for the sake of the family).
Also, how will GRUB react if the USB HDD is unplugged? Will an error be thrown or will it just not show Ubuntu as being there?
Thanks!

---

### Post by ajgreeny on 2008-10-23
You need to put grub on the external drive, not on the windows MBR where it will go by default if you use the Live CD to install.  Then you need to set the external drive as the first boot device ib BIOS.  Now when you bootup, if the external drive is attached, grub will appear; if it not attached, windows will boot from the MBR as if ubuntu did not exist on the machine.  The easiest way to do this is with the Alternate install CD which gives the option of where grub is installed, though you could use the live CD, install as default, then use ```
sudo  grub-install /dev/sd#
``` to put the grub onto your external disk, and restore the windows MBR to that disk.

---

### Post by DrMelon on 2008-10-23
Ah! Thanks very much. I'll be sure to make a note of this.

---

### Post by caljohnsmith on 2008-10-23
To make sure that you don't touch the MBR (Master Boot Record) of your internal drive with Windows (I assume that's where your Windows is), when you get to the last stage of the Ubuntu installation from the Live CD, just click the "advanced" button and tell Grub to install to /dev/sdb or whichever is your USB drive. If you don't do that, by default Grub will be installed to the MBR of your internal drive, which obviously you don't want. :)

---

### Post by DrMelon on 2008-10-23
Yeah, I've got it covered. Thanks to you all!

---

### Post by DrMelon on 2008-11-06
Okay, scratch that; I'm having trouble.
The Linux install goes fine, but it's booting that's my problem.
I can't get my BIOS to see the USB HDD: boot options are CD-ROM, MO, ZIP, LS210, USB FDD, USB ZIP. However, setting it to any of these doesn't work, and the USB HDD is not listed in my HardDisk boot Priority menu either. I have the latest BIOS firmware for my mobo too (which is an ASUS A7v8x-x.).

Any help, anyone?

---

### Post by caljohnsmith on 2008-11-06
> **DrMelon said:**
> Okay, scratch that; I'm having trouble.
The Linux install goes fine, but it's booting that's my problem.
I can't get my BIOS to see the USB HDD: boot options are CD-ROM, MO, ZIP, LS210, USB FDD, USB ZIP. However, setting it to any of these doesn't work, and the USB HDD is not listed in my HardDisk boot Priority menu either. I have the latest BIOS firmware for my mobo too (which is an ASUS A7v8x-x.).

Any help, anyone?
If your computer doesn't support booting from your USB drive, then you'll need to move your Ubuntu's boot files to a drive that will boot. Can you make an extra ~200 MB partition on your internal Windows drive? If so, you could make that Ubuntu's /boot partition, and your problem would most likely be solved. Or, if you can boot from CDs (which I assume you can), you could put all your Ubuntu boot files on a CD and boot the CD to boot Ubuntu. 

If you decide to put Ubuntu's boot files in a partition on your Windows drive, I would recommend resizing the Windows partition from the beginning (and not end) to make room, so that you can put the Ubuntu /boot partition at the beginning of the drive. The reason is because there are some BIOSes that can't access anything on a HDD past either 8.5 GB or 137 GB, depending on how old your BIOS is. And if your BIOS doesn't support booting USB drives, I think there is a fair chance one of those limits could apply to you. By putting the partition at the front of the Windows drive, you won't have to worry about running into that limitation. You will have to change the Windows boot.ini file though since Windows won't be the first partition anymore, and you will most likely have to use testdisk to do a few simple repairs on the Windows partition to get it booting OK. If you resize Windows from the end, you won't have to change the boot.ini file, but there's a possibility you would have to use testdisk to get it booting OK too. 

EDIT: I see sdrubble strongly disagrees with me :), so I've PMed someone who I know has successfully resized his Windows partition from the beginning and got Windows to boot just fine. I'm hoping he might offer his opinion of whether he thinks resizing Windows from the beginning would work for you too.

---

### Post by sdrubble on 2008-11-06
> **caljohnsmith said:**
> If you decide to put Ubuntu's boot files in a partition on your Windows drive, I would recommend resizing the Windows partition from the beginning (and not end) to make room, so that you can put the Ubuntu /boot partition at the beginning of the drive.
 
Please, [SIZE=4][COLOR=red]**DON'T !!!**[/COLOR][/SIZE]
 
If you'd take an advice from someone who already dared to [COLOR=blue]**MOVE THE BEGINNING**[/COLOR] of a Windows C:\ drive and had to live with the consequences, that is . . . ](*,)
 
Windows will think that a) it's a pirated version, or b) it's being unauthorizedly being copied to a 2nd machine. It might ask you (or not) to repair itself - but in any case your chances are high of being mightily screwed up.
 
In my case, I had taken a partimage backup of the C:\ partition, made way at the beginning of the disk for whatever reason I can't exactly remember, and [successfully] restored the C:\ partition with partimage further down along the disk. The restore was successful from a "content" standpoint, and also from a "boot" standpoint, but not from an "it works" standpoint . . . :cry:
 
I can't remember exactly which [unsuccessful] attempts I've done to restore Windows . . . I DO remember ending up re-installing from scratch however. :frown:
 
From my experience, there's no problem whatsoever as to stretching or squeezing the C:\ partition (GParted is a very good tool for this), as long as you move [COLOR=blue]**ONLY THE END**[/COLOR] of the partition and don't mess with its beginning.
 
YMMV of course, but I'm glad I could make this warning [supposedly . . .] in time.
 
Cheers & good luck
 
sdrubble
 
EDIT: just saw that caljohnsmith made some additions to his previous post after reading mine above. What I can add here is, I got the impression that Windows doesn't really care if you alter the number of partitions before its own partition (hence the boot.ini hack works), but it will detect any change in the **original offset** from the beginning of its own partition to the start of the physical disk, and [mis]act accordingly.

---

### Post by DrMelon on 2008-11-06
Well, my BIOS has the 137GB limit; however, since the Internal drive is only 80GB, putting the partition at the end would be fine; however, I prefer to use a boot CD. Going to get it working soon. Thanks for your suggestions, and keep them coming! I may still need them!

---

### Post by meierfra. on 2008-11-06
[QUOTE=caljohnsmith]so I've PMed someone who I know has successfully resized his Windows partition from the beginning and got Windows to boot just fine. I'm hoping he might offer his opinion of whether he thinks resizing Windows from the beginning would work for you too.
[/QUOTE]
I'm the someone and I indeed   have successfully resized a Windows partition from the beginning. But I don't recommend  it unless one really has to.
In addition to using testdisk to fix the file system parameters stored in the boot sector, I also had to used "regedit" on the Ultimate Boot CD to edit the Windows registry.           

[QUOTE=sdrubble]What I can add here is, I got the impression that Windows doesn't really care if you alter the number of partitions before its own partition (hence the boot.ini hack works), but it will detect any change in the original offset from the beginning of its own partition to the start of the physical disk, and [mis]act accordingly.[/QUOTE]

That is exactly right. The offsets is used in the  windows registry as an ID for the partition. If the offset  changes, windows will treat the partition as a new partition. 
 This can  lead to a change in drive letters, which in turn makes it impossible to boot Windows. As   I said one can fix the problem by  editing the Windows registry, but  that's not the kind of thing one likes to do, if one can avoid it.
It might also lead to the problems mentioned by sdrubble, but those did not happen to me.

---

### Post by DrMelon on 2008-11-07
Okay, I think I know what I'm looking for: 

Is there any kind of bootloader with USB Hard Drive Support for if your BIOS only Lists USB-ZIP and USB-FDD as bootable USB devices?

---

### Post by DrMelon on 2008-11-07
Sorry for the double post, wanted to get this bumped so that I could share my solution with anyone else experiencing similar problems:

**If you want to boot from USB but your BIOS does not support it, download the PLoP Boot Manager: it can replace your bootloader, run from NTLDR, run/install from Floppy or CD. It can boot from anything except USB-CDROM or USB-FDD. Also, has a nice starfield effect and green matrix-y text so it really impresses people when you go to boot up and you load that awesomesauce. Link is here: [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)**

---

