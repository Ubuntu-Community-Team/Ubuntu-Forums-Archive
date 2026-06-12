---
title: "Ubuntu Gnome 13.10 Fresh install - Kernel Panic error"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by averos on 2013-10-18
I was running 13.04 Ubuntu on my machine until last night. I was using Gnome Shell which was installed besides the default unity. Last night i decided to upgrade by replacing my 13.04 with Ubuntu Gnome 13.10. Downloaded the CD image from Ubuntu Gnome site and burned it on my USB using UNetbootin. I checked the MD5SUM and everything looked in order. I was successfully able to boot into the LiveCD and the entire installation went without any issues or problems. When i was prompted to restart after install i selected the Ubuntu option from boot loader and suddenly capslock started flashing and the screen was stuck at blank. After waiting for a while, i did a hard shut down by pressing the power button and tried to restart again, and since then i see the Kernel panic error that goes like this:

```
Kernel panic - not syncing: No init found.  Try passing init= option to kernel.  See Linux Documentation/init.txt
```

I have redownloaded the CD and repeated all steps again and same results. I also tried installing after deleting recreating boot partitions using GParted instead of using the partitioning option that runs within the installer to no avail.


Right now i am using my computer form my USB stick and everything seems to be running fine so i am not sure what is different between this version running from USB vs what has been installed on the hard drive. Is there a way to fix this issue? 

Any ideas will be much appreciated as i really don't have anything functioning besides this USB live cd that i can use for computing.

---

### Post by averos on 2013-10-18
I have now tried installing regular Ubuntu 13.10 and I have run into exact same issue. On first restart the machine gets stuck on purple screen and caps lock starts flashing. I left it like that for a while and nothing changed. On hard restart using power button I get same Kernel panic error.

Guess it is time to change to a different distro after 4 long years :-D

---

### Post by averos on 2013-10-19
Finally was able to fix it. I used GParted to delete the root partition as well as the swap. Then instead of recreating these partitions i ran installer and picked the option which offers to install Ubuntu Gnome besides Windows as opposed to the option which lets you tweak the partitions. This seems to have done the trick.

---

### Post by iloutzu on 2013-10-19
> **averos said:**
> Finally was able to fix it. I used GParted to delete the root partition as well as the swap. Then instead of recreating these partitions i ran installer and picked the option which offers to install Ubuntu Gnome besides Windows as opposed to the option which lets you tweak the partitions. This seems to have done the trick.

Averos, did the installer pick up your existing partitions? Can you please tell me your partitioning scheme before and after the install? Thanks!

---

### Post by xKJnyk4 on 2013-10-19
I have the exact same problem but chosing the option to install ubuntu besides windows  do not allow me to chose the my SSD. any other Solutions?

---

### Post by heir4c on 2013-10-19
Choose the option "try something else' (the last option in the list). Then you can select the disk and partition you want.

---

### Post by xKJnyk4 on 2013-10-19
> **heir4c said:**
> Choose the option "try something else' (the last option in the list). Then you can select the disk and partition you want.

That's what i'v done but doing that i have this error:
```
[COLOR=#000000][FONT=Ubuntu Mono]Kernel panic - not syncing: No init found.  Try passing init= option to kernel.  See Linux Documentation/init.txt[/FONT][/COLOR]
```
and i'm not able to boot the System.

---

### Post by averos on 2013-10-19
I was using "try something else" option and it resulted in this kernel panic error. Here is what i did in the last successful attempt.

1) Booted from Live USB.
2) Ran GPARTED.
3) Deleted the Partition that has root ( / ) mounted on it.
4) Deleted the Swap partition.

I left alone my other linux ext4 partition which i call "Data" and use for keeping my data separate from System partition . I also did not touch my Windows partitions. So in the end i had my windows partition intact as well as one other logical partition intact on extended partition. I have enclosed the two drives i deleted in black box in the attached screenshot. I did not try to create new partitions in the freed up space and left it alone. So basically there was grayed out "unused space" label where the black box is.

5) Let GPARTED finalize the delete operations and closed it.
6) Ran the installer.
7) On the screen where it gives you installation options, it showed me an option that offers to install Ubuntu Gnome besides Windows. I picked that option instead of the option i had used earlier i.e. "try something else". I was a little concerned that it might wipe out my "Data" partition on extended drive, but it didn't do it and i have everything in place.
8) Once the installation was done it worked without any issues for me.

I hope it helps, let me know how it goes and Good luck!

---

### Post by heir4c on 2013-10-19
xKJnyk4, If the above post don't help, maybe a screenshot of gParted and/or from the installer (where you see the partitions before installing) would be help us to help you and to see what you see.

---

### Post by xKJnyk4 on 2013-10-20
1) I tried to delete the previus ext4 partition from my SSD with Gparted(only Windows on it now): [http://imageshack.us/f/405/2837.png/](http://imageshack.us/f/405/2837.png/)
2) I proceded with the istallation but  chosing "install ubuntu along them" option, but now i can't select my SSD. On the Select drive menu there is only the default choice available: [http://imageshack.us/f/31/oinz.png/](http://imageshack.us/f/31/oinz.png/)
3) To be able to select my SSD drive and install Ubuntu in the same drive of Windows i manually mounted the 500GB drive partitions and the 1.5 TB drive before the installation. Now i can select the SSD but the installar crashes. It seems to crash because of insufficient free space, here is an example of how the automatic tool partitions the drive: [http://imageshack.us/f/19/kg71.png/ ]("http://imageshack.us/f/19/kg71.png/")
it will start isntalling ubuntu on the 2.9GB partition and crash when is full.
4) so i manually partitioned the drive keeping the swap and making a 10GB unallocated partition. the isntallation completes but i have the exact same kernel panic error as before.

---

### Post by heir4c on 2013-10-20
Is it solved or not? 
Have you MBR (i think yes) or UEFI?
Maybe if you have just MBR than he can't see so far on the drive. The Ubuntu parition is too far on the drive. I don't know how far the MBR can see for the init file. So maybe you have to bring Ubuntu more to the beginning of the HD/SSD.

---

### Post by averos on 2013-10-20
> **xKJnyk4 said:**
> 1) I tried to delete the previus ext4 partition from my SSD with Gparted(only Windows on it now): [http://imageshack.us/f/405/2837.png/](http://imageshack.us/f/405/2837.png/)
2) I proceded with the istallation but  chosing "install ubuntu along them" option, but now i can't select my SSD. On the Select drive menu there is only the default choice available: [http://imageshack.us/f/31/oinz.png/](http://imageshack.us/f/31/oinz.png/)
3) To be able to select my SSD drive and install Ubuntu in the same drive of Windows i manually mounted the 500GB drive partitions and the 1.5 TB drive before the installation. Now i can select the SSD but the installar crashes. It seems to crash because of insufficient free space, here is an example of how the automatic tool partitions the drive: [http://imageshack.us/f/19/kg71.png/ ]("http://imageshack.us/f/19/kg71.png/")
it will start isntalling ubuntu on the 2.9GB partition and crash when is full.
4) so i manually partitioned the drive keeping the swap and making a 10GB unallocated partition. the isntallation completes but i have the exact same kernel panic error as before.

Sorry i am not really an expert and a little vague on your situation but let me try.

In your last screen shot i see extended partition sdb3 divided into three sections.
unallocated 2.9 GB
Swap 250 MB
unallocated 7.01 GB

Have you tried deleting the 250 Swap and again letting Ubuntu try and install besides the Windows using that option?  When you delete 250 MB Swap it should result in one big unallocated space which will be a little over 10 GB in size.

I am guessing all your partitions sdb1,sdb2,sdb3 are on the same physical drive, correct?

---

### Post by xKJnyk4 on 2013-10-21
> **averos said:**
>  Have you tried deleting the 250 Swap and again letting Ubuntu try and install besides the Windows using that option?  When you delete 250 MB Swap it should result in one big unallocated space which will be a little over 10 GB in size.

I am guessing all your partitions sdb1,sdb2,sdb3 are on the same physical drive, correct?

yes i tried but it crashes for insufficient free space. and yes sdb1,sdb2 are windows partitions.

---

### Post by xKJnyk4 on 2013-10-21
> **heir4c said:**
> Is it solved or not? 
Have you MBR (i think yes) or UEFI?
Maybe if you have just MBR than he can't see so far on the drive. The Ubuntu parition is too far on the drive. I don't know how far the MBR can see for the init file. So maybe you have to bring Ubuntu more to the beginning of the HD/SSD.

I'm sorry but i'm not an expert user and i'm not sure about what are u asking. how can i know i have this MBR? 
what i can tell is that with the same partitions scheme i was running ubuntu 13.04 with no issues.

btw ty for the help guyz!

---

### Post by heir4c on 2013-10-21
To delete the swap partition you must set it off. In gParted (Partition Manager) you can right click on it and choose: Swapoff. Than you can delete it.

MBR is on old computers and it is needed to boot up Windows. Now there is GPT (I write UEFI but It's GPT, I have not yet experience with it. UEFI is the "new" BIOS)
I can give you a few links, but search for it via Google or wikipedia or on this forum (My English is not so good to explain it correctly):
[http://www.overclockers.com/forums/archive/index.php/t-611465.html](http://www.overclockers.com/forums/archive/index.php/t-611465.html)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by xKJnyk4 on 2013-10-22
i tried installing ubuntu using the option to erase the drive and install ubuntu. and it was not booting. then i tried the efi installation and it finally WORKS, now i have to reinstall windows in dual boot, do i need to install it in uefi mode or i can install it normally?

(before installing 13.10 in efi mode i tried to install the old 13.04 and it was not booting too. seems strange that i installed it normaly 1 week ago and now it works only in efi mode)

---

