---
title: "Whats the best partition setup?"
date: 2006-08-17
forum: Installation &amp; Upgrades
---

### Post by bobleny on 2006-08-17
I just purshaced a 250GB HDD specificly for Ubuntu and wasnt sure what the best partition for it would be? I want to get as much user usable space as possible but also want to be able to do updates with out loosing any data, like go from dapper drake to edgy. I also want to be able to maybe later install Gentoo over Ubuntu, again with out looseing my personal data.

So what do you recomend?

---

### Post by hecato on 2006-08-17
I personally Setup a master partition for GRUB (tought dont know if is the best way)... perhaps a copy of that partition would be nice... (Im thinking now in a second master partition mirror).


Anyway, after that the rest I do a extended partition and thereI put swap
, /, /home and I let some free space for downloads and such things, in fact I normally only have the data of the programms in /home, my actual files, projects, Downloads and other things are outside.... in a new partition of the free space.

In that way, you will keep your data files outside of any Linux "contract" /home/user (dont know how is called) and there only exist the data of the programms... and some other little things that I pass over or I need to take/access them at some clicks.



This is not the best solution, but can be a start... at less is what I use, but Im not sure about how to handle different kernels and setups without oerwrite the first partition... :D.

---

### Post by bobleny on 2006-08-17
Thanks. Any other ways to do it?

Oh, and what is the recomended way to do it?

---

### Post by bobleny on 2006-08-17
What about 10gigs for "/".
1gig for "swap".
And the rest for "/home".

I know that will worl for Ubuntu, but will it work for gentoo? I looked online but can't find anything.

I plan to play with Ubuntu and get used to linux and then try gentoo a little latter.

---

### Post by bobleny on 2006-08-17
And what about a "/boot"?

I've herd a /boot is a good thing to have, but really, I have no Idea. Thats why i'm asking, but it's starting to seem as though no one knows..... :confused: :x

---

### Post by VirtuAlex on 2006-08-18
For some reasons on certain machines it is required that /boot would be on lower cylinders of the drive. The easiest way to ensure this is to make small separate partition for it. Boot will hold all your kernels and grub. I would make it somethin half a gig.

---

### Post by bobleny on 2006-08-18
Thanks for the reply!
So, something like this would be ideal, you think?
/boot    512MB  Primary  Ext3
    /     10GB  Logical  Ext3
 swap      1GB  Logical  swap
/home     10GB  Logical  Ext3
 /usr      *GB  Logical  Ext3

That seems like it would be the best way to do it.
I added the "/usr" because I have read that it "/home" contains the setting and data of all users on the machine as well as the programs that are installed with Ubuntu, or Gentoo, or ect... Have I read right? So then wouldn't "/usr" be a good idea to have if I switch to Gentoo? This way all setting and user data (though I'm the only user) from Ubuntu will be over written?

Should "/home" and "/usr" have 10GB? Is that too much or too little?

---

### Post by VirtuAlex on 2006-08-18
I would make /boot Ext2, it does not really need journaling.
/usr will hold all installed programs. It is roughly like "Program Files" folder in the other OS. It is currently filled around 5G on my machine. So I think 10G is enough for regular user. If you plan to install and keep alot of software probably 20G will do. It all depends. And home you can think of as "My Documents" It will hold all your personal data. On my machine Pictures folder alone is more than 10G, and if you plan to edit videos you need plenty of space in your /home. You can judge for yourself how much space for your data you need.

Keep in mind that you do not have to delete ubuntu to try something else. Linuxes can coexist. They maybe could even share some partitions, at least /swap for sure. In any way you can resize, move around, and duplicate partitions easily with gui interfaces like gparted. Didn't like one os? No problem. Delete it's partitions and add freed space to wherever you need it. Want extra separate partition for some directory? Make it, mount it, move the data, edit fstab, and remount. So stop worrying, you can figure out your ideal setup later.

---

### Post by kbm on 2006-08-18
I go with two / partitions, one /home, and one swap.  This allows me to keep not only my home during an update, but the old OS (just incase).  When I do an upgrade, I just install it to the older (and by that time largely unused) / partition.  Both boots can share the swap as well.  I also have other mount points that I keep things on (one for music, one for photos, etc) - makes backing up and moving around when size needs change easier.  I also find that having the old OS around can help me out if I miss a config step (mount the old OS and start rooting around in etc).  I used to use the boot partition, but never ended up with a need for it after I switched from LILO to GRUB (better ability to boot off any partition) so I don't create one anymore.

---

### Post by wpshooter on 2006-08-18
I would do:

/root - 25gb ext3 - should give your plenty of room updates, etc.
/swap - 2gb - swap - probably most wasted, but what the hey.
/home - remainder ext3

The suggestion above for two(2) /root paritions is not a bad idea in theory, but I doubt that you would ever use the second one.

---

### Post by bobleny on 2006-08-18
> **VirtuAlex said:**
> I would make /boot Ext2, it does not really need journaling.
/usr will hold all installed programs. It is roughly like "Program Files" folder in the other OS. It is currently filled around 5G on my machine. So I think 10G is enough for regular user. If you plan to install and keep alot of software probably 20G will do. It all depends. And home you can think of as "My Documents" It will hold all your personal data. On my machine Pictures folder alone is more than 10G, and if you plan to edit videos you need plenty of space in your /home. You can judge for yourself how much space for your data you need.

Keep in mind that you do not have to delete ubuntu to try something else. Linuxes can coexist. They maybe could even share some partitions, at least /swap for sure. In any way you can resize, move around, and duplicate partitions easily with gui interfaces like gparted. Didn't like one os? No problem. Delete it's partitions and add freed space to wherever you need it. Want extra separate partition for some directory? Make it, mount it, move the data, edit fstab, and remount. So stop worrying, you can figure out your ideal setup later.

How big is the avrage linux software? I am used to windows beffy programes. And I might run WINE so that I can run all of my games. So then will I need a lot of room for "/usr", if I plan to run a bunch of games?

How much space do you think I should allocate for "/", which is the same thing as "/root" right?

And I have decided to partition my HDD to house both Ubuntu and Gentoo.

---

### Post by hecato on 2006-08-18
> 
How much space do you think I should allocate for "/", which is the same thing as "/root" right?


No **/root** is where GRUB and irc kernels will be saved.

**/** is a mount point that indicate where to put the rest of the files.... if in them you separate als the mount point **/usr**, then you will let all the other mount points to be saved where you put **/** partition.

---

### Post by bobleny on 2006-08-18
OH, OK, I get it! [http://www.pathname.com/fhs/2.2/index](http://www.pathname.com/fhs/2.2/index).

> The root account's home directory may be determined by developer or local preference, but this is the recommended default location.[footnote 14]

[14] If the home directory of the root account is not stored on the root partition it will be necessary to make certain it will default to / if it can not be located.

We recommend against using the root account for tasks that can be performed as an unprivileged user, and that it be used solely for system administration. For this reason, we recommend that subdirectories for mail and other applications not appear in the root account's home directory, and that mail for administration roles such as root, postmaster, and webmaster be forwarded to an appropriate user. 

So /root is like the admin account. So, If I don't make it its own partition, will I always be logged into it?

---

### Post by mdelorme on 2006-08-18
Wine does not play all windows games.  If you are absolutely set on being able to play all of your windows games, you should look into dualbooting between linux (for everyday use) and windows (for playing games).

As far as **/** and **/root** go, /root is the home directory for the user "root".  It is not located in /home/root, it is merely /root.  do not worry about /root since (being a ubuntu user) you will most likely not be logging in as root for day to day activities.

One option that you may consider if you are unsure of how much space you want to allocate to each partition is to use LVM2 (Logical Volume Manager).  Although you can resize linux volumes, for the most part you cannot move them (and those you can, you cannot do easily).  This may sound trivial, however keep in mind that shrinking/growing a partition by moving the begining of it actually requires moving the partition.

LVM uses logical volumes that (when combined with the appropriate file system) can be easily resized.

My partition layout (releavnt to ubuntu) is as follows:

/boot 120M ext3
/     4G   reiserfs   (this is already too big for me and a waste of space - currently < 300M used)
logical volumes - everything else

reiserfs is a good choice for your logical volumes because it's easily resizable (it even supports expanding without having to unount!)

to start off, try allocating about 6G-8G for /usr.  if it gets too full, just expand the logical volume

/var and /opt are also good to have as their own logical volumes.

and do not make your /boot partition half a gig... that is merely wasted space unless you plan on having MANY different versions of kernels for each distro you're using.

hope this helps.  cheers.

---

### Post by bobleny on 2006-08-18
Thanks.

This is the what I posted at Gentoo's forums. It has every question in it so I want to put it here too.

I just purchased a 250GB HDD specifically for Linux to go along with my first HDD, Windows Crappy XP, and wasn't sure what the best partition for it would be?

I want to set this drive up so I can put Gentoo and Ubuntu on it. So, this is what I was thinking would be the best way.

I don't want to partition it if this is wrong. Is something like this a good ideal?

```
/boot   20MB   Primary   Ext2   Unmounted
    /    5GB   Logical   Ext3     Mounted
/boot   20MB   Primary   Ext2   Unmounted
    /    5GB   Logical   Ext3     Mounted
 swap    1GB   Logical   swap     Mounted
 /usr   25GB   Logical   Ext3     Mounted
/home    *GB   Logical   Ext3     Mounted
```

Explained:
* Gentoo and Ubuntu will need there own “/boot” partition, I think...?

* They will also need there own “/” Partition, I'm pretty sure...?

* The swap should be sharable, especially considering you can only run one OS at a time, again though, I'm not suer...?

* If, I've read right, then “/usr” contains all of my programs, similar to Windows' program files. So, then I want to share this between the two of them, but I have no clue how big the average program is for Linux...?

* If again, I've read right, "/home" contains the setting and data of all users on the machine. So, I will want to share “/home” so I don't have to do everything twice, I think...?


I want to use GRUB to select the OS to boot into, but does it matter which HDD and partition I place it under?

So, for my biggest question, what do you think?
Do I have the Primary and logical in the places?
Do I have the right partitions mounted and unmounted?
Can I share “swap”, “/home” and “/usr” between Gentoo and Ubuntu?
Am I using the correct file formate (e.g. Ext2 or Ext3)?
Do I have too much or too little space allocated to each partition?
Will Gentoo or Ubuntu recognize which partitions are theirs?
If I install updates to either Gentoo or Ubuntu, will It know which partitions to update?

Thanks a lot!

P.S. I would greatly appreciate a long response with lots of answers. :D

---

### Post by LadyDoor on 2006-08-18
> How much space do you think I should allocate for "/", which is the same thing as "/root" right?

Point of interest...actually, /root is user **root**'s home directory--it gets its own because it's the magic-super-user. **/boot** is where grub and whatnot go. **/**, however, just happens to be **pronounced** either as "slash" or "root."

> wasn't sure what the best partition for it would be?
That depends what you want, honestly.

Be sure to use an official windows tool to do any resising on an NTFS partition.

> Can I share “swap”, “/home” and “/usr” between Gentoo and Ubuntu?

You can share /home and swap. When setting up the OS's, just tell them to use the given partitions as what you want them to be--or edit your /etc/fstab so that it'll have a line telling it where to mount each one.

As to sharing **/usr** between to linux os's, I honestly don't know how to do that--each program you install in ubuntu has been packaged specifically for use in ubuntu, and each ebuild for gentoo is gentoo-optimized, so I don't know what to tell you there...I would advise you to make, perhaps, two **/** partitions and no **/usr** partitions. Make each one, say, 17.5 GB (half of the 35 GB that would otherwise be taken up by the two 5 GB **/** partitions and the one **/usr** partition.

1 GB of swap should be more than enough; however, you might go with a 50 MB **/boot** partition, just to give yourself some breathing room.

Make home however big you see fit.

You *might* make a /opt partition if you're a gamer or something.

You only ever need one /boot partition.

> I want to use GRUB to select the OS to boot into, but does it matter which HDD and partition I place it under?

I don't know about HDD, but it should be in the very first partition--it'll be the first thing loaded at boot.

> Am I using the correct file formate (e.g. Ext2 or Ext3)?
That's just your preference.

> Will Gentoo or Ubuntu recognize which partitions are theirs?
Yup! In **/boot/grub/menu.lst**, there is a line in the configuration for each kernel telling it what partition to use as **/**. As for the rest, they're shared, right?

> If I install updates to either Gentoo or Ubuntu, will It know which partitions to update?

Do you mean if you upgrade the OS, or if you upgrade a program? The two **/** drives should not be loaded at the same time, so whatever you do should just effect whichever one you are *currently* running. Since my advice is to not share a **/usr** drive, you shouldn't have to worry about that. They will be completely separate operating systems that happen to share a /home drive and swap space.

Oh, and if you want to be able to read /home in your windows system, be sure to make the filesystem FAT.

---

### Post by VirtuAlex on 2006-08-18
Honestly, if you so much concerned about perfection, you can bug [gentoo forums]("http://forums.gentoo.org/") ;) on this. Seriously, they're more "geeky" and they have [nice faq]("http://forums.gentoo.org/viewforum-f-40.html"). For example here is what they tell you about boot partition: [Is a /boot partition needed?]("http://forums.gentoo.org/viewtopic-t-220302.html")

---

### Post by bobleny on 2006-08-19
> **VirtuAlex said:**
> Honestly, if you so much concerned about perfection, you can bug [gentoo forums]("http://forums.gentoo.org/") ;) on this. Seriously, they're more "geeky" and they have [nice faq]("http://forums.gentoo.org/viewforum-f-40.html"). For example here is what they tell you about boot partition: [Is a /boot partition needed?]("http://forums.gentoo.org/viewtopic-t-220302.html")

Im not. I am. I know.

And thanks for the responce, LadyDoor.

---

### Post by VirtuAlex on 2006-08-19
> **bobleny said:**
> Im not. I am. I know.
Just try to overdo it not. Partitioning is crucial for server, when all access you would have later is ssh. On desctop you can always fix it in 20 minutes if you run into troubles. So if your partitioning decision takes more than 20 minutes, you're wasting your time accounting for troubles you may never encounter. When I started with linux I dumped everything into root. When I installed new distro later, I resized it and moved /home to a separate partition, so I can share. It is all so flexible, you'd be amazed.
Good luck! :)
P.S. And since LadyDoor mentioned it, I resized my windows partition with gparted and had no troubles, so I do not know if there are real reasons to use native windows tools.

---

### Post by bobleny on 2006-08-21
As a quick note, according to the Gentoos only /home, /boot and /swap can be shared between linux distributions. So laydoor got it right.

---

### Post by kaptainlange on 2006-08-21
I was concerned that nobody gave you a reason why a /boot partition is a good idea.  The /boot partition is where your kernel and more importantly your GRUB config files are.  If you ever format your / parition, and /boot is not it's own partition, you've just clobbered your GRUB config file which will make your computer unbootable via grub.

This isn't a major problem if you have a little experience with such things, but for newer users it's disconcerting to see that GRUB error upon reboot.  So anyways, if you have more than one OS installed on a computer almost definately keep that /boot parition seperate so as to be able to boot into those other os'es once you format the other.

---

### Post by akshaysrinivasan on 2006-08-21
Well I've tried setting up a master partition for /boot ,but i've so far seen no advantages.infact whenever i meddle around with the partitions the grub boots saying some error.Besides when you install any flavour of linux ,they install grub all over again by default.

---

