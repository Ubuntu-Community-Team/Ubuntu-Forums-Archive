---
title: "Newbie dual boot question"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by scimitar123 on 2008-03-12
Hi all

I've just started to use Ubuntu and so far I'm delighted with it. I do however have a question regarding dual booting Ubuntu with XP. To begin with my PC a hard drive with 3 partitions, two XP boots and one for general storage. I deleted one of the XP partitions during the Ubuntu install process and installed Ubuntu over the top. Now my computer just boots into Ubuntu with no choice of operating system (which is what I suspected would happen) but I want the option of booting into the copy of XP that still exists on the hard drive.

Firstly is this possible by editing something in the grub? Secondly if not and I have to fresh install XP, is there a specific way I should go about doing this?

Many thanks

Alan

---

### Post by mikewhatever on 2008-03-12
Yes, you can edit GRUB's menu, no need to reinstall Windows. Can you please open the Terminal (Applications>Accessories) and post the following info:
sudo fdisk -l
cat /boot/grub/device.map
cat /boot/grub/menu.lst

---

### Post by sandysandy on 2008-03-12
> **scimitar123 said:**
> Hi all

I've just started to use Ubuntu and so far I'm delighted with it. I do however have a question regarding dual booting Ubuntu with XP. To begin with my PC a hard drive with 3 partitions, two XP boots and one for general storage. I deleted one of the XP partitions during the Ubuntu install process and installed Ubuntu over the top. Now my computer just boots into Ubuntu with no choice of operating system (which is what I suspected would happen) but I want the option of booting into the copy of XP that still exists on the hard drive.

Firstly is this possible by editing something in the grub? Secondly if not and I have to fresh install XP, is there a specific way I should go about doing this?

Many thanks

Alan

u can make an entry for the existing win Xp in ur ubuntu&#347; menu.lst file. a fresh install is not required.

regards

---

### Post by Herman on 2008-03-12
:) Hello scimitar123,
Was the copy of Windows XP you deleted your 'boot' partition?
When you install more than one Windows in a computer, you can install GRUB and use GRUB's 'hide' command to hide your existing Windows partition first. GRUB or some other third party boot loader is much better for dual booting with than Windows boot loader, which is not very good designed for dual or multi booting.
If you just let Windows install in the Microsoft default way (without help), it will detect the existing Windows installation and copy the vital boot loader files out of the new installation into the older installation.
The older installation becomes your 'Windows 'boot' partition, and the newer installation can't boot without it.
Crazy I know, but that's the way they do it.

To find out, just take a look for your vital Windows boot loader files NTLDR, NTDetect.com and boot.ini in your Windows partition. If they're there, you should be able to edit GRUB and boot Windows XP.
If they're gone, you probably deleted them in your other Windows install.
Here's what Windows XP shoud look like from Ubuntu, [A Birds's eye view of Windows XP]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP")...showing the important files needed for booting.
(Your Windows install should be already mounted in Ubuntu and you should be able to see that by opening your icon on your Desktop, but if you don't have an icon for Windows, you might need to 'mount' it yourself. Here's how, [File Systems and Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm")).

Regards, Herman :)

---

### Post by scimitar123 on 2008-03-12
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03601265

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       24792   199141708+   f  W95 Ext'd (LBA)
/dev/sda5            6375       12748    51199123+   7  HPFS/NTFS
/dev/sda6           12749       24672    95779467    7  HPFS/NTFS
/dev/sda7               1        6374    51199060+  83  Linux
/dev/sda8           24673       24792      963868+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0bf446cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666    7  HPFS/NTFS
alan@alan-desktop:~$ cat /boot/grub/device.map
(hd0)   /dev/sda
(hd1)   /dev/sdb


Is that any use??

---

### Post by mikewhatever on 2008-03-12
Yes, that's very useful. Can you also post the output of the third one <cat /boot/grub/menu.lst>. Can you also check from Ubuntu, which one is the Windows system partition. You have two NTFS ones on /dev/sda (sda5, sda6) and another one on /dev/sdb, but that's probably a storage drive, right? Just browse to each of these partitions and look for Windows standard C:\ with Program Files, Documents and Settings, etc.

---

### Post by scimitar123 on 2008-03-12
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=d0550c9f-333b-48ac-a97b-82a0e54fdd08 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=d0550c9f-333b-48ac-a97b-82a0e54fdd08 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,6)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

SDA5 is windows

the other is storage (on the same drive as the operating systems) There is also a separate hard drive which is pure storage, which I think is also NTFS

---

### Post by mikewhatever on 2008-03-12
Right, open the file for editing with <gksudo gedit /boot/grub/menu.lst> and add the following to the very end, after ### END DEBIAN AUTOMAGIC KERNELS LIST.
title           Microsoft Windows XP
root            (hd0,4)
savedefault
makeactive
chainloader     +1

---

### Post by scimitar123 on 2008-03-12
I think I deleted the main boot version of windows by the way.

---

### Post by scimitar123 on 2008-03-12
I've added the lines as you suggested, but ubuntu just loads as normal :(

---

### Post by mikewhatever on 2008-03-12
> **scimitar123 said:**
> I think I deleted the main boot version of windows by the way.

I think you can use Windows recovery console and fixboot to remedy that.

---

### Post by Herman on 2008-03-12
Well you can try going to this site,  [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm") and follow the instructions there and download the file to make a CD with NTLDR, NTdetect.com and boot.ini in it, I know for sure those will boot Windows in a primary partition almost no matter what.
I'm not so sure if you can get Windows to boot directly when it's in a logical partition. I don't think Windows can, but I'm not sure.
You can also go to this site (Microsoft), [How to make your own Windows Xp boot floppy.]("http://support.microsoft.com/kb/305595/EN-US/")  and learn how to make a floppy disk with NTLDR, NTdetect.com and boot.ini in it, and since it's a floppy disc you'll be able to edit boot.ini to try to boot Windows Xp in the logical partition and see if it will or not.




---

### Post by scimitar123 on 2008-03-12
I've tried the recovery, but the recovery console says it can't find any hard disks so nothing can be done :S Sorry to bother you and thanks for all the help so far!

Alan

---

### Post by sandysandy on 2008-03-12
try Super Grub Disk.

regards

---

### Post by Herman on 2008-03-12
You might find it easiest to use Ubuntu to copy all your files out of Windows XP and just use Ubuntu.
Or, use Ubuntu to copy all your files out of Windows XP to some other media like to another hard disk or a USB external drive and re-install Windows XP, then restore your files.

[COLOR=#cc0000][FONT=Arial][COLOR=#000000]Here is a link that explains what happened, [/COLOR][/FONT][/COLOR][http://www.goodells.net/multiboot/principles.htm](http://www.goodells.net/multiboot/principles.htm).
[CENTER][LEFT]
 Here is that website's home page, [Understanding MultiBooting and Booting Windows from an Extended Partition.]("http://www.goodells.net/multiboot/index.htm") 

I don't think you'll be able to get it to boot, I think you will be wasting your time, my advice is to re-install, and make sure you install in a primary partition, or just use Ubuntu and forget about Windows.
I'm mean that in a friendly way, I'm not being nasty or sarcastic, just practical.

Regards, Herman :)
[/LEFT]
[/CENTER]

---

### Post by scimitar123 on 2008-03-12
Thanks Herman, i was beginning to think that myself.

I realised why windows cant see the HDD, i have to install a raid driver from a floppy, problem is i have no way of making that floppy now haha. I need to find someone with windows and a floppy drive :)

---

### Post by Herman on 2008-03-12
Oh, RAID as well, I don't know very much about RAID, that makes it even a little bit more complicated. Sorry that you're in such a jam. 
If your files are all backed up then good, if not, you should be able to make a backup with Ubuntu. Ubuntu can make floppy discs, but for booting Windows you need a Windows boot floppy, a Ubuntu one isn't quite the same.
I have to go for now, good luck with it. I'll be back later on.

---

### Post by scimitar123 on 2008-03-12
I think i have the raid problem sorted. Its not proper raid, just JBOD. If i just re-install XP will it just work or will it mess the grub up?

Alan

---

### Post by sandysandy on 2008-03-12
> **scimitar123 said:**
> I think i have the raid problem sorted. Its not proper raid, just JBOD. If i just re-install XP will it just work or will it mess the grub up?

Alan

XP will mess the grub. but grub can be re-installed.

have a look at this link

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

regards

---

### Post by mikewhatever on 2008-03-12
> **scimitar123 said:**
> I think i have the raid problem sorted. Its not proper raid, just JBOD. If i just re-install XP will it just work or will it mess the grub up?

Alan

It will delete GRUB's part from the MBR, but not from the Linux partition. Can Windows see your HDDs now? If so, why not try fixboot from the recovery console again.

---

### Post by Herman on 2008-03-13
:) Well, it might be interesting to try to fix the remaining Windows installation as the other posters are suggesting.
You will need to run FIXBOOT, as mikewhatever says, plus a copy of NTLDR, NTdetect.com and boot.ini pasted into it. The boot.ini file would need to be edited.
Then you could try to boot it, but I'm not sure Windows will boot in a logical partition without another Windows in a primary partition to boot through. It might work.
On the other hand it might just be more trouble than it's worth too. 
I'm not sure if the average user would be able to accomplish all that easily.

It's interesting that you sign an agreement saying something like you're not allowed to 'diseminate; the software (or something like that, I haven't read it recently), but Microsoft themselves have a KB page about how to do just that, copy someone else's vital booting file to a floppy disc.  [How to make your own Windows Xp boot floppy.]("http://support.microsoft.com/kb/305595/EN-US/")  (Microsoft). 
I'm not sure if you can boot Windows in a logical partition without another Windows in a Primary, but maybe you can since you are using GRUB.
You'll still be left with a confused system that doesn't know if it's C or D or some other drive letter. I don't know how that will affect things. Maybe it will be okay.
If it happened to me I would try to get it to boot for fun when I have some time to spend on it, experimenting and finding out what happens. That's because I'm interested in learning more about this type of thing.
If you're the type of person who just wants the computer to work and isn't so interested in playing with boot loaders and their configuration files then re-installing will be the quickest sure way to get back to a system that will operate normally. I think most people will be happiest in the long run when they have a system that is stock standard to begin with and then customized from there. 

So do whatever you think will be best for you, scimitar123.

Regards, Herman :)

---

### Post by mikewhatever on 2008-03-14
Hey Herman, I actually thought fixboot would take care of all the needed files, but, have to admit, I know next to nothing about Windows own bootloader. It's nice to see you around :).

---

### Post by Herman on 2008-03-15
:) Hello mikewhatever, 
Thanks, it's nice to see you here too. :)

Some time ago I ran quite a number of experiments in my own computer and tried out all kinds of different partition arrangements for dual booting with, and as well I ran quite a few experiments involving moving Windows to different locations on the hard disk, and changing Windows to different partition numbers, editing boot.ini, and booting.

I'm pretty sure I tried to get Windows to boot in a logical partition and wasn't able to. Just by co-incidence, this thread popped up again today, from around a year ago, [Windows XP drive letters changed]("http://ubuntuforums.org/showthread.php?t=414133"), and as you can see in post #8, I was asking for information way back then. So far I haven't seen any information to suggest Windows in a logical partition can boot without depending on another Windows in a primary partition.

 I am still curious about that and would like to hear from someone who has. 
Just because I couldn't do it doesn't mean it can't be done, maybe there's something I don't know, or forgot or neglected to try.

FIXBOOT will restore the Windows boot sector, but as far as I know, that's all it can do. 
The boot loader and other important booting files can be replaced, and boot.ini can be edited. Then it might be possible to boot it, but I couldn't do it when I tried.

It would theoretically be possible to copy the whole operating system and paste it into a primary partition and then run FIXBOOT, paste in the booting files and edit boot.ini and maybe get it to boot. That depends on what the partition arrangement is like on that hard disk already and on space limitations, and would take a long time unless all the personal files would need to be copied out first.
I'm not certain I could recommend anyone try that because I would worry that Windows might have anti piracy booby-traps to cause the operating system to become unuseable after a certain length of time or something like that.
I know we can copy and paste free operating systems without any problems.
With Windows it might boot to the login screen  some day three months from now and not offer a login and the system will be unusable due to the fact that anti-piracy software has detected the fact that the system has been copied.

That's why I recommended re-installing, because it's the simplest option that I'm sure will work. 

Regards, Herman :)

---

