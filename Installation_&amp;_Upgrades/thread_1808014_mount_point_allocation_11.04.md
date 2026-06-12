---
title: "mount point allocation 11.04"
date: 2011-07-19
forum: Installation &amp; Upgrades
---

### Post by danieljames626 on 2011-07-19
I would like to allocate a mount point for a storage partition to be shared between 11.04 and a windows installation.  In the partitioning dialogue box I used to always type in the mount point text box, something like, "/media/storage" or, "/mnt/shed" and format it with ntfs or fat32.

However, Ubuntu 11.04 seems to not allow me to type in the text box and only allows me to select either "/dos" or "/windows" from a list when formating a partition with fat32.  This would not be an accurate description for me as I am not formating a drive for an operating system but just a /media or /mnt drive for access from either system in the dual boot environment.

How do I manually allocate a mount point in the Ubuntu 11.04 installation process.

---

### Post by danieljames626 on 2011-07-20
OK, so I left it as an unused partition cause it looked like no one active knew the answer and trusted that I would install gparted and then partition and mount it there.

Gparted lets me use the ntfs file system, which the natty install would not let me use but it wont give me an option for mounting at all.  I swear it used to.  What is going on? 

 Am I going to have to edit the fstab? Has Ubuntu gone backwards recently or something so that now I have to go back to the old Red Hat days of messing with fstab?  That doesn't always go so well.  What am I missing?

Also, cause of the way the install is demanding the mount point locations I have /windows instead of the normal /media/windows directory.  Are they making stuff harder or can someone show me what I am missing?

---

### Post by Quackers on 2011-07-20
Just create a NTFS partition and both systems should be able to use it.

---

### Post by Bucky Ball on 2011-07-20
> **quackers said:**
> just create a ntfs partition and both systems should be able to use it.

+1.

---

### Post by danieljames626 on 2011-07-20
> **Quackers said:**
> Just create a NTFS partition and both systems should be able to use it.

Well yeah!  that is exactly what I am saying I have already done.  I have also continued in the path I have tried to outline here by using the command 
```
sudo ls -1 /dev/disk/by-uuid
```

to ascertain the uuid of the new partition that I have created in ntfs using gparted so that I can edit the fstab to mount the new partition to "/media/storage"

My question is, what am i missing that means I can't just use gparted to mount the directory without editing the fstab configuration file and playing with uuid's.  and why can't I have just created mount points in the installation process like in previous ubuntu releases.

---

### Post by danieljames626 on 2011-07-20
> **Bucky Ball said:**
> +1.

So you also agree that I need to create an ntfs partition.  I will try to be helpful here and repeat my question.

Where do I allocate the mount point as /media/storage for my new ntfs partition.  the installation process no longer offers the opportunity to allocate a mount point and requests that I select either /dos or /windows from a list.  I can't just type in the desired mount point like I would normally have.  and then when I have finished the install and installed gparted I find that I can't do it there anymore either.  The menu list that usually offers the command 'mount' only has the option 'unmount' which is faded out because the partition is not mounted and it can't be unmounted until it has been mounted.  It used to be in the create partition dialogue box: a little text box that said "mount point"  and in it I would write /mnt/storage or /media/storage.

I am not asking about what file systems can be read by both os's

---

### Post by danieljames626 on 2011-07-20
Ok . . . So Ubuntu will automatically mount the partition and when restarting the computer and by default names it according to the UUID.  That certainly makes it clearer, at least, which UUID belongs to my new partition because in the fstab config file it only writes the uuid for the swap and the windows partitions, not the root partition.  So I did not know which one of two possible UUID's would belong to my new partition.  Now I still need to edit the configuration file so that i am mounting the partition in a more likely sort of way, hopefully without wrecking the permissions.

I would like to mark this thread solved but I still have not worked out how to simply allocate a mount point for a new partition.  Sure it is mounted but where is my option to allocate the mount point at the time of creation.

---

### Post by Elfy on 2011-07-20
You need to 

Create the partition

Find the UUID - ```
sudo blkid
```
Create a mountpoint ```
sudo mkdir /media/*name*
```
Add mountpoint to fstab (after bacckiing it up) ```
sudo cp /etc/fstab /etc/fstab.bak
``` then ```
gksudo gedit /etc/fstab
```

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by miklcct on 2011-07-20
This is a known bug (not being able to type into the mount box). Install it first and edit /etc/fstab later.

---

### Post by danieljames626 on 2011-07-20
> **forestpiskie said:**
> You need to 

Create the partition

Find the UUID - ```
sudo blkid
```Create a mountpoint ```
sudo mkdir /media/*name*
```Add mountpoint to fstab (after bacckiing it up) ```
sudo cp /etc/fstab /etc/fstab.bak
``` then ```
gksudo gedit /etc/fstab
```[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Thank you very much this was very helpful.  I do miss the little text box at install I could just type the mount point into, but at least it is fixed and neat now.  I very much appreciate the time you took to read and answer my question.

---

