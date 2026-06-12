---
title: "Upgrade ubuntu 12 - Ubuntu 13."
date: 2013-10-17
forum: Installation &amp; Upgrades
---

### Post by chetanmadaan on 2013-10-17
Hi -

i have a basic ubuntu 12 desktop i setup a couple of months ago and we use it for all sorts of local projects related to php/mysql. 

I am now trying to upgrade from 12 to 13 and at the same time upgrade the hard disk too. 

The current config is 200 GB and dual core processor. i am trying to upgrade to i5 and 2 TB HD with 8 GB Ram and all.

So, what i am thinking of doing is doing a fresh install of ubuntu 13 on the new hardware and the moving all the files from the old install to the new one and get it done that way??? is that possible? if so, is there a documentation avaliable?

Thanks
Chetan

---

### Post by grahammechanical on 2013-10-17
Would you be using the same hard disk? Or is the 2TB disk a second disk?

If you will be keeping the same hard disk then you should tell us how that hard disk is paritioned and you should think about ways of backing up the data that you do not want to lose.

If the 2TB disk is a new disk just for the new hardware, then think about how you want that disk partitioned. Then install Ubuntu 13.10 to it and then plug the old hard disk into the machine and copy the folders and files over to the new disk. This is possible. I have done it.

At some point you will need to partition the disk and install using the Something else option. So, you need to study that. You can certainly practice on the new disk before putting your data on it.

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Regards.

---

### Post by chetanmadaan on 2013-10-17
I would be using a new hard disk.

So, you are saying i should manually copy everything over??? how would that work with the /home directory where i have so many users with cron jobs for proper user file permissions and everything?

I didn't partition when i first setup the server and i don't think i need to do it now as i would just be using the whole disk for this server (assuming the partition is useful when i need to run vps or multiple OS on the same systems).

Yes, i can even practice on the new disk with data on it as i won't change anything on the current disk.

the only issue i worry about is how would it copy/take all my files/cron jobs/users/mysql databases and everything else over to new HD?

Thanks for your replies... We appreciate the free OS and free support too :).

---

### Post by pqwoerituytrueiwoq on 2013-10-17
partition the new hdd however you want it from a live disk using gparted
then from the live disk run 
[FONT=courier new]sudo cp -av /media/ubuntu/oldPartation /media/ubuntu/newPartation[/FONT]
use tunefs to change the UUID on the new partaion to match the one on the old partaion
then edit [FONT=courier new]/media/ubuntu/newPartation/etc/fstab[FONT=arial] and change the swap UUID to the new one, if you have a swap[/FONT][/FONT]
then you just reinstall grub like you would do if you installed windows second
then make sure it boots up right on the new hdd and if all goes well you can just upgrade on the new hdd or upgrade on the old disk to test it to make sure it will work before upgrading on the new one

---

### Post by chetanmadaan on 2013-10-17
Sorry... but too confusing..

isn't there a automated process for this thing?? :(

and by confusing.... i mean i am not really a server guy.

---

### Post by pqwoerituytrueiwoq on 2013-10-17
you can use something like clonezilla, you just need to clone to the new hdd then do the upgrade on the new disk

---

### Post by chetanmadaan on 2013-10-17
Already tried that weeks ago... and posted to cloneZilla Forums.

[http://sourceforge.net/p/clonezilla/discussion/Clonezilla_live/thread/257cfa2a/](http://sourceforge.net/p/clonezilla/discussion/Clonezilla_live/thread/257cfa2a/)

will probably try again.

---

