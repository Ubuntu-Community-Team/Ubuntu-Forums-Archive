---
title: "[SOLVED] Ubuntu 8.10 32 bit version installation: detecting/creating partitions probl"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by Happibun on 2008-11-04
Hi

I'm having problems partitioning my hard disk so that I can run my home folder from a separate partition from the Ubuntu installation. 

I've been using Ubuntu since 7.04 on a Dell laptop with one of those cursed Broadcom chipset WiFi cards. I've upgraded rather than reinstalled each new version of Ubuntu as it came out, and managed ok with Wicd, Ndiswrapper, and so on, but when I found out that 8.10 had broadcom driver patch built in, I decided to do a fresh install, and give my lappy a good old clean out in the process.

I backed up my home folder, reformatted, and installed Intrepid, got updates downloaded and gurgled with happiness at the WiFi connection as it just did what I wanted it to without any hassle.

The next step was to separate the home folder, because I am told (as I read around the forum) that this is good practice. I ran Gparted from the live cd, and shrank the first partition with the OS on it to 8 Gb, and made a new 45 Gb partition for my home folder to go in to. I followed the tutorial on :- 

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) and [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) , only the second part of the how to didn't work for me. I was left with no home folder, and error messages about being unable to update ICEauthority, sanity-check2 exiting with status 256, and inability to create subdirectories because there is no home/user file etc. The lappy eventually booted in to root, but with nothing other than the wallpaper on the screen.

Even a non techie like me can see that is not the desired outcome. I suppose it is no big deal because I can just reinstall from the cd, but now the installation cd is trying to put 8.10 in to the big partition rather than write over itself in the smaller one.

It is a bore because I would like to be able to overcome this. Even more so because for the first time in over a year, I am forced to boot up a Windows desktop just to get online and call for help :-(  (shivers)

Please be kind because I am dyslexic enough to find the terminal hard work and frightening.

Thank you.

---

### Post by Ek0nomik on 2008-11-04
That new broadcom driver is nice, isn't it?  :)

The file /etc/fstab is going to be involved in this process.  Can you please post the contents of it?

```
cat /etc/fstab
```

---

### Post by Happibun on 2008-11-04
Thanks ever so for running with this_ [Ek0nomik]("http://ubuntuforums.org/member.php?u=151914")_,

I will post it as soon as I have reinstalled 8.10 all nice and fresh.

I thought that it would be better to have a go again, because I am bound to have messed it up good and propper, and it is easier to help out if you have a fresh install with less user error to get in the way. The Live cd is over 50% through the reformat as I type. I'm off for a cuppa and will be back with the result in 10 mins or so.

That ok?

---

### Post by Happibun on 2008-11-04
Running updates now...

---

### Post by Happibun on 2008-11-04
:~$ cat /etc/fstab   
# /etc/fstab: static file system information.  
 #  
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>  
 proc            /proc           proc    defaults        0       0  
 # /dev/sda1  
 UUID=32882deb-ebe5-4010-8aa0-159558734ebb /               ext3    relatime,errors=remount-ro 0       1  
 # /dev/sda5  
 UUID=858065d3-8834-4669-88fc-111d3b36d97e none            swap    sw              0       0  
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 



Does that help?

---

### Post by tarps87 on 2008-11-07
You will need either need enough space to make a partition that you can copy all the data in your current home directory to or you will need to back up you data to another device.

Then you will need boot from the live cd and open up partitioner. Use this to shrink your current partition and the create a second (larger) partition which will be you /home partition
This link may help with partitioning:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Once you have done this boot the installed Ubuntu and edit fstab ```
sudo gedit /etc/fstab
```
add the line:> 
/dev/uuid   /home  ext3  nodev,nosuid,relatime  0  2

where uuid is your partition UUID.

Save the file then mount all the partitions in the fstab file
```

sudo mount -a

```

To get the UUID either first fine the device name and then that devices UUID by```
sudo fdisk -l
vol_id -u /dev/*deviceName*

```
alternatively you can use ```
blkid

``` but this may not be as easy to read

Edit: fstab should use UUID's now and corrected mount options

---

### Post by Happibun on 2008-11-07
Thank you Tarps87,

This will be my project for tonight then :-) I will report back to this thread when I have done it to let you know how I have done.

Cheers!

---

### Post by Happibun on 2008-11-07
Oh dear.

Computer says no. On the upside, at least I am being consistent. I'm getting the same kind of errors, so I must be doing the same thing wrong. I'm also stuck back with the Windows box until I either reinstall 8.10 to get out of this mess or find another way around.

I followed the instructions, I repartitioned the drive after having copied my home folder on to a removable HD. After I backed /jo upI removed most of the files from my /home/jo folder, but left /home/jo/desktop in situ, which was about 1.5Gb in size as a kind of place holder instead of the original 15Gb. I was hoping that I would be able shrink the disk space the partition used up, but no I could only shrink the Ubuntu section to 18Gb instead of my preferred 8Gb, but hey that was a start IMHO. I've got a screen grab of the end result [http://ubuntuforums.org/album.php?albumid=675&pictureid=2268](http://ubuntuforums.org/album.php?albumid=675&pictureid=2268)

To make sure I got it right, I cut and pasted this in to the terminal

sudo gedit /etc/fstab
Then I added this line to the bottom of my fstab file on a new line - 

/dev/sda3   /home  ext3  nodev,nosuid,relatime  0  2                      

and saved it.

Then I cut and pasted each of these lines in to the terminal individually -
sudo mount -a
sudo fdisk -l
vol_id -u /dev/[I]sda3

[/I]

On reboot the lappy is telling me :- 
> Your home directory is listed as: '/home/jo' but it does not appear to exist. Do you want to log in with the / (root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session.Then I get some whiffle about User's $HOME/.dmrc file is being ignored. That was something that I managed to cure before when I enquired in this thread - [http://ubuntuforums.org/showthread.php?t=971110](http://ubuntuforums.org/showthread.php?t=971110) , and was probably something to do with the way I had to cut and paste my home file from a portable hard drive having altered the permissions to the file (I guess)

After having hit return, I have a completely blank desktop for a bit before an error tells me it 'Could not update ICEauthority file /.ICEauthority, then a whole lot about sanity checks exiting with status 256.

Eventually I get to the desktop, but there are no panels or icons on it at all. I can only get in by running the Live CD.

           So, this is what you really want to know. Using the live CD to get in to the lappy I've managed to get this out.

 

 ubuntu@ubuntu:~$ sudo fdisk -l  
  

 Disk /dev/sda: 60.0 GB, 60011642880 bytes  
 255 heads, 63 sectors/track, 7296 cylinders  
 Units = cylinders of 16065 * 512 = 8225280 bytes  
 Disk identifier: 0xd155d155  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1   *           1        2435    19559106   83  Linux  
 /dev/sda2            6993        7296     2441880    5  Extended  
 /dev/sda3            2436        6992    36604102+  83  Linux  
 /dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris  
 
                ubuntu@ubuntu:~$ vol_id -u /dev/sda3  
 /dev/sda3: error opening volume  

I hope all this clearly shows you where I am goofing up, and that it can be solved without too much bother.

Thanks, Jo

---

### Post by Happibun on 2008-11-08
I am bumping this because I am still struggling.

Today's lightbulb moment was the realisation that what I thought was the UUID was *not* what I thought it was, but the new enthusiasm was squished by not being able to mount the new partition to find out what its UUID actually is. Without that, I can't edit fstab properly.

Here's a record of today's attempt. I reinstalled 8.10 again, mainly because I could not access the fstab file on the hard drive from the live CD (because I don't know how - not because it is impossible, it is probably easy - if you know what you are doing). At least I have got my Ubuntu partition down to the size I wanted. On the downside, my lappy is out of action until I get this sorted out, or I give up. 

                                 **When opening fstab this error message comes up:**
 

 > jo@Epsilon:~$ sudo gedit /etc/fstab   ** (gedit:7168): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.8W2DKU': No such file or directory  
 

 I/O error : No such file or directory  
 I/O error : No such file or directory  
 

 **But it opens fstab anyway. Fstab with extra line added:**
 

 # /etc/fstab: static file system information.  
 #  
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>  
 proc            /proc           proc    defaults        0       0  
 # /dev/sda1  
 UUID=ee752ebc-916b-4450-8431-9c1974e7c1b7 /               ext3    relatime,errors=remount-ro 0       1  
 # /dev/sda5  
 UUID=858065d3-8834-4669-88fc-111d3b36d97e none            swap    sw              0       0  
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0  
 /dev/sda3 /home ext3 nodev,nosuid,realtime 0 2
 

 **Error when trying to mount new partition.**
 

 > jo@Epsilon:~$ sudo mount -a   mount: wrong fs type, bad option, bad superblock on /dev/sda3,  
        missing codepage or helper program, or other error  
        In some cases useful info is found in syslog - try  
        dmesg | tail  or so  
 

 **Disk analysis:**
 

 > jo@Epsilon:~$ sudo fdisk -l   Disk /dev/sda: 60.0 GB, 60011642880 bytes  
 255 heads, 63 sectors/track, 7296 cylinders  
 Units = cylinders of 16065 * 512 = 8225280 bytes  
 Disk identifier: 0xd155d155  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1   *           1        1021     8201151   83  Linux  
 /dev/sda2            6993        7296     2441880    5  Extended  
 /dev/sda3            1022        6992    47962057+  83  Linux  
 /dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris  
 

 Partition table entries are not in disk order  
 

 **Attempt to get UUID:**
 

 > jo@Epsilon:~$ vol_id -u /dev/sda3   /dev/sda3: error opening volume  
 

 > jo@Epsilon:~$ blkid   /dev/sda1: UUID="ee752ebc-916b-4450-8431-9c1974e7c1b7" TYPE="ext3" 
 /dev/sda5: UUID="858065d3-8834-4669-88fc-111d3b36d97e" TYPE="swap" 
 /dev/loop0: TYPE="squashfs"  
 

Someone out there - Please help.

Thank you.

---

### Post by Happibun on 2008-11-08
Latest attempt. Lappy still broken :-(

**jo@Epsilon:~$ sudo blkid -c /dev/null ** 
 [sudo] password for jo: 
 

 /dev/sda1: LABEL="OS" UUID="ee752ebc-916b-4450-8431-9c1974e7c1b7" TYPE="ext3" 
 /dev/sda3: LABEL="JoHome" UUID="41013b30-40e1-41c4-8105-937d31500857" SEC_TYPE="ext2" TYPE="ext3"  
 /dev/sda5: UUID="858065d3-8834-4669-88fc-111d3b36d97e" TYPE="swap" 
 

 jo@Epsilon:~$ sudo gedit /etc/fstab  
 [sudo] password for jo: 
 

 ** (gedit:6810): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.XWS7JU': No such file or directory  
 

 I/O error : No such file or directory  
 I/O error : No such file or directory  
 

 But it opens up fstab anyway.
 

 **Modified fstab file (the last two lines are my guesswork)**
 

 # /etc/fstab: static file system information.  
 #  
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>  
 proc            /proc           proc    defaults        0       0  
 # /dev/sda1  
 UUID=ee752ebc-916b-4450-8431-9c1974e7c1b7 /               ext3    relatime,errors=remount-ro 0       1  
 # /dev/sda5  
 UUID=858065d3-8834-4669-88fc-111d3b36d97e none            swap    sw              0       0  
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0  
 # /dev/sda3  
 UUID=41013b30-40e1-41c4-8105-937d31500857 /home ext3 nodev,nosuid,relatime 0 2
 

 **jo@Epsilon:~$ sudo mount -a  **
 **jo@Epsilon:~$ sudo fdisk -l  **
 

 Disk /dev/sda: 60.0 GB, 60011642880 bytes  
 255 heads, 63 sectors/track, 7296 cylinders  
 Units = cylinders of 16065 * 512 = 8225280 bytes  
 Disk identifier: 0xd155d155  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1   *           1        1021     8201151   83  Linux  
 /dev/sda2            6993        7296     2441880    5  Extended  
 /dev/sda3            1022        6992    47962057+  83  Linux  
 /dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris  
 

 Partition table entries are not in disk order  
 

 **jo@Epsilon:~$ blkid  **
 /dev/sda1: UUID="ee752ebc-916b-4450-8431-9c1974e7c1b7" TYPE="ext3" 
 /dev/sda5: UUID="858065d3-8834-4669-88fc-111d3b36d97e" TYPE="swap" 
 /dev/loop0: TYPE="squashfs"  
  
 **jo@Epsilon:~$ vol_id -u /dev/sda3  **
 /dev/sda3: error opening volume  
 

 **Decide to remove the modified fstab line and rethink, only I could not open it.**
 

 **jo@Epsilon:~$ sudo gedit /etc/fstab  **
 No protocol specified  
 

 (gedit:7237): Gtk-WARNING **: cannot open display: :0.0 



**Laptop will not reboot for my user, all the same errors reported as listed in previous posts.**

---

### Post by shortylonglegs on 2008-11-09
I had this same problem, managed to wander my way to an answer.

Run```
blkid
```and note the uuid of the partition holding /home.  Open fstab  ```
sudo gedit /etc/fstab
```
It should look something like:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=cbccca10-33bb-4765-8477-8bc0d81c440b /               ext2    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=2b9de310-321d-42e9-895b-85f82d927630 /home           ext2    relatime        0       2
# /dev/sda1
UUID=270a13db-414d-42fa-b05e-a8bfc29e050c none            swap    sw              0       0
```
change the uuid of the second one, where it says '/home' to the uuid you found with 'blkid'
I think that's all I had to do and it was working.

---

### Post by tarps87 on 2008-11-10
Sorry for the slow reply been without internet for a bit. From the live cd you should be able to see the drives under places, clicking on the drive should mount it, it will be mounted to /media usually as disk, disk1, ...
If you can mount the os drive you should be able to open up the fstab file and comment out the home partition(add a # in front of it). This should get it booting again. While you are using the live cd see if you can mount the home partition by clicking on it?
The lines you entered should work but will have a closer look and post back

---

### Post by jmate24 on 2008-11-10
same thing happened to me when i went to adjust my / and /home/myusername partitions. assuming you have decided what your username will be.

Word of Advice: Durring the install you can use Partition Editor that comes with the install disk and Partition your hard drive with it. then restart and leave the disk in the CD/DVD Drive. when it boots up then click the 'Install' Icon and when you install the os and it asks you: "How do you want to partition your disks?" Select Manual then chose which partition(s) that you all ready set aside for your / and /home/myusername just select ehich partition will be / and which will be /home/myusername once you have selected the hard drive then click 'Edit Partition' then from the window change 'do not use' to Ext3 and in the blank space type / for your root partition and then click OK it may ask or tell you that the / partition has to be formated. Then choose the partition for your /home/myusername and select 'Edit Partition' then from the window change 'do not use' to Ext3 and in the blank space type in lowercase letters /home/myusername and click OK. then when it gets to asking for your name, username, and password then type in the username that you used for the mount point of the /home/myusername and it will treat that partition or hard drive as your home folder.

It is best to have a second hard drive for your /home/myusername folder so that if your / drive fails then you can just install a new hard drive and install the same or new OS if you remember your old username.

---

### Post by tarps87 on 2008-11-10
Once you can log back on can you try making a directory in /media
```
sudo mkdir /media/test
```
then mount the home partition
```
sudo mount -t ext3 /dev/sda3 /media/test
```
This will show where the problems is. i.e. with mounting for the fstab

Using gksudo with gui programs instead of sudo should stop the problems you are having with gedit I'm use to using sudo so forget when posting

---

### Post by Happibun on 2008-11-10
Right oh.

First of all, Thank you very much for coming back to the thread tarps87, and to shortylonglegs and jmate24 for coming in to it. I really appreciate the time and effort that you are taking to help me.

The state of play right now is that I reinstalled and repartitioned the lappy again yesterday afternoon. I decided to take it to the point where I would be ready to edit fstab, but have not actually done so. That means that I can log in with my user account, and that I am not forced to access the lappy with the live CD.

I can only see the sda3 partition if I use 
                                 **sudo blkid -c /dev/null **and not just **blkid**.
I am assuming that means that it is mounted for sudo, but not for my user, which means that when I log in as jo, I don't have permission to access that partition. That might explain all of those error messages, and why I can not log in as jo after I edit fstab. I don't know, I am only guessing, so please put me right if I am off the mark.


I may be the only account on the laptop, but I don't operate as a superuser most of the time. I read dire warnings about that, and am happy to jog along as just a user, poking in to sudo when I have to occasionally.


> **tarps87 said:**
> 
If you can mount the os drive you should be able to open up the fstab file and comment out the home partition(add a # in front of it). This should get it booting again. While you are using the live cd see if you can mount the home partition by clicking on it?



After editing fstab, I am not able to open the OS partition, and am only able to do anything with the laptop after using the live CD. That means that I can only open the fstab file on the CD, and that is no good for what I need to do. That is why I reinstalled and re-partitioned again.


After booting the laptop up this morning I navigated to places on the panel. the sda3 partition (labled JoHome) was not visible on the drop down menu, nor was it visible on the desktop, but it was visible in the window that opened up when I opened up home in one. I have a screenshot FWIW - [http://ubuntuforums.org/picture.php?albumid=675&pictureid=2291](http://ubuntuforums.org/picture.php?albumid=675&pictureid=2291)


 I had to enter my password to open it. Inside was my lost&found folder. Most appropriate!

Then I opened a terminal and entered the script tarps87 suggested :-
                          > jo@Epsilon:~$ sudo mkdir /media/test  
 [sudo] password for jo: 
 jo@Epsilon:~$ sudo mount -t ext3 /dev/sda3 /media/test 
I got no error messages, so I suppose it has worked. Now what do I do? 

Thank you :)

Jo

---

### Post by tarps87 on 2008-11-10
try browsing to /media/test, if you can see the files on the home drive the partition or mount is not the problem. Also if you set it as the /home partition when you reinstalled it should be added to the fstab automatically.
When you formatted the /home partition do you set any sepecial options or just used the defaults?

---

### Post by Happibun on 2008-11-10
The lost and found folder is sitting happily /media/test/lost+found, so as you say, the partition and mount is not the problem.

I have not set it as /home yet, and I think that it is working because I set the permission in the GUI that popped up when I was looking for the partition earlier. I don't know if it will remain mounted for my user account after reboot.

When I formatted the partition, I used the defaults except for the default filesystem format. the default came up as ext2, but all the stuff I have read suggest ext3, so I changed it to ext3. Was that a ditzy thing to do?

Update: On reboot, the partition is not automatically mounted, but is now visible in the Places drop down menu from the Panel. I know that to get it to be mounted at boot means editing the fstab file, but I'll wait for instructions before I do anything.

Here is the current fstab file and error message:

                          > **Latest fstab**  

 

 # /etc/fstab: static file system information.
 #
 # <file system> <mount point>   <type>  <options>       <dump>  <pass>
 proc            /proc           proc    defaults        0       0
 # /dev/sda1
 UUID=e3d90611-7b61-45c4-b34b-98b41e8de29f /               ext3    relatime,errors=remount-ro 0       1
 # /dev/sda5
 UUID=858065d3-8834-4669-88fc-111d3b36d97e none            swap    sw              0       0
 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
 

 **Latest gedit error:-  **
 

 jo@Epsilon:~$ sudo gedit /etc/fstab  
 [sudo] password for jo: 
 

 ** (gedit:6704): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.9RREKU': No such file or directory  
 

 I/O error : No such file or directory  
 I/O error : No such file or directory  

  	 	 	 	 	 	  **With  gksudo**
 

 jo@Epsilon:~$ gksudo gedit /etc/fstab
 I/O error : No such file or directory
 I/O error : No such file or directory
 SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSj
 
Thanks, Jo

---

### Post by Mark224 on 2008-11-10
If you are having lots of troubles with gedit I would suggest trying a basic editor instead:
```

sudo vi /etc/fstab

```

---

### Post by tarps87 on 2008-11-10
> **Happibun said:**
> When I formatted the partition, I used the defaults except for the default filesystem format. the default came up as ext2, but all the stuff I have read suggest ext3, so I changed it to ext3. Was that a ditzy thing to do?
Thought the default was ext3, any ext3 is the correct/recommended format to use

> **Happibun said:**
> Update: On reboot, the partition is not automatically mounted, but is now visible in the Places drop down menu from the Panel. I know that to get it to be mounted at boot means editing the fstab file, but I'll wait for instructions before I do anything.

That sounds better, now try ```
blkid
```
helpfully it will show up now
Also try```
sudo mount -t ext3 /dev/sdb1 /home
```
If this all works
```
sudo mount -t ext3 -U UUID /home
```
As long as these works the fstab bit should do

About the gedit errors I believe they are graphics problems with being root, I don't know of a work around other than a different editor. These problems should not stop it working for what we want to do.

---

### Post by Happibun on 2008-11-10
Hi Mark224,

That is a good suggestion, but I am avoiding vi. I'm way too wet behind the ears for it. I tried it once and came away with the shivers - and that was with a vi manual running on the PC next to me too...

Tarps87,

I am just wondering if there is some different about the partitioner that comes with Intrepid. 


There is still something odd going on, here are my inputs and outputs - 

> **jo@Epsilon:~$ blkid ** 
 /dev/sda1: UUID="e3d90611-7b61-45c4-b34b-98b41e8de29f" TYPE="ext3" 
 /dev/sda5: UUID="858065d3-8834-4669-88fc-111d3b36d97e" TYPE="swap" 
 /dev/loop0: TYPE="squashfs"  
 

 **jo@Epsilon:~$ sudo blkid ** 
 [sudo] password for jo: 
 /dev/sda1: UUID="e3d90611-7b61-45c4-b34b-98b41e8de29f" TYPE="ext3" LABEL="OSpartition"  
 /dev/sda5: TYPE="swap" UUID="858065d3-8834-4669-88fc-111d3b36d97e"  
 /dev/sda3: LABEL="JoHome" UUID="7747ed8f-52fe-4fbc-908a-9b278c6e7e42" TYPE="ext3"  
 

 **jo@Epsilon:~$ sudo mount -t ext3 /dev/sdb1 /home ** 
 mount: /dev/sdb1 already mounted or /home busy  
 mount: according to mtab, /dev/sdb1 is mounted on /media/KINGSTON  
 KINGSTON is the 1Gb USB key that I am using to transfer all this from the laptop to this desktop, because the laptop is not on the network.
I did not try** sudo mount -t ext3 -U UUID /home** because the previous commands did not go smoothly. 

So then I thought for a bit and decided that you really meant **/dev/sda3** instead of **/dev/sdb1**, so I tried 

**:~$ sudo mount -t ext3 /dev/sda3 /home **

which was accepted ok, but was a dumb thing for me to do because I have now have no home folder, and can not run any applications (like my text editor - so I can not copy the input and output of the terminal) on the laptop. I dare say that if I switch it off now, I won't be able to reboot. :oops:

Blah

Update:

For your edification, and to give you a right good laugh, I have hand copied the latest goof up I have made for you : 
>                                   **:~$ sudo mount -t ext3 /dev/sda3 /home ** 
 **:~$ sudo mount -t ext3 -U UUID /home ** 
 mount: special device /dev/disk/by-uuid/UUID does not exist
 

 **:~$ sudo mount -t ext3 -U UUID=”7747ed8f-52fe-4fbc-908a-9b278c6e7e42” /home ** 
 mount: special device /dev/disk/by-uuid/ UUID=7747ed8f-52fe-4fbc-908a-9b278c6e7e42 does not exist
 I guess that there is no more I can do except reinstall 8.10 again. Someone please remind me why it is such a good idea to have /home on another partition when it is relatively easy to back up the folder anyway. I can't fit another HD in to the lappy, so it is not like I'm putting it on another disk - for that I would have to upgrade the laptop.

:cry:

---

### Post by Happibun on 2008-11-10
Ready for the next instalment?

Since I had to reinstall, I decided to try jmate24's suggestion that I try a manual partition on installation. I was put off that before because when I clicked on it the partition showed just one blue bar, and I could not see how you changed it or divided it. I was too frightened that I might do something irreversible, and that I did not have a clue what to do anyway if I continued, that I decided not to do a manual partition on previous installs.

Anyway, this time, in for a penny, in for a pound. I can not do any worse than I Have already, let's face it. I went for a manual partition install.

Following jmate's post, I now have a working laptop with root in a 10Gb partition and my /home/jo folder sitting in a 45Gb partition. There are no error messages, and I am a very happy bunny.

Thanks in particular go to both jmate and tarps, Jmate for solving the problem, Tarps for putting up with my bumbling, putting so much effort in to getting me up and running, teaching me quite a lot about partitioning and bash, and getting so close to solving the situation.

Thank you guys.

Thread solved.

---

### Post by tarps87 on 2008-11-10
Sorry I couldn't work out what was wrong with the fstab it may be worth having a look at it sometime to  see what is different. If you open it without using sudo it won't be changed.
Hope the rest goes better

---

### Post by Happibun on 2008-11-10
No need to apologise.

I haven't got a clue what was happening with fstab either, but in my case, I was putting it down to general ignorance, and a remarkable inability to understand what the heck the man page was going on about. My fstab didn't seem to follow what anyone else's did anyway, and I am sure that at one point the lappy was sulking.

I think that this is one that needs to be put down to sod's law. Proof if any were needed that technology is developing it's own intelligence, and that it is out to get us. ;-)

My respect for this operating system, and this community that supports it remains undiminished.

You are stars :KS Thank you.

---

### Post by jmate24 on 2009-04-10
you can also use the live cd to change the permissions of your folders or a spare hard drive (but DO NOT USE IT ON YOUR ROOT '/" PARTITION!!) using the terminal ```
sudo nautilus /location/myfolder
```

jmate24--

---

