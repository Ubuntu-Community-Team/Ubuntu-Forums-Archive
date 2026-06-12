---
title: "[SOLVED] ubuntu 8.04 lts installation"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by hatmancan on 2008-10-13
hello all..this is my first post here and needed some help.
i just received my ubuntu cd. i want to install but here is my question.
i have 2 hard drives on my computer.both are 40mg's
i have windowsxp sp3 on first and i use my second for storing data.also have alot of business related files on first hd.
am i able to install ubuntu on my second hd? and still be able to use my c drive on first hd without losing data.
i use for my business and i want to try ubuntu out before completely switching.
can you direct me on how to install this scenero..
ty in advance

---

### Post by Partyboi2 on 2008-10-13
Yes you can install ubuntu to your 2nd hard drive, you will be able to set up a dual boot with windows.
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by tuxxy on 2008-10-13
Yes you need to create a partition on the second drive to install ubuntu to, which should keep your files safe.  Then you can use GRUB at boot to select which hard drive to run XP or Ubuntu.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by hatmancan on 2008-10-13
partyboi2 when i boot with the cd do i install on my second hd or on my usual first hard drive where windows resides?
if i put on second will both be picked up and give me the option of which os to log onto?
thanks again
hat

---

### Post by pieisgood4589 on 2008-10-13
Read Tuxxy's post, and then re-read Partyboi's. I belive the answer is already there.

First, partition that second drive using the link Tuxxy gave you. Then read the guide on how to dual boot from Partyboi.

Also- do you mean 40 GB of harddrive space, or do you honestly mean 40 MB?

---

### Post by hatmancan on 2008-10-13
oops..yes meant 40gb...
i read both but when i read the link from partyboi it doesn't mention anything about partitioning second drive first...
so now i am wondering...do i just boot up with cd and this should let me install onto 2nd hd and then grub should take over and give me the options
i hope i do this right ..
ty
hat

---

### Post by Partyboi2 on 2008-10-13
> partyboi2 when i boot with the cd do i install on my second hd or on my usual first hard drive where windows resides? At the partitioning stage under "guided use entire disk" there should be 2 listings one will be your first partition where window is and the 2nd one your 2nd hard drive. Choose the one that lists your 2nd hard drive. This will install ubuntu on the whole 2nd hard drive. If still unsure you can grab a screen shot when you are looking at the partitioning window by pressing the print screen key, then post the screen shot.
It will look something like the below screenshot

---

### Post by hatmancan on 2008-10-14
thanks partyboi
i will try this sometime today..

one other quick ?..can i use the first option for the second drive,i have a partition there now..this way i will not lose my data thats on there..is this true?
i will await response before trying..
ty
again hat

---

### Post by Sef on 2008-10-14
> one other quick ?..can i use the first option for the second drive,i have a partition there now..this way i will not lose my data thats on there..is this true?

**Back up **your data before installing.  There is no guarantee that all will go well.

Also read the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").

---

### Post by hatmancan on 2008-10-17
well i installed ok and got it up and running.. now problem is i only have 1 hd and before i had 2.. unfortunately i did not back up my data on the second and when i reboot to windows i cannot get into second drive as it tells me i have to format it..
i followed the instructions and i wanted ubuntu to install on my second hd not my first one... now i have no space left on this hd and cannot get into second??  what can i do now ?  i guess i am just not used to these icons and how can i get my microsoft outlook to run in ubuntu as i use this for my business? any help

---

### Post by Partyboi2 on 2008-10-18
Can you boot into ubuntu and open a terminal and type
```
sudo fdisk -l 
``` (small L) and post the output.

---

### Post by hatmancan on 2008-10-18
i am really new 
what is a terminal?

---

### Post by hatmancan on 2008-10-18
i now know what i did..
when i used guided instead of installing to second hd i just used the first hd instead
oops

---

### Post by hatmancan on 2008-10-18
how do i transfer ubuntu to my second hard drive?
then how do i take it off my first hd?
ty

---

### Post by hatmancan on 2008-10-18
hope this is what you needed
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd7ddd7dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2564    20595298+   7  HPFS/NTFS
/dev/sda2            2565        4865    18482782+   5  Extended
/dev/sda5            2565        4763    17663436   83  Linux
/dev/sda6            4764        4865      819283+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x931f931f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        4864    39062047+   f  W95 Ext'd (LBA)
/dev/sdb5               2        4864    39062016    7  HPFS/NTFS
dave@dave-desktop:~$

---

### Post by Partyboi2 on 2008-10-18
> **hatmancan said:**
> hope this is what you needed
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd7ddd7dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2564    20595298+   7  HPFS/NTFS
/dev/sda2            2565        4865    18482782+   5  Extended
/dev/sda5            2565        4763    17663436   83  Linux
/dev/sda6            4764        4865      819283+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x931f931f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        4864    39062047+   f  W95 Ext'd (LBA)
/dev/sdb5               2        4864    39062016    7  HPFS/NTFS
dave@dave-desktop:~$
You have indeed installed ubuntu to your first hard drive. Since you just installed ubuntu one way of moving it is to delete it and start again making sure that you choose the correct partition next time round. To delete the ubuntu partitions you can boot the ubuntu live cd and go to System>Admin>Partition Editor and right click on your swap (sda6) and turn it off then delete it, then right click on sda5 (ext3)  and unmount it and then delete it, then do the same for sda2.(extended) You should now have unallocated space which you can use the resize tool to increase your windows partition. Your windows parition is  sda1 and under "fileysystem" colum will say "ntfs" make sure you do not delete it by accident.. After you have finished increasing your windows partition you can reboot and run the installer again. Remember to backup your important stuff before working on partitions!

---

### Post by hatmancan on 2008-10-19
problem now i cannot boot from the cd..says not enough memory.
so i exited windows and now have logged into ubuntu system..can i do it from here
sorry i cannot use question mark..not used to this yet.
i am impressed by how fast it really is so far
i would like to get this working
cheers
hat

---

### Post by Partyboi2 on 2008-10-19
> **hatmancan said:**
> problem now i cannot boot from the cd..says not enough memory.
so i exited windows and now have logged into ubuntu system..can i do it from here
sorry i cannot use question mark..not used to this yet.
i am impressed by how fast it really is so far
i would like to get this working
cheers
hat
You will need to use a ubuntu live cd or [[COLOR=Blue]gparted live[/COLOR]]("http://gparted.sourceforge.net/") cd to delete the partitions as they cannot be in use when you delete them. How much ram has your system got?

---

### Post by hatmancan on 2008-10-19
partyboi..i just did a reinstall again and this is what i have now..
only thing is if i log into windows it wont show my 2nd hd..
do i have this installed there now?
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd7ddd7dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4787    38451546    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x931f931f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4660    37431418+  83  Linux
/dev/sdb2            4661        4865     1646662+   5  Extended
/dev/sdb5            4661        4865     1646631   82  Linux swap / Solaris
dave@dave-desktop:~$

---

### Post by Partyboi2 on 2008-10-20
> **hatmancan said:**
> partyboi..i just did a reinstall again and this is what i have now..
only thing is if i log into windows it wont show my 2nd hd..
do i have this installed there now?
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd7ddd7dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4787    38451546    7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40016019456 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x931f931f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4660    37431418+  83  Linux
/dev/sdb2            4661        4865     1646662+   5  Extended
/dev/sdb5            4661        4865     1646631   82  Linux swap / Solaris
dave@dave-desktop:~$
Yes it is now installed to your 2nd hard drive. Windows cannot read/write to ext3 filesystems by default, so you will not be able to view your 2nd hard drive from windows unless you download a small program to install in windows which will allow you to read/write to your 2nd hard drive. See [[COLOR=Blue]here[/COLOR]]("http://www.fs-driver.org/") for the program

---

### Post by hatmancan on 2008-10-20
thanks for all your help
does it look like i have all set up the way it should be?
i looked at the suggested program and looks like it should give me where everything is..
i have been experimenting and ubuntu is really quick..
only thing now is i have to learn how to change my pst files for outlook so evolution can import all my mail and contacts
ty
again
cheers
hat

---

### Post by Partyboi2 on 2008-10-20
>  does it look like i have all set up the way it should be? Yes, you have achieved what you where wanting to do in your original post.

---

