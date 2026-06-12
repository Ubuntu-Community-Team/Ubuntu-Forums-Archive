---
title: "Problem setting up partitions"
date: 2012-03-03
forum: Installation &amp; Upgrades
---

### Post by sfang on 2012-03-03
I want to run the following setup:

/dev/sda1 = /
/dev/sda5 = swap
/dev/sda6 = /home
/dev/sda7 = Data

All partitions are ext4 (except swap) and Ubuntu will be the sole OS on the system.

/home will store configuration files while my personal stuff will be in a partition called "Data". This way I can reinstall the system and decide if I want to start fresh or not. I also want to link "Data" to /home so that when I go to /home/Documents I'm actually accessing /data/Documents. From what I've gathered around the forums, I can use fstab to do so.

The first time I tried, I set the the mouting point of /dev/sda7 as /data while installing the system. After the installation I tried to copy my files to /data and got the "Permission denied" message. I thought I borked something and reinstalled.

With the system up and running again, I opened the terminal and typed:

```
mkdir /mnt/data
```The "Permission denied" showed up once more. Then I tried with sudo and managed to create the mounting point "data" for /dev/sda7. Next, I edited fstab and added the line

```
/dev/sda7/    /mnt/data        ext4   defaults          0       0
```saved and rebooted.

The problem is that when I try to copy anything to /mnt/data "Permission denied" shows up. I checked the permissions of /mnt/data and its set to root. Is it always set to root or am I messing up somewhere?

I hope it's not too confusing to read. I really have no clue of what I should do. I'm afraid to change the permissions and then expose the system to a security risk.

Any help will be much appreciated.

---

### Post by Herman on 2012-03-04
Try this command, it will change the user ownership and the group ownership of the mount point from root to usfang, 
```
sudo chown sfang.sfang /mnt/data
```After that you should be able to read and write to the file without needing to use any sudo command.

Now you can make it private if you like by changing the file permissions to level 7 for yourself and level 0 for your group and level 0 permission for anyone else, 
```
sudo chmod 700 /mnt/data
```That should protect your privacy somewhat from any other polite users, or users who may enter your computer via some network connection if you allow those. 
Of course it won't be much protection if somebody has physical access to your computer and has a Live CD. :)

---

### Post by Herman on 2012-03-04
If you're serious about security, you should consider using some kind of file system encryption for your data partition.
An encrypted file system won't protect you much from network intrusions, but it should give you pretty good protection from people with Live CDs.

---

### Post by sfang on 2012-03-04
Thank you very much, Herman! 

After I posted I came across a [topic]("http://ubuntuforums.org/showthread.php?t=1675381") that helped with the issue and one of the solutions proposed was the very one you describred. I ended up formating sda7 to NFTS and now everything is working as planned, including the separete /home and /data. Using NFTS never crossed my mind since I won't install Windows on this machine. Who would guess?

It's not much about privacy. I don't feel confortable enough doing something I'm not 100% of how to do myself, which means dealing with permissions and ownership. At least not yet, but I'll fire up a VM later and try it. I'm of the opinion that if you're not sure about what you're doing, you can unwilling open the system to some exploit. 

Still, thanks! Now I've learnt a bit more about permissions and ownership. :D

---

### Post by oldfred on 2012-03-04
One disadvantage of NTFS is you still need a Windows install or repairCD to run chkdsk. Ubuntu cannot run chkdsk and you need to occasionally run it, and may have to run it if the system has corruption.

Ubuntu automatically runs fsck on Linux partitions every 40 to 60 reboots.

---

### Post by sfang on 2012-03-04
Thanks oldfred, wasn't aware of that. For the time being I'll stick with NFTS while I learn more about permissions/owership.

---

### Post by Herman on 2012-03-05
File ownership and permissions are a really interesting and kind of a fun subject for some day when you have some spare time and feel like playing around a little and experimenting with them.

A good way to learn is to set up a fake user account under some other name and then log into it and pretend you're somebody else. Then practice changing permissions on files and directories in the home folder and see if you can open them when you log out and log back in as yourself.

If you want to be really safe, you may even want to install a spare Ubuntu installation in your hard drive or in a USB external drive just to experiment in without harming your regular Ubuntu installation.
It's okay to play around with ordinary files in the /home/username  directory but operating system files that belong to 'root' should only  be changed if we know what we're doing, (as you probably know).

You can easily change file permissions in GIU mode just by right-clicking on a file or directory and clicking 'properties', there's a 'permissions' tab. 

The command line way is maybe better than using the GUI method and you can work on a whole batch of files at once that way if you ever need to. You can use the ls -l command to see what files are there and all about them, and chmod and chown them. See [FilePermissions]("https://help.ubuntu.com/community/FilePermissions") - Understanding and using file permissions - Ubuntu Community Docs. Tuxfiles has a great page on how to use the chmod command, [_Linux File Permissions_]("http://www.tuxfiles.org/linuxhelp/filepermissions.html"). Tuxfiles has another great page on how to use the chown command too, [How to change a file's owner and group in Linux - 1.0]("http://www.tuxfiles.org/linuxhelp/fileowner.html")

Don't do what I did when I was learning, (well, I'm still learning actually). I used the -R option on my /home/herman directory and borked my Ubuntu installation and had to re-install. That's because the -R option changes file permissions for all files and folders inside the one you're running the the command on as well. There are a lot of special .hidden files inside our /home/username folders that aren't supposed to be chowned or chmodded. I had forgotten about those at the time.
Be careful with -R. You probably should not use it to chmod or chown a mount point either, (unless you're sure you know what you're doing).

File and folder ownership and permissions aren't too important if you're running a PC, (Personal Computer), and you're the only user. If you have a server or if you're sharing your computer with a number of other users though, or if you just want to learn stuff to prepare yourself for a job as a sys admin for a big company some day then file permissions might be worth learning about.
For the average Ubuntu user they're probably just a fun subject to explore on a rainey day and most of us can probably get by with a minimal understanding. :)

---

### Post by sfang on 2012-03-06
Hi Herman, didn't see there was a new post here.

Seems I've nailed down how the ownership and permission systems works, or at least a good part of it. And you're right, it's a fascinating subject once you start to understand the ins and outs. Very well-designed.

I agree it's not something essential for the normal user to know, but the more you understand about the system you're working with, the better!

Thanks for the tips!  :D

---

