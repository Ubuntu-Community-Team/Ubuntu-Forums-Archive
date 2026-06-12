---
title: "How should I partition this drive?"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by asintu on 2008-05-20
I have a 750gb drive (only 700gb available) of which 10% (70GB) is used for Windows XP. I also have 4GB of ram.
Now I wanna install Ubuntu and after reading about it so much my plan is to create 3 more partitions:  root(/), swap and /home (for storing/sharing files between xp and ubuntu). Six questions:

1. Is this a good plan?
2. What should be type and size of these 3 partitions for maximum performance?
3. Does it matter in which order the partitions are created? Should I set all of them to start at the beginning?
4. When I install new applications in ubuntu they go into the root directory right?
5. What's the best type for the /home (storage) partition for maximum performance and accessibility by both xp and ubuntu (ext3,reiserFS, jfs, xfs etc.?!)
6. Does swap need to format?

Thanx.

---

### Post by iaculallad on 2008-05-20
> **asintu said:**
> I have a 750gb drive (only 700gb available) of which 10% (70GB) is used for Windows XP. I also have 4GB of ram.
Now I wanna install Ubuntu and after reading about it so much my plan is to create 3 more partitions:  root(/), swap and /home (for storing/sharing files between xp and ubuntu). Six questions:

1. Is this a good plan?
2. What should be type and size of these 3 partitions for maximum performance?
3. Does it matter in which order the partitions are created? Should I set all of them to start at the beginning?
4. When I install new applications in ubuntu they go into the root directory right?
5. What's the best type for the /home (storage) partition for maximum performance and accessibility by both xp and ubuntu (ext3,reiserFS, jfs, xfs etc.?!)
6. Does swap need to format?

Thanx.

For question 1-3: Refer this [page]("https://help.ubuntu.com/7.04/installation-guide/hppa/apcs03.html")
For question 4: Newly installed applications can be stored in the /usr and /var
For question 5: The bigger the better if you're planning to save music, videos, and tons of documents. (I prefer Ext3 filesystem for home)
For question 6: By default, Swap does not need to be formatted.

---

### Post by nicedude on 2008-05-21
This is just my 2 cents as I am sure some would disagree with. I would suggest 3 new parttions as well but like this.

Swap partition maybe say 1.5-2 Gigs

Ubuntu partition complete with home directory maybe for your large disk 20GB in size should accomidate anything you want to install

And for 3rd parttion I would make a shared partition that you can access from Windows & Linux. You can use either Ext3 or NTFS but each of these will require using software in the other OS to allow access ( Ubuntu comes with ntfs util but for windows you will have to get an Ext3 one ), Or just format 3rd partition as fat32 which is supported by both by default. Some will say fat32 is no good but I find on my laptop it works just fine as my 100GB storage partition to save movies and MP3's and documents to. And before I kicked MS off my system XP & Ubuntu played nicely with it ( Now I just have 2 linux OS's :-) )

Also I don't know if you used advanced windows install options to specify a 70GB partition for it or if you mean it currently has 70GB of data on it but if you mean the latter you will need to use a bootable CD to resize the partition to give some of your freespace back ( However much of the 630 or so free that you want to use for Ubuntu and the data storage partition ).

And as a final note FYI all hard disk makers claim a capacity but it is not a true capacity as in your case & the 50GB you don't see are due to disk formating taking up space. If you knew that great, just threw it in because I have seen people asking why that is or thinking something is wrong and wanted to let you know in case you didn't already.

Hope this helps you,

nicedude

---

### Post by asintu on 2008-05-21
> **iaculallad said:**
> For question 1-3: Refer this [page]("https://help.ubuntu.com/7.04/installation-guide/hppa/apcs03.html")


I'm even more confused now.
From reading the article, since I have a big drive they recommended 4 more partitions in addition to the root one: /usr, /var, /tmp, and /home. What are they each used for? 
Right now I had 630gb of free (unpartitioned space).

Could someone give me a rough recommendation as to how much space I should allocate for each of these 6 partitions (root, usr, var, tmp, home, swap). Thanx.

---

### Post by MachineHead on 2008-05-21
A friend of mine gave me some notes on these things when I was doing my first install.
*searching on my desk...they gotta be somewhere around here?*

.......

**/   **      = Approximately the size of the Windows Program Files Folder, you could use that as an example. Mine is 8 GB

**/boot**   = 1 GB

**/home** = Takes up most of the hard drive, these are your personal files, music, movies, homework etcetera, choose your own size.

**SWAP**  = 2 times the size of your physical RAM (I got 4048 RAM, SWAP is 8096)

Install Windows first and then put Ubuntu Linux on there, Windows could be wining about not being number one or something.

To be clear, I'm a beginning user, no idea if this will be the best setting.

MachineHead

---

### Post by asintu on 2008-05-21
Ok, so for now I have these 2 partitions figured out:

swap (8GB) - used for memory purposes
/home (rest of drive) - used for personal files, movies, music etc.

Still confused about what the other partition types represent, what they'll be used for and how much space I should allocate them (ie: /usr, /var, /tmp and more recently /boot !!??).

--------

I've read some more and it seems that I can only have 4 primary partitions: NTFS (for windows), root, swap and home. Should I just stick with these?

---

### Post by Lord Landis on 2008-05-21
> **asintu said:**
> Ok, so for now I have these 2 partitions figured out:

swap (8GB) - used for memory purposes
/home (rest of drive) - used for personal files, movies, music etc.

Still confused about what the other partition types represent, what they'll be used for and how much space I should allocate them (ie: /usr, /var, /tmp and more recently /boot !!??).

--------

I've read some more and it seems that I can only have 4 primary partitions: NTFS (for windows), root, swap and home. Should I just stick with these?

'/usr' is just one location where you can install applications, and '/var' is much the same.  '/tmp' is a temporary folder that is used by the system as needed. '/boot' is where Grub and other boot-essential application/libraries wind up.  All of these are build off of '/' and you do not need to create separate mount-points or partitions for them.  

The only three 'nix partitions that you ever really need to worry about are '/', '/home', and 'swap'.  Create those and you should be good to go.

Now, as for sizing, I recommend the following:
1) approximately 50-80 GB for '/'
2) 4 to 8 GB for 'swap'
3) the remainder of your free space for '/home'

What you'll see on your disk in the partition editor is something like this:
sda1 - Windows - NTFS (or FAT32)
sda2 - / - ext3
sda3 - /home - ext3 (or FAT32)
sda4 - swap - swap

If you want Windows to be able to read anything that you have in '/home', you're going to have to format that partition with FAT32 - Windows will not read ext3 (or ext2, or xfs, or any other 'nix filesystem).

Like I said before, you really don't need to worry about the rest of the folders - the OS will handle them quite nicely.

---

### Post by asintu on 2008-05-21
> **Lord Landis said:**
> '/usr' is just one location where you can install applications, and '/var' is much the same.  '/tmp' is a temporary folder that is used by the system as needed. '/boot' is where Grub and other boot-essential application/libraries wind up.  All of these are build off of '/' and you do not need to create separate mount-points or partitions for them.  

The only three 'nix partitions that you ever really need to worry about are '/', '/home', and 'swap'.  Create those and you should be good to go.

Now, as for sizing, I recommend the following:
1) approximately 50-80 GB for '/'
2) 4 to 8 GB for 'swap'
3) the remainder of your free space for '/home'

What you'll see on your disk in the partition editor is something like this:
sda1 - Windows - NTFS (or FAT32)
sda2 - / - ext3
sda3 - /home - ext3 (or FAT32)
sda4 - swap - swap

If you want Windows to be able to read anything that you have in '/home', you're going to have to format that partition with FAT32 - Windows will not read ext3 (or ext2, or xfs, or any other 'nix filesystem).

Like I said before, you really don't need to worry about the rest of the folders - the OS will handle them quite nicely.

Sounds good..I'll split the partitions as per your recommendation.

Two more questions:

1). Does the order of the partitions matter?
2). I've heard that if the /home partition is ext3 (which i think is the most recommended these days for a common partition) windows will still be able to access it with some extra drivers or something installed. Is it true?

---

### Post by zvacet on 2008-05-21
Put them in thi order root home swap.For partition size **nicedude** give you good advice.I will format them all as ext3 (exept swap of cource).If you want to be able to read/write from Windows t oUbuntu then install [this]("http://www.fs-driver.org/") in your Windows.

---

### Post by asintu on 2008-05-21
> **zvacet said:**
> Put them in thi order root home swap.For partition size **nicedude** give you good advice.I will format them all as ext3 (exept swap of cource).If you want to be able to read/write from Windows t oUbuntu then install [this]("http://www.fs-driver.org/") in your Windows.

sweet, thanx.
So which partition would the programs/applications that i install for ubuntu be on? The root partition?
Will the root partition include the "Program Files" equivalent and will the /home partition include the "My documents and Settings" equivalent?

---

### Post by asintu on 2008-05-21
> **zvacet said:**
> Put them in thi order root home swap.For partition size **nicedude** give you good advice.I will format them all as ext3 (exept swap of cource)

from what i see here: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
the order they do it in is NTFS, home, root, swap...i'm confused, which will give better performance benefits? home before root or the other way around?

---

### Post by Lord Landis on 2008-05-21
It's better to set '/' before '/home', though the reasons why are largely irrelevant anymore.  Suffice to say, it has a lot to do with physical placement on the disk.

To answer your other question, '/var' and '/usr' serve the same general function as Program Files (occasionally the '/opt' directory as well).  Anything you install using Synaptic or apt-get will end up there.  '/' itself is pretty much the same as saying C:.

'/home' then becomes the equivalent of Documents and Settings with several hidden subdirectories where program-specific information is held.

The rest of the directories are things that are good to learn about, but you most likely won't need to worry about their contents for a while.  '/etc', for example, has a large number of system configuration files in it.  This is the sort of thing that can seriously bork your system if you make a mistake.  So the rule is 'look but don't touch' for anything except '/home' until you're more comfortable with the OS.

---

### Post by louieb on 2008-05-21
> **asintu said:**
> ...confused about ... /usr, /var, /tmp and  /boot...

As a general rule a production server will have separate partitions for different parts of the  OS. For a desktop install having / (root) and /swap is alright. Thats how Ubuntu will install itself by default. 

I use 4 partitions / (root), /home, /media/data and swap. Sometimes I'll add a 5th partition for testing another OS or the next Ubuntu version. 

As for the order the partitions are in  its not going to make any noticeable difference.

---

