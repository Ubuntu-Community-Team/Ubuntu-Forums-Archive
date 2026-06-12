---
title: "Creating &quot;Home&quot; partition with live cd"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by sleepyenglish on 2007-02-25
Hi all

I'm just installing Ubuntu on my laptop via the live cd and was hoping to create a home partition, could someone please give me a few pointers to how i would do this as i cant seem to find a way to flag a partition as a home partition.

Thanks

---

### Post by highneko on 2007-02-25
In the expert partitioner after you allocate the space and select the filesystems you want, it should then bring you to a screen where you can enter the mount location. In this case you would want to specify at least a "/home" and "/".

---

### Post by sleepyenglish on 2007-02-25
Thank you highneko for the reply, what do you mean by "expert partitioner" im running the live cd and via the desktop i clicked install ive got to the "prepare disk space" page and have chosen "manually edit partition table" when i right click and click "new" under "Filesyetem no "/home" is listed.

ext3
ext2
fat16
fat32
hfs
hfs+
jfs
linux-swap
reiserfs
ntfs
xfs
unformatted

are listed.

Thanks for any help.

---

### Post by floke on 2007-02-25
Basically you need to create an ext3 partition, and then mount it as your home directory once you are in Ubuntu.

Log in, then make a back up of your fstab file, so

sudo cp /etc/fstab /etc/fstab_backup

then edit your fstab to mount the partition as your home directory - lets say that the partition is called hda3, for example...

sudo nano /etc/fstab

then add the following line to the end of the file

/dev/hda3 /home ext3 nodev,nosuid 0 2

And that's it.

A useful guide on this can be found here

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by sleepyenglish on 2007-02-25
I now have ubuntu installed, is there a way i can confirm my date(home folder) is indeed on a different partition to that of which ubuntu is installed?

Thanks

---

### Post by sleepyenglish on 2007-02-25
I install gparted and took the below screenshot, does this mean my home folder is indeed on another partition?

Thanks

---

### Post by floke on 2007-02-25
Yep.
You can also go up through your file system and right click on the 'home' directory; click properties and it should tell you there. But your home. dir is now on sda2.

---

### Post by sleepyenglish on 2007-02-25
Thanks for the confirmation Steve.K.

---

### Post by floke on 2007-02-25
BTW: To see all your mounted partitions, you can also use 'mount' in the terminal.

---

