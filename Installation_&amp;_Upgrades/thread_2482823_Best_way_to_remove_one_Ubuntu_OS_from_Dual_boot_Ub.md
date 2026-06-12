---
title: "Best way to remove one Ubuntu OS from Dual boot Ubuntu system??"
date: 2023-01-11
forum: Installation &amp; Upgrades
---

### Post by DVD-R on 2023-01-11
Hello all,
I have a laptop with an older CPU which is a dual core - manufactured prior to the i3, i5, and i7 CPU technology.

I setup the unit up with a dual-boot - with the HD divided into two partitions and installed two different Ubuntu based OS(s) to compare them.
The OS in the first partition is now one I would like to remove - and if possible dedicate the full HD to the other.

Your words of wisdom on the best way to remove the first OS greatly apprecated.

Would it be pragmatic for me to simply delete the files within the first partition and shrink that partition down in size - and leave the whole system as a dual-boot
This would perhaps facilitate not worrying about re-configuring grub boot-up

Or I could take a CloneZilla snapshot of the OS I want to retain
And then wipe the HD and re-partition and restore the image to the full drive.

You suggestions and best wisdom very much appreciated!
Thanks

---

### Post by ubfan1 on 2023-01-11
Careful to not delete the partition from which grub was installed (last).  If you delete that partition, some grub files will be deleted also, and the grub bootloader will dump you at the grub command line.  Backup first, because things can go badly wrong with repartitioning, then grub-install from the OS you want to keep.  Then you can figure out the best way to move/expand the partition you want to keep.  If the free space is to the "right", no problem, just expand (and check that your partitioning tool runs the resize2fs to make the filesystem expand too).  If the free space is to the "left", the usual way is to move left, then expand right.  That's slow...  Consider a reinstall.

---

### Post by DVD-R on 2023-01-11
Thank you!
Yes - the partition I wish to retain is the 2nd partition - located on the right.
Is there a way for me to confirm that grub is installed in that partition?

I do have a live thumbdrive with grub restore - so that is something I could use in case I accidentally compromise the grub files.
But I'm hoping not to have to use it.

I will do some research on how to perform a new grub install - to make sure it is located in the partition I want to keep.
Thanks for that!

On your suggestion concerning partitioning tool runs the resize2fs - I'm not sure what that means.
I will be using Gparted.

And yes the free space is to the left - so I would be moving the right partition to the left and expanding.
In such case you suggest a re-install.
What steps would be involved in that - since I want to keep one of the OS exactly as it is.

Thanks!!!

---

### Post by DVD-R on 2023-01-11
AH!   I understand what you mean by resize2fs.
This is to compress an image.

The size of the partition which I want to keep is a total size of 52 gig.
I have a sandisk thumb-drive which is 250 gig in capacity - which I can use to capture a CloneZilla image of the partition I want to keep.

Perhaps my best steps would then be - to
1) Ensure grub is located on the partition I want to keep
2) Create the image of the partition I want to keep with CloneZilla
3) Wipe the HD and re=-partition
4) Restore the image to the newly cleaned HD.

However - there may be another option that might be easier.
I seem to recall there is a utility to create a LIVE ISO image of a current Ubuntu system which can be installed on any PC.
Perhaps creating that would be the easiest solution?

1) Create the LIVE ISO
2) Wipe the HD
3) Load the ISO into a live thumb-drive
4) Use the LIVE ISO to install the image

---

### Post by ubfan1 on 2023-01-11
I think the EFI's partition EFI/ubuntu/grub.cfg file uses the UUID for the root from which the install was done (by default,but you can override if done with options).  That's the key to the /boot/grub with the rest of the grub files.  

The move/expand is easy enough, just slow, and will really exercise the disk. What OS release do you currently have (and want to keep)?  If not at least 20.04, I'd do a 22.04 install.  Making an ISO of the current system seems like a lot of unnecessary work, but I've never done that.  For moving my files from one system to another, I usually just use tar, but I'm old fashion.;^)

---

### Post by DVD-R on 2023-01-11
Ok thanks!  

Greatly appreciate!

---

### Post by DVD-R on 2023-01-11
I'm back up and running on the whole HD!
I took a CloneZilla snapshot just in case before making the changes.
The used PartedMagic to remove the left partition and move the right partition to the left - and then expand it.

Went beautifully!!
My sincere thanks again ubfan1

Greatly appreciated your good wisdom!!   :-]
Thanks

---

