---
title: "Removing XP"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by idn on 2005-04-13
HI,

I have Hoary installed and I am currently dual booting with XP. I am going to set up a machine for each instead of dual booting, but how do I remove the XP install without effecting Ubuntu? To Complicate matters I have 2 disks, one SATA one normal, the swap space and boot partition are on the frist drive, the root partition is on the second drive. 

The NTFS XP partition is flagged as the boot partition, so when this is gone, what do I make the primary partition?

I was hoping to move the SATA drive to my new windows machine as space isnt a huge issue with linux (im using my windows machine mostly for gaming, so it is for that). 

I guess I could copy the root partition to the first drive, delete the NTFS partition first, making sure I update the fstab file to point to the new root dir. Would this work???

I would then be able to extend the size of my root partition to the old size of the NTFS partition. 

Also, what if I mess up fstab? will I be able to change this if its not pointing to the right partition once I have changed it? I dont want to have no OS i can boot into :)

Please help!

:)

---

### Post by Dr Gonzo on 2005-04-13
Another person had a similar problem, [see how I answered here.](http://ubuntuforums.org/showthread.php?p=131272#post131272)

However, your situation is a bit simpler.  Since /boot and swap are already on the correct drive, you really just need to format the windows partition, copy the data, update fstab, and update /boot/grub/menu.lst to point to the correct root partition.

However, just make sure you copy the data from a livecd (i.e. NOT booted from your normal Ubuntu system), otherwise you'll have trouble when it comes to things like /dev and /proc.

---

### Post by idn on 2005-04-13
Can I not just use GParted in my normal Ubuntu install? If not, what tools come with the live CD that will allow me to move the partition over?

Thanks for your help

---

### Post by Dr Gonzo on 2005-04-13
```
mount -t <fstype> /dev/<hardDriveDesignationForRootDisk> /mnt/old
mount -t <fstype>/dev/<newDiskPartition> /mnt/new
cp -a /mnt/old/* /mnt/new
```Unless you wanted something more complicated, of course.

You do this from the livecd because if you try something like this:```
mount <newpartition> /mnt/new
cp -a /* /mnt/new
```you'll have lots of problems, because every device and process is also part of the root filesystem.  Doing it without / mounted as / allows you to do a clean copy.

I've never bothered with Gparted or anything like that.  Things like that tend to make me nervous.  Especially when you've got enough extra space that you can just copy stuff over.

---

