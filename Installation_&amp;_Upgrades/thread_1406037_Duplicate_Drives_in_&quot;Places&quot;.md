---
title: "Duplicate Drives in &quot;Places&quot;"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by Grumblesareus on 2010-02-13
Just moved to Ubuntu from XP. Whole process has gone very smoothly, but left with a small problem (i.e. it isn't actually affecting usability) that I don't seem to be able to fix and can't find on forums/internet. I also have a problem with the Floppy drive, but I've seen that problem elsewhere in the forums.

It's a dual boot system with both NTFS and Ext4 drives.  All are visible and fully accessible.  I decided to convert one of the NTFS drive to Ext4.  That appeared to be successful and was successfully remounted as an Ext4 drive.  The drive label is "Data".  I did have a bit of a problem getting it remounted so that I could see/use it under my log-in as opposed to just under root.  It's at this point I think that I did something to create the problem.

I now have two entries for "Data" in drop down menu for Places.  The true one is shown as a standard hard drive icon, but the false one is shown as a different icon - possibly an external drive icon (note that the floppy drive is also showing as the same icon and I can't access that, but I've seen that's a problem elsewhere in the forums).

I can write and read to the true "Data" hard drive.  If I click on the other false "Data" icon, I get the message "mount: /dev/sdd1 already mounted or /media/Data busy mount: according to mtab, /dev/sdd1 is already mounted on /media/Data".  If  unmount the true drive and try to mount the false drive, the system mounts the true drive instead.

If I log into nautilus as root, neither the false data drive or the floppy appear in the left hand panel.

Any suggestions?  Please be reasonably explicit with any ideas/instructions as I'm very much a newbie in Linux. Thanks.

---

### Post by oldfred on 2010-02-13
Post a copy to /etc/fstab.

I believe nautilus shows all drive and all drives mounted in media and mnt and maybe something else but I am not sure. 

I created a data directory and mounted it, gave my self permissions and ownership and linked in all the folders. I set up my data directory with all the default folder sin /home and a few others. The only way I see my data is thru the linked folders that look like the standard folders in /home.

Similar to this is how I did my data partition:
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

---

### Post by Grumblesareus on 2010-02-13
Sorry, I'm not sure what you mean by "Post a copy to /etc/fstab."

Also I maybe should have been clearer that I'm having not trouble accessing and using the  mounted drive.  I just need to find a way to delete the unmountable duplicate entry in the places drop-down box.

---

### Post by 73ckn797 on 2010-02-13
> **Grumblesareus said:**
> Sorry, I'm not sure what you mean by "Post a copy to /etc/fstab."
Open terminal and enter:
```
gksudo gedit /etc/fstab
```Copy that resulting info into a new reply.

---

### Post by Grumblesareus on 2010-02-13
Copy of fstab:

/dev/fd0 /media/floppy0 vfat noauto 0 0
UUID=96c01cfb-2ade-44b8-9c87-179f04396838 /home ext4 defaults 0 2
UUID=0888B73288B71D5E /media/Music ntfs-3g defaults 0 0
UUID=258ef8c4-7286-4d35-930a-bda9e2f8e1cf /media/Data ext4 users 0 0
UUID=7ee568ca-f8f8-44b0-9443-daec77daa59b / ext4 defaults 0 1
UUID=8b205689-0343-4831-ae0b-6dd181439b82 swap swap sw 0 0

---

### Post by oldfred on 2010-02-13
Because you are mount in /media it shows in nautilus.

I mount my data elsewhere just so it do not see it in nautilus and use links to /home to see my data.

My method I just posted here if you are interested post 17:
[http://ubuntuforums.org/showthread.php?t=1405782](http://ubuntuforums.org/showthread.php?t=1405782)

---

### Post by Grumblesareus on 2010-02-13
Yes, but my understanding (which is limited!)is that if the drive is mounted under Media it will only show up only once under "Places" (and there is only 1 entry for this drive - Data - in the fstab list above).  I have 2 entries for a drive labelled Data under "Places" - one mounted and working normally (and which I want to retain)and this second rogue entry which doesn't work and I want to delete.  Thanks for bearing with me!

---

### Post by Grumblesareus on 2010-02-13
I seem to have solved this!  I decided to try and tackle the other problem - not being able to access the floppy disk - which appears elsewhere in the forums.  I used mount manager to try and mount the floppy.  It didn't mount the floppy, but the duplicate rogue drive has now disappeared.  It must be connected to the same problem.  Either way it's now sorted.  Thanks for your help on this my very first foray into the Ubuntu community.

---

### Post by 73ckn797 on 2010-02-13
Good deal. Enjoy Ubuntu.

You can mark this a solved via Thread Tools at the top of the page.

---

### Post by Cadeyrn on 2010-06-21
Sorry to be a necro, but I have the exact same problem as you. It was created the same way, it would be explained the same way, it is exactly the same issue. But I don't know exactly what you did. You said "I used mount manager to try and mount the floppy. It didn't mount the floppy, but the duplicate rogue drive has now disappeared." So I tried mounting my external hard drive in MountManager, but it was already mounted, and neither MountManager nor pysdm see the rogue drive. What exactly did you do?

EDIT: Ah, nevermind. I thought it was the same glitch, because it seemed the same, but it turns out mine came from ntfs-3g. Whenever I reconfigured my NTFS drive using pysdm, editing the fstab file, or using the ntfs-3g configuration tool, ghost drives of my external hard drive (ext2) and my NTFS partition would appear along with the original drives. The fix is to simply remove the configurations using pysdm and then recreate them.

---

### Post by Red Dot on 2010-07-05
I had a similar issue with some network NFS mounts.  I was able to fix using the defaults 0 0 options in /etc/fstab.
```

XXX.XXX.XXX.XXX:/multimedia	/home/user/Multimedia   nfs     defaults 0 0
```

---

