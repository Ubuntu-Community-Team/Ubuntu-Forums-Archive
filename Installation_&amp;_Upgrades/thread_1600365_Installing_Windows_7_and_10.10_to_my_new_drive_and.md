---
title: "Installing Windows 7 and 10.10 to my new drive and need help."
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by Portaljacker on 2010-10-18
I own a Dell Studio 1537 laptop with:
Windows 7 Home Premium 64-bit
a Dual Core T3400 2.16 GHz
4 GB of RAM
Intel Integrated 4500 MHD

It's basically the lowest end version of it. :P

So, the reason for the post: I have a 250GB drive, and ordered a 750GB to replace it so I have more space. So why not use some of it to finally get Ubuntu.

So this is what I'd like to do:
I have a copy of 7 Professional 64-bit from school & 10.10 64-bit.
I'd like to be able to access the usual data folders (documents, pics, music, video, code, etc) from both operating systems.

From Windows 7 it's easy, just change where the libraries point to. But for Ubuntu I'm a complete noob and have no idea how I should go about it.

All I can figure it out is that it would be a data partition (D: drive)

So how do I go about setting this up?

Install 7 first then Ubuntu and do the partition stuff during that install? Then how do I do what I want to do in Ubuntu.

Thanks very much for the help on my problem. I wanted to finally try Ubuntu/Linux and now I have my chance, I just want to be able to get my things for class from either OS.

---

### Post by Portaljacker on 2010-10-18
As for how I'm dolling out the space. I'm guessing about 50GB for the Ubuntu, 450GB for the data and 250GB for Windows and whatever games (15-30 of that is WoW alone) and programs I install.

---

### Post by jgor on 2010-10-18
Ubuntu can read and write to Windows file systems so you would be able to store all your document files in the D: drive.

---

### Post by Portaljacker on 2010-10-18
Does Ubuntu have the equivalent of those default data directories? (documents, music, pics, video, etc)
If so can you reassign those locations?
If not, then I assume you assign the default directory for each program program by program?

Also, is 50 GB overkill for the Ubuntu install?

---

### Post by jgor on 2010-10-18
Ubuntu likes to store your document files (music, pics, video, etc) and the vast majority of your application settings in the /home directory. It is usually recommended that /home be on a separate partition so that you can upgrade your distribution easily.

I wouldn't think reassigning the default directories would be necessary, you'd just probably want some shortcuts to the directories that hold your files on the D: drive.

50GB sounds about reasonable for trying out ubuntu, 50GB doesn't seem like much when you have 750 in total.

---

### Post by Portaljacker on 2010-10-18
> **jgor said:**
> Ubuntu likes to store your document files (music, pics, video, etc) and the vast majority of your application settings in the /home directory. It is usually recommended that /home be on a separate partition so that you can upgrade your distribution easily.

How does that work? Is it one of the partitions created in the empty space I leave for Ubuntu to do it's default install? Though I guess that's asking how Ubuntu installs itself.

One of the main reasons for the shared data directory was to share the Dropbox folder. Should have mentioned that. :P

---

### Post by oldfred on 2010-10-18
I use linking to put folders into my /home from my /data partition. My /data is ext3 but you can use NTFS so you can read from windows also.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

You have to create a mount point, edit fstab with the partition using the mount point you created and NTFS, delete the empty folders and link the new folders from your /data partition.

If you have all your folders just under you /shared or /data partition you do this for each folder

I move before deleteing:
mv Music oldMusic
mv Documents oldDocuments
mv Pictures oldPictures
Then link

ln -s /data/Music
ln -s /data/Documents
ln -s /data/Downloads

You can automate the linking if it is a lot of folders. see man ln

for i in `echo /data/*`;do ln -s $i; done

---

### Post by Portaljacker on 2010-10-19
> **oldfred said:**
> I use linking to put folders into my /home from my /data partition. My /data is ext3 but you can use NTFS so you can read from windows also.

Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)
Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

You have to create a mount point, edit fstab with the partition using the mount point you created and NTFS, delete the empty folders and link the new folders from your /data partition.

If you have all your folders just under you /shared or /data partition you do this for each folder

I move before deleteing:
mv Music oldMusic
mv Documents oldDocuments
mv Pictures oldPictures
Then link

ln -s /data/Music
ln -s /data/Documents
ln -s /data/Downloads

You can automate the linking if it is a lot of folders. see man ln

for i in `echo /data/*`;do ln -s $i; done
I did mention Linux noob right? I swear I said that.

---

### Post by oldfred on 2010-10-19
You are in the installation forum not the beginners, so I assume you can at least use a command line.

Using a shared partition is not really too advanced but making it easy to use is a little more advanced. 

Start off creating shared NTFS partition and then learn how to mount it and see the data in Ubuntu.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

I prefer the control manual editing gives, but
Some think it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

### Post by michaelzap on 2010-10-19
You probably don't need to do much of anything that's non-standard to use both systems and share data easily. For one thing, if you create a data partition and format it as NTFS (which you can do from Linux or Windows, whichever makes you more comfortable), you'll be able to read and access it from Ubuntu just as you do a D: drive in Windows (go to Computer, double-click on it, and it opens).

And that may be all that you really need to do. You could change the default documents, music, video, etc. folders in Ubuntu to point to folders in this data partition if you like, but it's not really necessary. I keep the vast majority of my data (including all my music, videos, etc.) on network drives, and I've never felt the need to specify different default folders. You can bookmark folders in your data partition in Nautilus for quick access, which is helpful.

If you really do want to point your various default personal folders to the data partition, install [Ubuntu Tweak]("http://ubuntu-tweak.com/") and you can change those easily. For the most part you shouldn't need to download software from websites on the internet, but afaik UT isn't in the standard software repositories. Just download the .deb installer, double-click on it, and follow the instructions to install (then look in Applications->System Tools for Ubuntu Tweak).

Let your browser and other Linux software store their configuration files in your home directory (not the data partition). That's because Linux expects a file system with a permissions, and NTFS doesn't fully fit the bill. It's fine to save all your actual data files to the shared partition, however.

I'd also say that 50 GB for Ubuntu is kind of small, but it's certainly enough (given your shared data partition). I squeezed Windows down to 100 GB on a 320 GB drive, with the rest dedicated to Linux. Of course, I pretty much never use Windows anymore.

---

### Post by Portaljacker on 2010-10-19
> **oldfred said:**
> You are in the installation forum not the beginners, so I assume you can at least use a command line.

Using a shared partition is not really too advanced but making it easy to use is a little more advanced. 

Start off creating shared NTFS partition and then learn how to mount it and see the data in Ubuntu.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

I prefer the control manual editing gives, but
Some think it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

Ok, I get it, I didn't notice the beginner forum section. I went here because it was about installing. I'll look into those links, thanks for posting them.

> **michaelzap said:**
> You probably don't need to do much of anything that's non-standard to use both systems and share data easily. For one thing, if you create a data partition and format it as NTFS (which you can do from Linux or Windows, whichever makes you more comfortable), you'll be able to read and access it from Ubuntu just as you do a D: drive in Windows (go to Computer, double-click on it, and it opens).

And that may be all that you really need to do. You could change the default documents, music, video, etc. folders in Ubuntu to point to folders in this data partition if you like, but it's not really necessary. I keep the vast majority of my data (including all my music, videos, etc.) on network drives, and I've never felt the need to specify different default folders. You can bookmark folders in your data partition in Nautilus for quick access, which is helpful.

If you really do want to point your various default personal folders to the data partition, install [Ubuntu Tweak]("http://ubuntu-tweak.com/") and you can change those easily. For the most part you shouldn't need to download software from websites on the internet, but afaik UT isn't in the standard software repositories. Just download the .deb installer, double-click on it, and follow the instructions to install (then look in Applications->System Tools for Ubuntu Tweak).

Let your browser and other Linux software store their configuration files in your home directory (not the data partition). That's because Linux expects a file system with a permissions, and NTFS doesn't fully fit the bill. It's fine to save all your actual data files to the shared partition, however.

I'd also say that 50 GB for Ubuntu is kind of small, but it's certainly enough (given your shared data partition). I squeezed Windows down to 100 GB on a 320 GB drive, with the rest dedicated to Linux. Of course, I pretty much never use Windows anymore.
And thanks as well for these more noob friendly options, I'll use it if I can't figure out the other guy's instructions.

My Windows partition will be large because of the programs I'll be installing including games such as WoW and my Steam collection.

---

