---
title: "Multi-drive / Multi-partition configuration help request"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by Subv3rse on 2013-02-07
Hi All!

Hoping someone could kindly lend a hand. I've finally made the switch from M$ to Ubuntu (Xubuntu flavour) and am looking for a bit of advice from a partitioning standpoint.

I built my rig a couple of years ago to the following specs: Core i5 Wolfdale, Asus P67 Sabertooth mobo, 8Gb RAM, nVidia GTX 670, 1x Crucial M4 128Gb SSD, 1x Samsung Spinpoint F3 1Tb, 1x WD 2Tb.

Yes, I'm a gamer :) I've also been playing around with Ubuntu (and about 8 other distros) since Saturday and I'm pretty much set on dual booting W8 alongside Xubuntu (For those games that Wine, aren't on Steam native yet, and for sites requiring Silverlight) Also, having Win8 installed acts as a great deterrent against moving back to Win.

Quick point to note, I have UEFI but not Sec UEFI. I have no problems with dual booting / multi installs etc, that's not the purpose of this post.

What I'd like to ask is if there's any way I can mimic the sort of setup I used to use in days gone by, which is to say my previous Win7 build had:

- Windows and Program Files installed on my C:\ (128Gb SSD, Default Win parition setup) 
- Steam, other games and music software all installed on my E:\ (1Tb Samsung, Single parition)
- Docs / music / movies / photos / System temporary files etc all catagorised into separate areas on my F:\ (2Tb WD, single partition)

Vet M$ users will recognise the attempt at culling fragmentation (not a problem with linux, i know), but keeping read times high between disks.

As such I'm looking to see if I can do something similar with my 'buntu install.

My goal would be something along the lines of a 100Gb NTFS Win8 install, post-installation resized from 128Gb, leaving the remaining 28 odd Gb space available for ext4 paritions, mainly Ubuntu's own system files, a /tmp mount and a /swap mount.

My 1Tb would be pure ext4 where my own apt-get install downloads and .deb / tar binaries would be installed to.

My 2Tb would be where my docs, music, photos, downloadables etc would sit (essentially my /home)

Now I've been hunting around and I can find very little on partitioning. It seems that most articles explain extreme basics, which is to say "this is how you would do it on a single drive" (Which Ubuntu by default blissfully ignores and sets everything up in 2 partitions anyway, one being swap), or they say "for anything else you need to know what you're doing". Fine, that's not a problem, but there's precious little documentation on "learning what to do". 

As far as I can tell, my traditional method for file organisation I don't think is going to work, so I'm looking for advice on the best way to set this thing up.

Caveats: 
- I don't really want to dedicate the SSD purely to Ubuntu, as it won't be enough going forward to install all the games. I'd also like to use that drive to dual-boot Win8, so space will be a premium. Still, if i can make use of the SSD for linux I'd like to.
- I "can" just install Win8 on the SSD, and Ubuntu on the 1Tb. Which is what I've been doing while testing for the past week. My 2Tb has been left unformatted during this time while testing everything out / reinstalling flavours. (Yeah, I did a total system nuke last friday), but again that won't let me take advantage of my SSD.
- I "could", I suppose, install Ubuntu to the SSD, mount the /home part to the 1Tb alone, and then install Win8 to the 2Tb (or vice versa), but I don't understand the linux file system enough to know if that would actually cause problems, or even if the /home folder is where programs are installed to.... Which is to say I don't know where programs "I" install are installed to in Ubuntu.

So, any guru's out there kindly able to advise by chance? :)

Thanks in advance!
Subv3rse

---

### Post by ahallubuntu on 2013-02-07
~

---

### Post by ajgreeny on 2013-02-07
I may be wrong about this, but I don't think you can choose where to install applications, ie, your games when they are installed in Ubuntu, unlike Windows, where if I remember correctly, you could choose to put installations into different disks or partitions.

If eventually you will not have enough space on the 128GB disk to take all your games installations, you are going to be limited to using a larger disk for the root partition (the system files, as you call them) as that is where all the files from installations of games and other applications go by default.

Wait for more answers before taking this as asbsolute gospel truth, as I believe there may be ways around it by using LVM, but my knowledge of using that is limited to zero.

---

### Post by Cheesemill on 2013-02-07
> **ajgreeny said:**
> I may be wrong about this, but I don't think you can choose where to install applications, ie, your games when they are installed in Ubuntu, unlike Windows, where if I remember correctly, you could choose to put installations into different disks or partitions.
The exception being Steam which actually stores all of its data in a users home directory.

If the majority of your Linux games are going to be downloaded using Steam then you will be OK with a smaller root partition.

---

### Post by oldfred on 2013-02-08
I do not do games and have multiple Ubuntu installs all in 25GB / (root) partitions. With my "new" 62GB SSD, I just made two / partitions. I have all my data on rotating drives and have folders in my data partitions that I mount with fstab and link the folders into my /home. I keep /home inside my /, but do not know if linking will work for your games or not.

       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
    
Also with larger hard drives this user has some I subscript to, but instead of Knoppix, I just have another Ubuntu install.
       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)

---

### Post by Subv3rse on 2013-02-08
Thanks for the advice all!

I was actually sitting on a GParted LiveCD when I wrote that; spent about 4hrs looking up various partitioning guidance and schemas and eventually came across this golden nugget: [https://help.ubuntu.com/12.04/installation-guide/i386/directory-tree.html](https://help.ubuntu.com/12.04/installation-guide/i386/directory-tree.html)

As stated before yes, I'm primarily looking to migrate to Ubuntu but as a gamer, so my requirements "may" have been a touch different to the average Ubuntu user. I say "may", because further research lead me to find out that Steam for Linux installs under ~/, which is a bonus. I had to research this bit because, stupidly, I forgot to check where it was on my previous build. Further I already know that Wine prefixes also install to ~/.

Finally, Linux partitioning is one of those beasts I found that looks incredibly complicated (and obviously, depending on requirements, can be) but actually isn't nearly as complex as it *looks* for simple setups if you have ample space.

Ultimately what I ended up doing was to mount as the following:

SDA (128Gb SSD)
 - 86 Gb mounted as /
 - 16 Gb mounted as Swap (Yes, I know that would be considered excessive, but again I'm dealing with Wine and Steam native, so *shrug*
 - The additional 25Gb is left over as un-partitioned. Again this is a little more than it needs to be, but I'm a fan of rounded numbers. Call it OCD :)

SDB (1Tb Spindle)
 - 1Tb mounted as /home

And that's it. Yes I know there will be people here who will raise their arms in disgust that I'm mounting my root to an 86 Gb partition, but hey, I prefer that to multi-booting.

I'll be installing Windows to what is essentially my SDC, but with SDA and SDB unplugged intitially to force the boot sector to create on that drive; after that I'll simply use boot override post bios to boot into Win if I (reluctantly) need to. Saves the pain of multi-booting GRUB/GRUB2 issues I've historically encountered.

Finally, after all this I've gone ahead and done the basic SSD optimisations for TRIM at boot only, swappiness values reduced, etc etc etc.

Seems to be working nicely so far (in the 20 or so minutes I actually got to use it last night); Xubuntu 12.10 x64 boots quicker than my BIOS posts from a cold start, which is to say between 4-7 seconds to the login screen!


Regards,
Subv3rse

---

### Post by oldfred on 2013-02-08
With 8GB of RAM you should never use swap, but who knows with games how much RAM they may use? 
You actually do not want to use  swap as even a fast SSD is many times slower than RAM. 
To see RAM & swap use
free -m

LInux does cache recent activity in RAM so it may fill up, but only if active process fill RAM will it then use swap.

       RAM memory use
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by MAFoElffen on 2013-02-08
> **oldfred said:**
> I do not do games and have multiple Ubuntu installs all in 25GB / (root) partitions. With my "new" 62GB SSD, I just made two / partitions. I have all my data on rotating drives and have folders in my data partitions that I mount with fstab and link the folders into my /home. I keep /home inside my /, but do not know if linking will work for your games or not.

       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)
    
Also with larger hard drives this user has some I subscript to, but instead of Knoppix, I just have another Ubuntu install.
       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
+1 w/ Oldfred and others...

But, yes, you can split out "partitions" of Linux out and put it back together in the fstab. (more than just the /home...)

Yes, your win games will be stored in /home which some split out /home into another partition or drive... This is common practice even in safeguarding data. But if you also play Linux games, which there are more and more interest in... Don't forget about "/usr". Here is a basic info on what usr is used for:
> 
/usr
This directory contains user applications and a variety of other things for them, like their source code, pictures, docs, or the config files they use. /usr is the largest directory on a Linux system, and some people like to have it on a separate partition or drive. 

Some interesting stuff in /usr:

/usr/doc
Documentation for the user apps, in many file formats.

/usr/share
Config files and graphics for many user apps. These are the global config's (with other spawned individual config's usually in /home).

/usr/src
Source code files for the system's software, including the Linux kernel.

/usr/include
Header files for the C compiler. The header files define structures and constants that are needed for building most standard programs. A subdirectory under /usr/include contains headers for the C++ compiler.

/usr/X11R6
The X Window System and things for it. The subdirectories under /usr/X11R6 may contain some X binaries themselves, as well as documentation, header files, config files, icons, sounds, and other things related to the graphical programs.

/usr/local
This is where you install apps and other files for use on the local machine. If your machine is a part of a network, the /usr directory may physically be on another machine and can be shared by many networked Linux workstations. On this kind of a network, the /usr/local directory contains only stuff that is not supposed to be used on many machines and is intended for use at the local machine only.

And one directory under "/usr" that I didn't mention there, that relates to your interest, "/usr/games/"... It is not well documented as even being there as a subdirectly directly under usr. Funny how that is a app sub-directory of it's own, right? Contains linux game app executables and their configurations files...

At least for me, dealing with servers and deskops, sometimes the applications themselves and how they are configured are almost as important to safeguard as the data... So I sometimes split out the "/usr" to a partition or drive (or network shared resource) of it's own. A lot easier to map these back in than to re-install and re-configure them.

Multi-boot, multi-partition and multi-drive... Yes. Has always made common-sense to me. Just makes things easier and safer. Definitely makes things adaptable and flexible.

---

### Post by Subv3rse on 2013-02-09
Good advice on both there, thanks for the info!

Oldfred - Yeah "linux" should never need to use swap (and that's also why my swappiness is set to 10), BUT - and big but here, it's Wine / Steam games that will be the (potential) killer. I've been gaming since the days of DOS, so yeah, whilst I know that linux itself is brilliant at memory management, it's the MS paradigm I'm catering for :)

MAFoElffen - I did read about a number of those actually, though yeah the usr/games one I didn't know about until I tried installing Doom3 native today. I'm going to tinker with a few more things and try and break linux further than I already have (I'm quite capable at that :P) while I get to grips with it all, then work out a plan that suits me. I'm one of those rip-it-apart/break-it-and-put-it-back-together types. :)

Regards,
Subv3rse

---

### Post by oldfred on 2013-02-09
Since you are experimenting, keep us up-to-date on your results. We see partitioning questions regularly and now with games that has to be included in the possibilities of alternatives. There is no one best partitioning layout but some can be better than others depending on use.

---

