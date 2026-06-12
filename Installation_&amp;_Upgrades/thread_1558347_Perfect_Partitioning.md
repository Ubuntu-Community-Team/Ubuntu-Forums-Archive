---
title: "Perfect Partitioning"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by daksai3 on 2010-08-22
I have a computer pre-installed with Windows 7 Ultimate. I want to install Ubuntu 10.04, and use a shared partition for my documents, pictures, videos etc.

[B]I know that you can only have 4 primary partitions.
Right now I have 2:[/B]
1. Windows 7 boot and system boot C:
2. Recovery disk D:

[B]So now I only have 2 primary partition spaces left.
They will be used for:[/B]

1. Ubuntu 10.04
*How much space is needed for the OS?*
2. Shared partition containing windows 7 program files and documents and the Ubuntu home directory.
*Can the shared partition be an extended/ logical partition?*
*When i download and install programs does it take up space from the OS partition or just from the shared partition?*


**Additional questions:**
1. Is this a possible partitioning scheme?
*Is there a better scheme?*
2. Which file system should I use for the shared partition? I want something that is readable and writable by both operating systems.
3. What is the required space for Windows 7 Ultimate 64 bit and Ubuntu 10.04 64 bit? 
4. What is that space used for, and is it possible to use only 1gb for each OS and use the shared partition to complete the rest of the requirements. 

Links will be appreciated but pls only post links that are recent as in written in 2010. But pls, if you can, help me urself instead of just posting other guides. 

I'm a newb but i can learn. :lolflag:

---

### Post by sikander3786 on 2010-08-22
> **daksai3 said:**
> I have a computer pre-installed with Windows 7 Ultimate. I want to install Ubuntu 10.04, and use a shared partition for my documents, pictures, videos etc.

[B]I know that you can only have 4 primary partitions.
Right now I have 2:[/B]
1. Windows 7 boot and system boot C:
2. Recovery disk D:

[B]So now I only have 2 primary partition spaces left.
They will be used for:[/B]

1. Ubuntu 10.04
*How much space is needed for the OS?*

I think you'll be ok with 10GB of spce.

> 2. Shared partition containing windows 7 program files and documents and the Ubuntu home directory.
*Can the shared partition be an extended/ logical partition?*

You will not be able to use an NTFS drive as your home partition. The shared partition ca be extended/ logical, it will be NTFS or can be FAT but used for sharing stuff between Windows and Ubuntu, not containing the home folder.

> 
*When i download and install programs does it take up space from the OS partition or just from the shared partition?*

That will take up the space in OS partition. Just the configuration for a few apps going in to the home partition.

> **Additional questions:**
1. Is this a possible partitioning scheme?
*Is there a better scheme?*
2. Which file system should I use for the shared partition? I want something that is readable and writable by both operating systems.
3. What is the required space for Windows 7 Ultimate 64 bit and Ubuntu 10.04 64 bit? 
4. What is that space used for, and is it possible to use only 1gb for each OS and use the shared partition to complete the rest of the requirements. 

Links will be appreciated but pls only post links that are recent as in written in 2010. But pls, if you can, help me urself instead of just posting other guides. 

I'm a newb but i can learn. :lolflag:

The best partition map will be to free up some space say 10GB for Ubuntu, it will contain the base install as well the home directory. And another shared partition whatever size you want should be NTFS or can be FAT, Ubuntu can read and write to both of them without any problems. That will not be a problem.

Let the boot loader install where it wants to be by default so it detects Windows 7 and adds for dual booting.

Regards.

---

### Post by jpaugh64 on 2010-08-22
> **daksai3 said:**
> *Is there a better scheme?*

I don't know how Windows would behave if it had to use multiple partitions; also, it seems far easier to make symlinks (under Linux) to all of the pertinent folders/files that reside on Windows. 

This scheme integrates well with both operating systems (nothing has to be in an unusual place); it has the least setup/use hassle. Also, there is nothing to gain by choosing any certain filesystem for an intermediary partition: there are few filesystems that Windows can understand. You can't really get a better solution than that, in my opinion.

If you're brave, you might even replace some of the "Default" folders in your Ubuntu home folder (e.g. Documents, Pictures, Music) with symlinks that point to the corresponding folders on your Windows account.

---

### Post by daksai3 on 2010-08-22
> You will not be able to use an NTFS drive as your home partition. The shared partition ca be extended/ logical, it will be NTFS or can be FAT but used for sharing stuff between Windows and Ubuntu, not containing the home folder.


will ubuntu be able to find the home directory in another partition? and im sure i can put the home directory in a ntfs partition as it will have no trouble reading and writing to it if i use ntfs- 3g. if i can place the home directory in a ntfs partition then i should be able to place it in a shared partition which windows 7 can read and write to.

> That will take up the space in OS partition. Just the configuration for a few apps going in to the home partition.
so say if i download ccleaner on ubuntu, will it take up the 2.7 megabytes of space from the home directory or something else?

im thinking that it takes up space from the home directory since the home directory is like windows "program files" with space for documents, pics, videos etc, and in windows the space is taken from the c drive which holds the program files. 


> The best partition map will be to free up some space say 10GB for Ubuntu, it will contain the base install as well the home directory. And another shared partition whatever size you want should be NTFS or can be FAT, Ubuntu can read and write to both of them without any problems. That will not be a problem.

Let the boot loader install where it wants to be by default so it detects Windows 7 and adds for dual booting.

im thinking of installing ubuntu with 10 gb in ext4 and placing the home directory in a shared partition which will be in ntfs which ubuntu can read with ext4.

---

### Post by daksai3 on 2010-08-22
> I don't know how Windows would behave if it had to use multiple partitions; also, it seems far easier to make symlinks (under Linux) to all of the pertinent folders/files that reside on Windows. 


what if i make a shared partition with all my documenrs from both os's and also include my windows 7 program files and ubuntu home directory. then i would use symlinks to connect everything in the shared partition to the windows 7 and ubuntu partitions. this way if i were to go to the music folder in my windows 7 documents it would redirect me to the corresponding folder in the shared partition. and another bonus is that if i update or upgrade my os installations they would never affect the shared partitions. so i could do a clean install with ubuntu and never really have to backup everything. every damn 6 months.

---

### Post by sikander3786 on 2010-08-22
You are right. Both Ubuntu and Windows can read/write NTFS, but in case of /home, NTFS is not the choice because of the permissions issues. It doesn't support the permissions needed which ext does support.

I am sure the installed programs will use up space in the /root partition. Still it will be quite difficult and will take some time to fill up 10GB of space with software. 10GB will be more than enough if you store your documents and personal files on another partition.


[COLOR="Red"]**Edit:**[/COLOR] Almost all the software gets installed in /usr/bin/xxx.

---

### Post by daksai3 on 2010-08-22
Everything else seems to be sorted but here is are some
**New Questions:**

1. What file systems does Windows 7 support natively (not with 3rd part software?

2. What file systems does Ubuntu support?

3. What file systems have permission for the home directory?

> Edit: Almost all the software gets installed in /usr/bin/xxx.

is that in ubuntu? and if so, what do u mean? is it like the entire program or just the settings? is it like my ccleaner example where the entire thing is installed in windows 7 "program files"?

---

### Post by sikander3786 on 2010-08-22
1. Windows 7 natively supports NTFS.

2. Ubuntu can use ext2, ext3, ext4 or reiserfs as a file system. It has support for reading and writing NTFS and FAT, but doesn't use them as its native filesystems.

3. All the above mentioned except NTFS and FAT.

/usr/bin is the Program Files Folder of Ubuntu.

---

### Post by daksai3 on 2010-08-22
can windows 7 read and write ext/2/3/4 with any 3rd party software?

---

### Post by sikander3786 on 2010-08-22
Some poor support with [Ext2IFS For Windows]("http://www.fs-driver.org/").

---

### Post by daksai3 on 2010-08-22
I think i might have a solution, just a few things to clear up.

1. what are the folders on the home directory other than the documents, pictures, videos and other media things, that wouldnt work on another partition? in other words, which parts of the home directory dont work on a another partition?

2. what EXACTLY goes in the home directory?

3. when you make a symlink are u making a full copy of something or just altering the path of a file?

4. is it possible to have the original home directory in a different partition and have a symlinked one in the OS partition?

5. Can i periodically backup a copy of the home directory on the shared partition?

6. its only the config files that wont work from the NTFS file right?

---

### Post by daksai3 on 2010-08-22
> Some poor support with Ext2IFS For Windows.

no support for ext4

---

### Post by daksai3 on 2010-08-23
bump

---

### Post by mango42 on 2010-08-23
I've followed this thread just to see how it panned out and I'm wondering whether Win7 is not just making life more difficult for you?

Is there anything you do in Win7 that cannot be done in Ubuntu? I very much doubt it these days, so why not just dump it and do a clean Ubuntu install with a separate /home partition a la [http://ubuntuforums.org/showthread.php?p=9141619](http://ubuntuforums.org/showthread.php?p=9141619)

---

### Post by daksai3 on 2010-08-23
Well the biggest thing is that there are many programs that are only for windows and not linux users. Even if u do use wine, its not as good as the real deal. Then there are video games which the linux community lacks since most game developers dont both with linux. and u have to understand that open office is not even as good as office 2003 (i use 2007). 

basically windows has a good reason for being the most used operating system. 

windows 7 has less bugs, i mean seriously... almost everything in linux forums include something about compatibility issues. i like how linux is as a unix system and i would no doubt use it if it had more software developers that were at the level of windows developers. 

i hope that there will actually be a reason for why ubuntu is bettter after i install.

---

### Post by daksai3 on 2010-08-23
Ok i have moved this topic over to another thread becuz i feel that half the questions have been answered. this new thread is based on what u guys said and if u guys see a problem pls post on the thread.  

new thread (an extension really): 


[http://ubuntuforums.org/showthread.php?t=1559218](http://ubuntuforums.org/showthread.php?t=1559218)

---

