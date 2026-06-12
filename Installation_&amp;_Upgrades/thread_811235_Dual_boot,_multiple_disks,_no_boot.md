---
title: "Dual boot, multiple disks, no boot"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by charlemagneb on 2008-05-28
We are dealing with Ubuntu 8.04 and Win2K on two disks (there are actually three disks, but the third is "blank".

Win2K is the legacy OS and is installed by itself on one disk, and Ubuntu is installed by itself on another.  What has created the problem is that when Ubuntu was installed, the Win disk was (intentionally) off the system, so neither OS knows of the other.  As long as ubuntu was on sda, it booted, and as long as Win2k was on "sda" it was OK too.

Problem is that I tried to use SuperGrubDisk to change grub so that Win2k is on sda as it wants to be, and ubuntu is on sdb since it doesn't care.  What I have now is that neither OS will boot, and rather than screw things up any worse than they are, I am calling for wiser minds.

Thanks for any help.

Chuck

---

### Post by housam on 2008-05-29
Boot from Ubuntu live cd and type in the terminal :
```
sudo fdisk -l
```
where -l ia a small L and post the results
Also type :
```
gksudo gedit /boot/grub/menu.lst
```
and post the results too .

---

### Post by charlemagneb on 2008-05-29
Hi Housam, thanks for the call back.  I don't have live Ubuntu (or at least couldn't get the live display to work for me), so I am using Knoppix which does the job, I guess.

You will note that menu.lst points to (hd0,0) and should point to (hd1,0) to find linux in its current location, and of course there is no reference to Windows.  I know all that, but just wasn't sure what to do.  I've already got enough of a mess without making it messier.

So, here, I hope, are the files.  The darned thing said they uploaded, but I don't see any evidence of them.  Sorry to be so lame.

---

### Post by Em-Buntu on 2008-05-29
It sounds like when you installed, you pointed grub to install on hd1,0.
Instead have grub install to the same disk as Windows, hd0,0.
Grub will include the win boot block in it's options list like so;

1) Ubuntu 8.04
2) Ubuntu 8.04 Safe
3) Memtest
4) Windows 2000

I have the same setup as you, three disks, with disk 1 being Windows, disk 2 being Ubuntu, and disk 3 being for backup.

---

### Post by meierfra. on 2008-05-29
If your bios allow you, just  set you Bios to boot from the Ubuntu drive. 


If you cannot change the boot order in the bios, you could physically swap the location of  your Windows and Ubuntu drive.

If none of this work, you would have to install grub to the MBR of the Windows drive. Click on   FixGrub in my signature for instructions.


You also will  have to add Windows to "menu.lst". But we worry about that once you booted into ubuntu.

---

### Post by meierfra. on 2008-05-29
> So, here, I hope, are the files. The darned thing said they uploaded, but I don't see any evidence of them. Sorry to be so lame.

Just copy and paste the data into your post. But use the Code Tags (#)

---

