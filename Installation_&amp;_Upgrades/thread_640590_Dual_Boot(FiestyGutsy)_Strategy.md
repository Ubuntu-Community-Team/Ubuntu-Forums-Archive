---
title: "Dual Boot(Fiesty/Gutsy) Strategy"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by slikwill on 2007-12-14
I have a Dell notebook with 7.04 installed and partitioned thusly:
slikwill@slikwill-laptop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7133    57295791   83  Linux
/dev/hda2            7134        7296     1309297+   5  Extended
/dev/hda5            7134        7296     1309266   82  Linux swap / Solari

The HD was new when I installed.  I am very happy with the 7.04 as such, but would like to keep pace with new releases.
I have the 7.10 release DVD.
I am thinking of a partitioning with a /home partition, a 7.04 partition,  a 7.10 partition, and the swap partition.  Obviously I have two of the four already..
All of the postings deal with dual booting with XP, or trying to troubleshoot other dual boot configurations.
Given my novice status, is there a cookbook solution to this?  I also have a copy of "The Official Ubuntu Book", but this did not shed any light on the issue.
Last point.  Should I do this with the Gnome Partition editor, or during the 7.10 installation.
Any advice before I embark on the endeavor would be appreciated.

---

### Post by logos34 on 2007-12-14
Do it during the 7.10 installation (root cannot be mounted/in use).  

Use 'guided' option or manually shrink hda1 down, make two new ext3 partitions in the freed space with mountpoints '/' and '/home'.  Use the existing swap.  (you might even move any personal files in 7.04 home folder to another drive temporarily (allowing you to shrink hda1 down even further) and then transfer those files to your new /home partition.

On reboot you will have new grub menu with a choice of 7.10 or your old 7.04.  Note: your /home is for gutsy--you can store personal files there from either version but don't attempt to combine the two.

---

### Post by slikwill on 2007-12-14
Thank you.  I think I understand.

The only thing I don't understand is:

"Note: your /home is for gutsy--you can store personal files there from either version but don't attempt to combine the two."

I understand that /home is created by gutsy, but I don't understand how I would attempt to combine the two?

Once again, many thanks.

---

### Post by logos34 on 2007-12-14
some people think they can use one /home for two different releases and/or architectures (x86/amd64) on separate partitions...can't do it

---

### Post by slikwill on 2007-12-14
Oh, OK, I get it.

So there is not much utility to a /home partition in the dual boot scenario.

I was attempting to create an environment that would install a later release alongside a stable release with common data access.  Based on the forum  experiences I read about, it would be worthwhile to be able to boot to a stable release to get back on line and seek help for installation catastrophies.

Thanks again for assisting me.

---

### Post by logos34 on 2007-12-14
I understand where you're coming from...I'm super cautious and don't like surprises, so I often keep a partition with the older release until well after I've decided it's safe to transition to the newer one (i.e. absolutely everything works to my satisfaction and the are no surprises).  If internet access is what you're worried about, you have that (or should) on the live cd.  But if you want a little more security and a place to work from if your new installation gets borked, then that setup should work--a separate /home partition still makes sense, you can still access it from either and store all your files, downloads, etc. there.  Then when you are satisfied with gutsy 7.10, wipe the 7.04 partition and reclaim it for data storage or something.  You can use all the space you can get on a 60 GB.

---

### Post by pmdkh on 2007-12-14
I have to say that I'm still a bit confused about sharing a /home partition. So, if **slikwill** had a configuration file (say ~/.vimrc or ~/.bashrc) saved in his/her Fiesty home folder, and then transferred those to the new /home partition created by Gutsy, would Fiesty applications access those configuration files?

Does my question make sense, or am I totally missing something?

I don't currently dual-boot multiple Linux distros, but I plan to one day, and I've been trying to figure out how to partition my computer. This info would definitley come in handy when making that decision.

Thanks for the help.

---

### Post by logos34 on 2007-12-14
ok, I stand corrected on this.  I had heard it's not a good idea to share /home but a quick search proves me wrong. I'm going to have to look into this matter some more.  I'm still not convinced (especially different distros--seems to me like you're just asking for problems).  But in this case with two ubuntus, if you're running the same desktop then issues will be apparently minimal.  Or so it is claimed.  There's a few other threads on diff distros--google around.

[http://www.uluga.ubuntuforums.org/showthread.php?p=3896723](http://www.uluga.ubuntuforums.org/showthread.php?p=3896723)
[http://ubuntuforums.org/showthread.php?t=324582](http://ubuntuforums.org/showthread.php?t=324582)
[http://ubuntuforums.org/showthread.php?t=344635](http://ubuntuforums.org/showthread.php?t=344635)

---

### Post by Herman on 2007-12-15
You can do whatever you like as long as you're having fun with Linux and learning things. :)

Personally, I prefer single '/' (root) partition + swap installs, especially for dual or multi booting, it's so much tidier.

Many good and learned linux experts espouse the virtues of the separate /home partition, but remember, we still need to make regular backups, so why is the separate /home partition really needed? (If you have your system and files properly backed up anyway?) :confused:

I prefer to have a separate shared data disk or data partition that all the operating systems can access.

That's just my 2 cents worth. :)

Regards, Herman  :)

---

### Post by Zack McCool on 2007-12-15
> **logos34 said:**
> ok, I stand corrected on this.  I had heard it's not a good idea to share /home but a quick search proves me wrong. I'm going to have to look into this matter some more.  I'm still not convinced (especially different distros--seems to me like you're just asking for problems).  But in this case with two ubuntus, if you're running the same desktop then issues will be apparently minimal.  Or so it is claimed.  There's a few other threads on diff distros--google around.



The separate /home partition is fine, but some apps may encounter issues, as the newer version of Ubuntu will be using newer versions of some apps and/or libs.

Having a separate /home is a good idea, IMO, as it facilitates a rebuild of an OS if you are playing around with it a lot.  But like I said, it will not be a complete success in a dual-boot between distros, unless you are using the same versions of all applications...

---

### Post by slikwill on 2007-12-15
One of the things I just did was to peruse my /home directory with hidden files being displayed.  In there was the installation of Firefox and Thunderbird.  I didn't look any further, but there may be other applications in there.  So I think I will make a /data partition and leave the /home directory be unique to both the fiesty and gutsy partitions.

Any comments...

---

### Post by Irihapeti on 2007-12-15
> **slikwill said:**
> One of the things I just did was to peruse my /home directory with hidden files being displayed.  In there was the installation of Firefox and Thunderbird.  I didn't look any further, but there may be other applications in there.  So I think I will make a /data partition and leave the /home directory be unique to both the fiesty and gutsy partitions.

Any comments...

Sounds like a good way to go. I've currently got both Feisty and Gutsy on my PC, and I discovered that using the same /home partition caused problems. The desktop configuration file was created by Feisty, as it was the original system. Gutsy, not having all the same programs, didn't quite know what to make of it. Incidentally, it's very easy to share the thunderbird and firefox profiles between the two installations.

I ran into a problem with Grub. Didn't install it when I did the first Gutsy install, but edited my Feisty Grub. That worked fine, but when I wanted to install Grub on the Gutsy partition, nothing seemed to work properly. Even supergrub disk didn't help me. In the end, I did a complete tar backup of the Gutsy partition (except for /boot and a few other directories), reinstalled and then restored from the tar file. In fact, the install detected the Feisty partition and added it, plus all the earlier kernels, to the menu.lst. So I'd recommend putting the bootloader on the Gutsy partition when you first install.

---

### Post by slikwill on 2007-12-15
Hmm...
So at what point in the gutsy install would I do the install of Grub on gutsy? 
It seems I will have trouble if I do any boot before installing Grub in gutsy, or am I confusing myself here.

I seem to be going two steps forward one step backward here.

---

### Post by logos34 on 2007-12-15
> **Irihapeti said:**
> Sounds like a good way to go. I've currently got both Feisty and Gutsy on my PC, and I discovered that using the same /home partition caused problems. The desktop configuration file was created by Feisty, as it was the original system. Gutsy, not having all the same programs, didn't quite know what to make of it. Incidentally, it's very easy to share the thunderbird and firefox profiles between the two installations.

[QUOTE=Zack McCool]The separate /home partition is fine, but some apps may encounter issues, as the newer version of Ubuntu will be using newer versions of some apps and/or libs.[/QUOTE]

So then there are problems even on the same desktop enviroment?  Maybe my original fears were not entirely unfounded after all... 

[QUOTE=Herman]Many good and learned linux experts espouse the virtues of the separate /home partition, but remember, we still need to make regular backups, so why is the separate /home partition really needed? (If you have your system and files properly backed up anyway?)

I prefer to have a separate shared data disk or data partition that all the operating systems can access.[/QUOTE]

You have a point there...You can even back up gnome desktop settings with gnome-reset (and I suppose there's something similar for KDE), so you can restore files and settings back to exactly what they were before.  Then there's AptonCD.  So why do I bother with a separate home?

---

### Post by pmdkh on 2007-12-16
[quote="slikwill"]Hmm...
So at what point in the gutsy install would I do the install of Grub on gutsy?
It seems I will have trouble if I do any boot before installing Grub in gutsy, or am I confusing myself here.

I seem to be going two steps forward one step backward here.[/quote]

Don't take my word for it, but I believe that when you go to install Gutsy, it should give you the option to install grub. When you do that, it should automatically detect the other OSs already on your computer. That is how I understand it, at least.

[quote="logos34"]So then there are problems even on the same desktop enviroment? Maybe my original fears were not entirely unfounded after all...[/quote]

I am coming to agree with you more and more. I think I'm going to use a /data partition for things like music and pictures, but use a separate /home directory for each distro. I plan on testing out a lot of different distros in the future, so I don't really want to deal with extra configuration files hanging around.

I did see in one of the links that you posted that someone mentioned using symbolic links from the home directory for different distros. That sounds like an ok idea, but I would prefer to just have a clean install, with a new /home directory, for each new distro.

---

### Post by Irihapeti on 2007-12-17
OK, I probably didn't make myself very clear - it comes of posting when tired. If Gutsy is installed after Feisty, then, unless you tell it not to install Grub, it will detect your existing Feisty install and put it in the boot menu. (I *did* tell it not to, and that's what caused my problems.) It's a good idea to have a copy of SuperGrubDisk on hand, before you begin:)

As I understand it, a separate /home partition is useful if you have one distro only and you want to be able to reinstall it without affecting your data files - useful if you are doing a lot of tweaking which may or may not work. 

If you have two or more distros, my experience is that you are better off sharing a data partition and having separate /home directories for each distro.

---

### Post by logos34 on 2007-12-17
> **Irihapeti said:**
> As I understand it, a separate /home partition is useful if you have one distro only and you want to be able to reinstall it without affecting your data files - useful if you are doing a lot of tweaking which may or may not work. 

If you have two or more distros, my experience is that you are better off sharing a data partition and having separate /home directories for each distro.

That's the way I see it too.  I usually reinstall a given release at least once, so this saves a lot of hassle. And sharing a home between distros just does not sit well with me, despite what some say.

OTH, Herman (as always) has a good point.  What sense does a separate /home make if we are doing backups as we should?  I have to admit I am one of those who get lazy and do not observe a strict backup schedule.  But I am determined to change that.  Since desktop (i.e. nautilus) preferences and settings can also be backed up, along with all of home, /usr/local, /opt (manually-installed 3rd party apps) and the .deb pkgs in /var/cache/apt/archives (using AptOnCD), then a /home is not really necessary or even a convenience for that matter (in fact it's just taking up a partition which, if primary, are scarce--four is the max).  

I still haven't decided, but my thinking is evolving on this matter.

P.S.--

Irihapeti,

Is that your cat in the avatar?  It looks exactly like my Russian Black.  (But then all black cats look alike!)  He's heading into his golden years (16+ years).  A distinguished senior citizen cat with silvers and all.

---

### Post by Irihapeti on 2007-12-17
One of the problems I've found with multiple partitions is not being able to combine the free space if it's needed. E.g. if I'm doing video editing and I need, let's say, 5 GB to work with and I've got 3 GB free on one partition and 4 GB on another. If everything is on one partition, I've got 7 GB free and I'm in business.

Regular backups of the /home folder would certainly solve the problem just as well as a separate partition. I've ended up being much more diligent about backing up my Ubuntu installs than I ever was when I used Windows - not sure why.

logos34:
Yes, that's my cat in my avatar. She's called Melanie (a name derived from the Greek word for "the black one") and she's 9 1/2 years old. Still thinks she's a kitten sometimes and is a good hunter. I hope she has a fair few years left in her.

---

### Post by logos34 on 2007-12-17
melán&#333;sis ?  funny, my cat has a color-reference in his name too--'Ebony'.  When the light hits his coat just so you can see the brownish undercoat hair.  Really exotic black-brown, kind of like the wood. And it's the softest, most luxurious coat I think I've ever felt on a cat.  Satin-smooth, feels like a million bucks.  Now if I can just get him into commercials, help defray some of the vet bills! He hasn't been well lately...dehydrated, little appetite.  Luckily, blood tests negative for chronic renal failure, fiv, UTC, etc.  May just have anemia.  I have to hydrate him with a syringe.  Still hangin in there, but barely.  I just want him to live a couple more years.

oh well, enough of boring you with my cat problems. 

> I've ended up being much more diligent about backing up my Ubuntu installs than I ever was when I used Windows - not sure why.

probably because you know from tweaking linux how easy it is to bork an installation! Seriously, I think it's simply because linux forces one to become more hands-on and aware of what's going on.  You have to do a lot of stuff manually.

---

### Post by slikwill on 2007-12-17
Well I did it.

Installed gutsy using the guided.  Made a new 10GB partition.  It installed a new boot loader an I can use it to boot between fiesty and gutsy.

Now the bad news.  
My partition looks thusly

:slikwill@slikwill-laptop:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d46ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1301    10450251   83  Linux
/dev/sda2            6971        7296     2618595    5  Extended
/dev/sda3   *        1302        2576    10241437+  83  Linux
/dev/sda4            2577        6970    35294805   83  Linux
/dev/sda5            7134        7296     1309266   82  Linux swap / Solaris
/dev/sda6            6971        7133     1309234+  82  Linux swap / Solaris

Partition table entries are not in disk order

I have A 35 GB partition that I can't for the life of me figure out how to make it a partition called /data using the Partition Editor.  Any help would be appreciated.

By the way, this is being sent from the Gutsy boot.

---

### Post by Irihapeti on 2007-12-17
I'm assuming your intended data partition is /dev/sda4. You would need to create a directory called data in the /media directory of each install, and then modify /etc/fstab, again in each install, to tell the system to mount the partition in that place.

Something like this:

```
/dev/sda4     /media/data     ext3    defaults        0       2
```

or you can use the UUID instead of /dev/sda4

You'll need to have the proper permissions for that directory, of course :) 

There's something on the psychocats website about this. From memory, it's called "mount Linux" or something similar.

By the way, it looks like you have two swap partitions. Only one is needed, as far as I know.

---

### Post by slikwill on 2007-12-18
Yes!!!!!!!!!!!!!

You rule, Irihapeti  	

Between your post and the pschocats site, I now have a data directory on both desktops and can read and write to it from both fiesty and gutsy.

That just leaves my swap file.  Do I do essentially the same thing for swap?

Once again, many thanks for your help.  I think I will construct a how to (once I fix the swap problem) and post it to that sticky thread about gutsy installation experiences.  Of course I will want to run it by you.  I would e-mail it to you if I could have your permission to do so.
Moving forward with gutsy!   Just have to make Java work, and my wireless adapter card work, install some apps and I'm ready for the next update encounter.

---

### Post by Irihapeti on 2007-12-18
Now here I'm guessing a bit, because I've never had more than one swap partition, but, yes, I imagine that you'd choose one of those partitions and put it in your fstab file, and delete the other. You might then want to resize your extended partition so that the space is attached to one of the other existing partitions, where it will be more useful :)

---

