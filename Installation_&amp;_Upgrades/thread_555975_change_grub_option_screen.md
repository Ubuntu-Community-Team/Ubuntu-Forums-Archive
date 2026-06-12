---
title: "change grub option screen"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by MacDuff on 2007-09-20
I had two versions of Ubuntu on a computer and at boot time I naturally had the option to select the one I wanted to boot to.  I decided to remove one of the versions and used the Gnome partition editor to delete that partition and re-format it.

I don't have any problem booting but I still have the original option screen offering me two systems on boot-up.  

How can I remove the option to boot to the non-existent system?

Also, I cannot gain access to the partition that I deleted/reformatted.  One file manager tells me the partition is not mounted and another file manager seems to indicate it is mounted but that I don't have permission to use it.

I am a little confused and need some kind soul to tell me how to resolve these two matters.

Thanks

---

### Post by yabbadabbadont on 2007-09-20
Assuming that you did not manually add the second boot option for the partition that you removed, running the following will probably fix the Grub menu for you:
```
sudo update-grub
```

Please explain in more detail, your second issue as it is unclear to me what you have/have not done and are trying to do.

---

### Post by MacDuff on 2007-09-21
yabbadabbadont:

Tried your suggestion to use "sudo update-grub" but it did not change the boot menu.

Regarding your question:
There are two drives on this computer.  One is formatted for Linux (Disk1)and the second is formatted NTSF (Disk2).

After reformatting the second partition on Disk1 which contained a second Ubuntu OS, the cleared partition shows up in the Thunar file manager as "65G volume" and it contains a file called "lost and found".  So evidentaly  I can read the partition. Thunar reports that the drive is mounted under [media] as [disk].  However, when I right click on the right panel of Thunar to add a new folder,  the options to "create file" and "create folder" are greyed out, so it appears that I cannot write to the partition.   

The second drive on this machine is formatted NTFS because it is available to other machines on the LAN which still have Windows as their OS.  This drive shows up in Thunar as [Data Backup] and shows as being mounted as [media] v[Backup].  I can read and write to it, seemingly, with no problem.  However when I try to use GNOME Commander to write files to this drive, an error message appears "Mount failed: Permission Denied".

So question 1 is:  How can I get my boot menu (Grup) to stop showing a non-existent operating system?

Question 2 is:  How do I get the system to allow me to use the second partition on Drive 1 that it refers to as "65G volume".

Question 3 is: How do I allow all applications to read/write to Drive2  [Data Backup].  

I am a little confused as to why one application would report a drive as mounted and another would say that "Mount failed:Permission denied".   I suspect that the error messages are not always correctly worded, but not knowing enough about Ubuntu yet, I am a bit reluctant to muck about any more.

---

### Post by Nikitas350 on 2007-09-21
First for the grub menu run this command "sudo gedit /boot/grub/menu.lst". After a lot of lines it appears something like this 

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=3f62b108-7e40-465a-998b-5bf00a68a5de ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

it appears a lot of times. Each time is for each entry in grub. Delete what you dont want :).

For the partitions that you dont have read/write permissions open the nautilus to the partitions you want and press ctrl+l it. It appears to the "location" (up left) something like /media/hda1 or something. Now open the terminal and run this command "sudo chmod 777" and the location that the partition is. for example for the /media/hda1 partition run "sudo chmod 777 /media/hda1". Enjoy :popcorn:

---

### Post by MacDuff on 2007-09-21
Thank You Nikitas350 !

The Grub menu now only shows the actual operating system.

For the second part, I  ran the command you suggested on the empty partition of the first drive and that fixed it.  I can now write to the partition.   Thank you also for that.

But when I ran the command on the second DRIVE,  the following message appeared:

mac@ubu-comm:~$ sudo chmod 777 /media/Data Backup
chmod: cannot access `/media/Data': No such file or directory
chmod: cannot access `Backup': No such file or directory
mac@ubu-comm:~$ 

Since this is a drive, not a partition, the error message is probably correct. 

The drive shows up on the Nautilus desktop and I can get access to it from there but it seems that Gnome Commander (and probably other applications that I have not yet discovered) does not have access to the drive.  Why is this and how can I allow Gnome Commander et al to read and write to the drive?

Mac

---

### Post by yabbadabbadont on 2007-09-21
```
sudo chmod 777 "/media/Data Backup"
```
or
```
sudo chmod 777 '/media/Data Backup'
```
or
```
sudo chmod 777 /media/Data\ Backup
```
Just like Windows, you have to take special care when working at the command line with files/directories whose names contains spaces/special characters.  :D

You probably can't write to the second drive because it is NTFS.  You will need to install and configure the ntfs-3g package before you will have write access to that drive.  See here for details:
[https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite](https://help.ubuntu.com/community/MountingWindowsPartitions?action=show&redirect=NTFSReadWrite)

---

### Post by MacDuff on 2007-09-21
Tried all of yabadabadont's three lines of code and still could not get access to the second drive.  I also checked on one of my windows computers and it does not show the Data Backup drive, 

FYI I do have the ntfs-3g package installed and configured.  I can read and write to the drive using the Thunar file manager but not with other applications and also not from another windows computer on the LAN.

Any more suggestions?

Mac

---

### Post by Nikitas350 on 2007-09-22
A few questions: 1) when you run the command "sudo chmod 777 /media/Data\ Backup" what is the output of the command. Also try this command sudo nautilus /media/Data\ Backup this command will open the nautilus wiht root privileges. If you can read the contents of the hard disk drive now you cna change graphically the permissions of the hard disk drive. And one other alternative is to run first the command su enter the password of the root and type chmod 777 /media/Data\ Backup (it's the same thing with the previous). good luck

---

### Post by MacDuff on 2007-09-22
Nikitas350:

First let me thank you for your assistance.  I did run your suggested command (sudo chmod 777 /media/Data\ Backup) and this is the output:
mac@ubu-comm:~$ sudo sudo chmod 777 /media/Data\ Backup
Password:
mac@ubu-comm:~$ 

That is what I would expect but it did not change anything with using Gnome Commander.

You second suggestion (sudo nautilus /media/Data\ Backup)  does work to allow esisting files to be shared,  however it does not address my root concern which I have probably not made clear.

Normally when I (manually) mount a volume or device, I can see it from anywhere and I can create directories or files in it.  The drive with which I am having trouble, mounts automatically on startup and  the only way I can graphically create new directories/files is to use the Thunar file manager.  If I try to use Gnome Commander to gain direct access to the drive I immediately get an error "Mount failed:Permission denied"   I can, however access files on that drive by going through SMB shares.

Thinking that there must be something wrong with the mount I have tried to un-mount the drive but when I try to do that I get a message that "You are not privileged to unmount the volume "Data Backup".  I understand that when a drive is auto-mounted it belongs to root, but does that prevent some applicatons from creating directories/files in the drive?   If so, why can Thunar create directories/files in the drive without changing privilages?     Should I change some of the auto-mount settings to allow me to create directories on the second drive from any application on this computer?

Another way of asking the question is:   Why can I not see files on the second hard drive (Data Backup) using Gnome Commander on the local computer without having to go through the Samba network?  By the way, other local applications see see existing files on the Data Backup.

Perhaps there is a bug in Gnome Commander and I am asking for help in  the wrong forum but any advice you can offer would be gratefully received because as a newcomer to Ubuntu, I really don't yet know what to expect when I use an application.

---

