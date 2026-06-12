---
title: "SSD upgrade"
date: 2012-06-15
forum: Installation &amp; Upgrades
---

### Post by KegHead on 2012-06-15
Hi!

I hope to purchase a new ssd for my Atom based self build.

What's the best way to copy my current setup onto the ssd?

Also once copied, I'd like to completely wipe the old hd clean and use as a 2nd drive.

Thanks!

KegHead

---

### Post by habana on 2012-06-17
Hello Keghead

Here's what I did. These notes were made for my own benefit so they might be a bit cryptic! I installed the SSD and  used Ubuntu 11.10 to partition/format the SSD. I made a separate partition on the SSD for the home directory and used a symlink to store all data on the HDD. You may not wish to do that. The SSD (60GB) is much bigger than I needed but was the smallest available. I used 20GB for the OS and 40GB for /home. 

I did have a boot problem initially (see para 5). Not sure why but I had to restore grub 2.

None of this work is original - all gleaned form various forums.

[SIZE="3"]**New PC notes**[/SIZE]


**1.   SSD alignment**

Use fdisk to align the partitions on the SSD

First partition must start on second cylinder start or later. By default fdisk uses 255 heads and 63 sectors to make a cylinder.. OCZ recommend H=32 and S=32 so H*S = 1024.

Use f disk -l to identify SSD - in my case sda

Now use fdisk -H -S -u -c /dev/sda and follow:
[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226#post373226](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&p=373226#post373226)

For 20G, 2,097,152 sectors out of a total 117231408

Thus sda1  start 2048 end 41945087 and sda2 start 41945088 end 117231407

**2. SSD formattting**

sudo mke2fs -t ext4 /dev/sda1
sudo mke2fs -t ext4 /dev/sda2

For more info see:
[http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&highlight=format+ext4](http://www.ocztechnologyforum.com/forum/showthread.php?54379-Linux-Tips-tweaks-and-alignment&highlight=format+ext4)

**3. Download OS**

Download OS desktop ISO from [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Burn to CD 



**4. Copy hidden hiles from /home to sda2**

sudo mkdir  mnt/data

cd /mnt
sudo chown -R bill data
sudo mount /dev/sda2 /mnt/data

sudo umount /mnt/data (make sure no utilty is looking at sda2)

[B]5. OS installation
[/B]

Install from Live Disk. 
Boot problem so see separate document to sort this out (boot restoration.doc). 
If grub menu shows, sudo gedit /etc/defaultgrub and uncomment GRUB_HIDDEN_TIMEOUT=0. This didn't work because I have more than one OS on the system. Revisit this when 11.10 removed.
Once into new OS, check that a theme is selected in "Appearance" otherwise text may not be visible.

**6. Link data drive to /home**

Mount point for the data drive is /mnt/data under bill so symlink required is 
ln -s /mnt/data/bill /home/bill/data

This points all files saved to home/bill/data (which doesn't exist) to the data drive. Strangely, this data folder appears on the desktop. It is possible to change which folder is used for the desktop by editing the users-dirs.dirs file in the .config directory, see
[http://www.howtogeek.com/howto/17752/use-any-folder-for-your-ubuntu-desktop-even-a-dropbox-folder/](http://www.howtogeek.com/howto/17752/use-any-folder-for-your-ubuntu-desktop-even-a-dropbox-folder/)

gedit the desktop entry from $HOME  to $Home/data/Desktop

**7. Trim**

To enable Trim, back up the fstab file and then add discard to the options for sda1 and sda2

sudo cp /etc/fstab ~/fstab.bak
gksudo gedit /etc/fstab

**8. Fine tuning**

Edit fstab to add noatime to each ssd partition. This stops writing to SSD every time a file is accessed.
Edit fstab to store temporary files on ramdisk
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
tmpfs /var/tmp tmpfs defaults,noatime,mode=1777 0 0

To change the scheduler, install sysfsutils amd add the following to the /etc/sysfs.conf file:
block/sda/queue/scheduler = noop
After reboot confirm with
cat /sys/block/sda/queue/scheduler


I hope some of the above is useful to you

---

### Post by KegHead on 2012-06-18
Hi!

I'll check it out!

Also, anyone had any luck with momentus  intel drives?

KegHead

---

### Post by adad on 2012-08-04
I followed the instructions on this blog to tweak my SSD under Ubuntu 12.04.

[http://brizoma.wordpress.com/2012/08/04/running-ubuntu-and-other-linux-flavors-on-an-ssd/](http://brizoma.wordpress.com/2012/08/04/running-ubuntu-and-other-linux-flavors-on-an-ssd/)

I have a single partition on my SSD and just pick the old installation from the HDD for the swap file. I have plenty of RAM, so there is no problem using the slower HDD file.

Just remember to select no swap file during Ubuntu's install.

---

