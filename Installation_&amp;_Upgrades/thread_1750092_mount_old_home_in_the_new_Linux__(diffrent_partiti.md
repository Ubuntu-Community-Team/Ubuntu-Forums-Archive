---
title: "mount old home in the new Linux  (diffrent partitions)"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by Marcus-Sweden on 2011-05-05
Hey, since I'm bad at Linux but want to learn, I usaly seperate my instalation and my private files at seperatde partitions, and earlier keept the /home/ folder empty. 


But In 2010 I manage to put /home directory on a separate partion. 
And then again now at the latest uppgrade I happened to destroy something. Therefore I formatted and installed the Linux fresch and I have now a perfect Ubuntu 11.04 on one partition.

But now I want to mount on my old /home/ on its own partion as /home in my new linux. 


How do I do? 

I guese I should unmount my new /home, and then mount on my old home on this mount point? and how do you do? 

I also understand that it has something with /etc/fstab file to do? 

But then I get I dont understand. 


When I open Disk Utillity in Ubuntu I get the following information. 

My partion with my dear old home directory called: /dev/sdb5 and if I understan right its type is ext4 (version 1.0) (since it says nothing about Linux Partition Type (0x83) 

It says that it is mounted: 
Mounted at /media/4f91178c-dd93-40ff-b548-d15c48f37c77 


So if I got it right this partion instead of being mounted on /media/ so it should be mounted at /home/ but how do I do it? and what do I write? And how do you avoid destroy anything? files etc.


Also:
When I open this "old" /home in Ubuntu from the desktop, I find three folders. 
friend (old home directory I created for friends) 
Lost-found 
marcus (my old directory with all my files that I do not want to spoil) 
Is there a risk that they will disappear? 



I have opened my / etc / fstab and so here it is on it.


Very very gratefull for help an answer!!!  :-) 


Kind regards.





# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=c2c7fcb3-09a9-4b35-b589-7f0dc386630f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3c6da7e7-66a9-4c56-a187-40bac6a29412 none            swap    sw              0       0
# swap was on /dev/sdb6 during installation
UUID=65e2d94d-072c-4038-a98c-e3b059337696 none            swap    sw              0       0

---

### Post by Nerotriple6 on 2011-05-05
Hello. :)

I have a text file stored on my Home folder with a how-to. Be happy to share it. It's easily explained.

> Move /home to it’s own partition


Having the “/home” directory tree on it’s own partition has several advantages, the biggest perhaps being that you can reinstall the OS (or even a different distro of Linux) without losing all your data. You can do this by keeping the /home partition unchanged and reinstalling the OS which goes in the “/” (root) directory, which can be on a seperate partition.

But you, like me, did not know this when you first installed Ubuntu, and have not created a new partition for “/home” when you first installed Ubuntu. Despair not, it is really simple to move “/home” to its own partition.

First, create a partition of sufficient size for your “/home” directory. You may have to use that new hard drive, or adjust/resize the existing partition on your current hard-drive to do this. Let me skip those details.

Next, mount the new partition:


$mkdir /mnt/newhome
$sudo mount -t ext3 /dev/hda5 /mnt/newhome


(You have to change the “hda5&#8243; in the above to the correct partition label for the new partition. Also, the above assumes that the new partition you created is formatted as an ext3 partition. Change the “ext3&#8243; to whatever filesystem the drive is formatted to.)

Now, Copy files over:
Since the “/home” directory will have hardlinks, softlinks, files and nested directories, a regular copy (cp) may not do the job completely. Therefore, we use something we learn from the Debian archiving guide:


$cd /home/
$find . -depth -print0 | cpio --null --sparse -pvd /mnt/newhome/


Make sure everything copied over correctly. You might have to do some tweaking and honing to make sure you get it all right, just in case.


Next, unmount the new partition:

$sudo umount /mnt/newhome

Make way for the new “home”
$sudo mv /home /old_home

Since we moved /home to /old_home, there is no longer a /home directory. So first we should recreate a new /home by:
sudo mkdir /home

Mount the new home:
$sudo mount /dev/hda5 /home
(Again, you have to change “hda5&#8243; to whatever the new partition’s label is.)

Cursorily verify that everything works right.

Now, you have to tell Ubuntu to mount your new home when you boot. Add a line to the “/etc/fstab” file that looks like the following:

/dev/hda5 /home ext3 nodev,nosuid 0 2

(Here, change the partition label “hda5&#8243; to the label of the new partition, and you may have to change “ext3&#8243; to whatever filesystem you chose for your new “home”)

Once all this is done, and everything works fine, you can delete the “/old_home” directory by using:

$sudo rm -r /old_home
Good luck. :guitar:

---

### Post by Marcus-Sweden on 2011-05-06
Thank you!!! that was a good help :-) 



QUOTE=Nerotriple6;10772393]Hello. :)

I have a text file stored on my Home folder with a how-to. Be happy to share it. It's easily explained.


Good luck. :guitar:[/QUOTE]

---

