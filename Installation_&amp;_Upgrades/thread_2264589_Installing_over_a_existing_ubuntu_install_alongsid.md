---
title: "Installing over a existing ubuntu install alongside windows"
date: 2015-02-08
forum: Installation &amp; Upgrades
---

### Post by hebdave on 2015-02-08
I have windows 7 and Ubuntu 14.04 Lts. If I want to overwrite the ext.4 partition using "something else " in the installer do I do the following this from this forum -

[COLOR=#000000][INDENT]Firstly, make sure you know what partition your 11.10 installation is on. MAKE SURE YOU BACKUP ALL YOUR FILES before you do anything in Windows and Ubuntu! 

After booting from Ubuntu live cd, wait for it to load and click 'install Ubuntu'. Follow the onscreen instructions. Soon it will ask you where to install your new system. You need to use the installation option**'something else'** from the installation menu that comes up on the screen. The next menu that appears will show your partitions, one for Windows and one for Ubuntu. You can identify fairly easily the one with Ubuntu on it as Windows partitions will be marked as 'NTFS' file system. Ubuntu is Ext4 files sytem. Now, I'm going from memory here but I believe Windows has to be the primary partition and Ubuntu will be in an extended partition with it's own swap file at the end somewhere. You don't need to do anything will the swap file, it sorts itself out. But you need to highlight the main Ubuntu extended partition and click 'change'. Select the file system you wish to use from the drop down menu, this is normally 'ext4 journaling. To overwrite it without removing your files and programs do NOT click format the partition. However, I believe to get the best results it's best to do a clean install by formatting this partition. If you wish to do this just tick the 'format' box. This is easy if you have backed up your files, but the choice is yours. Just remember it overwrites all files which will be lost if you haven't backed them up.

At this point you need to mark this partition as '/'(root) from the menu options by selecting it from the drop down menu. Don't do anything to the swap file partition. That will sort itself out. Now just click 'forward'. Ubuntu will now install over your old version and install the bootloader Grub so you have a dual boot system.[/INDENT]


[/COLOR]

Please note I was considering installing over Ubuntu with Zorin. However how would I adapt the above for adding a 3rd operating system ( a 2nd distro).

I am a novice. Step by step like the above is clear enough for me (assuming its right). A break down of the steps used is even better again if possible.

Hope that is not asking to much and many thanks. :)

---

### Post by yancek on 2015-02-08
> [COLOR=#000000]Now, I'm going from memory here but I believe Windows has to be the primary partition [/COLOR]

No, but to install it the boot files need to be on a primary.  I don't see what difference it makes, you already have windows installed. 

> [COLOR=#000000] Ubuntu will be in an extended partition with it's own swap file[/COLOR]

An Extended partition is a primary partition and when used as an Extended partition, can create logical partitions within the Extended.  You can't put data in an Extended partition.  Generally a swap 'partition' is created and if you already have Ubuntu 14.04 installed you most likely have a swap partition.  Leave it alone.

Determine which is the Ubuntu / (filesystem) partition.  Open a terminal and run;  sudo df -h, the output should be similar to the below which shows root (/) on sda8.  you w

```
df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda8        39G   25G   13G  66% /
```

You select the '/" symbol in the drop down box to the far right of Mount point.

If you want to install Zorin in addition to Ubuntu, you would first use the Live DVD or whatever installation medium you have for Zorin, use GParted to shrink one of your partitions to create unallocated space or use current unallocated space or use a partition that you are willing to overwrite, if you have one.  You would repeat all of the steps above selecting the new partition for Zorin.  Ignore the swap.

---

### Post by sudodus on 2015-02-08
I think you got it right :-)

Backup first!

Added instruction: Make sure that you*** install the bootloader*** (look at the bottom of the partitioning screen) into the head of the correct drive, normally (but not always) the same drive as you install Ubuntu into,

**/dev/sda**

Do *not* add any digit for a partition.

-o-

What is enough space? It depends how you intend to use the linux  systems. 8 GB is enough for each linux installed system to run well, and  they can share the same swap partition. If you intend to hibernate, you  need as much swap as RAM in Gibibytes (base 2), otherwise 1 or 2 GB is  enough.

If you want to run one of the linux systems as your working environment I  would suggest that you give it at least 20 GB plus a data partition,  that might be shared with Windows. But do not use the Windows system  partition as data partition. Use a separate data partition.

-o-

You want to add another distro (and make it triple boot). If there is not enough space, you should boot into Windows and use  Windows tools to shrink the Windows partition. Reboot into Windows and  let it get happy with the new size.

Now you can use also the unallocated space for the two linux partitions. Boot from the Ubuntu install drive 'Try Ubuntu' and run ***gparted***. This is a partitioning tool, that is easier to use than the one built into the installer. If you have enough drive space for Ubuntu now for two separate linux distros, fine, go ahead. It is easier and faster to remove the current ext4 partition and then create two ext4 partitions. Click the green tick icon to make gparted really perform the editing operations.

After these operations, you can start the installer according to your original plan (using 'Something else').

---

### Post by hebdave on 2015-02-09
Thanks for all the help.

---

