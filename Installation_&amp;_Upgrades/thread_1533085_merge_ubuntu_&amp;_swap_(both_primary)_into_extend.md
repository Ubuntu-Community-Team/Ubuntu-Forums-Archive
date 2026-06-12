---
title: "merge ubuntu &amp; swap (both primary) into extended / logical partitions"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by lightgeek on 2010-07-17
Hi,

I have a dual boot on my laptop between XP and Ubuntu with a storage  partition.that gives me total of 4 primary partition
-Windows
-Storage
-Ubuntu
-Swap

I now want to add a OSX to my laptop in tripple booth. I did shrink the  windows partition and now I realized that all my partitions are primary  and cannot create a new one with the space I shrink from windows.

Is it possible to merge ubuntu and its swap into extended/logical  partitions so I can create a new primary for Mac OS X?

right now my drive look like

-windows (NTFS)
-free space
-storage(NTFS)
-ubuntu(ext3)
-swap(linux-swap)

please help, I do not want to re-install linux or windows.

---

### Post by Malac on 2010-07-17
It's certainly possible so long as your free space has enough room to hold the Ubuntu and swap partitions. You would need to create a backup of the Ubuntu partition (there are loads of ways to do this, search this forum) to an external hard drive is probably easiest. Use a Live CD and then create your extended partition and copy the Ubuntu partition back create a swap partition then edit the /etc/fstab settings to reflect the partition numbering changes or UUID changes.

Hope this helps.

---

### Post by lightgeek on 2010-07-17
do I have to modify the Grub boot menu (menu.lst)?? or will it boot as normal?

---

### Post by Malac on 2010-07-17
> **lightgeek said:**
> do I have to modify the Grub boot menu (menu.lst)?? or will it boot as normal?
Sorry should have mentioned that too. Yes you will have to change the /dev/sdXX options or root=UUID in menu.lst from the LIVE CD too.
Remember to write down which partition number contains which system to make this easier.

---

### Post by oldfred on 2010-07-17
Partition number & UUIDs will all change, so both grub and fstab will have to be edited.

Alternate is to backup /home, make list of all installed apps, copies of any manuall edited conf or ini files in /etc and reinstall.

---

### Post by lightgeek on 2010-07-17
ok, so for the ubuntu backup,
can I just copy and paste to an external hard drive the whole root? even if the external is formated NTFS?? and after I delete the partition, I use the live CD to do the same to the empty partition.
and If I do that, the swap assignment will also have to be change as it will no longer be the same location??

---

### Post by efflandt on 2010-07-17
Just so you know, I did try doing something similar to what you are trying to do, by simply using fidsk from live iso on USB to delete a primary partition, create an extended parttition that covered it, then recreated the primary partition with its exact start and end points as a logical partition within the extended partition.  But that did not work (I think gparted could not determine its filesystem and it could not be mounted).  So there must be something different for a logical partition than a primary partition.

But note that deleting or changing partitions does not necessarily delete any data, as long as you have not formatted it.  So I was able to access it again by reversing that and changing it back to a primary partition with its original start and end points.  Although, that would be risky to even try with things like gui tools that do not give you exact partition start and end points.

So you will need to back up anything you want to preserve first, before trying to change it to logical partitions.

---

### Post by Malac on 2010-07-17
> **lightgeek said:**
> ok, so for the ubuntu backup,
can I just copy and paste to an external hard drive the whole root? even if the external is formated NTFS?? and after I delete the partition, I use the live CD to do the same to the empty partition.
No, you are better using cp with the preserve permissions option and a Ext3 or Ext4 partition or something like partimage to create a proper backup of the partition, again from a Live CD. As copying to NTFS won't preserve the file ownership/permission data. 
You could tar the whole system to one file and copy that to NTFS, there is a thread on how to do this on the forum.

> **lightgeek said:**
>  and If I do that, the swap assignment will also have to be change as it will no longer be the same location??
Yes, all partition numbers should be written down and checked against /etc/fstab and /boot/grub/menu.lst files before trying to boot the new system.

---

### Post by lightgeek on 2010-07-17
ok, I just thaight of an other alternative here,
What if I dellete the swap partition, move all remaining partition next to each other keeping the free space at the end, then create a extended partition with 2 logical partition in it, one of them would be the swap, that I could re-assign to ubuntu, I imagine in the /etc/fstab ?? and the other one would be the Mac OS X I want to install, than to run os x I would just patch the os x into the grub menu.lst would that work or an OS have to be on a primary partition to boot from grub? what about ubuntu ans its swap, is that cool if the swap is under a logical with something els?

---

### Post by ajgreeny on 2010-07-17
Any UUID changes could be dealt with easily enough with an edit of menu.lst in legacy grub, but surely in grub2 it is not quite so easy, and I wonder how that can be changed in the **/boot/grub/grub.cfg** file.  If the changes to UUID had been made while ubuntu was running you could simply run "sudo update-grub" from that, but on the live CD I am a bit uncertain how to overcome that problem.

So perhaps oldfred can tell us, does update-grub work from a live CD, or would it be necessary to run ```
sudo grub-install /dev/sda
``` just to make sure all changes were taken on board?  I can't figure out how to get that change into the grub.cfg file by any other means, but I may be overlooking something very simple.

---

### Post by sisco311 on 2010-07-17
> **ajgreeny said:**
> Any UUID changes could be dealt with easily enough with an edit of menu.lst in legacy grub, but surely in grub2 it is not quite so easy, and I wonder how that can be changed in the **/boot/grub/grub.cfg** file.  If the changes to UUID had been made while ubuntu was running you could simply run "sudo update-grub" from that, but on the live CD I am a bit uncertain how to overcome that problem.

So perhaps oldfred can tell us, does update-grub work from a live CD, or would it be necessary to run ```
sudo grub-install /dev/sda
``` just to make sure all changes were taken on board?  I can't figure out how to get that change into the grub.cfg file by any other means, but I may be overlooking something very simple.

One could chroot into the Ubuntu installation or load the kernel manually from the Grub rescue prompt. Both methods are described in the community doc: [uhelp]community/Grub2[/uhelp]

---

### Post by lightgeek on 2010-07-17
I am not sure I am running grub 2. If I remember corectly, I first installed 8.10 and kept upgrading. how could I be sure?

---

### Post by ajgreeny on 2010-07-17
> **sisco311 said:**
> One could chroot into the Ubuntu installation or load the kernel manually from the Grub rescue prompt. Both methods are described in the community doc: [uhelp]community/Grub2[/uhelp]
OK, thanks sisco331.  I should have looked harder as that's a grub2 source I use quite a bit.

---

### Post by Malac on 2010-07-17
> **lightgeek said:**
> I am not sure I am running grub 2. If I remember corectly, I first installed 8.10 and kept upgrading. how could I be sure?
You're probably running Grub legacy then.
Take a look in /boot/grub and if there are a load of .mod files then it's GRUB 2

---

### Post by lightgeek on 2010-07-17
I do not see any .mod files, all files are either plain text or unknown

---

### Post by Malac on 2010-07-17
> **lightgeek said:**
> I do not see any .mod files, all files are either plain text or unknown
GRUB legacy then. You can just edit menu.lst then with new UUID or /dev/sdXX values.
Definitely read up and/or print off instructions on installing grub from a Live CD just in case you need to do this.

---

