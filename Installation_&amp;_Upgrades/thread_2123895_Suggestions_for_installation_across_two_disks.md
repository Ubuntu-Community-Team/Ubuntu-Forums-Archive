---
title: "Suggestions for installation across two disks"
date: 2013-03-09
forum: Installation &amp; Upgrades
---

### Post by edfast on 2013-03-09
Hello,

being a relative beginner at this game I would like the forum's suggestions on installing ubuntu studio across two disks. I am building a system for image and video editing, mostly, and will be fresh-installing on one 120Gb SSD and one 500Gb HDD. I would hope to end up with a seamless solution where I keep system and programme files on the SSD and all the data files on the HDD, but without having to think twice about the matter once everyting's installed. In other words keeping a file system GUI that I am familiar with, where both units mount automatically and where files are saved simply by aiming and shooting, no extra clicking, no finding the media disk, no having to assign a location to save outside of 'home' every single time, etc. I think you all understand what I'm talking about. Can this be done, and more to the point, 'Can I do it?'. With help from the forum I feel confident that I could. But How? :)

Cheers,

---

### Post by oldfred on 2013-03-09
Two choices, install /home to hard drive which is the easiest for a new user. Or create data partition(s) on hard drive, mount & link those partitions into /home so install looks like a standard install and files saved to Videos are really saved to a Videos folder in the other drive's partition.

Info just posted in this thread.
[http://ubuntuforums.org/showthread.php?t=2123833](http://ubuntuforums.org/showthread.php?t=2123833)

---

### Post by darkod on 2013-03-09
Since many program settings go into /home it might be better to actually have /home on the SSD to maximize speed access. You can create something like /data mount point for the HDD. With the corresponding entry in /etc/fstab for /data it will mount on boot and you don't have to do anything manually.

Depending on the programs you use, and whether the data destination can be set permanently to /data instead of folders inside Home, your programs could be able to use /data without too many additional clicking around, which seems is what you want to achieve. But that depends how the programs have the data/working directory set.
If your programs look for Home by default you could still use symlinks for some of the folders in Home linking them to folders on /data and that way the large data will end up on the HDD again without too many additional clicking.

---

### Post by edfast on 2013-03-09
@oldfred: Oops, didn't notice info was readily available elsewhere. Sorry!> Info just posted in this thread.
[http://ubuntuforums.org/showthread.php?t=2123833](http://ubuntuforums.org/showthread.php?t=2123833)@darkod: As for which programmes I will use, I think I will simply run with the standard ubuntu studio for awhile. I know most of them relatively well, and as this is part of a newly built computer project, I think I'll will first make sure I get the system up and running to my liking using the default programmes, *then* adding more, making a royal mess of everything. From what you wrote I assume every added programme might have to be tinkered with even if at first I manage to set up an initially flawless system?

@oldfred, darkod: Thank you both for your suggestions and advice. I was not aware that programme preferences go in different places, so perhaps this project will prove more complicated than I had hoped. I will get fiddling and come back to this space when I have failed, and with concrete questions!

---

### Post by oldfred on 2013-03-09
Programs themselves are in various places in / (root). If installed from Ubuntu repositories with Software Center, synaptic or command line you should not have any issues. And almost anything you want is available in the repositories.

Settings are by user and therefore in /home. Most applications also save data in /home, some in hidden files or folders. Applications my have files to define where to save like Firefox & Thunderbird use a profile.ini.

Data is normally saved in the data folders in /home like Documents, Video, Music, etc. But with links you can make those folders or others you may want be on other partitions on other drives.

---

### Post by fiodev on 2013-03-09
Use a LVM and it will let you install across multiple disks

---

### Post by darkod on 2013-03-09
> **fiodev said:**
> Use a LVM and it will let you install across multiple disks

That was my first thought when I saw the title but you have to note that the OP has one SSD and one HDD. Using LVM will not be very good since you can't separate to have specific mount points (like root) on the SSD to use the speed.

If you had two HDDs, LVM would be a natural choice.

---

### Post by edfast on 2013-03-10
> **oldfred said:**
> Data is normally saved in the data folders in /home like Documents, Video, Music, etc. But with links you can make those folders or others you may want be on other partitions on other drives.This is exactly what I'm after. How would you go about creating such links and then 'hiding' them, and would it have to be done for each programme separately?

---

### Post by edfast on 2013-03-10
Tell me if this is undoable: Unless the forum deems the approach singularly stupid, I propose to install 'all' onto the SSD, later add the HDD, and lastly make a data partition,migrate or link data, automount and see what happens. Anyone think this might work?

---

### Post by oldfred on 2013-03-10
I have all the details posted in several of the links in the other thread on using links. 
And I have a one liner that is a mini-script to link all folders from a mounted partition at once.

One of them
[http://ubuntuforums.org/showthread.php?t=1811198&p=11081384#post11081384](http://ubuntuforums.org/showthread.php?t=1811198&p=11081384#post11081384)

---

### Post by mirearts KING SUNNY on 2013-03-10
Choose a greater size for / and significantly more for /home and /data

---

### Post by edfast on 2013-03-10
> **oldfred said:**
> I have all the details posted in several of the links in the other thread on using links. 
And I have a one liner that is a mini-script to link all folders from a mounted partition at once.

One of them
[http://ubuntuforums.org/showthread.php?t=1811198&p=11081384#post11081384](http://ubuntuforums.org/showthread.php?t=1811198&p=11081384#post11081384)Looks good. Shall try, and get back. Will explore you're efforts in other threads as I go along. Thanks.

---

