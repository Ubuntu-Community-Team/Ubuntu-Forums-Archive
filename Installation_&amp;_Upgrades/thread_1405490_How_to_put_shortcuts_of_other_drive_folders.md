---
title: "How to put shortcuts of other drive folders?"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by karumudi7 on 2010-02-12
Hi, I want to know how to put a shortcut link of a folder, which is in other drive to Home drive/Desktop. For example, I have 4 partitions one has a Windows,other has Kubuntu, other two was used for Storing my personal data. 
Generally, My music folder is in F: drive, if I made a shortcut of this folder to dektop/ Home folder, after a restart of Ubuntu the shortcut link is not working.!!!

---

### Post by WindPower on 2010-02-12
That is because your other partitions are not mounted automatically after a reboot. You need to edit /etc/fstab so that your partitions are always mounted when your computer starts, that way they'll always be there. See this wiki page: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab), or this thread: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by oldfred on 2010-02-13
Some info on mounting a data partition:

[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

I set mine up like poster Morgan Hall, then my data partition does not automatically show in nautilus, but just as links.

---

### Post by karumudi7 on 2010-02-16
> **WindPower said:**
> That is because your other partitions are not mounted automatically after a reboot. You need to edit /etc/fstab so that your partitions are always mounted when your computer starts, that way they'll always be there. See this wiki page: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab), or this thread: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

I seen the link u gave, but I am a Newbie, I cant understand that.
PLZ give the commands in order so that I will run In Terminal, so that I run them In order.
Anyone Plz solve this!
Thanks!!!

---

### Post by oldfred on 2010-02-16
I saved my history but did not do everything in order. My data partition has all the folders from /home so I delete the empty folders in /home and from home run the ln command. Of course you will have to change fred to your login name.

I mounted data here so I do not see a mount in nautilus. (only thru the links)
   21  sudo mkdir /usr/local/fred
   22  sudo mkdir /usr/local/fred/data
edited fstab and added the mount next command remounts fstab and displays any errors if any
   23  sudo mount -a
   64  sudo chown fred:fred /usr/local/fred/data
   72  sudo chown fred:fred /usr/local/fred
   47  sudo chmod 766 /usr/local/fred/data

From home I linked the folders in data.
   92  ln -s /usr/local/fred/data/Music
   93  ln -s /usr/local/fred/data/Documents
   94  ln -s /usr/local/fred/data/Pictures
etc for every folder

My entry in fstab:
# Entry for /dev/sdc6 :
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2

---

### Post by Morbius1 on 2010-02-16
> [I][B]Step 1: Get a list of your partitions
[/B][/I]
Open **Terminal**
Type [B]sudo blkid -c /dev/null
[/B]
You will get an output that looks like this:
[QUOTE]/dev/sda1: UUID="DA9056C19056A3B3" LABEL="WinD" TYPE="[COLOR=Blue]ntfs[/COLOR]"
/dev/sda6: LABEL="COMMON" UUID="C4DB-C1B0" TYPE="[COLOR=Blue]vfat[/COLOR]"
/dev/sdb2: LABEL="Data" UUID="e92eaf02-ff61-4db0-9397-35f1aadb98e8" TYPE="[COLOR=Blue]ext3[/COLOR]"*** Step 2: Create a home ( mount point ) for your partition to live in:***

Open **Terminal**
Type [B]sudo mkdir /media/FDrive
[/B]
NOTE: The mount point can be anywhere. If it's in your /home or /media folders it will show up under "Places". If it's directly off "/" or /mnt it will not.

*** Step 3: Create an entry in fstab that will automatically mount that partition at startup. Use the following examples as templates depending on how the partition was formatted:***
> /dev/sda1 /media/FDrive [COLOR=Blue]ntfs[/COLOR] defaults,nls=utf8,umask=007,gid=46 0 0
/dev/sda6 /media/FDrive [COLOR=Blue]vfat[/COLOR] utf8,umask=007,gid=46 0 2
/dev/sdb2 /media/FDrive [COLOR=Blue]ext3[/COLOR] relatime 0 2The first two will mount an ntfs or FAT32 partition with owner = root and with permissions for all local users ( gid=46) to read and write.

The last one will mount a linux formatted partition with owner = root and with read / write permissions to root only so that will have to be adjusted after mounting. For example:

Open **Terminal**
Type **sudo chown -R **karumudi** /media/FDrive**
[COLOR=Blue]*This will change ownership from root to you.*[/COLOR]

There are a great number of different options you can use with these fstab entries depending on your particular needs. Some are only applicable to specific filesystems, but for the most part this is a good starting point. In fact the templates you see in step 3 are what happens when you allow Ubuntu to set up these non-system partitions when choosing the manual partitioning option during an install.[/QUOTE]When you are done with editing fstab, save it and in a Terminal type: **sudo mount -a**
This will mount the new entries in fstab and tell you if there are any errors.

Now create the shortcut, however one does that in KDE, and see if you can access the Music directory.

---

