---
title: "move home folder to a NTFS file system?"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by pearldrums on 2009-11-25
hey, does anyone know if you can map your home directory to a NTFS file system? I've looked at the psychocats guide on moving a home folder but here is what i'm trying to do. I have windows and Xubuntu installed on a 120gb HD, I have a partitition for windows, a partition for Xubuntu, and a partition for data. For windows to be able to access it, I need the data partition to be NTFS. I want to move my Ubuntu home folder onto that partition as well... I know I'm asking a lot, but Im kind of new and was hoping someone could walk me through this process step by step just because of the danger associated with it.

---

### Post by audiomick on 2009-11-25
No you can't.
The system uses /home to store all your config stuff as well as your files. You can't put it on an NTFS.

What you can do is change the default storage path for most programs so that they automatically go to a folder on the ntfs partition instead of the home folder. I think this is what you wanted, so that your date is available in Ubuntu and in Windows

---

### Post by raymondh on 2009-11-25
as audiomick said ....

create a 3rd partition (if able) in NTFS format to be used as a data storage partition.  You can map or you can drag your files into it.  Both OS' can then access/read/write to it.

Regards,

---

### Post by coffeecat on 2009-11-25
So long as your NTFS partition is mounted on bootup with a line in fstab, you could have symlinks in your home folder pointing to folders in your NTFS partition. For example a symlink named 'Music' pointing to Music in the NTFS partition, and the same for whatever else you want.

---

### Post by pearldrums on 2009-11-25
So if I did that would it effectively change the data portion of my Home directory (I.E. if I opened up file manager would it display those folder in home)? I still would like to be backing up my config files by moving my home folder because I do plan on changing my OS back to 9.04.  How big would you suggest I make my home partition if I plan on storing data elsewhere?

---

### Post by raymondh on 2009-11-25
> **pearldrums said:**
> How big would you suggest I make my home partition if I plan on storing data elsewhere?

My root is 15GB.  /home is 30GB and I think that is generous/comfortable.

Regards,

---

### Post by louieb on 2009-11-25
> **pearldrums said:**
> How big would you suggest I make my home partition if I plan on storing data elsewhere?

I use a 5GB home - have 2 users.  Current use is about 250MB per user.  Firefox and Thunderbird and the big space users. If you can move their profiles off too you can easily get by with about .5GB per user.

---

### Post by coffeecat on 2009-11-26
> **pearldrums said:**
>  I still would like to be backing up my config files by moving my home folder because I do plan on changing my OS back to 9.04.  How big would you suggest I make my home partition if I plan on storing data elsewhere?

Do not move /home config files to a NTFS partition. Some of them need special permissions which NTFS does not support. If you want the whole of /home in a separate partition it needs to be ext3 or ext4. But if you only want to store data files - documents, music, videos, etc - then NTFS is OK either symlinked to /home as I suggested or accessed through the Places menu.

---

### Post by Mr_B on 2009-11-26
You said you wanted the windows OS to access your data. So instead of moving your data to a NTFS partition, why don't you access the data directly on your linux EXT3 partition from windows using either [EXT2FSD]("http://www.ext2fsd.com/") or [EXT2IFS]("http://www.fs-driver.org/"). I use the latter on the rare occasions I have to boot up in Windows 7.

---

### Post by coffeecat on 2009-11-26
> **Mr_B said:**
> You said you wanted the windows OS to access your data. So instead of moving your data to a NTFS partition, why don't you access the data directly on your linux EXT3 partition from windows using either [EXT2FSD]("http://www.ext2fsd.com/") or [EXT2IFS]("http://www.fs-driver.org/"). I use the latter on the rare occasions I have to boot up in Windows 7.

There could be big problems with both of those. For starters, the OP is using Karmic so their Ubuntu root partition is probably ext4 and not ext3. The FAQ from your first link says:

> Open source ext2/ext3 file system driver for Windows (NT/2K/XP/VISTA, X86/AMD64)Until that project says categorically that the driver supports ext4, I personally wouldn't use it. Even then I wouldn't use it.

The second link also only mentions ext2 and ext3. In addition, the release notes say:

> **Large inodes**                 The current version of Ext2 IFS only mounts volumes with an inode size of 128 like old Linux kernels have.             
              Some very new Linux distributions create an Ext3 file systems with inodes of 256 bytes. Ext2 IFS 1.11 is not able to access them. 
              Currently there is only one workaround: Please back up the files and create the Ext3 file system again. Give the mkfs.ext3 tool the -I 128 switch. Finally, restore all files with the backup.
Ubuntu has defaulted to 256-byte inodes since Jaunty at least, possibly Intrepid. Ext2IFS simply doesn't work on 256-byte inode filesystems. This issue crops up occasionally in the forums here.

---

### Post by pearldrums on 2009-11-26
> **coffeecat said:**
> Do not move /home config files to a NTFS partition. Some of them need special permissions which NTFS does not support. If you want the whole of /home in a separate partition it needs to be ext3 or ext4. But if you only want to store data files - documents, music, videos, etc - then NTFS is OK either symlinked to /home as I suggested or accessed through the Places menu.

sorry if I was a little confusing there. What I'm thinking is that I could do both. Create a partition for my home folder in ext3 format, but only a small partition meant to hold config and settings files, not large data files. Then symlink to a NTFS partition for all my data. Would that be a plausible solution? I'm going to try doing the symlink right now because I'm really unfamiliar with how its going to change everything.

---

### Post by pearldrums on 2009-11-26
Alright, I think I had a basic non-understanding of what a symlink was. It is basically the equivalent of a windows shortcut, right?

> **raymondh said:**
> as audiomick said ....

create a 3rd partition (if able) in NTFS format to be used as a data storage partition.  You can map or you can drag your files into it.  Both OS' can then access/read/write to it.

Regards,

When you say I can "map" my files into it what exactly do you mean. I guess I'm kind of assuming that there is something in the system that says "this file is your home music file" and "this file is your home videos file" that programs check when they are operating and that I would be changing what files they are pointing to. But maybe I'm just making a bad assumption, is it as simple creating symlink files and moving all my data into them then deleting the original files?

Thanks for all your help everyone.

---

### Post by audiomick on 2009-11-26
I assume "map" means what I meant; tell the programmes that you use to store by default into your data partition.
In open office, for instance,
Extras> options
In the first section under "paths"
Most Linux programs will let you change this somewhere or other. Some Windows ones I know of don't.


If you can't find the option, just get into the habit of doing "save as" the first time you save a new file, and tell it where you want it to go.

I am not aware of it being a system variable. As far as I know, the only thing  that the system as such knows and cares about are the things that it saves itself, and you want those to stay where they are.

---

### Post by coffeecat on 2009-11-26
> **pearldrums said:**
> Alright, I think I had a basic non-understanding of what a symlink was. It is basically the equivalent of a windows shortcut, right?

Yup! :wink:

And you don't even have to use the terminal. Try this once you've got your NTFS partition up and running.

Go to the NTFS partition and create a folder - say "Music". Right-click on this and choose "Make Link". A new symlink folder will appear called "Link to Music". Of course, that's no use yet because it's in the wrong place, so open your home folder and simply drag and drop the "Link to Music" across. A new link folder will appear in /home which, if you double-click on it, will open and let you access the files in "Music" in your NTFS partition. You can rename it to "Music" if you want and you can now delete the original symlink which is now surplus to requirement. Repeat as required for "Videos", whatever you want.

But if you do want to use the terminal, it's much quicker. Assuming your NTFS partition is mounted on /media/data, make sure you are in your home folder and...

```
mkdir /media/data/Music
ln -s /media/data/Music Music
```

---

### Post by presence1960 on 2009-11-26
> **coffeecat said:**
> There could be big problems with both of those. For starters, the OP is using Karmic so their Ubuntu root partition is probably ext4 and not ext3. The FAQ from your first link says:

Until that project says categorically that the driver supports ext4, I personally wouldn't use it. Even then I wouldn't use it.

The second link also only mentions ext2 and ext3. In addition, the release notes say:


Ubuntu has defaulted to 256-byte inodes since Jaunty at least, possibly Intrepid. Ext2IFS simply doesn't work on 256-byte inode filesystems. This issue crops up occasionally in the forums here.

I would not use that because of the inherent vulnerablity of the windows system to infection, malware, attacks, etc. if windows would be compromised then your linux files are at risk also. All my personal files are on linux, none are on windows.

---

### Post by pearldrums on 2009-11-30
Well, I got it all worked out the way I wanted. I'm still learning how the whole file structure of Linux/Ubuntu works (and... everything else). I ended up not creating a partition for the config settings and just using symlinks to the windows partition. I had to do a little bit of work to restore the settings I wanted, but it wasn't that bad, and it helps me learn more. I guess you guys (and girls) all know what its like migrating to a new system. Its neat that the symlinks point to another file, but you browse them like the contents are in the main file of the symlink.

Coffeecat. I've noticed you've had several replies to several of my topics. You've turned private messages off, but I just wanted to say thank you. You've obviously made it a mission to help other people, and I know that people like you are sure to say "aw don't mention it." But really, you know how basic the things are that I'm doing, and it doesn't take the smarts an expert to help me out. However, sometimes it takes the intelligence of an expert to recognize just how helpful he or she can be. Everyone has been very helpful, but you have been especially so. Thanks for bearing with me.

---

### Post by coffeecat on 2009-11-30
> **pearldrums said:**
> Coffeecat. I've noticed you've had several replies to several of my topics. You've turned private messages off, but I just wanted to say thank you. You've obviously made it a mission to help other people, and I know that people like you are sure to say "aw don't mention it." But really, you know how basic the things are that I'm doing, and it doesn't take the smarts an expert to help me out. However, sometimes it takes the intelligence of an expert to recognize just how helpful he or she can be. Everyone has been very helpful, but you have been especially so. Thanks for bearing with me.

Actually, I do appreciate the thanks, and thank you for saying that.

I've just remembered that there is a potential issue with the way the installer sets up NTFS mounts, but if you've created your own fstab mount line, this may not affect you. If you want to post your fstab NTFS partition line, I could check this for you.

The issue is that the date/time gets changed to current if you copy a file from your ext3/4 partition to the NTFS partition. I'm not sure whether this will affect writing into a symlink - probably not - because I routinely use mount options that avoid this problem. Anyway - over to you.

---

### Post by pearldrums on 2009-11-30
I did set it up with NTFS config tool as you can see. How does it look? Thanks again.

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=d344bec5-2aee-47cf-8e08-81face267d1d / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=45d32aaf-d817-44bf-92c2-2a41e3c467cd none swap sw 0 0
/dev/sda3 /media/Shin-Stabber ntfs-3g defaults,locale=en_US.UTF-8 0 0
```

---

### Post by coffeecat on 2009-12-01
Hi. Sorry for delay. Been busy.

Hopefully, that will be OK. If you specify a mountpoint in the 'manual' option at the partitioning stage of the installer, you get something similar to:

```
UUID=3C034B17236A5E09 /media/Data     ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
```(It doesn't matter whether you have 'ntfs' or 'ntfs-3g' in the third field.) You get the problem I described with those options. It's possibly the 'gid=46' bit that's unmasking a bug somehow. I routinely simplify that line to:

```
UUID=3C034B17236A5E09 /media/Data     ntfs    defaults 0       0
```... which works just fine for me. Or, at least, I haven't had a problem with it yet. Simply try a drag and drop copy from your home partition to somewhere in the ntfs partition. If the date doesn't change, you're OK - at least for this issue.

---

