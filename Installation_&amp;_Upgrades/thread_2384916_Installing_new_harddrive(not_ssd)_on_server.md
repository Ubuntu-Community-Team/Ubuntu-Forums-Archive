---
title: "Installing new harddrive(not ssd) on server"
date: 2018-02-14
forum: Installation &amp; Upgrades
---

### Post by blumarmalade on 2018-02-14
Hi, i've just aquired a WD red drive for my 16.04 server but i'm unsure how to install it as i'm completely new to linux. I'm taking a course on lunux, but i just want to get this done right.

Background:
So i'm developing a media streaming app that needs a harddrive for large video files(I know an ssd is better but i only have this old harddrive to use). The app streams the video to an url that is to be used for another mobile app. I already got the app running behind nginx. But this harddrive must also function as a share with windows machines, so that users can put their movies here. 

In short:
Could anyone point me in a direction on how to add this drive on a headless server? I'm talking very basic stuff like formating(would ext4 be correct for my use?) it and partitioning it and putting it in the best directory for my usecase. I'm used to windows, but even there I remember I had to do some magic to set up these old harddrives unlike ssd.

Any help much appreciated :)

---

### Post by TheFu on 2018-02-14
There is nothing different that I know between using a spinning disk and a normal SATA connected SSD on Linux.
Assuming you are booting from other media and these disks are NOT for RAID and you have a backup solution planned (data loss sucks).
There are no absolutes, but a few ideas:
* Ensure GPT partition table is made. 
* Use parted to make partitions. I'd use 1.
* Use LVM to make physical volumes (full partition), volume groups (full partition) and at least 1 logical volume (20% of the available space for now).  There are many reasons for using LVM. Do not allocate all the available storage to the LV.  It makes sense on SSDs too, BTW.
* mkfs on the LV - I'd use ext4
* create a mount point for the storage somewhere. A mount point is just an empty directory (well, it actually doesn't have to be empty, but it doesn't make sense 99.99999999% of the time to mount storage to a non-empty directory).  I'm partial to using /D or /Data for mount point locations for stuff like this. Short, but clear, since I plan to put lots of disks there. For media - /D/M, /D/TV, /D/Music ... you get the idea.  Then I had to go with /D/M2, /D/TV2, etc ... and /D/M3, .... 
* mount the LV to the mount point.  That's via the fstab if permanently connected or through autofs if USB or NFS mounted.
* setup backups; All disks fail. They seldom fail when it is convenient. 1 month, 3 yrs, 7 yrs, 13 yrs - they all fail and we don't get to pick when.
* setup ssh, fail2ban so you and your users can access the storage using ssh, sftp, scp.
* You might want to use tune2fs to remove the reserved blocks for the LV that ext4 (and all Linux file systems) creates.  The default reserved amount is 5%, which can be significant, especially on 4T disks.

Be happy.

Nothing about these steps is specific for spinning HDDs. I'd do the same with a large, non-OS, SSD.

LVM is an intermediate skill, but definitely worth using on a "server" for all the conveniences it can provide. It is also faster at mkfs - nearly instantaneous regardless of the underlying LV size.

Why leave most of the storage unallocated?  LVM lets you increase storage to an existing LV as needed.  People do automate that process, though I never have.  Running tight on storage, but being able to add some, as needed, gives you an opportunity for users to learn that storage isn't infinite and there is a cost.  At 75% used, get more money for more storage - don't forget to get money for more backup capabilities too.

Clear as mud?

---

### Post by blumarmalade on 2018-02-15
Thanks for the help, much apreciated!

I will have to look more into LVM. I've been wondering where some of my storage went, haha.

---

### Post by TheFu on 2018-02-15
> **blumarmalade said:**
> Thanks for the help, much apreciated!

I will have to look more into LVM. I've been wondering where some of my storage went, haha.

There are easier methods than what I described above.
There are shorter methods than what I described above.
I tried to say specific tools with the expectation that you would research EACH and learn to use them sufficiently so that no damage would happen.  THAT is on you.  These are dangerous tools with very little error checking. If you tell parted to delete the partition containing the OS, it will.  If you tell mkfs to create a new file system on the wrong partition/LV, it will, wiping the prior data that might be there.

The training wheels are off when you are a Linux admin.  Be certain you understand every option and every input BEFORE hitting <enter>.  Total data loss is very possible.

---

### Post by Doug S on 2018-02-15
> **TheFu said:**
> These are dangerous tools with very little error checking. If you tell parted to delete the partition containing the OS, it will.  If you tell mkfs to create a new file system on the wrong partition/LV, it will, wiping the prior data that might be there.+1.
When adding a new disk, I will actually unplug my main drive, boot with a bootable gparted live CD, and then partition and format the new drive.

Myself, I never use LVM.

---

