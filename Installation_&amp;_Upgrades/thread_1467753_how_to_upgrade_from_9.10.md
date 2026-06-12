---
title: "how to upgrade from 9.10"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by archithcr on 2010-05-01
hi

i've downloaded the live cd image for 10.04 and ran a live session and was happy with the performance on a asus eee 1005HA. 

i have a 250 GB hard disk, with the setup as follows. 

[IMG]http://img688.imageshack.us/img688/5160/diskmap.gif[/IMG]

the 18.8 + 1 GB partition is where i've installed ubuntu 9.10 and swap respectively.

so i clicked on the " Install ubuntu 10.04" button on the live cd desktop.
When it comes to the hard disk screen, the installation gives me two options, 
1) install 10.04 alongside existing operating systems (which includes Karmic)

2) Overwrite existing hard disk

3) advanced options.

now, i want to know, if i delete the partitions for Karmic in Windows with Easeus, resize my windows partition to split the space between windows and Lucid Lynx equally and then run the live cd installation, will i get the option to choose largest available free space under advanced installation?

or would deleting the 9.10 partition affect GRUB 2, rendering my computer ubootable?

what would be the best way to do a clean removal of karmic, and a fresh install of lucid lynx?  or is the alternate CD image the only way to go ahead?

any help would be appreciated.

Thanks

:)

---

### Post by mahela007 on 2010-05-01
I'm no expert on formatting. However, instead of the software you are currently using to format, you might want to use Gparted which is available on the live CD by default. It allows you to see (interactively) what you want to do with your hard drive before actually applying the changes. Sorry I couldn't give a more direct solution..

---

### Post by Don1500 on 2010-05-01
> what would be the best way to do a clean removal of karmic, and a fresh install of lucid lynx?  or is the alternate CD image the only way to go ahead?

any help would be appreciated.

Thanks

:)

I would use gparted also (If nothing else but to format the NON-WINDOWS partitions as ext4) but lets see what we can do with what you are showing.
Partition #1 (C: ) is your windows partition and should not be touched. Do not format this partition.
#2 and #3 look like where you wish to place Lynx. I would resize these to #2 = 3 gig and #3 = 16 gig, if you reformat these during install the mount points should be: #2 = "/" and #3 = "/home", doing that will completely remove Karmic.
NOTE: Because #5 is so small you may want to forget it and take 2 gig from #3 to make a swap partition,
#4 is a hidden FAT32 partition, probable where your recovery files for windows are kept. Do not format this partition.
#5 is a small partition that could be used for SWAP, although it is kind of small (Swap should be 2X RAM.) You will have to delete this partition if you make the swap as described above. If you want,add #5 to #4 (Only 4 logical partitions allowed), but make sure you do it right, you don't want to mess up #4, DO NOT FORMAT THIS PARTITION.

In gparted all this can be set up and then run like a program. Using your mouse on the graphic and doing the steps to make it look like what you want, such as:
1. Resize #2 = 3 gig
2. Resize #3 = 14 gig
3. Delete #5
4. Make #4 SWAP = 2 gig (This is a new #4, the old #4 is now #5)
5. Resize #5 (the old #4) to include the space from the deleted #5
Then hit APPLY and it will be done.

This sounds a lot harder than it actually is.

---

### Post by archithcr on 2010-05-01
hey, thanks for the replies. i don't have problems with the partitions  themselves, although why Asus reserves 16 MB for the boot booster program is beyond me.

my only concern was that removing or formatting the karmic partition would affect GRUB2 somehow. but if i use Gparted during the Lucid install and reformat the home and swap partitions, i would get a Grub with Windows 7 option post intall right?

Sorry if i sound paranoid. i use karmic for personal use, but for official use, when we make presentations, i have to fall back on windows for network connections as well as projector connects.

thanks for the inputs guys :)

---

### Post by Don1500 on 2010-05-01
> **archithcr said:**
> hey, thanks for the replies. i don't have problems with the partitions  themselves, although why Asus reserves 16 MB for the boot booster program is beyond me.

my only concern was that removing or formatting the karmic partition would affect GRUB2 somehow. but if i use Gparted during the Lucid install and reformat the home and swap partitions, i would get a Grub with Windows 7 option post intall right?

Sorry if i sound paranoid. i use karmic for personal use, but for official use, when we make presentations, i have to fall back on windows for network connections as well as projector connects.

thanks for the inputs guys :)

When you install Lynx it will reinstall grub2 and include windows.

---

