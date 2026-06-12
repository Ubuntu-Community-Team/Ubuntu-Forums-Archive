---
title: "Ubuntu 12.04 x64 install on SSD"
date: 2012-07-25
forum: Installation &amp; Upgrades
---

### Post by adschem on 2012-07-25
Hi

I have been using 10.04 on my PC for a while now and was wanting to upgrade to 12.04 and have recently got a new 60gb SSD I was wanting to use this for boot purposes and for added speed, I have a 2TB drive that I was planning on using for main storage of data. 

I have been reading around and found that people suggest putting the swap partition on the HDD as apposed to the SSD, I have 8gb of RAM (AMD x6 processor), but seem to eat into swap space when using matlab and virtual box (XP). Another thing that I have found is that some suggusted putting /home on the SSD with a /data partition on the HDD which would make loading program's faster etc, I was wondering if anyone had any advice on this? 

What would be the best partitioning set up for a fresh install to make my computer as fast as possible?

Thanks
Adam

---

### Post by 2F4U on 2012-07-25
Think about putting swap, and maybe /var and /tmp on the harddisk. This would probably increase the lifetime of your SSD. Personally, I would not put /home on the SSD due to the potential high amount of writes.

---

### Post by adschem on 2012-07-25
Thanks for the reply, any suggestions on what size to make the swap, /var and /tmp? 

In 10.04 I had 16gb of swap not sure if that is overkill though?

---

### Post by ddk1965 on 2012-07-25
Swap is easy just the size of your current memory, I take always 1GB because on 1T drive 1G is nothing ;-) /tmp and /var you better take them a bit big /tmp 16Gb and var depending on your websites sizes ...

---

### Post by adschem on 2012-07-25
Ok, I shall go for 8gb of swap then on my HDD, is it worth putting more in for times when RAM is being eaten by various other programs? 

Will I need to configure any files for the SSD to make its life longer/keep its performance high?

---

### Post by drmrgd on 2012-07-25
Here's a link to the Arch Linux Wiki page concerning SSDs that someone posted here yesterday:

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

I found this to be extremely informative to understand some of the options regarding the formatting of SSDs and what might be the best way to go about it.

---

### Post by adschem on 2012-07-25
Would using GParted not be a suitable way of partitioning an SSD then? Can anyone give me some advice on how to automatically enable TRIM on my new SSD please?

---

### Post by darkod on 2012-07-25
> **2F4U said:**
>  Personally, I would not put /home on the SSD due to the potential high amount of writes.

This is true if you let the Downloads, Music, Video, etc folders to get filled up with big files.

On the other hand, I do see a point /home to be on the SSD to allow for faster programs loading since settings are in hidden folders in your Home.

If you create /data mount point (partition) on the HDD and make a habit to keep all big files there, your /home won't grow big at all.

That's what I would do.

EDIT PS: I just noticed it says high amount of writes which doesn't always mean high amounts of data. But I would still put /home on the SSD. You would have something like 3yrs warranty anyway, you would probably want new SSD after that time. :)

---

### Post by adschem on 2012-07-25
Hi Darkod (also everyone else!)

As you have done it and I am yet to is there a way of setting the default location for things like Documents, Downloads, music etc to the /data mount point? If so then I can defiantly see the logic of putting /home on the SSD, it has a 5 year warranty with it so by that time I will probably have ended up changing it anyway/adding more memory to my system.

---

### Post by oldfred on 2012-07-25
My 'new' (last Dec) 60GB SSD has 4 partitions. I hope to build a new system soon (those that may pay attention say Fred has said that for a while :) ), so I also put a efi partition for the new system which will be UEFI, a bios_grub for use with BIOS and gpt partitioned drives and two / (root) partitions. I converted to using 25GB / including /home with 9.10 and conversion to 64bit. But all data is on other drives and I aggressively move some hidden data folders like Firefox & Thunderbird also. The one large data is my .wine with Picasa as that is a bit more complex to move.

I like links and have all the data folders like Documents, Music etc as folders in my data partition at /mnt/data and /mnt/shared (NTFS) and link each folder to /home. But Morbius1 has good points on using bind not links especially if using Samba.

Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

The Arch site has a lot of really good info on SSD. It recommends gpt partitioning unless you want Windows. Then you can only use gpt if booting with UEFI.

```
fred@fred-Precise:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdd3        28G  9.2G   18G  35% /
udev            2.0G  4.0K  2.0G   1% /dev
tmpfs           791M 1016K  790M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  188K  2.0G   1% /run/shm
/dev/sda1        55G   36G   20G  65% /mnt/cdrive
/dev/sdc2       100G   30G   71G  30% /mnt/shared
/dev/sdc6        97G   45G   47G  50% /mnt/data
/dev/sdb4       122G   26G   90G  23% /media/MavData
/dev/sdd4        28G  5.3G   22G  21% /media/quantal

```

```
fred@fred-Precise:~$ sudo parted /dev/sdd unit s print
[sudo] password for fred: 
Model: ATA SSD G2 series 64 (scsi)
Disk /dev/sdd: 117231408s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End         Size       File system  Name     Flags
 1      2048s      616447s     614400s    fat32                 boot
 2      616448s    618495s     2048s                            bios_grub
 3      618496s    58925055s   58306560s  ext4         Precise
 4      58925056s  117229743s  58304688s  ext4         Quantal


```

---

### Post by adschem on 2012-07-25
Thanks for the reply OldFred

I have had a look at you other post and seen the following code: 

sudo mkdir /mnt/data
sudo chown $USER:$USER /mnt/data
#sudo chmod 766 /mnt/data
#OR - The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /mnt/data
# find your UUID
sudo blkid
#Edit fstab with your UUID, use ext3 or ext4 depending on format:
gksudo gedit /etc/fstab
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext3         auto,users,rw,relatime               0  2 
#Verify entry is ok, if no errors it is:
sudo mount -a
#from home so default location of link is in /home/$USER
# cannot have duplicate entries, so move current to temporary location, repeat for each folder you want to move.
mv Music oldMusic
# Music is then also the folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music
#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done 


I am not quite sure I fully understand what I need to do to implement this. I have created a /data partition on my HDD with /home (30GB) on my SSD. The folders that I will need to move to my HDD would be Documents music etc, and /.virtualbox 

would the below be the correct way of using your code? 

sudo mkdir /data
sudo chown $USER:$USER /data
#sudo chmod 766 /data
#OR - The big "X" will also not make files executable unless they were executable to begin with.
sudo chmod -R a+rwX /data
# find your UUID
sudo blkid
#Edit fstab with your UUID, use ext3 or ext4 depending on format:
gksudo gedit /etc/fstab
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /mnt/data    ext4         auto,users,rw,relatime               0  2 

^I have no idea if i need to change the above/if i do how I should?

#Verify entry is ok, if no errors it is:
sudo mount -a
#from home so default location of link is in /home/$USER
# cannot have duplicate entries, so move current to temporary location, repeat for each folder you want to move.
mv Music oldMusic
# Music is then also the folder in the partition mounted as /mnt/data
ln -s /mnt/data/Music
#Or link all folders with one command:
for i in `echo /mnt/data/*`;do ln -s $i; done


One other way I have seen of doing it is,  

ln -s /data/Videos

Now i am not sure if this will work, but If i was to delete the old locations in home and move them across? 

Apologies for my apparent incredible lack of knowledge.

---

### Post by oldfred on 2012-07-25
With your mount in / of a /data partition your version looks ok. Make sure you have copied/backed up all data and do it one command at a time. 

Comments: 
The linking depends totally on where/how you mount in fstab. I use /mnt/data. A mount in /mnt will not show in Nautilus by default which is what I want since I link all the folders in the data partition. If you mount in /data you have to use that in all your links. I did that for one or two installs and an old timer said that was not good practice. I also had found other locations. Some argue over /mnt or /media to mount drives, but the real difference is /mnt is not in Naulitus and /media is.

My data partition is ext3, I would suggest ext4 now, so you also have to change that depending on format. I also do the same with a NTFS shared partition but only link the top level.

The first time or two I did it manually. I had used rsync to copy all the data folders over and now do the linking as soon as I install, so I know the current folders (Music, Documents, etc) all all empty, so I know I can just delete them. Otherwise best to mv to another name until you know everything works.

I did it all manually the first few times, but was installing to two computers and on desktop reinstall alpha, beta & each new install and go frustrated running all the same command. Found the one short cut that mounts all of them, but if for example Music already exists it gives an error. I then listed history and copied to a bash file which I run with each new install.

---

### Post by adschem on 2012-07-26
Thank you for all your help all up and running now! :)

---

### Post by oldfred on 2012-07-26
Glad you got it working.

---

### Post by adad on 2012-08-04
I found this article very useful to tweak my SSD under Ubuntu 12.04.

[http://brizoma.wordpress.com/2012/08/04/running-ubuntu-and-other-linux-flavors-on-an-ssd/](http://brizoma.wordpress.com/2012/08/04/running-ubuntu-and-other-linux-flavors-on-an-ssd/)

I have a single partition on my SSD and just pick the old installation from the HDD for the swap file. I have plenty of RAM, so there is no problem using the slower HDD file.

Just remember to select no swap file during Ubuntu's install.

---

