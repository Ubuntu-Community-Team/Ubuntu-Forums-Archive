---
title: "Using a second hard drive for storage/programs?"
date: 2012-07-30
forum: Installation &amp; Upgrades
---

### Post by djt on 2012-07-30
I'm currently running Ubuntu 12.04 on a system that has two hard drives. The OS (Ubuntu) is installed on one 150GB drive and I have a 300GB drive that I would like to use just for programs (X-Plane).

 I've been able to successfully get the second drive to be recognized in the disk utility but I still can't get it listed as a available location for installation when I use the X-Plane installer.

 Using *Gparted *to format the drive (Ext4) didn't help the problem either. The drive does show mounted and it is listed in “*My Computer*”.

 Does anyone have any ideas on what I'm doing wrong?

---

### Post by darkod on 2012-07-30
When you say it shows as mounted, be careful. All partitions will show in Nautilus in the left side menu, not just mounted ones. The best is to check if it's really mounted with:
df -h

That will list all mounted partitions and their mount points (except swap).

Otherwise, if you have really configured it to mount at a certain mount point, it should be available there. Not sure if it will show as default destination for programs or you need to select it, but it should be at the mount point.

How are you mounting it, using an entry in /etc/fstab?

---

### Post by djt on 2012-07-30
> **darkod said:**
> When you say it shows as mounted, be careful. All partitions will show in Nautilus in the left side menu, not just mounted ones. The best is to check if it's really mounted with:
df -h


                                  Thanks for the response.


I checked with the df -h command and it shows :


/dev/sdb1, Size: 280G, Used 4.3G, Avail: 261G, Used 2%/media/sdbl






>                                    
Otherwise, if you have really configured it to mount at a certain mount point, it should be available there. Not sure if it will show as default destination for programs or you need to select it, but it should be at the mount point.
  I do have to manually select the drive during the X-Plane installation, but like I said earlier the drive isn't even available in the installer.


When I open the *Computer: 300GB Hard Disk: Programs* icon there is a folder “*lost+found*” but all I get is an error message “*no permission to view*” when I try to open it.
   
 



>                                    
How are you mounting it, using an entry in /etc/fstab?
                                    I used the *Storage Device Manager* program to mount the drive.

---

### Post by darkod on 2012-07-30
Hmm, I'm not an expert on permissions. It seems that's where the problem is.

What if you open Nautilus as root, can you browse it then:
gksu nautilus

Of course, opening it as root you would expect to have maximum permissions so there should be no problem to browse it.

---

### Post by djt on 2012-07-30
> **darkod said:**
> Hmm, I'm not an expert on permissions. It seems that's where the problem is.

What if you open Nautilus as root, can you browse it then:
gksu nautilus

Of course, opening it as root you would expect to have maximum permissions so there should be no problem to browse it.


                                  I should have mentioned this in the beginning but I'm pretty much Linux illiterate, how do I open Nautilus as root?
 

 Also, how do I get full permissions over the entire system (OS)?

---

### Post by darkod on 2012-07-30
> **djt said:**
> I should have mentioned this in the beginning but I'm pretty much Linux illiterate, how do I open Nautilus as root?
 

 Also, how do I get full permissions over the entire system (OS)?

It was in my post, sorry if it wasn't clear. Because nautilus is GUI program, you open GUI programs by typing gksu <command> in terminal.

So, open terminal and execute:
gksu nautilus

That should ask you for your password and then open nautilus as root.

If you need to execute in terminal a command that is not GUI as root, you use:
sudo <command>

---

### Post by djt on 2012-07-30
> **darkod said:**
> It was in my post, sorry if it wasn't clear. Because nautilus is GUI program, you open GUI programs by typing gksu <command> in terminal.

So, open terminal and execute:
gksu nautilus

That should ask you for your password and then open nautilus as root.

If you need to execute in terminal a command that is not GUI as root, you use:
sudo <command>


                                  Thanks, that worked, I was able to open the “*lost+found*” folder, which is empty.

Is there a way to get full permissions all the time without using the terminal?

---

### Post by oldfred on 2012-07-30
If the disk is permanently installed you can create a permanent mount inside fstab and it will auto mount with the correct permissions and ownership each time.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Most of the old gui tools have not been maintained. Best just to add a line to fstab. You have to create a mount point, like data, files, drive2 or whatever name makes sense.

from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
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
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a

---

### Post by djt on 2012-07-30
> **oldfred said:**
> If the disk is permanently installed you can create a permanent mount inside fstab and it will auto mount with the correct permissions and ownership each time.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Most of the old gui tools have not been maintained. Best just to add a line to fstab. You have to create a mount point, like data, files, drive2 or whatever name makes sense.

from Morbius1-----------------------------------------------------
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6
For ntfs:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
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
gksu gedit /etc/fstab
** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. :
sudo mount -a


                                  Thanks for taking the time to provide me with that information.


I just read through some of it and tried using fstab but still can't get the drive to be recognized as a  installation option in X-Plane. The drive still still shows as being mounted in the disk utility.
 

 I would have thought that something this simple would be as easy as formatting the hard drive in disk manager in Windows.

---

### Post by oldfred on 2012-07-30
Applications do not install to different directories as a standard rule. Actually they are not in one place at all but bits and pieces are in the various system folders.

Linux is not Windows and it just works differently. You should be able to store data or settings in your /home or in you /data if you use links.

Windows is not Linux
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by djt on 2012-07-31
> **oldfred said:**
> 
Linux is not Windows and it just works differently. You should be able to store data or settings in your /home or in you /data if you use links.

Windows is not Linux
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)


                                  Yes I know that's one of the reasons why I've become attracted to Linux, lol.


Using the *Disk Utility* in Ubuntu is very similar to using the *Disk Management* utility in Windows but in this case the hard drive still isn't available for storage.

---

### Post by darkod on 2012-07-31
Is the mount point /media/sdb1 or /media/sdbl?

Anyway, a quick way to allow access to all to a folder, is to give read-write permissions to all. I guess the folder was created as root so only root has permissions now.

Give read-write to ALL to a folder:
```
sudo chmod a+rw /media/sdbl
```

Later you can change permissions if you want limitations instead of access for all.

As far as installing a program into that folder, if the installation procedure allows you to select a destination, it should work. Otherwise, I don't see an easy way that I know of.

---

### Post by djt on 2012-07-31
> **darkod said:**
> Is the mount point /media/sdb1 or /media/sdbl?

Anyway, a quick way to allow access to all to a folder, is to give read-write permissions to all. I guess the folder was created as root so only root has permissions now.

Give read-write to ALL to a folder:
```
sudo chmod a+rw /media/sdbl
```Later you can change permissions if you want limitations instead of access for all.

As far as installing a program into that folder, if the installation procedure allows you to select a destination, it should work. Otherwise, I don't see an easy way that I know of.

                                  The mount point was /media/sdb1 so I tried your suggestion and ran  sudo chmod a+rw /media/sdb1 in the terminal but the X-Plane installer still doesn't see it.


I'm in the process of wiping both drives again (with Parted Magic) and reinstalling Ubuntu 12.04.
 

 After I get Ubuntu installed and updated (along with installing the latest Nvidia drivers) what should I do first this time?
 

 Should I use the  *User Accounts* options in the *System Settings* console to get full *Administrator*  permission?

---

### Post by darkod on 2012-07-31
> **djt said:**
> The mount point was /media/sdb1 so I tried your suggestion and ran  sudo chmod a+rw /media/sdb1 in the terminal but the X-Plane installer still doesn't see it.


I'm in the process of wiping both drives again (with Parted Magic) and reinstalling Ubuntu 12.04.
 

 After I get Ubuntu installed and updated (along with installing the latest Nvidia drivers) what should I do first this time?
 

 Should I use the  *User Accounts* options in the *System Settings* console to get full *Administrator*  permission?

The permissions are not related to the X-plane installer. That command was to only allow read/write to a user different than root.

As for the installer, I really have no idea what it needs. It might be like oldfred said, linux works in different ways and maybe you will not be able to select the installation folder.

Does the installer ask you for a destination at all? Can you select or type /media/sdb1 because it seems that is what you want the destination to be?

---

### Post by djt on 2012-07-31
> **darkod said:**
> 
Does the installer ask you for a destination at all? Can you select or type /media/sdb1 because it seems that is what you want the destination to be?

                                  Yes the installer does ask for a destination but /media/sdb1 isn't one of them. I'll try to just type it in manually once I get up and running.

 By the way this Linux install is primarily for testing X-Plane. Would I be better off installing Xubuntu 12.04 64-bit instead of Ubuntu 12.04 64-bit?  Would there be a performance advantage to using  Xubuntu?

---

