---
title: "Fixed GRUB &amp; menu.lst, but how to get Ubuntu image on 2nd drive to boot?"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by OzzyFrank on 2006-12-15
OK, I've copied over the Ubuntu partition from hdb (single partition, besides the swap of course, on old 10Gb drive i used to see if I liked this OS/Linux in general) to hdc (80Gb drive with 2 FAT32 partitions as well, in case that makes a diff) and all the files seem to be there, as i could mount the partition, open files and edit menu.lst etc. Tried to see if making an entry in the GRUB list of the original install (hdb) for the hdc-Ubuntu would work, and seemed to want to, but would hang before the progress indicator got anywhere.

Figured the new drive needed a GRUB of its own, and looking around it seems definitely the case... so did my homework and successfully installed it, to the point Acronis OS Selector could finally see it and make an entry for it. After ending up in my original install a couple of times, hehe, I realised the new drive's menu.lst still had a reference or two to hdb, so have fixed all that up.

So now when I choose the hdc-Ubuntu from Acronis, its GRUB menu comes up, not that of the original hdb, and choosing the standard option doesnt take me back to hdb, but the boot process hangs in exactly the same spot on hdc. So that means technically one Ubuntu can boot another that doesn't have a GRUB, from what i've seen, since hdc has a boot loader for Ubuntu now and hangs in the same spot.

Are there more files pointing to hdb that i should be changing to hdc (like in menu.lst)? Could it be some kind of hardware thing, like it spinning out it is on a different drive, or larger partition now (I did copy the partition over as-is, then tripled its size to 29Gb, and the swap was originally less than 500Mb so i tripled that to 1.5Gb... and perhaps I shouldn't forget to mention that I had errors copying the swap partition, so just created a new empty one after the copied Ubuntu partition... could that be a factor??).

Hope that's enough info, and that someone can help. Cheers. OzzyFrank

---

### Post by bernied on 2006-12-15
This doesn't sound like a grub problem to me. You are booting the install on hdc. If you take out the 'quiet' option from the kernel line for that entry in menu.lst, you can see what goes on during the boot.

My guess is that the problem is your /etc/fstab file. Fix that first. That may not be the whole problem, as when you boot you use a ramdisk image, which contains vital modules and a basic filesystem. If anything in that ramdisk points to the old drive configuration that will mess you up.

This might be solved by uninstalling and reinstalling your current kernel and modules. You might be able to achieve this by chroot. But first things first, check your fstab.

---

### Post by OzzyFrank on 2006-12-17
I've fixed the problem, so thanks to bernied for suggesting "fstab". Being a newbie, I had only just come across mention of the file, in relation to automatically mounting drives on startup. I had briefly looked in it, at the bottom to where I could put my own entries later, so now see the top entries are for the system drive and swap. I thought I would look around for info on editing fstab, for the parameters after the device path, and saw mention of another file in /etc called "mtab" that would probably also have a reference, so sure enough had to change hdb1 to hdd1 there as well.

I figured all the files were alright, and the kernel should have been fine (though I am no expert... just figured an image copy wouldn't mess with anything like that), so now know that if I again want to move my system, that the 3 files to edit are /etc/fstab, etc/mtab, and /boot/grub/menu.lst. Cheers, and hope that helps some other newbies!

---

### Post by lha on 2006-12-17
> **OzzyFrank said:**
> ... so now know that if I again want to move my system, that the 3 files to edit are /etc/fstab, etc/mtab, and /boot/grub/menu.lst. Cheers, and hope that helps some other newbies!

From 'man mount':

       The programs mount and umount maintain a list of currently mounted file
       systems in the file /etc/mtab.  If no arguments  are  given  to  mount,
       this list is printed.

You don't have to edit mtab by yourself.

---

