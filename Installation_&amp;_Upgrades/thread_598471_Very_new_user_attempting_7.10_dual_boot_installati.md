---
title: "Very new user attempting 7.10 dual boot installation"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by SouthernPott on 2007-10-31
Greetings all,

I downloaded and burned the Ubuntu 7.10 Live CD and have used it successfully to boot up.  I also used the error check and it came back fine Now I want to install it but I need to keep my XP Home.  I have gotten into the installation up to the partitioning part.

My problem is that I only get two choices.  Use the whole disk or manual partitioning.  I do not get the choice of resizing the present space and setting up a partition in the unused space.

The disk I want to use is my C: drive, 80gb with less than 20gb presently used.   My partition table looks like the following:

/dev/sda
       /dev/sda1     fat16    /media/sda1              32mb                32mb
       /dev/sda2     ntfs      /media/sda2             79990mb           unknown

/dev/sdb
       /dev/sdb1      fat32         media/sdb1         8620mb            5800mb

/dev/sda is the disk I want to use of course.  /dev/sdb is an older small disk I may use for backups and is designated F: in Windows.  

I am the type of person that needs either very specific instructions on what to do or a very detailed tutorial, especially if I have to do the partitioning manually.  My understanding is that the option for using the whole disc will erase or overwrite the C: drive.  

Being new the Linux terminology is confusing me right now so I need to be careful how I approach this and I could use some suggestions on partition designations as well.  From what I have read I believe I am looking at a partition for XP home (sda2), a partition for Ubuntu (hda?), a small swap file (unknown name), and possibly a /home file for Ubuntu (unknown name).  Do I set these up in  GParted during the manual partitioning or is it something I do in the terminal?

So either I need someone to give me very direct, very explicit, very accurate instructions so that I can keep my present XP setup  or a link to some better reading material.  

Thanks for any help.

Malcolm

---

### Post by scrooge_74 on 2007-10-31
You have to make a manual partition, is very intuitive and easy to use, you will be able to rezise the disc and then make the corresponding partitions

My advice is to take the empty space and make three partitions: one for the system, one for your /home folder and another for the swap.

There are good tutorials[ here]("http://www.psychocats.net/")

---

### Post by SouthernPott on 2007-10-31
If I am understanding correctly you are recommending setting up the partitions so that they will look like 
[http://img379.imageshack.us/my.php?i...ioning4mz5.png]("http://img379.imageshack.us/my.php?i...ioning4mz5.png")

I have already combed through the link your provided  and I kind of understand this is the direction I am to go but there are a few steps missing in the details.  When I get to the partitioning I will have to select manual and then I get the partition table.  This is where I am stopped.  

Given that Gparted is pretty intuitive, what happens next?  I don't remember my choices but do I open a new partition table and write in all the old information, resizing the sda2 from 79990mb down to like 30000 or 40000mb?  Will Gparted then ask me what I want to do with the rest of the space?

What labels do I give the new partitions and how do I assign them?  How much space do I allocate for each one and how do I assign this?  Does Gparted ask for a space allocation and assign labels according to what I input?


Malcolm

---

### Post by scrooge_74 on 2007-10-31
Could not see the image, anyway 

You select manual partition, then you click on the partition you have already and pick the option to resize. After you resize, then you make one partition at a time leaving the following space as unused until you get them all. 

For system and 7home you tell the system is an ext3 partition, the swap partition is swap

As for Gparted asking if you want to do anything with the empty space it wont, you have to tell it what to do.

If I remember correctly you have to set the mount option, the system will be /, the home partition is /home.

After that when you install the system you installed to /

---

### Post by SouthernPott on 2007-10-31
Sorry, that image was supposed to be from the psychocats website you posted, under the "Planning your Partitions" section.  Should have been the graph showing XP(ntfs), then Shared Files (Fat32), then Ubuntu/home(ext3), then Ubuntu(ext3), then SWAP.

Thank you for the help.  That makes a lot more sense now.

So let me see if I can explain it back to you.  When I get to the partition and select "MANUAL" it will take me to the present partition table.

I click on the  /dev/sba2 which is the hard drive I want to partition.  GParted will ask me if I want to resize it and how much?  I resize it to 45000mb which is more than enough for what is there now and any future needs I might have.

Then I have 30000mb of free space that I will divide into system / (20000mb), /home (5000mb), and SWAP (5000mb), give or take a little on each one.

These numbers are just rough estimates but pretty close.

Now for the "mount" terminology.  I saw that on the partition table and have seen it referenced extensively but I don't know the meaning.  I am assuming that after I do the resizing I then click on the "mount" button and assign "/" for the main installation of Ubuntu, tell it to allot 20000mb for usage, and make it ext3.  Then the same for the "/home".  Then do the "swap" and call it swap, not ext3. 

What about a section for "shared files (FAT32)"?  I forgot about this when I was setting the space numbers.  What does this section do?

Malcolm

---

### Post by SouthernPott on 2007-10-31
[http://img379.imageshack.us/my.php?image=partitioning4mz5.png](http://img379.imageshack.us/my.php?image=partitioning4mz5.png)

The link above should have the correct graphic or actually be an image.  New to this board also so I am not sure how things are showing up until after I post them. 

Malcolm

---

### Post by scrooge_74 on 2007-10-31
The share section is if you have files you need to open in Windows and also in Linux you put them in there and the system will make a reference to it like /windows or something similar.  You can also have it to be ntfs and Linux can read it also.

Your / partition  needs to be at least 2 GB for the file system, 1 GB will be to close, because all the system files, the packages to instaling files, de log files, other programs you install from outside the repositories, the config files of the system, the temp folder, etc go in there.

Swap you are correctr has to be swap system for the your Linux OS to consider it as its swap space, a good rule is for the swap to be at least twice the amount of RAM you have.  

You are basically on track keep posting any questions you have either me or someone else will help you

---

### Post by SouthernPott on 2007-10-31
I think I am still following along correctly.  New numbers for space allocation.

XP home           25gb      NTFS

" / "  Ubuntu system       10gb    ext3

" /home " personal settings     2gb  ext3

" swap  "                            2gb   (computer has 1gb RAM)

Shared files           ~35gb       NTFS


Thanks for your patience and yes I have more questions. 

 After I get to the partition table and select the section I want to resize and partition, in my case it will be " /dev/sda2 " I will see a slider bar that I can move from ~80gb down to ~25gb, correct?  I then select/save or continure/forward for this?  I don't remember the buttons exactly.

If this is correct I should now have one partition showing as ~25gb and ~70gb  of free space.  

Now I want to "mount?" the system partition with " / "?  Do I get a slider bar for setting the size or a box for inputting the  " / ", size, and file type?  Then save or select?

The "/home" and "swap" will do the same procedures?

Is "shared files" handled the same way? 

Malcolm

---

### Post by scrooge_74 on 2007-10-31
Ok once you resize the partition you can save it, after or you can make all the changes and then save. It will take some time since it has to format the new partitions and everything. The same steps are involved in making /home and swap, you pick the free space, tell the system what type of filesystem you want to use and then the mount point.

The share space you tell the system to use fat32 and to have it thee I dont remember if there is a mount point but you can make mount points later on for a fat32 since you can't install the system there.

You can even make the / partition smaller than 10 GB since I doubt you are going to fill that unless you install lots of packages and never take them out

---

### Post by SouthernPott on 2007-10-31
Thanks again for the help.  I will give this all a try a little bit later.  Finally starting to make enough sense that I can work through it now.


If I run into issues or questions during the middle of it I will stop and ask again.  Otherwise I won't post until I have a successful install.


Malcolm

---

### Post by SouthernPott on 2007-10-31
Not going smoothly so far.

When I click on the disk, "  /dev/sda2  ",  I  get three buttons at the bottom of the box, Edit, Delete, Undo.  When I click on Edit I get a small box with the file system type and the present name of the partition but no box for resizing.  I can change the name to " /windows " from the shown name of " /media/sda2 "  Do I need to do this first?

If I click on either of the other two "  /dev/sda1 " or " /dev/sdb " and click on edit I do get the option for resizing and changing the name.  /dev/sda1 seems to be a small part of the main disk and is called " /media/sda1 ".  /dev/sdb1 is the small 8gb hard drive that is slaved to the primary.

Someone mentioned on another forum that the names showing in the present partition table indicate USB attached devices rather than hard drives.  When I originally downloaded the LiveCD I still had a USB card reader attached and the first time I booted up with the LiveCD it was showing in the partition table.  I removed it and it no longer shows.  Is it possible that I need to do a new download of the LiveCD without the USB cable attached and maybe even remove the secondary hard drive removed?   

Malcolm

---

### Post by wirechief on 2007-10-31
before you partition windows it is a good idea to do a defrag of the windows partition as a first step.
then do the resizing...

---

### Post by elctb on 2007-10-31
I just had to do the same thing 2 weeks ago. I used partitionMagic to make a new partition out the unused disk space. It went perfect. PartitionMagic has choices on how to partition to install a second OS. It's a commercial product though, and no, I'm not suggesting you use a bittorrent to download a pirate version. Make sure you go through the tutorial first.

I've always created 4 partitions when installing linux:
    /
    /usr
    /home
    swap.

The root "/" partition should be 2-3G. You'll need at least 5G for /usr (it depends on how much software you intend to install). The swap partition as suggested above, and then /home gets the rest. The important thing is to keep the root partition separate from /usr and /home since linux can't boot up if the root partition is full.

---

### Post by SouthernPott on 2007-10-31
I am getting a little lost on this again.  Thanks for the reminder on the defrag.  I have done this in the past couple of days but did start another one and it should finish shortly.  

I appreciate the advice on partition names but I need more details.  Please tell me what they are for and how much space you are allocating for them.

I have an 80gb drive that has never been partitioned.  Presently there is less than 20gb of space used on it.  Do I rename this during the partition process to /windows ?  Still need to know why it did not allow me to resize it when I clicked on the Edit button and what is the significance is of the present labels in the partition table before I do anything.

What is the " /usr " partition for?

I am using GParted which is a Linux partition manager and part of the LiveCD so I won't be using PartitionMagic.  Definitely not any illegal downloads.  Not a saint but I have never downloaded anything I didn't pay for.  

Malcolm

---

### Post by PmDematagoda on 2007-10-31
Actually all you would need is:-

about 1Gb of Swap space

and the rest for the root partition(/), a seperate /usr partition is not necessary as that would be just a waste of space and would cause some more problems incase you do run out of space in your /usr space.

---

### Post by scrooge_74 on 2007-10-31
If you could not resize the disk is most probably because there is some windows data farther ahead in the drive than you expected, make the free space a little smaller and try again

---

### Post by SouthernPott on 2007-11-01
I have defragged and compressed as much as possible.  I agree that there must be something on the disk that is preventing the resize but I don't know how to find it and if I do find it I might not be able to move it. 

I removed the small hard drive so I only have the C: drive and on the partition table it now looks like this:

/dev/sda
       /dev/sda1     fat16      /media/sda1        32mb          32 mg (space used)
       /dev/sda2     ntfs        /media/sda2       79990mb       unknown (space used)

When I click on the /dev/sda2 line it still gives me the Edit button, Delete button, and Undo Changes button.  I click on Edit and a small box pops up with two small boxes for the file system type and the name of the present partition but not the third box which should have 79990mb in it and allow me to change the number to the resize.

The only thing I can think to do at this point is a reformat unless anyone has any ideas why this is happening.  Not the best idea because I have never done it before but I have been copying everything I need on to CDs for the past couple of days so there really isn't anything I will lose but a little more time.  I have the reinstallation disk for Windows XP that came with the computer, a Dell, but I read something about creating a boot disk.  Do I need to do this?

Guess I need to go through everything one more time just to make sure I have everything copied that I want.

Thanks for all the thoughts and help.

Malcolm

---

### Post by scrooge_74 on 2007-11-01
More for you to read, hope it helps


[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)

It is a good idea to backup first in this case.  If you get to the point you feel you need to reformat the drive.  You can even use Gparted to wipe the disk clean and make a new partition table

ntfs for windows
ext3 for /
ext3 for /home
swap
fat32 for share files if you feel you need them 

then after you have the disk with the new partitions table go and install XP first, because if yo do it the other way then you will have to take extra steps to get Linux to boot since XP wipes the master boot record and deletes the controls that with let you dual boot. (XP does not like to play with other children)

---

### Post by SouthernPott on 2007-11-01
I didn't discover what was preventing setting up the partitions so I went ahead and reformatted the drive, reinstalled Windows which did allow me to change the partition size during the setup, and then installed Ubuntu 7.1.  Once I got to the partition setup in 7.1 it gave me the three options I was expecting and I chose to use the "Guided in the largest free space" rather than manual.  It set up a system partition and a swap partition.  I will have to go back in and look it over to see what I need to do to install a /home and a shared files partition.

I have had this computer for almost 6 years and it has never had a reformat/reinstall and still had tons of junk that was originally put on it plus all the junk I have added and then stopped using.   It had become very disorganized as well.  This was a great way to unload it and put back only the stuff I need or want.

All in all it worked flawlessly once I cleaned up the drive.  Very impressed with how easy it turned out to be and how smoothly the computer boots up with GRUB.  A fresh install is definitely the way to go.

Still have some work to do  but mostly done on the XP side.  Can't wait to work with Ubuntu.

Just wanted to say thanks again for all the help!!!

Malcolm

---

### Post by scrooge_74 on 2007-11-01
Glad to hear you got it working in the future if you want to make a separate /home, [this]("http://www.psychocats.net/ubuntu/separatehome") is a very good guide I used once.

Another[ tutorial]("http://www.psychocats.net/ubuntu/mountwindows") that could benefit you 

For your reference, the basic concept behind having a seperate /home partition is if you decide to test another Linux distro or want to reinstall the current one that way your home folder is away safe from changes.

Example I have a laptop in which Iearned to do things, it started with Ubuntu Dapper, later I wanted to play with Xubuntu Edgy so I went in and did separate partitions for the OS versions, but /home was in its own place.  That way i could boot to any of them and have the same config files and data.

Later on I have reformated that PC for my kids and kept the separate /home, I put in there Xubuntu Feisty, got bored and tired of it so I change that to Debian Etch running Xfce4.  Since the /home was in a separate partition the changes to the data were minimum and it was up an running very soon.

---

