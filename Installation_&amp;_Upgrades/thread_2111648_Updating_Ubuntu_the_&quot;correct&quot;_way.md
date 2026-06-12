---
title: "Updating Ubuntu the &quot;correct&quot; way"
date: 2013-02-02
forum: Installation &amp; Upgrades
---

### Post by beenny on 2013-02-02
Hello All,

I need to reinstall ubuntu on my work computer so that I can have an encrypted disk. Usually when a new distro comes out I do a direct upgrade. I know this is not the "best" way to do it and that you should do a clean install but I hate having to reinstall my programs again, recreate my directory structure, getting my settings back etc.

My questions are:

(1) Is there prep work I can do before a clean install so that I don't lose everything i've accumulated over the past few years

(2) Is there a way to install ubuntu from the beginning to make a clean install less painful in the future. I've seen stuff about mounting the home drive on its own partition but not quite sure how this works

(3) Anything I should be aware of for setting up an encrypted disk. It seems that it is now native in 12.10 so I'm assuming should be straightforward...

Thanks,

bg

---

### Post by zealibib slaughter on 2013-02-02
setting up home and root partitions can be done by selecting manually set up partitions when you reach the partitioning part of the installer. 

there you can change the layout of how the partitions work
you may have to delete whatever partition table is there and create a new partition table 
**only do this if you dont have any other partitions you need to keep like a windows partition **if you have a partition that you need to keep you can just delete and change the individual partitions and not create a new table

once you have enough free space showing from either deleting partitions or making a new table click add and you will get a gui that looks like this [http://ubuntuforums.org/picture.php?albumid=2023&pictureid=6754](http://ubuntuforums.org/picture.php?albumid=2023&pictureid=6754) (btw this is a very old picture but it will still apply to whats going on) now you need to make the root partition. lets say you want it to be 20 gb or 20480 mb enter this info at location labeled 2 in the picture.

at 4 select the type of file system you want
at 5 select ( / ) as mount point then click ok

click add again and go through the process to create the home partition
at 5 select (/home) and click ok

lastly click add one more time
add about 1 - 2 gig for the size
at 4 select swap
click ok

as far as prep work see this [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

---

### Post by beenny on 2013-02-02
Thanks for the quick reply. A few questions

> **zealibib slaughter said:**
>  lets say you want it to be 20 gb or 20480 mb 

Is 20 gb the best size. Conserving space is not really an issue for me as most of my big files are saved on my company's server. 


> **zealibib slaughter said:**
>  at 4 select the type of file system you want 

To be a bit dense what is the file system I want? (and to educate myself what are the differences?)

> **zealibib slaughter said:**
> 
click add again and go through the process to create the home partition
at 5 select (/home) and click ok 

So this is adding the home partition. Do I need to add anything at 4?

> **zealibib slaughter said:**
> 
lastly click add one more time
add about 1 - 2 gig for the size
at 4 select swap
click ok 

And this the swap partition. Curious what the 2gb here is used for?

On a more fundamental level (I'm trying to move beyond basic user) what is this buying me. My sense is that my home directory is now a mounted drive just like I would mount any drive (external hard drive, server etc.) That mean that when I go to upgrade again I'm just changing the 20gb of allocated space and all my files stay the same, correct? 

Some other questions to help my understanding:

(1) Where are my programs being saved - the main partition or the home partition? Do I need to control that when installing new programs?

(2) I don't have a windows partition (so I will just make a new table) but I do use VBox for windows. Does that have any implications? I'm assuming that needs to be installed off the root not, correct?

(3) Since the impetus for doing this is encryption does that change this around at all?

Thanks again for the help in understanding.

bg

P.S. exactly what I had in mind:
> **zealibib slaughter said:**
> [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

---

### Post by zealibib slaughter on 2013-02-02
ok im gonna edit this to answer those questions without having to quote you and making a long post

the 20 gb is just an example it can be any size but keep in mind that your root partition only expands as you add applications or your system generates log files so I try to keep mine small just depends on your hard drive though. I wouldn't recommend anything less than 10 gb and if you make it over 60 then you will be wasting space unless you have a special need for a large root partition.

file system type refers to which format ext2, ext3, ext4 etc.  I use ext4 but there is good points and bad points to all system formats. wikipedia has a good article on this [http://en.wikipedia.org/wiki/File_system#Linux](http://en.wikipedia.org/wiki/File_system#Linux)  i suggest ext3 or ext4 but there again its a lot do do with a persons preferences.

question three for the home partition yes you have to select a file system type at 4 use whatever type you did for root.

as far as swap goes there is many different thoughts as to how much to add but if your system has 2 gb or better of physical ram then swap looses a lot of meaning.  I use the recommendations found here (btw a good explanation of why you need swap) [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

your programs are saved on the root partition usually at /local/bin or /local/usr/bin i believe but could be wrong.
your vbox is saved in your home folder in .virtualbox i think (i know its saved on home just not sure exactly which sub directory)
encryption will not have an impact to this process and vice versa.
the main reason for doing this is so your personal files doesnt get lost in a system reinstall
when you reinstall you can tell the system to use your *existing* home directory and keep all your files (which can include a sh script for synaptic to install all your extra programs. basically at a new install grab a list of everything extra you want to install.  open synaptic and find and mark all of this then go to file save markings as and you have a neat importable document that makes synaptic grab all your programs for you. or after you have everything set up to your liking you can go to status - installed in synaptic and then go to file generate package download script and do the same thing see this page here [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by beenny on 2013-02-02
Thanks again for the details. So it sounds like in practice this avoids the step (that I usually take) of transferring all of my files and directory structure to an external hard drive, doing a fresh install and then transferring back.

I still have to worry about getting settings etc back together. 

One more detail, if VBox sits in Home does that mean that the Windows OS is also sitting in home so when I do clean installs in the future I won't have to reinstall windows? I'm not 100% clear on how VBox works but my understanding is that there is the full windows install sitting within a single partition (as oppossed to a separate partition when I used to dual boot). this is kind of a big deal b/c IT doesn't love having to reinstall windows for me and associated (licensed) programs...

Anyway, going to try this on an old laptop first and see how it goes!

Thanks again,

bg

---

### Post by zealibib slaughter on 2013-02-02
dont have to worry about settings either since almost all user settings are stored on the home partition,
you will still have you windows vbox appliance since it is just a file in your home folder no reinstall needed
and yes you are right it removes the step of back up and transfer since it effectively makes your home folder its own mountable volume.

---

### Post by beenny on 2013-02-02
thanks - time to try this out...

---

