---
title: "Upgrade to 10.04 failed - need help to unlock files."
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by doihavetodothis? on 2010-09-10
My upgrade has failed and I cannot access anything except the command line - 
results below:
sudo apt-get upgrade
W: Not using locking for read only lock file /var/lib/dpkg/lock
E: dpkg was interrupted you must manually run 'sudo dpkg --configure -a ' to 
correct the problem
When I do this it says
dpkg: unable to access dpkg status area: read only file system.

if I try to remove the lock using 
sudo rm  /var/lib/dpkg/lock
it says rm cannot remove `/var/lib/dpkg/lock': read only file system.
I cannot run any other commands like (sudo get-apt) -f install or --fix -missing install or dist-upgrade, they all give me the read only error. 

I can run the live CD, which I have since downloaded. I don't want to use it to 
install because it will overwrite my home folder, as far as I can see. I don't 
have the home folder on a separate /. I can't copy or back up my mail from my 
home folder or some of my other files, permission is denied. I can't copy them 
using gksu nautilus either. I don't know how to back them up using the command line only, or if that is possible. I am running a dual boot with windows XP. XP is 
still working.
Please help me to fix this and save my data.
Thank you.

---

### Post by viralmeme on 2010-09-10
> **doihavetodothis? said:**
> My upgrade has failed and I cannot access anything except the command line - 
results below:
Boot from the Live CD and run 'fsck -y /dev/hda1`, replace hda1 with the Linux partition.

---

### Post by doihavetodothis? on 2010-09-10
> **viralmeme said:**
> Boot from the Live CD and run 'fsck -y /dev/hda1`, replace hda1 with the Linux partition.
If i boot from the livecd and run that command as sudo it only checks itself, not my hard drive. This is what i get from the live cd check.
 ubuntu@ubuntu:~$ sudo su
root@ubuntu:/home/ubuntu# sudo fsck -y/dev/sda3
fsck from util-linux-ng 2.17.2
Am I doing it correctly?

 my linux partition in on sda3. if I run fsck when i am in recovery mode it tells me that it's ok:

---

### Post by sharathcshekhar on 2010-09-10
> 
I can't copy or back up my mail from my
home folder or some of my other files, permission is denied. I can't copy them
using gksu nautilus either. I don't know how to back them up using the command line only, or if that is possible.

I can probably help a little with this. Are you able the see you files and folders in your home directory when you mount boot from live cd? Is your linux partition visible under "Places" in live cd? If not, what about under fdisk -l?

---

### Post by doihavetodothis? on 2010-09-10
> **sharathcshekhar said:**
> I can probably help a little with this. Are you able the see you files and folders in your home directory when you mount boot from live cd? Is your linux partition visible under "Places" in live cd? If not, what about under fdisk -l?

Thanks:) When i boot from the live cd  I can see my home directory, just can't copy all of it, some folders and files are read only (like my mail). The output of fdisk -l is this:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb345b345

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3966    31856863+   7  HPFS/NTFS
/dev/sda2            3967        4090      996030   82  Linux swap / Solaris
/dev/sda3            4091        9729    45295267+  83  Linux

Disk /dev/sdb: 8005 MB, 8005787648 bytes
32 heads, 63 sectors/track, 7756 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x079f595b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7756     7818016+   b  W95 FAT32

---

### Post by sharathcshekhar on 2010-09-11
In that case, I am suspecting permission problems. Like if your directory does not have executable permissions, you cannot enter it, even if you are root!
You can try 2 things: 
1. In command line, cd to the path of the directory which you cannot access and give "ls -l". If the first column does not have something like this:
"drwxr-xr-x", then it is definitely permission problem. You can solve by:
chmod +x directory_name. Unfortunately you will have to do this for all the directories you cannot access. Giving a 
"sudo chmod 755 /home/username -R" Solves your problem. But is not recommended as all the files will get executable perms.
2. Since you are using live cd, if there is no permission for a file, or if you are not the owner of the file, using "sudo nautilus" would essentially solve it. You can always give ls -l in the terminal to check the permissions.

Finally I would say, this just a solutions to back up data. Once it is safe, you can probably play around to investigate the real problem. Post back if this does not solve your problem.

---

### Post by doihavetodothis? on 2010-09-11
HI Sharath,
Thanks so much for your help - I've learnt a lot ! including navigating using the command line In the end though, sudo nautilus was the answer, I had tried gksu nautilus before but that didn't seem to work. Or I have just discovered more since then. chmod returned read only file system everywhere I used it. Anyway once I was in nautilus I changed file permissions there and copied my whole home folder onto my windows partition, Now I am going to make a mount partition for the os and a partition for /home and start all over again... instead of having it on one partition. In your opinion will I be able to restore my data by copying the home folder back into the home partition - is this the right way to go?
Thanks for your help!
Karin.

---

### Post by sharathcshekhar on 2010-09-12
Good to know your data is still alive. Having a separate home partition is always recommended. You can restore all your data from your Windows drives. But all the file permissions shall be reset. Which means, even though you are the owner of the file, all files would behave like having 777 permissions when you copy them from a windows filesystem. Of course, you wont have any problems to access them can change it anytime you want. But You will to spend some time changing the permissions unless you can manage to write a quick script to do it for you!

---

### Post by doihavetodothis? on 2010-09-12
Thank you for your help - I'm really pleased to have this fixed! I don't know how to write a script but I will go through them and re-set them all. :)

---

