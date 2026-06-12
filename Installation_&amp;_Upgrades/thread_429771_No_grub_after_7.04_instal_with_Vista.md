---
title: "No grub after 7.04 instal with Vista"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by mohawk622 on 2007-05-01
I am a new Ubuntu user with little linux experience.  I have windows Vista installed on the first petition of my hard drive.  The second petition is for Windows data.  The third petition I have used to install Ubuntu.

After installation, there is no grub in my boot menu.  The machine just boots up to windows Vista.

I have tried a second installation of Ubuntu, but still no grub, and the machine boots directly into windows Vista.

What is wrong?  I really would like to get a Ubuntu working.  I haven't googled all over trying to find a solution to my problem, but none seems to be available.  Does anyone have any ideas.

Thanks for any help that you might have.

---

### Post by bulldog on 2007-05-01
We have always ideas,but if they work..........:) 

Boot the ubuntu install cd and when you come to the desktop,open a terminal and copy and paste the commands.
You have just one hdd?Look carefully for any error it will return to you and copy and paste any error to the forum please.

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

If you encountered no errors,you can reboot.

---

### Post by mohawk622 on 2007-05-01
Thanks for you help.

I got this:
 grub> find /boot/grub/stage1
 (hd1,2)
Then:
grub> setup (hd1,2)

Error 12: Invalid device requested

Any other ideas?

Thanks

---

### Post by bulldog on 2007-05-01
Hmmm,you have more than one hdd?
```
sudo fdisk -l
``` it's a lowercase L
Can you give me the output of this command?

---

### Post by pinoytechie on 2007-05-01
This is for XP, i don't know if Vista has the same boot mechanism...

[GRUB4DOS]("http://sourceforge.net/projects/grub4dos")

1. Extract GRUB4DOS package file to a temporary folder
2. Copy grldr file from it to C:\
3. Edit C:\boot.ini (using notepad) and add the following line at the bottom:

    ```
C:\grldr="GRUB4DOS"
```

4. Save c:\boot.ini
5. Create a new text file and put the following lines:

 ```
   timeout 30
    default 0

    title My Beloved Ubuntu!
    root (hd?,?)
    kernel /boot/<your_kernel_filename> <kernel_params>
    initrd /boot/<your_intial_ramdisk_image>
```

6. Save this new text file "menu.lst" in C:\ as this is will be used by grldr

---

### Post by mohawk622 on 2007-05-01
My output after fdisk -l

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5737    46080000    7  HPFS/NTFS
/dev/sdb2            5737       13142    59481088    7  HPFS/NTFS
/dev/sdb3           13143       17989    38933527+  83  Linux
/dev/sdb4           17990       18241     2024190   82  Linux swap / Solaris

Disk /dev/sdc: 995 MB, 995474944 bytes
4 heads, 8 sectors/track, 60758 cylinders
Units = cylinders of 32 * 512 = 16384 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60759      972139+   b  W95 FAT32

Disk /dev/sdd: 16 MB, 16384000 bytes
4 heads, 16 sectors/track, 500 cylinders
Units = cylinders of 64 * 512 = 32768 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1         500       15979+   1  FAT12
ubuntu@ubuntu:~$

---

### Post by bulldog on 2007-05-01
You boot from the sdb device?Your windows disk.
It should because it goes right into windows.

The other devices listed,what are they?

EDIT;
You stated the find command returned (hd1,2) which indicates there should be another hdd which should be (hd0)
Can't see this device in your fdisk output.
But you also stated it boot right into windows which is on the same hdd as ubuntu is,so you should boot from this hdd.
Somewhat confusing,because it can't be that way.
Did you remove any hdd during install or what.

---

### Post by mohawk622 on 2007-05-01
I have a scsi drive array in raid 5 for windows data.

My boot drive with vista has patition 1 in ntfs. the second patition is a ntfs patition for windows data,  The third patition is Ubuntu ex3 and the 4th patition is the swap drive.

Thanks

---

### Post by bulldog on 2007-05-01
Yes,I understand how your partitions are listed,but I have no knowledge about Raid array's.
I see your find command points to a second hdd,I see no first hdd where GRUB obviously is installed.

I can not assist you with this problem,never worked with a raid,so really can't tell what to do.

---

