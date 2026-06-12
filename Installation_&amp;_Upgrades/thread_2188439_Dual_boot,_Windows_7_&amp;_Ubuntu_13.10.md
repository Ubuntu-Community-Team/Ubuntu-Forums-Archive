---
title: "Dual boot, Windows 7 &amp; Ubuntu 13.10"
date: 2013-11-17
forum: Installation &amp; Upgrades
---

### Post by Niemil on 2013-11-17
I have thought about this in the previous days, and I started read about it at Thursday.

Now I am finally home for a few hours, on the computer that I wanna do dual boot.
It's an HP 625 that have Windows 7 (64-bit) installed inside the computer itself, so I wont need to install via CD or USB.

I am not 100% sure to make this, I only understand how I am going to install Windows 7, just normally right?
But then what? I had been reading a big article in doing this, but cannot find it right now.
What I think is hard and what I don't even understand is the partition part.

My computer have about 290 GB space on harddrive, and I don't understand if I shall fill that space up in partition or if it's just needing the installation files sizes?

I watched some YouTube video for a moment ago, where they already shrinked Windows 7 in Windows 7's computer managment ( [http://www.youtube.com/watch?v=PvP_4J2MUEc](http://www.youtube.com/watch?v=PvP_4J2MUEc) ), is this the way to go? Because I didn't even see this part in the article that I read, and that I cannot find right now.

I wanna dual boot today, I am sure I will run on errors and everything. I am going to go through some stuffs now and try things out, if it turns out wrong which I am sure it does, I sure will learn me something new and I will correct problem during time.

I will write in this thread later about the problems etc, and maybe I can get some great tips and maybe some easy step to step tutorial if it's even possible.

For now I am using Ubuntu 12.04.3 LTS, but I will soon wipe it clean and install Windows 7, and therefor try to do something for dual boot installation.

---

### Post by Bucky Ball on 2013-11-17
Simply put, install Windows 7 on a partition big enough to take it and leave the rest of the drive as FREE SPACE. DO NOT create partitions for Ubuntu as it uses EXT4 partitions which Windows knows nothing about and can't create.

Install Ubuntu to the free space.

You need to make a plan, i.e. how do you want the partitions at the end of all this? Get a paper and pencil and know what you are doing before you start. 

Ubuntu, the OS, doesn't need more than about 20Gb (I've never used more than 15), but that is if you want a separate /home partition and you are not keeping your personal files in a /home directory inside Ubuntu, or /.

Do you want to share files with Windows? If so, you are going to need an NTFS partition which both OSs can read and write.

Confusing, because you are talking about shrinking Win partition but then say you are about to install Win, so no idea there.

If Windows is already installed, yes, use its own software to shrink the partition, but defragment the Win partition several times first.

There's a start. Main thing: make a plan for what partitions you want. Stick to four primary partitions. You can also use an extended partition which acts like one primary partition but can contain as many logical drives (effectively partitions) as you like, theoretically. So, three primary partitions, an extended partition with four logical drives in that. Ubuntu is fine on a logical drive. Windows needs to be on a primary (preferably first partition, first disk). 

Good luck.

---

### Post by Niemil on 2013-11-17
Well, first problem:
I can't install Windows 7 from system boot!

Somehow, I just cannot find the installation. Maybe it erased when I installed Ubuntu? I have no idea :S I may need to download a Windows 7 image file after all and put that on another USB memory stick, doh.

Also, I still don't understand to 100%.

I know already what sizes I want and need. Windows I need maybe 50 GB for softwares etc, + the system settings on Windows, idk, but lower than 100 GB for Windows, nothing more I shall need because it's just a couple of softwares and maybe store some files on it.
That's it, rest goes to Ubuntu, and that will be over 100 GB, so no problem with space I believe. I also have an 1 TB extern harddrive that I use a lot.

Now however, I need first install Windows 7, then I may watch on that YouTube video, cus I found massive other videos where they done that technique, and that seems to work?


But in the article I read about something I could make some kind of bridge between Windows 7 and Ubuntu? So I could transfer over files to them directly? Does it still work if I would do like in that YouTube video? or is it something different I have to do?

---

### Post by Niemil on 2013-11-17
JESUS CHRIST!
The "Make Startup Disk" doesn't work for Windows 7? I have downloaded an .iso file for Windows 7 ultimate install. The USB I have having 7.4 GB (8gb stick) free space, it's all clean.
I chosed the .iso file for windows 7, but it just doesn't get accepted. Instead the previous ubuntu 13.10 I've in the list is just keep on showing. It just wont want to change to Windows 7.

I am totally stuck with Ubuntu.

[edit]
Found a DVD+R CD with a 4.7 GB space. Right now I am trying to burn the Windows 7 .iso file to the CD. I hope that will work.

---

### Post by oldfred on 2013-11-17
HPs with Windows 7 almost always use all 4 primary partitions. If you tried to force an install of Ubuntu it probably erased entire drive as that is about all it can do when all four partitions are used.

 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
For a complete blow-by-blow on dealing with HP's four partitions, see Full Circle Magazine, issue 41, page 36. - gordintoronto
[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)
This suggests removing system partition and making c: the bootable partition. But has details on all alternatives
[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/How-to-repartition-HDD-of-HP-notebook-with-pre-installed/td-p/742019)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by Niemil on 2013-11-17
Ah, thank you both!

I now have succefull installed Windows 7, and from there I made something with the partitions like in the video, I shared up the space into about 150g for windows and 150g for ubuntu.
Now I have just installed Ubuntu, and it seems to be working well, I will try reboot my computer and see how windows doing, but I believe it will also work.

However, it says that I got a volume disk/harddrive on around 150gb, where I see the windows root files!
I wonder what happends if I would click on unmount icon? if I ever would accidentally click it, what happends? I don't dare click it now if it would mess up.
If it does mess up somehow, is it able to kind of configure it so accidents wont happend? just in case, like if I would have an USB in the PC and unmount it, and misclick or something.

---

### Post by oldfred on 2013-11-17
The way to hide or prevent a mount is to actually mount it so Nautilus will not auto mount it and hide it and set default permissions as read only.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

   For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2

   ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

   Hide mount 
UUID=200C11850C1156DE /mnt/SysRes ntfs defaults,noauto 0 0
Hide windows mount with noauto: 777 is no permissions at all
/dev/sda2 /Windows/sda2 ntfs defaults,noauto,umask=777 0 0

   sudo mkdir /mnt/SysRes

   Set windows boot partition Read only - Morbius1
[http://ubuntuforums.org/showthread.php?t=2043862](http://ubuntuforums.org/showthread.php?t=2043862):
After Ubuntu has done it's thing I usually go in and change the umask to 227 which will make the C Drive read only.
/dev/sda1 /media/sda1 ntfs nls=iso8859-1,ro,umask=227 0 0 
UUID=xxxxxxxxxxxxxxx /WinC ntfs defaults,noauto,ro,umask=227 0 0

   Mount in /media or /home will show in Nautilus left panel mounts in / or /mnt will not.

---

### Post by Niemil on 2013-11-17
Doh well, that's confusing. I quite not understand anything really.

I want access to the Windows files, I like that, atleast if it works to copy over files to it etc. Would be cool if it worked to copy over files other way too (Windows to Ubuntu).

I will however try read your post again carefully and google on all those terms I don't understand.

But one problem have occured yet so far in Windows. When I first booted Windows after completing install on Ubuntu, it said it had to repair some stuffs, so I ran Windows repair, and I went away 2 hours while waiting. When I got back now, it said that it couldn't repair.
So well, I restarted and booted Windows again, and now it worked. However, now the Wireless is gone on Windows, and I also seem not to be able to save anything in C: drive.
I wanted to save a text file just to see if I can see and transfer it from ubuntu, but in Windows when I wanted to save the text file, it said that I have no permission to do so.

I will try install some drivers via ubuntu and send over to windows if it works, and then try install driver on windows and get the wireless to work. But still the permission part I need for Windows may be left to fix too.
[EDIT]
Whaaat, I cannot even install Gnome on Ubuntu!!

> [B]user@UB:~$ sudo apt-get install gnome-shell
[sudo] password for user: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

[/B]

---

