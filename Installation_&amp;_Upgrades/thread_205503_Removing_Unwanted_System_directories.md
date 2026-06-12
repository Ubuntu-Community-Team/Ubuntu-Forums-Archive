---
title: "Removing Unwanted System directories"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by saphil on 2006-06-28
I have successfully moved /var /usr and /home to hdb1, hdb2, and hdb3 partitions successfully by 
1st. giving those partitions arbitrary mountpoints in my file system and copying the original /var /usr and /home contents into them and adding a small text file to the new directories so I could tell it had migrated properly.
2nd. individually edit the fstab to mount the new directories and make sure the change registers.  I did the /home directory first to check the idea.  It worked!  Hurrah.

Now I want to address the issue that prompted me to try this in the first place:
My hda1 directory is a win2k space.  
     hda3 is the / partition but had only .8GB in it, and was causing a slowdown of file transfer.  

By moving the /usr /var and /home to the new partitions, I should have cleared about 4GB on hda3, however that has not happened.

Using knoppix (in aterm as root), I inspected the directory file structure on hda3, and found the old /usr, /var and /home folders there as before  (this is not a surprise).
Again using knoppix, I attempted ```
rm -dR /mnt/hda3/usr
``` and got a system message that it was a read-only system and could not be removed
So, I tried to ```
chmod 777 -R /mnt/hda3/usr

``` and got the same error.  I am in as root of the current OS.  What am I missing??

Would live-disking in with Ubuntu make a difference??


I am pleased that I do not have to reinstall the system, but I would like to free up the space on hda3

---

### Post by jchau on 2006-06-28
I think (but I'm not sure) that Knoppix tries not to touch any files on the HD (except for the swap partition), so maybe it mounted it readonly.  Try checking with the command
```
cat /etc/mtab
```
If there is a "ro" next to the device instead of a "rw", the device is read only.  If it is, try unmounting and remounting the partition using the mount command and with the rw option.  See ```
man mount
``` for more information.  However, the command
```
sudo mount -w /dev/hda3
``` should do the job after you unmount the partition.

---

### Post by aysiu on 2006-06-28
There's an option in Knoppix to browse in superuser mode (this gives you root privileges on any Linux partition you mount). Just launch that (it's in the KMenu somewhere), and you can delete whatever you want.

---

### Post by saphil on 2006-06-28
I tried to use the aterm as root and that didn't work, so I tried loading a Ubu-live disk.  From there I could delete the contents of the old hda3 /var, /usr and /home.

I got cocky and deleted the actual folders as well, and so the system refused to load.
I used [ctrl] [alt] [f1] and logged in as root

I typed in 
```
mount
``` and it said the 3 new partitions were not loaded
I tried
```
mount /dev/hdb1
``` and it said the target directory did not exist
I loaded into recovery mode and made new /usr, /var and /home directories

logged out and restarted the machine.  Great news, I can log into my own home folder.  Yayy!!
Thanks!

---

### Post by saphil on 2006-06-29
Now I am going to do it again, using your suggestions on a machine with different partitions.  By and by, I will be good at this.

---

