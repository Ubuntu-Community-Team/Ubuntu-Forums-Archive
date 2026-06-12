---
title: "grub doesn't recognize extended partition?"
date: 2006-12-02
forum: Installation &amp; Upgrades
---

### Post by jms830 on 2006-12-02
Originally, I installed Windows 2000 and then Ubuntu (and dual booted). Then I had to install Windows XP, so I installed it over my Windows 2000 partition. I then reinstalled grub to the MBR. However, I cannot get grub to recognize Windows XP. I think this may have something to do with that Windows XP got installed to an extended partition somehow. It is hda1 extended to hda5. 

Any help would be appreciated. I've tried update-grub and manually editing the menu.lst

I only get errors when I try to boot into it.

---

### Post by Herman on 2006-12-02
Hello jms830, :D
If you can post a copy of the output you get from 'sudo fdisk -lu',```
sudo fdisk -lu
```, and a copy of the bottom portion of your /boot/grub/menu.lst in Ubuntu, someone should be able to help you a lot easier,```
sudo gedit /boot/grub/menu.lst
``` Also, can you try to remember exactly or as near as you can what error messages you are getting when you try to boot Windows. Error messages from Grub, or from Windows?
Regards, Herman :D
[]("http://users.bigpond.net.au/hermanzone/p15.htm#How_To_boot_Windows_using_GRUBs_CLI")

---

### Post by jms830 on 2006-12-03
output of *sudo fdisk -lu*

```
Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders, total 39070080 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1           16065     6281414     3132675    5  Extended
/dev/hda2         6281415    35969534    14844060   83  Linux
/dev/hda3   *    35969535    38025854     1028160    b  W95 FAT32
/dev/hda4        38025855    39070079      522112+  82  Linux swap / Solaris
/dev/hda5           16128     6281414     3132643+   7  HPFS/NTFS
```

end of /boot/grub/menu.lst, which I have edited. I have tried (hd0,0) and (hd0,4) with no luck.

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

when I tried to boot it this way (hd0,0) I got a grub Error 12: Invalid Device Requested
EDIT: (hd0,4) gives me the same error message

---

### Post by Herman on 2006-12-04
There are two ways of trying to handle this. 
One possibility would be if you want to edit your menu.lst file to try to boot it the way it is and hope it won't be a lot of trouble, (you may also need to edit boot.ini or maybe not).
Otherwise, if you do not have very much data in your partitions and can resize then a lot smaller, you should be able to delete certain partitions and copy and paste others around to make it into a more conventional type of partitioning scheme.
I think the first method will be the easiest to try first.

Try editing your menu.lst file to this instead: (change (hd0,0) to (hd0,4) because your Windows is on /dev/hda5, not /dev/hda1.   [LEFT]```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda5
title        Microsoft Windows XP Professional
root        (hd0,4)
savedefault
makeactive
chainloader    +1
```I am not sure, but you may need to edit boot.ini also, if it isn't automatically set up with the correct partition numbers for this situation, (if you get error messages from Windows). But on the other hand it might just boot right up okay right away. You'll only know when you try. 
If you have more trouble you can make your own Windows XP boot floppy disk with ntldr, ntdetect, and boot.ini on it if you have another Windows XP computer around somewhere. You can always access boot.ini on the floppy disk and edit that if required. Then when you have Windows booted you cannot access your regular (installed) boot.ini and edit it from inside Windows itself, only if you need to though. For how to make your own Windows Xp boot floppy, [Click Here]("http://support.microsoft.com/kb/305595/EN-US/").
These Windows XP boot floppy disks are great, they boot Windows almost no matter what. They bypass Grub and the MBR, the bootsector, boot.ini, NTLDR and NTdetect.com, so they are very good. :D

Regards, Herman
[/LEFT]

---

### Post by jms830 on 2006-12-04
1) Yes I tried (hd0,4) and the same thing happened. Is there any way to move windows from the extended partition to the primary partition? Or force it to install there on hda1? Why does it install to the extended partition?


2) For the boot disk...what would I make the boot.ini say to work with my setup?
Below is the boot.ini from the windows website... what should I change
```

[boot loader]
   timeout=30
   Default= multi(0)disk(0)rdisk(0)partition(1)\windows

   [operating systems]
   multi(0)disk(0)rdisk(0)partition(1)\windows="Windows XP"
```

---

### Post by Herman on 2006-12-04
>  2) For the boot disk...what would I make the boot.ini say to work with my setup?
Below is the boot.ini from the windows website... what should I change
     Code:
     [LEFT][boot loader]
   timeout=30
   Default= multi(0)disk(0)rdisk(0)partition(1)\windows

   [operating systems]
   multi(0)disk(0)rdisk(0)partition(1)\windows="Windows XP"[/LEFT]

 Oh, wow! It looks to me as if your boot.ini is  autoamtically configured as if Windows presumes it is in partition number  1, so you can just leave it like that now if you want to change things around and make Windows to be partition number 1 now.
If you had wanted to leave it is partition number 5 though, you'd just change where it has 'partition (1)' on both the upper and lower lines to 'partition (5)'.  (Someone please correct me if I'm wrong, I've only done that a couple of times and I'm not very experienced with Windows at all). Anyway, we don't have to do that now.

```
 Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders, total 39070080 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1           16065     6281414     3132675    5  Extended
/dev/hda2         6281415    35969534    14844060   83  Linux
/dev/hda3   *    35969535    38025854     1028160    b  W95 FAT32
/dev/hda4        38025855    39070079      522112+  82  Linux swap / Solaris
/dev/hda5           16128     6281414     3132643+   7  HPFS/NTFS
```>  Is there any way to move windows from the extended partition to the primary partition? Or force it to install there on hda1? I recommand the [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") for working with partitions with. It's free and only 30mB download, burn to CD-ROM. 

1) Resize all partitions as small as you can first. You may need top copy data out to CDs and delete some from the hard disk first to make sure you'll have enough room. It's a good time to make a back-up anyway.

2) Move all partitions towards the beginning of your disk so you'll have enough free space at the end for copying and pasting your /dev/hda5 partition there.

3) You don't need the swap area to be a primary partition, we can only have four primary partitions, we need that partition number for now, so delete your swap area, we can make a new one before we finish.

4) Copy your WIndows partition number 5 and paste it behind all the other partitions in the free space we made at the end of your disk. Paste it as far as you can towardsd the opposite end of your disk. I hope there will be enough room. GParted will automatically offer to let it take up the whole space, reduce the size of it to as small as it can be before applying the changes. It will be automatically given partition number 4, which  we freed by deleting the swap area.

5)When your Windows is safely copied as partition number 4, you can delete the original copy of it from partition number5, and also delete the extended partition number 1 that it is in.
This frees up the number '1', and makes it available for use again.

6) You can copy a partition to an equal size or larger area of free space, but not to a smaller area. So now we have an area of free space where Windows came from, but it might not be large enough to paste WIndows back there if Windows has been pasted to a (slightly) larger area. Just check, if so, you might need to move your other partitions one at a time to the right just a little to make sure your have a large enough free space at the beginning of your disk to paste Windows back.

7) Paste Windows partition number 4, back to the free space at the beginning of your disk. It should be allocated the now available partition number of '1', and be a primary partion. Resize it to the size you want.

8)Delete the temporary copy of Windows, (partition number 4), we don't need it anymore, and it's in the way now. Make a new partition there and make it an extended and make it the size your swap area was or about 500 to 1025 miB, and click apply. It will be allocated partition number 4 now.
Make your swap area inside extended partition number 4 and it will be allocated partition number 5.

Adjust the other partitions to the sizes you want and move them around, but do not copy and paste them as copying and pasting will alter the partition numbers when we don't want to now. Only 'move' them, that doesn't change the partition numbers. Arrange then how you like so they fill up the free space as you desire.

9) You can reboot and remove your GParted LiveCD now. 
Windows should boot normally now.
 You will need to edit your /etc/fstab file in Ubuntu to get Ubuntu working properly.
> Why does it install to the extended partition? I don't know, but normally the swap area is logical, although it works just as well as primary, but occupies a primary partition number. We can only have four primary partitions, so having the\at number occupied may have forced Windows to take the next option available. I'm just guessing. :-k

Do you know how to edit your /etc/fstab? I'll be back later to help you with that if you need any, unless someone else jumps in.
That's all for now, regards, Herman :D

---

### Post by bulldog on 2006-12-04
Thank you so much Herman.

If I understand it,alter the boot.ini file  should be the thing to do,to get windows running from another partition as the first primary.

Have looked for this a long time,I hope I understand it well.

---

### Post by jms830 on 2006-12-04
Thanks Herman for taking the time to write this out. I have to try it later tonight when I am home. Just wondering though, if the problem is that there are too many primary partitions, could I delete my swap and windows partitions, then reinstall windows (leaving some unformatted space), and then make a new swap partition once windows is already installed? It might be easier/less risky for me than moving all my partitions around. So I guess I'm just asking if there would be any reason not to do it this way. Thanks again.

---

### Post by Herman on 2006-12-05
Hello bulldog,
> If I understand it,alter the boot.ini file should be the thing to do,to get windows running from another partition as the first primary. Er... If you mean 'alter_ing_ the boot.ini file should be the thing to do, to get Windows to boot from a partition _other than_ the first primary', then I would agree with you. Normally that would (should) be the case. 
...Or do you mean "alter_ing_ the boot.ini file should be the thing to do, to get windows running from another partition as the first primary." If that *is exactly what you mean* then how do you do that? You might quit likely know a lot more about booting Windows than I do. I have experimented with booting Windows up in a few different situations, but I have no experience with booting in in a logical partition. I am afraid there might be some mystery or trick to it that I don't know. Please help if you can shed some light on that.

My thinking so far is that if Grub has chainloaded Windows successfully at all, which I would have expected it to normally be able to do,  jms830 would be complaining of some sort of Windows booting error such as a blue screen with 'HAL is missing or corrupt' or something similar. A Windows boot error message like that can usually be solved by editing boot.ini.

However, this time jms830 has not complained of a Windows error message, the complaint is that Grub isn't even able to chainload Windows, and we have a Grub error 12,
> when I tried to boot it this way (hd0,0) I got a grub Error 12: Invalid Device Requested
EDIT: (hd0,4) gives me the same error message Personally, I have never tried to get Windows to boot up on a non-primary partition, and I have no idea whether that would be simple or if it would be a difficult feat to accomplish. I think I have seen /etc/fstab files where some people do have Windows installed in logical partitions, but it is a less common thing to do. That's why I agreed with  jms830 about wanting to change things around so that Windows is in a first primary partition. If it doesn't fix the problem, at least it will mean one less uncertainty to deal with.
However, if you are sure that having Windows in a logical partition would not cause any problems, feel welcome to help. Perhaps it is some other problem or problems. I do think that it would be necessary to edit boot.ini if the partition is left as it is, (as partition number 5). but if the partition is changed to make it partition number 1, which is more common, then I think jms830's boot.ini can be left as it is.

Regards, Herman  :D

---

### Post by Herman on 2006-12-05
> Just wondering though, if the problem is that there are too many primary partitions, could I delete my swap and windows partitions, then reinstall windows (leaving some unformatted space), and then make a new swap partition once windows is already installed? It might be easier/less risky for me than moving all my partitions around. So I guess I'm just asking if there would be any reason not to do it this way. Thanks again.Hello jms830,
Yes, that would be another way to do it, and if this is a fresh Windows install, (no work has been put into a lot of updating and tweaking and added software and the like), then now that you mention it, that might even be the better way. Then if the reason why grub said your Windows was an invalid device was somethiong to do with a faulty installation, re-installing should clear that possibility too. Do  it whichever way you prefer.

If you find that after changes to your partitions, Ubuntu halts with a black screen halfway through booting, it will likely be a failed fielsystem check on the other partitions Ubuntu expects to be there, but have been moved around now. Just press 'Ctrl + d' , or 'Enter', then 'Ctrl + d', to continus booting anyway. Your computer might be slow until you edit /etc/fstab with the changes and fix the number for the swap area.

I am still interested in hearing from bulldog or anyone about booting Windows from a logical partition though. I will try that myself sometime soon and find out for myself what problmes I run into. It's just something I haven't tried yet.

Regards, Herman :D

---

### Post by bulldog on 2006-12-05
Thanks Herman to give me a lesson in plain English :D ,I'm Dutch and all I know about the English language is picked up without any education in the language,so I will be making mistakes again. 

Okay,ontopic shall we?
I had several times the pleasure to try and help users with problems booting windows from GRUB.
If windows was on the first primary,it was just pointing GRUB in the right direction and it would run in most cases.

The trouble began when people had moved their windows partition to a rather strange place like in an extended partition.
I never had the pleasure to resolve this,although there were users who stated it would be no problem,and windows could be installed where ever you want.
When I asked how they managed that,the big silence began,and I never had an answer on this question.

Now I ran into this topic,and saw your answer,so I presumed that all what is necessary to do,is altering the boot.ini to get windows back on track again.
I'm not a windows power user,or how it's called anyway,but I know a few things about it and I know some things about computer configurations and what can go wrong with it.

But as I understand,you're not sure either if this is the way to do it?
I for sure,don't know the answer,and I'm too lazy to look it up :D

---

### Post by Herman on 2006-12-06
Hello bulldog,
Now I understand. :D You are better than me, I have a Dutch name but I can only speak English, I have lived all my life in English speaking countries. Anyone who can speak more than one language is very intelligent in my opinion. :D

 A long time ago, I also read one or two threads about Windows users who for some reason have their Windows partition numbers changed during disk partitioning. It is relatively rare, and I don't know if it is the users fault or not. But it can be a big headache for them if no-one knows how to help. 
I did some googling about it and after a few experiments with my own computer I found out that they just have to edit their boot.ini file with the correct partition numbers and it should boot okay. Mine does anyway. I tested it.
The problem is, normally they need to boot Windows before they can edit boot.ini, but they can't boot Windows because boot.ini is wrong for their partition number. So they are stuck.
The best solution is for them to make a Windows Xp boot floppy disk, with a copy of boot.ini, NTdetect.com and NTLDR on the floppy disk. It needs to be formatted with a command from a DOS prompt as far as I know. I would like to learn how to format the Windows boot floppy correctly and make it in Linux. The ones I tried to make from Linux didn't boot. It is okay to copy the files to the floppy disk in Linux. It's just the formatting I want to find out about.
Here is a link to the Microsoft how-to for that, [Click Here]("http://support.microsoft.com/kb/305595/EN-US/").
Most importantly, the floppy disk's boot.ini can be easily edited from Linux.

Here is a link I made in Super Grub Page about the Windows error messages they might see, 
**  Error messages from Windows** .....(Windows begins to boot, but...)........................................[GO]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows_Booting_errors")

Here is a link from my MBR page with some more on boot.ini and where to find it and how to relax file permissions for it if it is in a FAT32 filesystem, (if they want they can even edit it from Linux if they have Windows with the FAT32 filesystem). 
**            A Birds's eye view of Windows XP **(showing the bootloaderfiles)...................................[GO]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP")

Those links should help someone with that problem. You ( or anyone else) are welcome to pass them on as you see fit. I tested the information in those links myself, (for primary partitions), but I didn't try it with Windows in a logical partition yet. Maybe be it's just the same, or maybe there will be something tricky about it that I will need to learn. I won't know for sure until I get some time to try it. Right now I am working on a different problem for now. I will try putting Windows in a logical partition sometime soon and see what happens. 

All the best,
Regards from Herman :D
     [SIZE=+1]
[/SIZE]

---

### Post by bulldog on 2006-12-06
I made a copy of your post for later reference,it's a lot of very useful information.
I have to chew on it for a while,to understand all this :D

But I'm very glad to know that the boot.ini is the thing to look for,if windows refuses to boot.

About the boot floppy,you can go into windows and format a bootable floppy by right clicking the floppy drive and choose to do so.
But I think you know that already.

The only problem is,as you discribe,when you can't boot windows you can't make a bootable floppy neither.
But there should be someone around in the neighborhood who can help you with that I suppose.

Thank you for all the info you've provided,I have something to read now.

Thanks again and hope to see you around,with all the interesting problems users are getting in to.:D

---

