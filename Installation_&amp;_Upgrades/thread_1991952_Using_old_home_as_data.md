---
title: "Using old /home as /data"
date: 2012-05-31
forum: Installation &amp; Upgrades
---

### Post by Dry Lips on 2012-05-31
Ok, here is the deal. I've got a machine with two disks. One smallish SSD, and one big regular HDD... I'm going to replace the OS I'm running now, because it unfortunately has got a few glitches. At the moment I have my home partition at the HDD, but I want to speed things up and have my /home on the SSD... 

Now, what I want to do is to use my old /home partition on the HDD as /data... Can I simply assign my old /home partition to /data when I do the reinstall? Can I do this without formatting my old /home so that I retain the files stored on it? 

Thanks in advance!

---

### Post by Lars Noodén on 2012-05-31
Yes, you should be able to do it like that.  Just be sure which partition it is on (/dev/sd[a-f]) and remember to uncheck the box for formatting.

---

### Post by Dry Lips on 2012-05-31
> **Lars Noodén said:**
> Yes, you should be able to do it like that.  Just be sure which partition it is on (/dev/sd[a-f]) and remember to uncheck the box for formatting.

Ok, thanks! I suspected it was as simple as that, but I just wanted to make sure I didn't make any stupid mistakes. 

Would it be possible to have 
/home at (SSD)  (sdf)
and assign my old home as:
/home/data  (HDD) (sda)
?

Would the /data partition show up in my home folder then?

---

### Post by Lars Noodén on 2012-05-31
The old /data would not show up in *your* home directory then, but it would show up in /home in the subdirectory 'data' accessible in the ways that directories are normally accessible.  You can give it whatever name you want.  

When you do a fresh install you might not have the same users nor even the same order of users so the numeric UID might differ between your old and new systems.  In that case, if you want write access, you might have to chown the items in /home/data once your new system is running.

As with everything, make a backup copy first.

---

### Post by Dry Lips on 2012-05-31
Ok, here is what I just tried in Virtualbox:

I created these partitions:

sda1:       /                                                                      
sda2:              /home                                                          
sda3: /home/**username**/data                        
sda5: /swap 

It actually worked! As you said I had to change the permissions, but the /data folder do show up when you click on home. I curious to see if this worked, because the partitions are created *before* you create your username, but it seems to be all right. 

The only limitation of this experiment is that I used one virtual HDD with these partitions, not two virtual HDDs... But hopefully it *should* work the same way when I try this out "for real". :P

I'll do the reinstall later this afternoon, so expect me to post an update!

---

### Post by darkod on 2012-05-31
Also, you can simply use the old partition as mount point /data, not /home/data.

That way it will not be inside your home, but it will be one click away in /data.

Depends what is easier for you and how you want it to work.

---

### Post by Dry Lips on 2012-05-31
> **darkod said:**
> Also, you can simply use the old partition as mount point /data, not /home/data.

That way it will not be inside your home, but it will be one click away in /data.

Depends what is easier for you and how you want it to work.

Wouldn't it then be mounted next to all the other folders in / ?
When you open nautilus you'd have to click on filesystem>/data. But if you create
/home/username/data, you will have the folder accessible right away when opening nautilus...

---

### Post by oldfred on 2012-05-31
I created a separate /home for all of 5 minutes & realized I wanted /data, but I now mount it at /mnt/data so it does not show in nautilus but since all the old /home folders like Music, Documents etc are in my data partition I delete those folders in my new install (I then know they are empty) and link the folders from my data partition. I originally did it one command at a time but then found a one line script to mount them all at once.

sudo mkdir /mnt/data
# ( permissions stay with the partition not with the mountpoint ).
# so chown & chmod after mounting either manually or via fstab
sudo chown $USER:$USER /mnt/data
#sudo chmod 755 /mnt/data
#OR - The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /mnt/data
#Edit fstab with your UUID:
sudo blkid -o list
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext4         auto,users,rw,relatime               0  2 
#Verify entry is ok, if no errors it is:
sudo mount -a
#from home so default location of link is in /home/fred
mv Music oldMusic
# Music is a folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music
#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done

---

### Post by Lars Noodén on 2012-05-31
> **oldfred said:**
> 
#sudo chmod 766 /mnt/data

I think you might have wanted 755 or 775 instead of 766.  755 gives read access to Other, whereas 766 gives write access to Other.

---

### Post by darkod on 2012-05-31
> **Dry Lips said:**
> Wouldn't it then be mounted next to all the other folders in / ?
When you open nautilus you'd have to click on filesystem>/data. But if you create
/home/username/data, you will have the folder accessible right away when opening nautilus...

Correct.

As I said, depends entirely on you. For example, if you create a shortcut to /data you can open it with one click, while Home and then data folder still needs two steps. If you are after quick access, you can always create shortcuts to anywhere.

---

### Post by oldfred on 2012-05-31
Thanks Lars,
I think someone corrected me before but I have copies in several places in my notes. I actually have used 777 which can be too permissive. I find that the default for /home is 664 for files & 775 for folders and that should work well also.

I will edit my post above just in case someone uses it before reading rest of thread.

---

### Post by Dry Lips on 2012-05-31
What I outlined above worked!

My old data folder is now accessible from my /home/username folder, so it's right there when I open up Nautilus. 

Thanks to all the contributors in this thread!

---

