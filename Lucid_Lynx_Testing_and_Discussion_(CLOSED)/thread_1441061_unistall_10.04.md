---
title: "unistall 10.04"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lochbroom on 2010-03-28
I have 10.04 installed with Windows 7 and it works great but how does one uninstall it. I would like to reinstall it to a separate partition.

Thanks John

---

### Post by Sef on 2010-03-28
1) Moved to Lucid.

2) How did you install Lucid?

---

### Post by VMC on 2010-03-28
> **lochbroom said:**
> I have 10.04 installed with Windows 7 and it works great but how does one uninstall it. I would like to reinstall it to a separate partition.

Thanks John

You could just use gparted and copy to desired partition. Keep in mind though both will have same UUID. use tune2fs to change the old partition, or just delete it. You can also use the dd command.

Are you using windows boot manager or grub to boot?

---

### Post by kansasnoob on 2010-03-28
> **lochbroom said:**
> I have 10.04 installed with Windows 7 and it works great but how does one uninstall it. I would like to reinstall it to a separate partition.

Thanks John

So is this a Wubi install?

Since you say, "I would like to reinstall it to a separate partition.", it makes me think that.

If so you remove it like any other piece of software in Windows. (add or remove)

---

### Post by garvinrick4 on 2010-03-28
There is a folder in C: drive that says Ubuntu right next to Users, in that folder is a uninstall. Better to use that. Every once in a while using Add & Remove programs in Windows leaves the wubi in the Windows bootloader. You can check by command line
in Windows 7 or Vista by useing Code: "bcdedit" without quotes and see if there is an
entry with wubibllder or something close to that in any of the entries. There is a easy way
to remove it so if it is there it is no disaster. But it will screw up the next grub install.

---

### Post by lochbroom on 2010-03-28
Thanks for the help. I just booted from the CD and let it install, I accepted every default and let it go merrily on it's way. It installed nicely and it picked up my wireless connection and everything seems to work fine. 

On the first boot screen I have the option to tab to Windows 7 or stay with 10.04.

Funny I dont see any trace of it on my hard drive, not in Add/Remove programs or anywhere. I have all the 'views' turned on in Folders Option. Not under 'U' either in Explorer.

It doesnt appear to be a dual boot situation. I know it is a Beta but it seems to work well so all I want to do is take it off and put it back on an empty partition.

Thanks...John

---

### Post by garvinrick4 on 2010-03-29
> **lochbroom said:**
> Thanks for the help. I just booted from the CD and let it install, I accepted every default and let it go merrily on it's way. It installed nicely and it picked up my wireless connection and everything seems to work fine. 

On the first boot screen I have the option to tab to Windows 7 or stay with 10.04.

Funny I dont see any trace of it on my hard drive, not in Add/Remove programs or anywhere. I have all the 'views' turned on in Folders Option. Not under 'U' either in Explorer.

It doesnt appear to be a dual boot situation. I know it is a Beta but it seems to work well so all I want to do is take it off and put it back on an empty partition.

Thanks...JohnType this in a Terminal:
sudo fdisk -l   (that is a small L ) can you copy and paste it in this thread. You just might have a install and not a WUBI in a folder!!!

---

### Post by mdurham on 2010-03-29
> **garvinrick4 said:**
> Type this in a Terminal:
sudo fdisk -l   (that is a small L ) can you copy and paste it in this thread.  He means do the above from within Ubuntu

> You just might have a install and not a WUBI in a folder!!!
Sounds like that to me.

---

### Post by lochbroom on 2010-03-29
Here is the dump on fdisk...John

Disk /dev/sda: 100.3 GB, 100256292864 bytes
183 heads, 34 sectors/track, 31471 cylinders
Units = cylinders of 6222 * 512 = 3185664 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9b599b59

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12785    39774118    7  HPFS/NTFS
/dev/sda2           21596       26618    15624758    7  HPFS/NTFS
/dev/sda3           12786       21596    27408384+   5  Extended
/dev/sda4           26619       31253    14416896   83  Linux
/dev/sda5           12786       16986    13068100   83  Linux
/dev/sda6           21218       21596     1176576   82  Linux swap / Solaris
/dev/sda7           16987       21024    12559360   83  Linux
/dev/sda8           21024       21217      602112   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 999 MB, 999555072 bytes
255 heads, 63 sectors/track, 121 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x002c6701

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         122      976096+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(120, 254, 63) logical=(121, 133, 12)
john@john-desktop:~$ ^C
john@john-desktop:~$

---

### Post by shindou01 on 2010-03-29
yes that looks like an install and not a WUBI....if it is an install then worry not as you already have it on another partition created by the installation...you wont see the Ubuntu partition on Windows 7...I also use Windows 7 and Lucid Lynx beta1...
if you've installed it the way I did then It's already in another partition...
My dual boot screen is GRUB which is Ubuntu's default I assume (I'm also a noob here) and not windows dual boot screen :D...

---

### Post by lochbroom on 2010-03-29
Ok, Shindou01, thanks and that is exactly as I have it, not a dual boot as such but I do have the option of picking Win 7 on the initial screen. 

I dont see partition in Win7 but I do see it on Lucid.
I'm just tinkering and trying to learn as I go as this maybe the OS for my laptop after Beta.

Someone may know how to uninstall.

Thanks again...John

---

### Post by VMC on 2010-03-29
> **lochbroom said:**
> I have 10.04 installed with Windows 7 and it works great but how does one uninstall it. I would like to reinstall it to a separate partition.

Thanks John

Now that we know you have ubuntu installed on a separate partition, do you still want to move it?

Also to get a bigger picture of your boot process, download boot_info_script(see my blue link), and run it. It will dump a file named RESULTS.txt

---

### Post by lochbroom on 2010-03-29
Ok, VMC thanks very much.....was that a good way to install it, I mean how I did it?

How would you install, using 'virtual box' or do as I did?

Thanks  John

---

