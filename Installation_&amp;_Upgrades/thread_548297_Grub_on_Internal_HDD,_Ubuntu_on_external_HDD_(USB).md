---
title: "Grub on Internal HDD, Ubuntu on external HDD (USB)"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by pacut on 2007-09-11
Hello there.

BIOS of my portable PC doesn't have USB booting option :mad:
I was thinking of installing Ubuntu on external USB drive AND placing Grub on MBR of main internal HDD (the one which hosts Windows XP). Not into MBR of USB drive. Why this ? Because, as I said, my PC doesn't have USB option during boot AND, mainly, because my external HDD might be at home and not in the office.

If I do install Ubuntu on external HDD  and if I say to installation process that Grub has to install in MBR of HDA, does it work ? Or do I risk to compromise current XP install ?

Thanks
Paolo

---

### Post by logos34 on 2007-09-11
Well, to begin with, what will happen during installation is that grub will by default overwrite the windows bootloader on the MBR of your internal drive.  You may think 'that's what I want' but you really don't because grub needs to be able to access menu.lst on the ubuntu root partition (in /boot/grub), which is on the external USB...But if the USB drive is disconnected you won't be able to boot anything. And even if it is connected that's no guarantee you'll actually be able to boot ubuntu on the USB.  Hence it might be wise to put grub on a floppy (if that's an option for you) instead of the internal drive, at least initially until you get everything functioning properly. (use the **Alternate install CD**).  This will leave your windows bootloader untouched.

It can be tricky finding a viable workaround if your Bios doesn't support booting from USB devices.

You could try the [methods here]("https://help.ubuntu.com/community/BootFromUSB?highlight=%28bootfromusb%29") (--> 'Booting via Grub' and 'Booting the kernel from an internal hard drive').

You might even be able to incorporate the first method into [ WinGrub]("http://users.bigpond.net.au/hermanzone/p9.html"), which basically modifies your windows bootloader to chainload Grub.  

Don't hesitate to post back if you have any questions.

---

### Post by pxwpxw on 2007-09-11
This is the method I have used where the PC BIOS cannot boot from the external drive.

 Put a small fat32 partiton on the internal drive, copy the complete external /boot directory to there, with kernel images and grub menu.lst and other files, ntfs won't work here. 
 Install grub to the internal MBR, using the internal fat32 partition as grub root. The kernel still uses the external /boot files to mount the root system. Involves a bit of extra effort with grub installation.

 XP is booted from the grub menu.lst, the linux kernel is booted from the internal drive,
and the kernel mounts the external file system.
 With a 1999 vintage pc it works, (also for a usb flash stick), but there seems to be some variation in driver capability to deal with external hard disk usb, it is a good idea to check this out with a live CD or rescue CD at the start, see if it can mount. 

 A grub floppy or grub CD is very useful to check grub accessibility to drive partitions, and help get the system set up.

---

### Post by logos34 on 2007-09-12
> **pxwpxw said:**
> ...Install grub to the internal MBR, using the internal fat32 partition as grub root. **The kernel still uses the external /boot files to mount the root system**. Involves a bit of extra effort with grub installation.

 XP is booted from the grub menu.lst, **the linux kernel is booted from the internal drive,**
and the kernel mounts the external file system....

That's basically what I had in mind too for the OP (using either method in the first link I posted above).  But I don't have any old hardware I can test this out on...So clarify one thing for me if you would, I'm curious: your grub points to the internal drive /boot partitiion, but the menu.lst entries for vmlinuz and initrd.img point to the external /boot?  Or to the copies on the internal /boot?

---

### Post by pxwpxw on 2007-09-12
> **logos34 said:**
> That's basically what I had in mind too for the OP (using either method in the first link I posted above).  But I don't have any old hardware I can test this out on...So clarify one thing for me if you would, I'm curious: your grub points to the internal drive /boot partitiion, but the menu.lst entries for vmlinuz and initrd.img point to the external /boot?  Or to the copies on the internal /boot?

The internal menu.lst points to its local copies of vmlinuz and initrd, and the only refernece to the external is the kernel parameter  root=/dev/sdax. The other kernel /boot files are not really needed on the internal,  its just easier to copy the whole /boot directory.
Has to be redone for kernel upgrades of course.
That is for the case where grub can't load the kernel (vmlinuz and initrd.img)  direct from the external.

---

### Post by logos34 on 2007-09-12
> **pxwpxw said:**
> The internal menu.lst points to its local copies of vmlinuz and initrd, and the only refernece to the external is the kernel parameter  root=/dev/sdax. The other kernel /boot files are not really needed on the internal,  its just easier to copy the whole /boot directory.
Has to be redone for kernel upgrades of course.
That is for the case where grub can't load the kernel (vmlinuz and initrd.img)  direct from the external.

That's what I suspected you meant, it didn't make sense to me the other way round.  Thanks for elaborating on your answer.  Although I would have thought you would need to use 'root=/dev/<internalbootpartition>'. 

And yes, the kernel upgrade part is the only downside.  

I'm leaning more and more to the idea of using a separate /boot partition on the internal drive in cases like this (ubuntu on external drive, no Bios support for USB boot).  It makes a lot of sense. No need for Grub USB boot CD.  In fact, it makes sense even if your Bios supports USB booting: You can install grub on the internal and still dual-boot windows even when the external is disconnected.  No need either to toggle the boot drive in the Bios in cases where you put Grub on the external drive's MBR.

---

### Post by pxwpxw on 2007-09-12
> **logos34 said:**
> Although I would have thought you would need to use 'root=/dev/<internalbootpartition>'. 


Just to clarify, the menu.lst "kernel /boot/vmlinuz root=/dev/sdxx ...."
is referring to the internal copy of the kernel, but the "root=/dev/sdxx" is the kernels only link to the external linux file system to be mounted.
Maybe the UUID for the external partition would be a better choice sometimes.

The catch is the need for a fat32 partition, sometimes difficult to add without repartitioning. (could use linux ext3, but fat32 allows access from windows).

EDIT:
/**dev/sdxx** is the linux root partition /  on the **external drive**, which has the originally installed  full /boot partition.

---

### Post by pacut on 2007-09-12
I got lost !

Correct me if I am wrong:

1) I put a FAT32 small (how much?) partion on my internal HD 
2) boot from Live CD of Ubuntu (I don't have linux installed yet)
3) I copy the complete external /boot directory (from Live CD  I assume)  to the new FAT32 partion
4) where can I find kernel images and grub menu.lst and other files to be copied into /boot ? From the Live CD ?
5) I install Ubuntu telling that root (/) has to be on external USB hard drive and and telling GRUB to place itself on MBR of main internal HD ?

:confused::confused::confused:
Thanks

---

### Post by logos34 on 2007-09-12
> **pacut said:**
> 1) I put a FAT32 small (how much?) partion on my internal HD 

Actually, you can make it fat32 or ext3 (just not NTFS), because Grub chainloads windows NTLDR (which is on C: drive), it doesn't boot it directly...stage2 and menu.lst are the important files on /boot partition.

25MB should be adequate, unless you plan to keep a lot of kernels and/or multiboot other linux distros.

> 2) boot from Live CD of Ubuntu (I don't have linux installed yet)
3) I copy the complete external /boot directory (from Live CD  I assume)  to the new FAT32 partion
4) where can I find kernel images and grub menu.lst and other files to be copied into /boot ? From the Live CD ?
5) I install Ubuntu telling that root (/) has to be on external USB hard drive and and telling GRUB to place itself on MBR of main internal HD ?

No, you want to install first, make a / and /swap (a separate /home is a good idea too), then copy /boot over to the new partition on the internal.  Just let grub install to it's default location (the MBR of the internal drive).  But then you'll have to reinstall grub so that stage1 on the mbr points to the internal /boot and not /boot on the root partition on the usb drive.

---

### Post by pacut on 2007-09-12
Understood.

On when I can copy /boot into internal HDD ? At the end of Ubuntu installation process ? Is it possible at the real end of this, or does system automatically reboot at the end of installation process (which might create reboot issue, eventually) ?

I will find how to reinstall grub, also. The concept is clear now.

Thanks

---

### Post by logos34 on 2007-09-12
so, for example, if your internal drive /boot is hda2, you would do this:

-after installation is complete, choose not to reboot and continue working on the live cd.  
-Mount hda2 and copy the usb drive /boot (including /grub subdir) contents over to hda2.  
-edit menu.lst on hda2 so that all the 'root' lines point to '(hd0,1)'--i.e. hda2.  
-reinstall grub to the mbr so stage1 points to hda2:

> [B]sudo grub
root (hd0,1)[/B]  -->substitute your internal boot partition 
**setup (hd0)**   -->this rewrites grub to the mbr 
**quit**

---

### Post by meierfra on 2007-09-12
logos34 and pxwpxw:

I have no experience with external hard drives ( since I don't own one).  But can't  one avoid the kernel upgrade problem by using

title ubuntu
root (hdx,y)    # location of external ubuntu partition
configfile /boot/grub/menu.lst

in the internal  menu.lst? (Also set "timeout 0" and "hiddenmenu" in the external menu.lst, so that one does not have to deal with the external grub menu  at boot up)

---

### Post by pxwpxw on 2007-09-13
> **meierfra said:**
> logos34 and pxwpxw:

I have no experience with external hard drives ( since I don't own one).  But can't  one avoid the kernel upgrade problem by using

title ubuntu
root (hdx,y)    # location of external ubuntu partition
configfile /boot/grub/menu.lst

in the internal  menu.lst? (Also set "timeout 0" and "hiddenmenu" in the external menu.lst, so that one does not have to deal with the external grub menu  at boot up)

The problem there is that grub wont get past the "root (hdx,y)" statement if the BIOS does not support it, which is the case being considered here. A good way to establish such limitations is to test by using a grub floppy or grub CD, which has only the BIOS to work with.

The kernel update only requires copying the new vmlinuz and initrd .img, not the whole /boot, not too difficult.

---

### Post by logos34 on 2007-09-13
> **pxwpxw said:**
> The problem there is that grub wont get past the "root (hdx,y)" statement if the BIOS does not support it, which is the case being considered here.

Yep, that would be it.  I recommend the 'configfile' format whenever possible to avoid the kernel update issue, but unfortunately that doesn't work if Grub can't reach the external root (/boot) because the Bios doesn't support USB boot.  There's no way around it that I know of, unless maybe you could figure out a way to have 'groot' point to two different /boot partitions and so simultaneously update both or something.  (Kernel updating is even more involved with the Grub boot CD--you have to redo the whole disc with the new images and usb modules).

---

