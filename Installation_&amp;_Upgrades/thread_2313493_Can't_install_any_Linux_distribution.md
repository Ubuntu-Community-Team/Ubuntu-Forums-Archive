---
title: "Can't install any Linux distribution"
date: 2016-02-13
forum: Installation &amp; Upgrades
---

### Post by Christophe_Duchesn on 2016-02-13
I have a HP Pavilion notebook 17 -g078.ca. processor i5-5200U, 12 Gb of RAM and a 250 GB SSD(that I intalled myself)
My laptop came with windows 10 and for my class we need a Linux partition.I followed all the instruction; I made an Ubuntu bootable USB, I disabled my windows fast startup, I modified my booting order on my bios and finally I even disable my security boot in my bios. I started my laptop with my usb key in. I am able to try ubuntu, everything work just fine. When I clic on the installation icon I can select my language and continue, after I'm getting in the "preparing to install ubuntu" menu, I have enough memory and my laptop is plugged to a power source so I can click on the continue button. But then when I click on the button "continue" it start running for ever and the next page never show up. (waited like 3 hours the first time). I tried a lot of distributions (Mint, Archliux and other) but the same bug occurs. I have search in so many forums but nobody seams to have the same bug as me... Even my teachers who's an expert in linux doesn't know the problem. I tried so many thing from the forum but doesn't work. The only modification I made on my PC is to switch my 2Tb HDD to a 250Gb SSD samsung evo. 

If you need any other specification about my laptop let me know, hope you can help me be a part of Linux.
:D

---

### Post by sudodus on 2016-02-13
Welcome to the Ubuntu Forums :-)

When booted into the live session of Ubuntu, 'Try Ubuntu', you can check the SSD. Use the hotkey combination ctrl + alt + t to start a terminal window, and run the following commands

```
sudo parted -ls  # ... space minus ell ess

sudo lsblk -fm
```

Please post the output of the commands (copy and paste into a reply window and put it within [noparse]```
tags
```[/noparse].

-o-

Maybe you have no partition table in the SSD. If that is the case we will see it from the output of those commands. You can create a partition table with ***gparted*** (while running the live session of Ubuntu, 'Try Ubuntu'). There is also the complication of UEFI mode and BIOS mode. If you want to switch easily between the Windows drive and the Ubuntu SSD you should run Ubuntu in UEFI mode, and use a GUID partition table. Otherwise it is easier to switch to BIOS mode and use the old style MSDOS partiiton table.

See the following links and links from them for more details

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

---

### Post by Christophe_Duchesn on 2016-02-13
Since I don't have any internet connection on my bootable key and no ethernet cable until monday, I hab no choice but to take a picture with my cellphone, really sorry.

hope you can help me.

---

### Post by sudodus on 2016-02-13
***parted*** says that you have a GUID partition table (GPT), but gets and error and cannot list any partitions.

***lsblk*** finds four partitions in the SSD identified as /dev/sda

```

/dev/sda                232.9G
/dev/sda1 vfat            260M 
/dev/sda2                 128M
/dev/sda3 ntfs Windows    120G
/dev/sda4 ntfs            898M

```

There seems to be unallocated drive space in the SSD, which should be possible for Ubuntu to identify. Maybe we can see the partitition table with ***gparted*** started from the System menu in Mint or Dash in Ubuntu, when booted live. Please take a picture of the SSD's partitions and attach it like before :-)

- How did you create the content (partition table, partitions and file systems, and files) in the SSD?

- Which distro and version were you running live, when you made that screenshot (Mint xxx, Ubuntu xxx ...)?

- Were you running in UEFI or BIOS mode? Test it with the following command line:

```
test -d /sys/firmware/efi && echo efi || echo bios
```

- Can you run Windows from the SSD? In that case, please take a picture of the partitions, 'drives' in Windows language, and attach it like before :-)

-o-

***This is very risky***, and you might destroy everything on the drive including Windows. So you need some kind of ***backup*** or at the very least Windows recovery disks, so that you can reinstall it (without paying for it again).

You might be able to repair the partition table with ***gdisk***. Install it (temporarily) into the live session with

```
sudo apt-get install gdisk

sudo gdisk /dev/sda
```

and try to repair it (in recovery mode or expert mode)

-o-

If you are free to overwrite everything, it is probably straightforward to use mkusb to wipe the SSD and create a new partition table.

[mkusb](https://help.ubuntu.com/community/mkusb)
[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

And after that it should be easier to install Ubuntu (or another linux distro).

***Edit:***

If you created new partitions in Windows, they might be dynamic partitions, which do not work in linux. In that case they should be removed (by Windows) and the space should be left unallocated. New partitions can be made from a live session of Ubuntu (or another linux).

---

### Post by Christophe_Duchesn on 2016-02-13
I don't know how I created the content ( there is 110Gb unloccated in my ssd)
I'm trying Mint cinnamon 17,3 right now
When I typed the following line:[COLOR=#000000][FONT=Ubuntu Mono]test -d /sys/firmware/efi && echo efi || echo bio:
```

efi

```

I have a windows backup so I will try gdisk

thanks. [/FONT][/COLOR]

---

### Post by sudodus on 2016-02-13
You have a GUID partition table and are running in UEFI mode: Good to know :-)

After fixing the partition table with gdisk you reboot into a live session and start gparted which has a graphical user interface. Let us hope that you will see the unallocated space (similar to what you see in Windows).

I suggest that you do no intend to hibernate the computer, because then you need a swap partition with at least 12 GiB approx= 13 GB. Otherwise it is probably enough with 2 GB swap unless you know that you will strain the memory of the computer and expect a lot of swapping 'linux swap'. The rest of the unallocated space can be used for the root partition.

After that you start the installer. Select ***Something else*** at the partitioning window and select the big new partition as ext4, root = /, and format it.

The swap partition should be selected automatically. Since it is UEFI mode, I think the bootloader will be automatically using the EFI partition with a FAT file system. You cannot and need not bother about it with Ubuntu. I'm not sure about Linux Mint, but I think it is similar.

---

### Post by Christophe_Duchesn on 2016-02-13
But there is a lot of command on gdisk and I'm not really sure which command should I use ^

---

### Post by sudodus on 2016-02-13
In the first menu:

```
r     recovery and transformation options (experts only)
x     extra functionality (experts only)
```

In the following lists I high-light commands that might be useful in your case.

In the recovery and transformation menu:

```
Recovery/transformation command (? for help): ?
[B]b	use backup GPT header (rebuilding main)
c	load backup partition table from disk (rebuilding main)
d	use main GPT header (rebuilding backup)
e	load main partition table from disk (rebuilding backup)[/B]
f	load MBR and build fresh GPT from it
g	convert GPT into MBR and exit
h	make hybrid MBR
i	show detailed information on a partition
l	load partition data from a backup file
m	return to main menu
o	print protective MBR data
[B]p	print the partition table
q	quit without saving changes[/B]
t	transform BSD disklabel partition
[B]v	verify disk
w	write table to disk and exit[/B]
x	extra functionality (experts only)
?	print this menu
```

In the expert menu:

```
Expert command (? for help): ?          
a	set attributes
c	change partition GUID
d	display the sector alignment value
**e	relocate backup data structures to the end of the disk**
g	change disk GUID
h	recompute CHS values in protective/hybrid MBR
i	show detailed information on a partition
l	set the sector alignment value
m	return to main menu
n	create a new protective MBR
o	print protective MBR data
[B]p	print the partition table
q	quit without saving changes[/B]
r	recovery and transformation options (experts only)
s	resize partition table
t	transpose two partition table entries
u	Replicate partition table on new device
[b]v	verify disk
w	write table to disk and exit[/b]
z	zap (destroy) GPT data structures and exit
?	print this menu
```

If they do not help, you might try with ***testdisk*** from the following link

[https://www.cgsecurity.org/](https://www.cgsecurity.org/)

---

### Post by Christophe_Duchesn on 2016-02-13
Doesn't work..

---

### Post by Christophe_Duchesn on 2016-02-13
Thank you for your help, I'm going to try again.

---

### Post by sudodus on 2016-02-14
Did you try with ***testdisk*** from the following link?

[https://www.cgsecurity.org/](https://www.cgsecurity.org/)

-o-

- What does not work? The same problem as in post #1, that the installer gets stuck:> But then when I click on the button "continue" it start running for ever and the next page never show up. or is there another problem now?

- Is Windows still working?

- Did you install Ubuntu, but the installed Ubuntu system does not boot?

It seems to me, that for some reason there was and maybe is a problem with the partition table. One alternative is to start from the beginning, and create a fresh GUID partition table (GPT).

- Do you need both Windows and Ubuntu?

- If yes, are you prepared to reinstall Windows?

- Would it be enough to boot and run Ubuntu from an external drive, for example from a fast USB 3 pendrive? See this link

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by Christophe_Duchesn on 2016-02-14
finaly I whiped out all my disk and created a new partition with fdisk, is it possible with the terminal to install linux on that new terminal ?
Yes same problem and no windows at all now(still have my copy). I can live without windows and yes for my classes Linux should be in my computer.

---

### Post by Christophe_Duchesn on 2016-02-14
And since I'm partitioning a new partition, wich system file should I use ? NTFS volume set, GPT, EFI  ?

---

### Post by Christophe_Duchesn on 2016-02-14
OMG IT WORK ,thank you so mutch

---

### Post by sudodus on 2016-02-15
Congratulations :KS

You succeeded while it was night here :-) Please share your solution - it can help other users!

And finally, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by Christophe_Duchesn on 2016-02-16
I used the fdisk method to clean all my SSD and created a partition. I did exactly every step from this video : [https://www.youtube.com/watch?v=5kVAzxTwy5Q](https://www.youtube.com/watch?v=5kVAzxTwy5Q). Except when we have have to chose a system file type where I chose a GTP system type instead of  FAT32 like you proposed to me. After reformatting my entire SSD, the installation was a piece of cake and I can if I choose to, reinstall my windows partition. 


Thank you and have a good week.

---

### Post by kurt18947 on 2016-02-16
If you install Windows, you might break your Linux bootloader. You are using GPT/UEFI which might be different but using legacy BIOS, Windows will overwrite GRUB and it's necessary to create a repair disk. I wouldn't install Windows late on a Sunday nite if I needed linux early Monday morning. Make sure you have time to fix any breakages from installing Windows.

---

