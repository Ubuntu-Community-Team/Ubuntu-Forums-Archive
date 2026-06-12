---
title: "Urgent: Need help accessing crashed system"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2008-02-13
I am using the Live CD to access this board. I can not access the desktop of my regular Ubuntu due to a messed up upgrade from fiesty to gutsy.  I thought I had restored all the settings to fiesty but when I turned the machine off and tried to reload fiesty grub showed it as version 7.10 and it would not load the GDM.

 I could not work out how to use Aptitude to restore the versions to 7.04. Is it easy because I could not make it do the rollbacks to fiesty. I could not work out the correct key movements to do that. 

Can I burn the iso of gutsy onto a cd using the live cd of fiesty? The only option seems to be Serpentine CD music creator. Will that do it?

I have mounted the drives from within the live cd. I would like to copy my home directory to another drive. So far it has said that I can not access the drive because I am not the owner.

Currently I wish to copy the home drive that is on disk to disk-2. What is the syntax? I tried

sudo cp disk/home disk-2

that did not work. 

Please help. I have an unusable system at the moment.

Robin

---

### Post by Herman on 2008-02-13
> I could not work out how to use Aptitude to restore the versions to 7.04. Is it easy because I could not make it do the rollbacks to fiesty. I could not work out the correct key movements to do that.  I didn't know you could 'roll back' an upgrade in Ubuntu. I don't know how either.
>  I have mounted the drives from within the live cd.:) Good.
> I would like to copy my home directory to another drive.Good idea.
> So far it has said that I can not access the drive because I am not the owner. Providing it's only a data drive and not an operating system, you should be able to change the file ownership and permissions with a chown or a chmod command. sudo chmod -777 /media/datapartition/ should do it,
```
sudo chmod -777 /media/datapartition
```Where: /media/datapartition is the mount point for the file system you want to copy your data to.
>  Currently I wish to copy the home drive that is on disk to disk-2. What is the syntax? I tried sudo cp disk/home disk-2  that did not work. How about 'cp -rf /media/ubuntu/home/Robbyx/* /media/datapartition/', or something like that?
```
cp -rf /media/ubuntu/home/Robbyx/* /media/datapartition/
```I'm not at all sure what names you actually have for your directories and mount points so I just made that up, but you should be able to get an idea of the syntax from that, I hope.

Ask me and tell me more and I'll be able to help you better.

Regards, Herman :)

---

### Post by Robbyx on 2008-02-14
Thank you for helping me.


I have 3 hard disks in the machine:

/dev/hda1 ext3  (this contains the old messed up operating system including home which I am trying to copy to hdd3)
hdd1 ( contains the new gutsy operating system)
hdd3 (empty and to where I am copying the home from hda1)
sda1 this is a 3ware 8006-2 raid drive and it is not being loaded or being seen other than under gparted.

This is what my fstab looks like:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdd1
UUID=180be6dd-045d-483d-970e-ef032ab617fb /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdd5
UUID=a7803544-2f7d-4727-ba44-9ffbafa2b51b none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

Both hda1 and hdd3 will not mount manually. I should be able to mount a drive from within Pc man file manager.

I have previously altered fstab so as to bring in the extra drives but it looks as if Ubuntu has reverted to an earlier version.

I have created hdd1, hdd3, sda1 as subdirectories within media.


So my first problem is to get the drives to be mounted. Can you help? My next problem is to copy over the old home.

Robin

---

### Post by Herman on 2008-02-14
Okay, I don't know what you mean when you say 
>  sda1 this is a 3ware 8006-2 **raid **drive and it is not being loaded or being seen other than under gparted. I don't know very much about RAID, I have never tried any kind of RAID myself, so I don't feel comfortable giving advice if it has anything to do with some kind of RAID. I understand there are lots of different kinds and probably I'd need to do a lot of studying.

If it's just a normal setup with three hard disks I can help you to edit your /etc/fstab file. 
Please post the output from 'sudo fdisk -lu' and 'ls /dev/disk/by-uuid/ -alh' here and I'll see what I can do for you,```
sudo fdisk -lu
``````
ls /dev/disk/by-uuid/ -alh
```I'd need to know what type of file system each partition contains too, at least for the ones you want to mount in /etc/fstab.. You probably already know that or can just take a look with GParted.

Regards, Herman :)

---

### Post by Robbyx on 2008-02-14
I am trying to work my way through the problem.
Does this help?

sudo fdisk -l produces:

> robin@robin-desktop:~$ sudo fdisk -l
[sudo] password for robin:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02470247

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       13790   110768143+  83  Linux
/dev/hda2           13791       14593     6450097+   f  W95 Ext'd (LBA)
/dev/hda5           13791       14593     6450066   82  Linux swap / Solaris

Disk /dev/hdd: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf55bf55b

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        2493    20024991   83  Linux
/dev/hdd2            4796        5005     1686825    5  Extended
/dev/hdd3            2494        4795    18490815   83  Linux
/dev/hdd5            4796        5005     1686793+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 250.0 GB, 250058301440 bytes
64 heads, 32 sectors/track, 238474 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table


---

### Post by Robbyx on 2008-02-14
Our replies crossed. Here is what you asked for:

> robin@robin-desktop:~$ sudo fdisk -lu

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x02470247

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   221536349   110768143+  83  Linux
/dev/hda2       221536350   234436544     6450097+   f  W95 Ext'd (LBA)
/dev/hda5       221536413   234436544     6450066   82  Linux swap / Solaris

Disk /dev/hdd: 41.1 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders, total 80418240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf55bf55b

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *          63    40050044    20024991   83  Linux
/dev/hdd2        77031675    80405324     1686825    5  Extended
/dev/hdd3        40050045    77031674    18490815   83  Linux
/dev/hdd5        77031738    80405324     1686793+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 250.0 GB, 250058301440 bytes
64 heads, 32 sectors/track, 238474 cylinders, total 488395120 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table


>  ls /dev/disk/by-uuid/ -alh
total 0
drwxr-xr-x 2 root root 140 2008-02-14 19:17 .
drwxr-xr-x 5 root root 100 2008-02-14 19:17 ..
lrwxrwxrwx 1 root root  10 2008-02-14 19:17 180be6dd-045d-483d-970e-ef032ab617fb -> ../../hdd1
lrwxrwxrwx 1 root root  10 2008-02-14 19:17 221d448e-c456-4e67-b1f4-675a654e16c8 -> ../../hda1
lrwxrwxrwx 1 root root  10 2008-02-14 19:17 a2bd8bc4-f245-4fb3-b135-11ef71c29fe5 -> ../../hda5
lrwxrwxrwx 1 root root  10 2008-02-14 19:17 a7803544-2f7d-4727-ba44-9ffbafa2b51b -> ../../hdd5
lrwxrwxrwx 1 root root  10 2008-02-14 19:17 f453ce62-336b-490b-8447-55acd2adc952 -> ../../hdd3


---

### Post by Robbyx on 2008-02-14
hda1 (the old linux system that crashed in the upgrade to gutsy)

hdd1 (the newly created clean gutsy)


and hdd3 (a drive waiting to take the old home directory)


 are all ext3

---

### Post by Herman on 2008-02-14
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/hdd1   contains the new gutsy operating system
UUID=180be6dd-045d-483d-970e-ef032ab617fb /    ext3    defaults,errors=remount-ro 0       1

#/dev/hda1  contains the old messed up operating system
UUID=221d448e-c456-4e67-b1f4-675a654e16c8 /media/hda1    ext3    defaults    0       2

# /dev/hdd3 empty and to where I am copying the home from hda1
UUID=f453ce62-336b-490b-8447-55acd2adc952 /media/hdd3    ext3    defaults    0       2

# /dev/sda1 this is a 3ware 8006-2 raid drive and it is not being loaded or being seen other than under gparted
# /dev/sda doesn't contain a valid partition table

# /dev/hdd5
UUID=a7803544-2f7d-4727-ba44-9ffbafa2b51b none            swap    sw              0       0

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```:) Here's my edited /etc/fstab file for you.

Please boot your Ubuntu Live CD first and either [run a filesystem check with GParted]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_")on each of your ext3 file systems OR [run a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") - from a Live CD - command line.

Also, you said you made a mount point in media for hdd1, hdd3, sda1. Isn't hdd1 the one you're working from?  Do you need one for hda1?

I can't help you with your sda1 3ware 8006-2 raid drive, according to fdisk it doesn't have a valid partition table, so you might need to use whatever hardware or software it was used with before to access it again. Sorry I don't know much about RAID setups.

Try that and see if it works,
Regards,Herman  :)

---

### Post by Robbyx on 2008-02-14
Thank you for your help. I have the directories mounted.


 I am struggling with copying the old home contents to the new home ie hdd3. 

I tried 


sudo chown -R robin:robin  /hdd3
sudo chmod -R 755 /media/hdd3

I tried the same for the old home.

I have gone in as sudo and copied and pasted  from the old home to the new location and yet it ceases to copy when it gets to .multiget/cmdline.pipe

I am wondering what to do. I am assuming the active home should be under my ownership  not that of the supervisor.

Do you suggest that I  first copy the current home to the new location and then copy over  just those .directories in the old home that look as if I need them because I will be installing their applications?

---

### Post by Herman on 2008-02-14
I wouldn't care too much if everything doesn't get copied. You really just need all your regular files (photos, music, documents, etc.), and a few other things like your email, addressbook and other .evolution stuff, and your bookmarks from .mozilla.
If you have some files pertaining to other special applications you use you will want to copy the files and settings that belong to those as well. For example, I like to use 'Password Manager' so I need to copy my .gpass directory when I'm backing up or restoring my system.
I also use Seahorse, so I have PGP keys I need to keep, (actually I'm not sure where to look for those in a disabled system, probably .gnupg), but for my RSA keys for SSH, I just copy my entire .ssh directory to save time.
You need to click on 'view', 'show hidden files' to see them all, of course, just in case anyone doesn't know that yet.

It's just quicker and easier sometimes to copy the entire  /home/username directory in a backup if we're in a hurry.

When you go to restore all your stuff in your new /home/username directory, you'll already have some new updated versions of some of the files you need  or they will be created for you as you  open applications for the first time and get things set up.
It might actually do some harm to overwrite files relating to certain software we don't understand with files from maybe an older version from the old /home/usernam directory, I'm not sure. Just to be on the safe side I only restore what I need. That is my own personal data and files I can recognize and understand: addressbook, calendar, mail, memos and tasks I copy into my new  .evolution directory.
I open firefox and use the import wizard in firefox to import the bookmarks file  out of .mozilla.
I paste my .gpass dierctory into my new /home/username directory too, and when I install password manager and open it for the first time it automatically finds that file and I don't need to do anything.
The rest of the files I don't bother with because I don't know what they are and I don't want to break anything.

If you want to wait a little while I can try some commands out for you and see if I have any trouble copying an entire /home directory to another partition in another hard disk, just for fun. 

:idea: One more thought, (which we probably should have thought of first) is to try 'sudo nautilus', and do the job in GUI, but with root priveleges. Try that and see if you like it.:) ```
gksudo nautilus
```I'm trying that out right now in one of my other computers and it seems to be working fine, but it will take some time to finish.
EDIT: It worked almost seamlessly, but there was one error message, something about a symlink I thing, I just clicked 'skip', to continue.

Regards, Herman :)

---

### Post by Herman on 2008-02-14
```
sudo cp -pvr /media/hda1/home/robbyx /media/hdd3/
```:) You can use the command line if you  want to be a cool linux user. I'm not sure what your real username is in your computer, but that command should work if you check it for mistakes first. That does exactly the same thing as we just did with nautilus, but it makes lots of interesting text scroll up your terminal while it does the work, making the person sitting behind the screen appear super intelligent and geeky to anyone who happens to walk past who doesn't know much about Linux. 

The -p option preserves your file ownership and permissions, the -v option gives your the impresssive scrolling text, and the -r option is to make it 'recursive' (inclusive of all the folders and files with possibly more inside those and more inside those and so on).

This in not something I need to do every day so I ran an equivalent command in one of my computers and running that command went without a hitch at all.

---

### Post by Robbyx on 2008-02-15
Thank you very much for all your help. 

I have a problem with the raid drive not being recognised. I have posted a separate message.

Robin

---

### Post by Robbyx on 2008-02-17
I am now running with the new location of the home directory having moved it from the standard location  to a new partition.

Running under the standard location  partition the desktop was showing some fancy graphics. This caused windows to close in a fast  reducing fashion and for moving windows to be wobbly. Now that I have accessed the home page I used under Fiesty these fireworks have gone. 

Do you know what files and  folders I should copy from the Gutsy produced home over the older  files in the new location home?  I do not want to copy the lot for feat or upsseting my firefox and thunderbird settings

Robin

---

### Post by Robbyx on 2008-02-17
I have just switched on the graphics by changing the  appearance setting, but please still comment on whether or not I should be copying over any of the gutsy created files in the home directory.

---

### Post by Herman on 2008-02-17
Well, I never copy everything, I only copy the things I can identify,

After starting Evolution and running the setup wizard, I close it again and from the .mozilla folder I copy the addressbook folder, calendar, mail folder, memos and tasks folder. Then reboot and all those things are restored.

For Firefox I have the bookmarks file copied out of my backups folder or wherever you kept it and pasted out where I can find it in my /home/username folder ready to be imported.
Then I start my firefox web browser. Click 'Bookmarks', then 'Manage Bookmarks', then on the 'File Menu' of the 'Bookmarks Manager' window, click 'import'. That will start the 'import wizard'. Click 'next;, and navigate to your '/home/username' folder. Find your bookmarks file to be imported and click 'Open'.

That's most of it done already.

The rest depends on what programs you have installed.
If I missed anything you might find it in this page, [Back Up and Restore.]("http://users.bigpond.net.au/hermanzone/p13.htm")

Regards, Herman :)

---

### Post by Robbyx on 2008-02-18
Thank you very much for all of your comments. They were of great help. It is a pity that there is not a simple script that steps through each drive attached to the machine and asks how and where each drive is to be mounted defaulting to /media and creating the directories if they are not present. 

Robin

---

### Post by Herman on 2008-02-18
It would probably be worth a look through Synaptic Package Manager or Add/Remove Software, I'll bet there are several programs like that.

Hmm, how about 'Storage Device Manager', or 'Disk Management'? It might be worth trying out some programs like that to see which one you like the best.

Regards, Herman :)

---

### Post by Robbyx on 2008-03-04
I am struggling with a new hard disk. I have formated the partitions to reiserfs. I have it loading via fstab. That part works.  I now need to get the contens of the ext3 system drive over to a reiserfs format drive.  I am struggling.

 Should  I use the Ubuntu live CD. If so   how do I  copy the contents of drives that are not mounted? Is there a method that works? I can see from elsewhere that the command is cp -av from to, but I think the from and two have to be mounted folders. 

In the case of an unmounted drive what is the syntax for from and to? Alternatively is there a way of mounting drives from within the live cd?

Hope you can help

Robin

---

### Post by Herman on 2008-03-05
:) Hello Robbyx,
Well, you will need to mount your file systems first if they're not already mounted.
To mount your file systems you first need to make a mount point. A mount point is just an empty folder somewhere you will be able to open to see all the files in whatever file system it is you have mounted.
A mount point can be anywhere, but the normal places to make them are in either your /media directory or in your /mnt directory. The /media directory is the most popular choice for Ubuntu users, because than you'll have a Desktop icon for the mounted file system.

You won't need to use your LiveCD if you have a hard disk install Ubuntu, but let's pretend you want to do it with your Live CD for some reason.
First you would do 'sudo fdisk -lu' to check what your partitions are called in Linux. ```
sudo fdisk -lu
```Or you can look with Gnome Partition Editor, 'System'-->'Administration'-->'Partition Editor'.
Now, I don't know what your new hard disk will be, but I'll pretend for now that it's /dev/sdb

Next, you make your mount point, for example,
sudo mkdir /media/reiserfs_data
then then you can mount your file system from your new hard disk,
```
sudo mount -t reiserfs /dev/sdb1 /media/reiserfs_data

```You'll need to do the same with your ext3 data partition where I think you copied your files to,
```
sudo mkdir /media/ext3_data
``````
sudo mount -t ext3 /dev/hdd3 /media/ext3_data
```Now if you open the icons on your Desktop you can drag and drop the files from one hard disk to the other.
If you want to use a Linux command and you want to copy all the files from your ext3_data to your reiserfs_data, then try this,
```
cp -r /media/ext3_data/* /media/reiserfs_data/

```You might also be interested in taking a look at this page, [Back Up and Restore]("http://users.bigpond.net.au/hermanzone/p13.htm") .

I hope I have been helpful to you, feel free to ask more questions if you want to.

Regards, Herman :)

---

### Post by Robbyx on 2008-03-05
Thank you for that help. I have found the man pages lacking in examples. Can you  suggest a more explained source for the the various commands?

I will come back if I need further guidance. In the meantime I had a quick look at your backup page and it is most useful. Have you thought about recommending the foxmarks addon? It is an online bookmark synchroniser.  This means that I have been able to do a clean install of Firefox and import all the old bookmarks from foxmarks. No need to work out how to do the backup and restore and it backs up the bookmarks on a regular basis.

Robin

---

### Post by Robbyx on 2008-03-05
For one of my drives I would have liked to use reiser4. Am I right that it is not easily supported within Ubuntu ie without having to patch the kernel?

---

### Post by Herman on 2008-03-05
> Thank you for that help. I have found the man pages lacking in examples. Can you suggest a more explained source for the the various commands? Well I have attempted to explain different ways to mount your file systems here, [File Systems and Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm"). 
I agree with you about man pages, they're fine for someone who's already an expert, but they don't help much if you don't already know quite a bit about Linux. There's scope for someone to make up a more verbose version of man pages that people new to Linux will find easier to cope with. That would be a big job though. Best is to try some Linux courses. For some commands there are web pages made by people who have fallen in love with that command and want to share their knowledge, for example, AwesomeMachine's [Learn the DD command - LinuxQuestions.org]("http://www.google.com.au/url?sa=t&ct=res&cd=3&url=http%3A%2F%2Fwww.linuxquestions.org%2Fquestions%2Flinux-newbie-8%2Flearn-the-dd-command-362506%2F&ei=WfLOR_O6CqOGpASj7MGjCw&usg=AFQjCNGJ_jNkqIV2rfGQnWKXQlIk2w807A&sig2=FbX73Bs4sCO1KG3LvklArQ") or Nana Långstedt's  [_Linux File Permissions_]("http://www.tuxfiles.org/linuxhelp/filepermissions.html"). When we can find helpful pages like those it makes life a lot easier. There are lots of other great resources too, it's just a matter of finding the right ones that suit you. 
>  I will come back if I need further guidance. In the meantime I had a quick look at your backup page and it is most useful. Have you thought about recommending the foxmarks addon? It is an online bookmark synchroniser. This means that I have been able to do a clean install of Firefox and import all the old bookmarks from foxmarks. No need to work out how to do the backup and restore and it backs up the bookmarks on a regular basis. Thank you, I'll look into that as soon as I can.

Regards, Herman :)

---

### Post by Robbyx on 2008-03-05
Do you know the position on reiser4? I checked I do not think it is supported despite there being some reiser4 programs available for download in synaptec. I installed some of them but Ub complained about reiser4 in the fstab file.

> **Robbyx said:**
> For one of my drives I would have liked to use reiser4. Am I right that it is not easily supported within Ubuntu ie without having to patch the kernel?

---

### Post by Herman on 2008-03-06
I don't know, is reiser4 very much better than other file systems. I have tried reiserfs but normally I just stick with ext3.
Regards, Herman :)

---

### Post by Robbyx on 2008-03-07
All my efforts have come to nothing. I can get the new drive to load. It boots, and checks the files before loading Ubuntu. It starts to load and then freezes. In safe mode it stopped at s6-0000:00:0b.0-6. 

I used the super grub boot disk to choose the correct partition to start Ubuntu.
I do not want to have to reinstall Ubuntu. Do you have any ideas as to how to avoid this?


Robin

---

### Post by Herman on 2008-03-07
Sorry Robbyx, but I'm getting confused about what you're doing. :confused:

Back in post # 1 you had a messed up upgrade.
By post #12 we had made a backup of your files from your old /home directory to /dev/hdd3, but you couldn't get your 3ware RAID drive recognized.

Then in post #18 you bought a new sata hard disk and created a partition in /dev/sdb1 ( I think) , reiserfs, and copied the /home backup from your old /dev/hda1 /home in /dev/hdd3 files there (to /dev/sdb1).

Now, you're talking about trying to boot an operating system in your new hard drive. I am guessing you have installed Ubuntu there and you mounted your old /home backup as /home? 
Or did you install Ubuntu there and restore the files from the backup to your new /home/username directory? (That would be best).
Or did you copy Ubuntu from another hard disk and paste it there or something? (Because you said you don't want to have to re-install).

I'm confused, please fill me in on what it is you're doing. :)

Regards, Herman :)

---

### Post by Robbyx on 2008-03-07
> **Herman said:**
> 

Now, you're talking about trying to boot an operating system in your new hard drive. I am guessing you have installed Ubuntu there and you mounted your old /home backup as /home? 
Or did you install Ubuntu there and restore the files from the backup to your new /home/username directory? (That would be best).
Or did you copy Ubuntu from another hard disk and paste it there or something? (Because you said you don't want to have to re-install).


Thank you for your patience. What I am currently trying to do is use a much larger and faster disk for Ubuntu. I bought at 500gig drive and partitioned it so that sda1 is to be the system area, sda2 the home and sda3 the media. I will retain my rade drive for my documents.

I hoped to avoid a new install and so have copied over the old system disk to sda1 and the old home to sda2. I have kept the home on a separate partition. I tried changing the fstab so that it pointed to the new home address. When the installation failed to start  I changed the fstab so that the home was still on sda1. I intend to point to the new home once Ub loads and runs. Currently it will not load beyond an initial start. That is where my last message had reached.

Getting a bit fed up with the effort needed to get the old system working on a new drive,  I had also thought about just installing from scratch on to sda1 and reinstalling the software I need.  I have just loaded the Ubuntu live CD and I can not  see see how to load UB from the CD into a preformatted partition, so I have been unable to use that solution. 

Robin

---

### Post by Herman on 2008-03-07
:) I think you'll find it easier to just re-install.
If you don't want to re-download the same software all over again, just copy your .deb files out of your old /var/cache/apt/archives to your new /var/cache/apt/archives and re-install the same software. It will be a lot quicker because most of it won't need to be re-downloaded.

It is possible to do something like what you're talking about -copy the files and folders from the Ubuntu Live CD to a partition and boot it. 
Here are a couple of examples, [Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux"), that makes a partition that boots like a Ubuntu Live CD, but instead of installing with it you could rename your /home file system 'casper-rw' and mak e a boot entry that will mount it at boot time. It wouldn't be the same as a real Ubuntu installation though, it would bemore like a USBstick installation, like this, [HOW TO make a USB Disc with Ubuntu LiveCD and Super Grub Disc in it]("http://ubuntuforums.org/showthread.php?t=575406"). 
I don't think that would be the best way to do things though.

:) It only takes about half an hour to install Ubuntu the normal way and maybe another half an hour to get things back to normal again. That's what I would be doing. 

Regards, Herman :)

---

### Post by Robbyx on 2008-03-09
> **Herman said:**
> :) I think you'll find it easier to just re-install.
If you don't want to re-download the same software all over again, just copy your .deb files out of your old /var/cache/apt/archives to your new /var/cache/apt/archives and re-install the same software. It will be a lot quicker because most of it won't need to be re-downloaded.

It is possible to do something like what you're talking about -copy the files and folders from the Ubuntu Live CD to a partition and boot it. 
Here are a couple of examples, [Installation/FromLinux]("https://help.ubuntu.com/community/Installation/FromLinux"), that makes a partition that boots like a Ubuntu Live CD, but instead of installing with it you could rename your /home file system 'casper-rw' and mak e a boot entry that will mount it at boot time. It wouldn't be the same as a real Ubuntu installation though, it would bemore like a USBstick installation, like this, [HOW TO make a USB Disc with Ubuntu LiveCD and Super Grub Disc in it]("http://ubuntuforums.org/showthread.php?t=575406"). 
I don't think that would be the best way to do things though.

:) It only takes about half an hour to install Ubuntu the normal way and maybe another half an hour to get things back to normal again. That's what I would be doing. 

Regards, Herman :)

Thank you very much for all your help. I followed your advice and reinstalled from scratch on the new drive, but have used a separate home location so as to reduce the amount that was lost. It was not a quick exercise. A big time consuming problem related to the level of permission on the home disk. It was not enough to set the chmod to 777. After carying out a  search I found I had to change other permissions  before I could run Ub because it would keep closing on me after 10 seconds. I have it now working and thank you for your time and patience. May  I suggest that some of our correspondence go into a faq because I believe that the problems I have faced are faced by many others when they upgrade to a larger drive.

Robin

---

