---
title: "Steps Needed to Install Windows 7 from a USB drive using Linux"
date: 2010-10-24
forum: Installation &amp; Upgrades
---

### Post by rukkin on 2010-10-24
How to Install Windows 7 using Linux
 1. Download Windows 7 iso
 2. Acquire a removable drive (4GB minimum)
 3. Format Removable Drive as NTFS
   a.System >Administration >Disk Utility
   b.If the removable drive has an partition what you are going to want to do is unmount the partition to be able to Format the removable drive then remember to format it as NTFS
   c.After it is done formating you will want to create a partition
   d.What you are going to want to do after is go to Partition Settings and check the box for bootable
 4.After you have finished setting up the removable drive what you will want to do is mount the Windows 7 iso
 5.After mounting the .iso you will want to copy all the files inside and copy them to the removable drive
 6.After the files have finished coping over open up the terminal:
[INDENT]Applications >Accessories >Terminal[/INDENT]
 7.Type in: sudo lilo -M /dev/sda mbr (then hit Enter)
   Type in: sudo apt-get install lilo (then hit Enter)
 8.After it finishes installing reboot your computer
 9.When your computer turns on press F12 until the boot options appear
 10.Then go to "Hard Disk"
 11.After that you will want to go to your USB drive
 12.Once you have selected your USB drive the computer will automatically reboot
 13.Once you computer reboots it will start installing Windows 7 from your removable drive
 14. Congratulations (Be patient because it takes a bit for everything to start installing because it is having to get all the information from the USB drive.)

P.S. Took me about six hours to be able to get it working, I made many mistakes and tried different ways of doing it and this seemed to be the best and fastest way to do it if you have no CD/DVD Drive in your computer.

Hope you enjoy

---

### Post by nicvia on 2010-11-12
> **rukkin said:**
> How to Install Windows 7 using Linux
 1. Download Windows 7 iso
 2. Acquire a removable drive (4GB minimum)
 3. Format Removable Drive as NTFS
   a.System >Administration >Disk Utility
   b.If the removable drive has an partition what you are going to want to do is unmount the partition to be able to Format the removable drive then remember to format it as NTFS
   c.After it is done formating you will want to create a partition
   d.What you are going to want to do after is go to Partition Settings and check the box for bootable
 4.After you have finished setting up the removable drive what you will want to do is mount the Windows 7 iso
 5.After mounting the .iso you will want to copy all the files inside and copy them to the removable drive
 6.After the files have finished coping over open up the terminal:
[INDENT]Applications >Accessories >Terminal[/INDENT]
 7.Type in: sudo lilo -M /dev/sda mbr (then hit Enter)
   Type in: sudo apt-get install lilo (then hit Enter)
 8.After it finishes installing reboot your computer
 9.When your computer turns on press F12 until the boot options appear
 10.Then go to "Hard Disk"
 11.After that you will want to go to your USB drive
 12.Once you have selected your USB drive the computer will automatically reboot
 13.Once you computer reboots it will start installing Windows 7 from your removable drive
 14. Congratulations (Be patient because it takes a bit for everything to start installing because it is having to get all the information from the USB drive.)

P.S. Took me about six hours to be able to get it working, I made many mistakes and tried different ways of doing it and this seemed to be the best and fastest way to do it if you have no CD/DVD Drive in your computer.

Hope you enjoy

Will this also work if, instead of the .iso file, I used all of the files in my Windows 7 DVD?

---

### Post by sikander3786 on 2010-11-12
> 7.Type in: sudo lilo -M /dev/sda mbr (then hit Enter)
Type in: sudo apt-get install lilo (then hit Enter)

I fear this might mess up one's MBR and make his system unbootable. It is too dangerous to try.

Can you explain a bit?

---

### Post by nicvia on 2010-11-12
> **sikander3786 said:**
> I fear this might mess up one's MBR and make his system unbootable. It is too dangerous to try.

Can you explain a bit?

Thanks for the warning. Whew

---

### Post by nicvia on 2010-11-13
I have a feeling that the OP will never reply...

---

### Post by kimchi_sg on 2010-11-24
Steps after #5 don't seem to be needed, see [this post]("http://ubuntuforums.org/showpost.php?p=9458199&postcount=6")

---

