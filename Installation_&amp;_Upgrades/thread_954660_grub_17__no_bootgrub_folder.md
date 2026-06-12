---
title: "grub 17:  no /boot/grub folder"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by Mount on 2008-10-21
Hello All, 

I've looked through many solutions to this error but have not been able to find an answer to my specific situation. 

I have a dual boot system and have tried to do an upgrade of Ubuntu. During the installation I selected the partition which contained the previous version of Ubuntu, formatted (EXT3) and installed there. I also specified the mount point "/". 

Now when I reboot I get "Grub Error 17". I started looking for a solution and have tried: 

Changing the boot priorities. 
Reinstalling again (just in case) 

In addition to this I have tried booting from the live CD and inspecting the /boot/grub/menu.lst file. The problem is is it is not there! I only have five files in this folder and no deeper folders. What does this mean? 

Any suggestions .....?

---

### Post by ammikulka on 2008-10-21
i have no clue but if i have a thumb drive in the USB i get an error 17 message do you have anything in your usb? 
other than that sorry i cant help you

---

### Post by Mount on 2008-10-21
Hi I tried taking the USB stick out for the second install but that didn't change anything. Thanks anyway

---

### Post by Mount on 2008-10-21
oops, I've found the menu.lst file not. It was in a place i didn't expect. I have a drive (at least it looks like a drive) called FileSystem which is where I was looking. This file contained all the usual folders /etc/ /bin/ et cetera. strange. 

Could some one go through the contents of the menu.lst file with me and check it against what I get from gparted? 

//***************************************************************
// gparted pages. 
//page 1

/dev/sda1  ntfs
/dev/sda2  extended
  /dev/sda5   ntfs
  /dev/sda6   ntfs
  /dev/sda7   ntfs
  /dev/sda8   ntfs

// page 2

unallocated
/dev/sdb2   extended
   /dev/sdb5  ntfs

//page 3

/dev/sdc3  linux-swap
/dev/sdc2  ext3
/dev/sdc1  extended
   /dev/sdc5  ntfs

// End gparted
//***************************************************************

//***************************************************************
// menu.lst

..........

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7d88c471-3171-4a0d-985a-167ab3c5701c ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd2,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=7d88c471-3171-4a0d-985a-167ab3c5701c ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd2,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

.........

// End menu.lst
//***************************************************************
 

I don't really understand how I should have my harddrives set up!


Thanks



//***************************************************************

---

### Post by Mount on 2008-10-21
Hello, 

I've just noticed that the mount point for "/dev/sdc2  ext3" in my about post is "/media/disk". 

Do I need to change this? or is this a consequence of using the Live CD? 

cheers

---

### Post by caljohnsmith on 2008-10-21
Since your Ubuntu entries use (hd2,4), that means that Grub must be installed to the MBR (Master Boot Record) of one of your other drives. That's OK, but it's not as ideal as when you can simply boot from your Ubuntu drive directly and leave your other drives untouched. Can you set your BIOS to boot your sdc drive (Ubuntu) on start up? If so I would recommend putting Grub in its MBR, and just boot from that drive. That will save you a lot of headaches if you have problems with drives or move anything around. 

To get a better idea of your setup, please open a terminal (applications > accessories > terminal) and post:
```
sudo fdisk -lu
```
Also, to install Grub to the MBR of your Ubuntu drive, try this:
```
sudo grub
grub> root (hd2,1)
grub> setup (hd2)
grub> quit
```
Then set your BIOS to boot the Ubuntu (sdc) drive, and see if you can at least get the Grub menu; if you can get that far we can work from there. :)

---

### Post by Etrruugo on 2008-10-21
just my two centsbumpWhen you came into the world, she held you in her arms.&#12288;&#12288;You thanked her by weeping your eyes out.&#12288;&#12288;When you were 1 year old, she fed you and bathed you.&#12288;&#12288;You thanked her by crying all night long.&#12288;&#12288;When you were 2 years old, she taught you to walk.&#12288;&#12288;You thanked her by running away when she called.&#12288;&#12288;When you were 3 years old, she made all your meals with love.&#12288;&#12288;You thanked her by tossing your plate on the floor.&#12288;&#12288;When you were 4 years old, she gave you some crayons.&#12288;&#12288;You thanked her by coloring the dining room table.&#12288;&#12288;When you were 5 years old, she dressed you for the holidays.&#12288;&#12288;You thanked her by plopping into the nearest pile of mud.&#12288;&#12288;When you were 6 years old, she walked you to school.&#12288;&#12288;You thanked her by screaming, &#8220;I'm not going!&#8221;&#12288;&#12288;When you were 7 years old, she bought you a baseball.&#12288;&#12288;You thanked her by throwing it through the next-door-neighbor's window.&#12288;&#12288;When you were 8 years old, she handed you an ice cream.&#12288;&#12288;You thanked her by dripping it all over your lap.&#12288;&#12288;When you were 9 years old, she paid for piano lessons.&#12288;&#12288;You thanked her by never even bothering to practice.&#12288;&#12288;When you were 10 years old, she drove you all day, from soccer to gymnastics to one birthday party after another.&#12288;&#12288;You thanked her by jumping out of the car and never looking back.&#12288;&#12288;When you were 11 years old, she took you and your friends to the movies.&#12288;&#12288;You thanked her by asking to sit in a different row.&#12288;&#12288;When you were 12 years old, she warned you not to watch certain TV shows.&#12288;&#12288;You thanked her by waiting until she left the house.Thsale is a professional, loyal and reliable wow gold supplier online, we pioneered selling cheap wow gold. Welcome to thsale buy world of warcraft gold Buy Cheap WoW Gold, World of Warcraft Gold, Please look here! We are a Great MMORPG company. wow money and wow items,which is very cheap WOW Gold&#65281;All US Server 24.99$/1000G on sell! Cheap wow gold,rs powerleveling,wow power leveling,Buy Cheapest/Safe/Fast WoW US EU Gold Power leveling ---------------------------------------------------**  [Pet products](http://www.lovelonglong.com),     [dog bed](http://www.lovelonglong.com),   [pet supply](http://www.lovelonglong.com)    [wow power level](http://www.powerleveling-wow.com/siteMap.asp),     [WoW Power Leveling](http://www.powerleveling-wow.com),**

---

### Post by Mount on 2008-10-22
Hello caljohnsmith, 

Thanks for the reply. 
Since your posting I have done something which enables me to boot as far as the GRUB menu. When I select any of the items 
from the menu I get: 

```
Error 17: Cannot mount selected partition
```
for the Ubuntu and: 
```

Error 12: Invalid device requested
```
for the Windows menu item. 

Does this help you diagnose the problem? 

Thanks .....

Here's the output of the fdisk command in any case: 

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa3661429

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   195350399    97675168+   7  HPFS/NTFS
/dev/sda2       195350400   976768064   390708832+   f  W95 Ext'd (LBA)
/dev/sda5       195350463   390700799    97675168+   7  HPFS/NTFS
/dev/sda6       390700863   586051199    97675168+   7  HPFS/NTFS
/dev/sda7       586051263   781401599    97675168+   7  HPFS/NTFS
/dev/sda8       781401663   976768064    97683201    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa7b16004

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2           16065   312576704   156280320    f  W95 Ext'd (LBA)
/dev/sdb5           16128   312576704   156280288+   7  HPFS/NTFS

Disk /dev/sdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbb6a7f7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1       155878695   320159384    82140345    f  W95 Ext'd (LBA)
/dev/sdc2   *     4193028   155878694    75842833+  83  Linux
/dev/sdc3              63     4192964     2096451   82  Linux swap / Solaris
/dev/sdc5       155878758   320159384    82140313+   7  HPFS/NTFS

Partition table entries are not in disk order


```

---

### Post by caljohnsmith on 2008-10-22
Well like I mentioned in my previous post, it would be a lot more ideal to set your BIOS to boot your Ubuntu drive on start up, because if you are booting another drive that now has Grub in the MBR (Master Boot Record), then if either your Ubuntu drive or that other boot drive have any problems in the future (or if you even just disconnect one), you won't be able to boot either. 

I would recommend following the instructions from my previous post to boot the Ubuntu drive directly, but if you want to live with your current setup, then go ahead and reboot again, and when you get the Grub menu, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change the X to be either 0, 1, or 2; press return to save the change, then press "b" to boot. One of those values of X should work to boot Ubuntu if your Grub menu isn't too far out of whack. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "# groot=(hdX,Y)" to whichever (hdX,Y) worked to boot Ubuntu; save, quit gedit, then run:
```
sudo update-grub
```
And you should be able to boot Ubuntu on start up next time. If you want help booting Windows, let me know which (hdX,Y) worked to boot Ubuntu.

---

### Post by Mount on 2008-10-22
Hi, 

Great i've got Ubuntu back! Thanks so much!

Only problem is that I can't get into Windows. I have tried, from the grub menu, editing the 'root (hdX, Y)' statements with a series of Xs and Ys but I can't seem to find Windows. I get several errors depending on the X and Y values. 

Do you have a suggestion on what values to use? BY the way Ubuntu boots with 'root (hd2, 1). 

Thanks

---

### Post by caljohnsmith on 2008-10-22
So is Windows on your 500 GB sda drive? If so, open your menu.lst again with:
```
gksudo gedit /boot/grub/menu.lst
```
And then add the following entries at the bottom of the file:
```
title Windows XP (hd0)
root (hd0,0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

```
Save, reboot, and most likely one of those entries will work to boot Windows. If not, let me know exactly what happens when you choose each one. :)

---

### Post by Mount on 2008-10-22
Ok, 

Selecting 'Windows XP (hd0)' gives 
```

Starting up ...

``` 
and the system just hangs

Selecting 'Windows XP (hd2)' gives
```

Error22: No such partition 

Press any key to continue...

``` 


Windows in indeed on the 500Gb drive. When I got the machine this disk was split into 5 equal partitions

Thanks

---

### Post by caljohnsmith on 2008-10-22
OK, you can remove the (hd2) Windows entry from your menu.lst, because it looks like the (hd0) is correct. From a terminal in Ubuntu, try the following:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and try and boot Windows again. Let me know what happens. :)

---

### Post by Mount on 2008-10-22
really I can't thank you enough for going through this with me. I'm completly lost otherwise.

After doing "Rebuild BS" I had a message "Extrapolated boot sector and current boot sector are identical" also I don't seem to have a 'write' option. I have a 'Dump' one though...

---

### Post by caljohnsmith on 2008-10-22
> **Mount said:**
> really I can't thank you enough for going through this with me. I'm completly lost otherwise.

After doing "Rebuild BS" I had a message "Extrapolated boot sector and current boot sector are identical" also I don't seem to have a 'write' option. I have a 'Dump' one though...
You're welcome, glad to help out when I can. :) Since your Windows boot sector is OK according to testdisk (the boot sector matches with the backup boot sector), you can go ahead and quit testdisk. If you have your Windows Install CD, I would recommend booting that, go to the "recovery console", and running:
```
chkdsk /r
```
And run chkdsk as many times as necessary until it reports no errors. After that reboot, try Windows again, and let me know what happens.

---

### Post by Mount on 2008-10-22
I don't think i have the windows cd is was a preinstalled machine. Is there another way round? 
Could I use any Windows XP CD?
cheers,

---

### Post by caljohnsmith on 2008-10-22
I think you're most likely going to need your Windows Install CD, but since you don't have one, you can download a Windows Recovery CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip"). That will at least let you run the "chkdsk" command, but I'm doubtful that a chkdsk will be enough to fix Windows. You will probably have to do a Windows Repair, but you'll need your Win Install CD for that.

---

### Post by Mount on 2008-10-22
Hi, I found a XP Cd and did what you said and seemed to finish fine. Not when I select 'Windows' from the grub menu i still get 
the "Starting up ..."

Regarding windows disks. I have an XP cd but it is not the same one that was used to install windows on my machine. Could this be used to perform the Windows repair?

---

### Post by caljohnsmith on 2008-10-22
> **Mount said:**
> Hi, I found a XP Cd and did what you said and seemed to finish fine. Not when I select 'Windows' from the grub menu i still get 
the "Starting up ..."

Regarding windows disks. I have an XP cd but it is not the same one that was used to install windows on my machine. Could this be used to perform the Windows repair?
I think you can use the other Windows CD to do the repair, but it will ask you for your product key I believe; you'll need to find the product key if it is a sticker on your laptop or somewhere else.

---

### Post by Mount on 2008-10-22
Then is would seem that we've been foiled!

I have just found the Windows Recovery Disk which came with this computer. I tried to run the repair thing. Problem is i don't seem to know the administrator password ](*,)

why? why? why?

---

### Post by caljohnsmith on 2008-10-22
> **Mount said:**
> Then is would seem that we've been foiled!

I have just found the Windows Recovery Disk which came with this computer. I tried to run the repair thing. Problem is i don't seem to know the administrator password ](*,)

why? why? why?
If you google it, I know there are many ways to recover the admin password for Windows; I just don't remember any off-hand since I've never had need for them. Good luck. :)

---

### Post by Mount on 2008-10-22
Yes! Sorted. 

Thanks for your guidance caljohnsmith. I really apreciate it.

Here's the final solution: 

In the BIOS I changed the 500GB drive (the one with XP on) to be
second in the Hard Drive sequence. Then I changed the Window grub command to be:

```

grub> root (hd1,0)
grub> chainloader +1
grub> map (hd0) (hd1)
grub> map (hd1) (hd0)

```

taken from this site [http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q5](http://www.gnu.org/software/grub/grub-legacy-faq.en.html#q5) 

finally ... time for bed

---

