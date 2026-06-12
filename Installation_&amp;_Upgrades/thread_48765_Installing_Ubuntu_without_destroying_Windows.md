---
title: "Installing Ubuntu without destroying Windows"
date: 2005-07-13
forum: Installation &amp; Upgrades
---

### Post by Comrade on 2005-07-13
Greetings everyone. I already have Fedora Core 3 installed on my computer, along with Windows XP Home Edition. I want to install Debian on my compouter, and overwrite **only the Fedora Core 3 partitions** . I do **not** want to keep the FC3 partitions. I hear that the default Ubuntu installation wipes the hard disk clean - this is something I want to avoid entirely. I liked the Fedora Core 3 installer because it gives you the option of only removing Linux partitions, and having no risk of deleting Windows partitions. But the Ubuntu installer does not appear to have this capability. I realize I am being very vague right now, but I hope to get some sort of explanation. I am new to the Ubuntu installer, and I read the Install Guide, but that did not help in regards to my question. Is there an option like the one in anaconda (the FC installer)?
[CENTER]
 ](*,)[/CENTER]

---

### Post by varunus on 2005-07-13
Ubuntu has the overwrite just the Fedora partitions.  Just manually configure your partitions in the install process, and create the ones Ubuntu needs (and delete the Fedora ones).

---

### Post by BKonkle on 2005-07-13
The installer will also let you manually edit your partitition tables.  If I remember correctly, it will be the option on the bottom when you are presented with the partitioning question.  Tell it you want to do it manually, and then delete all of your FC3 partitions.  (I didn't like Fedora that much, either)  Then, create your own new partitioning scheme for Ubuntu.

Personally, I use the following:

A primary 10-gig NTFS partition for the few things I still do with Windows.
A primary 75-MB ext2 partition being used for /boot
A logical 30-gig ext3 partition for the root filesystem using ext3
A logical 10-gig ext3 partition being used for /home
A 2-gig swap space partition (because I have 1 gig of memory)

That leaves about 40-gig of space free on my hard drive to use in case I ever need another partition, or for playing around with other distros.

I also have a slave hard drive entirely formatted in FAT32 and used to store files that I can use both in Linux and Windows (mp3s, pictures, movies, documents, etc.)

---

### Post by Comrade on 2005-07-13
I need to delete and create partitions? I can't use the existing FC3 partitions? 

I installed Debian before I had FC3, and overwriting worked just fine for installing FC3.

Is there no other way? I'm far more comfortable with overwriting the FC3 partitions, rather than deleting those partitions and creating new ones.

---

### Post by BKonkle on 2005-07-13
Well, you can certainly use those partitions if you'd like.  For each of those partitions, you need to tell the Ubuntu installer how you would like them to be used, and make sure you tell Ubuntu not to format them.

I wouldn't recommend it, though, because it doesn't truly overwrite the entire partitions.  You will still have quite a bit of useless FC3 junk hanging around.  It would be much easier, simpler, and cleaner to delete the partitions and create new ones.

---

### Post by Comrade on 2005-07-13
How would I have it do that? I do not know how to create and remove new partitions in a way that is "easy". Is there a method that comes with the Ubuntu installer.

---

### Post by not_yet on 2005-07-14
see if this helps [http://www3.telus.net/linux4u/](http://www3.telus.net/linux4u/)

---

### Post by varunus on 2005-07-14
Comrade,

The post above has some nice pictures of everything...very nice.  I already wrote the below explanation before looking at the link though...

The ubuntu installer's partitioning tool isn't that scary.  When you boot the installer, it will ask you about partitioning; say you want to do it manually.  Then, it will list all of your current partitions.  If you want to keep your old ones, you can do that; just make sure to set the mount points correctly.  (You can just use the up and down arrow keys to select a partition, and hit enter to bring up its info.)  You can also delete after you bring up the info if you want to.  I'd recommend just deleting and recreating your fedora partitions.  (This will wipe them clean.)

To do this, boot the installer, choose manually partition, and it will list your partitions.  Highlight each fedora partition and choose "delete".  Then, you will see free space.  Highlight the free space, hit enter, and choose a size and mount point (probably /) for a new partition.  Then make another new partition once you are done with this, and mark it swap.  If you want other partitions, you can make them here.  Make sure / is set to primary, for everything else, logical.

Good luck.

---

### Post by radeon4 on 2005-07-14
I do believe that you have to enter "expert" at the startup screen minus the quotes.  Then you can select the partition disks and highlight the partitions you want to use.  I would also recommend reformating them since you dont want to have any extra files taking up space.

---

### Post by varunus on 2005-07-14
You don't have to enter expert mode to manually partition; you get the option even in the normal install.  (I know because that's how I did it.   :) )

---

