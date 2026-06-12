---
title: "ubuntu boots perfectly but searches for an obsolete partition"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by neo_rocco on 2010-07-04
I just installed Ubuntu 10.04 lucid lynx, I am a beginner but have had experience with Ubuntu distros for about 2 years...

Basically the Ubuntu OS loads perfectly and takes me to desktop, but just prior to loading it searches for an obsolete partition - a primary partition (ext4) that i created when I partitioned my disk using ubuntu live cd wizard. 

This partition I deleted and reformatted the unallocated space to NTFS and a new label. 
The message I get is:

"The disk drive for /storedv5 is not ready or not present continue to wait or press s to skip mounting or m for manual recovery"

note /storedv5 was the name of the previously deleted partition, it was basically a data store, not a boot partition. 

I don't want to see this message every time I boot and if I can have some one time solution it'll be great...so please help me out ubuntu maestros! 

cheers

---

### Post by darkod on 2010-07-04
Why did you create it and set amount point with the installer, just to delete it later? If you want to create any additional partitions, just do it later, not with the installer and not setting mount points for them.

Anyway, open fstab with:

gksudo gedit /etc/fstab

and put the # symbol at the start of the line where /storedv5 is mounted. That symbol will make that line be ignored. Save and close the file.

Be careful when editing fstab, making a mistake there can make the system unbootable.

---

### Post by neo_rocco on 2010-07-04
Hi i had no idea it would cause problems later on - i used the partition wizard in place of using gpart or similar program later on, obviously lessons learnt...
below is the fstab file text, as u can see there is already a '#' in front of '/storedv5' so what shall i do? can i just delete the line highlited in blue?

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=ee995810-1464-459e-bdb3-76710116576d /               ext4    errors=remount-ro 0       1
[COLOR=Blue]# /storedv5 was on /dev/sda3 during installation
UUID=cc277218-dd65-47e7-bc80-1abbd01f837b /storedv5       ext4    defaults        0       2[/COLOR]
# swap was on /dev/sda5 during installation
UUID=3a9d6c08-9c9b-409b-be47-559371589083 none            swap    sw              0       0

---

### Post by darkod on 2010-07-04
# /storedv5 was on /dev/sda3 during installation
UUID=cc277218-dd65-47e7-bc80-1abbd01f837b [COLOR=Red]/storedv5[/COLOR]       ext4     defaults        0       2

The first line is actually just a comment, that's why it has # already. Notice all the three mount points have the same, one line as comment, another below mounting the partition. The second line is actually the mount command. Put a # in front of it too.[COLOR=Blue]
[/COLOR]

---

### Post by neo_rocco on 2010-07-04
thank you sooooooo much your help is invaluable! As an aside if I had deleted the line what would have happened...

---

### Post by darkod on 2010-07-04
> **neo_rocco said:**
> thank you sooooooo much your help is invaluable! As an aside if I had deleted the line what would have happened...

Nothing. :) But sometimes it's better as a precaution to just put a # to make the line ignored. You could have deleted both lines and there shouldn't be any problems too.

Just watch out not to delete or edit the lines mounting / and swap.

---

