---
title: "Little problem with mounting"
date: 2005-02-23
forum: Installation &amp; Upgrades
---

### Post by Patrick on 2005-02-23
Goodday to u all  :-) 

I've got a little question about mounting.

I made a dir for my windows disk. I mounted it , but when i check the folder ( windows ) its empty.

This is what i think i did wrong. I gave the wrong hdd with mounting. I have 2 x 40 Gigs in my workstation . HDA = Windows HDB =  Ubuntu.

When i saw that the folder was empty, i realised that probably i mounted the wrong disk.  :roll:  ](*,) 

Can somebody tell how to change this??  I think i mounted hdb , if thats true i only have to change the name of the folder from Windows to data.  But how do i do that. I tryed right mouse button, but the change name was not selectable 

But if i mounted HDA,, why dont i see the folders......

---

### Post by mirons on 2005-02-23
What command did you use to mount the disk? Is the disk partitioned? what about the filesystem? Something like  mount /dev/hda /mnt/dir -t vfat should work. If it doesn't should report some kind of error.

---

### Post by Patrick on 2005-02-23
[QUOTE=mirons]What command did you use to mount the disk? Is the disk partitioned? what about the filesystem? Something like  mount /dev/hda /mnt/dir -t vfat should work. If it doesn't should report some kind of error.[/QUOTE]

I mounted it llike this 

mount /dev/hda /mnt/windows -t ntfs

There is something mounted , because when i look at the properties of the folder windows, the size is 33GB.  But if i mount it like that and it is HDA  then i should see folders, right?

---

