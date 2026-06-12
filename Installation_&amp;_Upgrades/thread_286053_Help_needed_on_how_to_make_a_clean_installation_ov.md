---
title: "Help needed on how to make a clean installation over a dual boot machine?"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by javierfh on 2006-10-27
Hello,

i have a dual boot machine, windows XP and linux.
Someone adviced me to make a partition for my /home and so i did (well with the help of one guy from qunu online help service).
So now the situation is that i want to update to Edgy, but for some reason my ubuntu, its not very stable in dapper, so probably i have installed something that makes it unstable. I decided then to format and make a clean installation.

So how should i proceed? Do you have some instructions for dummy? or is there some link how to do it?

Is there any way to see all my partitions?

Once i see them all, is there some command that i should run to do the formating of the particular partitions?or should i boot up with some boot cd?or would some of the install cds offer me the posibility of formating partitions?
So once i will get it installed, how should i map again the partition that i have currently as /home to be again /home in the new system? or will it be done automatically?

Where is the grub located? will the format affect to the grub?

Well im not sure if i forget some important question, but feel free to add more things, if you think i should consider.


Thanks in advance,

Javi

---

### Post by rsambuca on 2006-10-27
Javi,

It looks like you are in a very similar situation as me.  I am quite new to linux, and have been playing around with ubuntu 6.06, and also kubuntu.

I tried many different set-ups with 6.06, ie. XGL/compiz, XGL/beryl, mythTV (never did quite get that one working very well).  Anyways, as I am new to this, I just re-installed the ubuntu O/S every now and then to make sure everything was not messed up after my changes.

I now have Windows XP on one partition, a separate ntfs partition for my Windows data (I configured it so My Documents folder was on this separate partition - You can then re-install Windows without losing any data).  I now have freshly installed 6.10 overtop of my old dapper.  I have put the linux stuff all into one large logical partition, with a 20G root, 2G Swap, and an 80G /home partition.  This way, whenever you want to re-install ubuntu, you install overtop of the pre-existing root and swap partitions, but leave your /home partition, and all of your basic settings are left intact.  Works pretty well.

I used the gParted live CD (version 0.3.1-1) to create all of these partitions for both the Windows and linux stuff, and it worked perfectly.  I didn't lose any data at all (although I did back-up my data just-in-case).

After the partitions were created, I then used the standard ubuntu desktop live CD to boot, and then install the O/S.  When you get to the partition section, select Manual partitions.  Worked pretty well for me.

As far as I know, Grub is located in hd0,0.

By the way, it seems like there is a problem with the Edgy installer when trying to recognize certain partition schemes, but there is a workaround that I found.  Hope all goes well.

---

### Post by javierfh on 2006-10-27
> **rsambuca said:**
> Javi,

It looks like you are in a very similar situation as me.  I am quite new to linux, and have been playing around with ubuntu 6.06, and also kubuntu.

I tried many different set-ups with 6.06, ie. XGL/compiz, XGL/beryl, mythTV (never did quite get that one working very well).  Anyways, as I am new to this, I just re-installed the ubuntu O/S every now and then to make sure everything was not messed up after my changes.

I now have Windows XP on one partition, a separate ntfs partition for my Windows data (I configured it so My Documents folder was on this separate partition - You can then re-install Windows without losing any data).  I now have freshly installed 6.10 overtop of my old dapper.  I have put the linux stuff all into one large logical partition, with a 20G root, 2G Swap, and an 80G /home partition.  This way, whenever you want to re-install ubuntu, you install overtop of the pre-existing root and swap partitions, but leave your /home partition, and all of your basic settings are left intact.  Works pretty well.

I used the gParted live CD (version 0.3.1-1) to create all of these partitions for both the Windows and linux stuff, and it worked perfectly.  I didn't lose any data at all (although I did back-up my data just-in-case).

After the partitions were created, I then used the standard ubuntu desktop live CD to boot, and then install the O/S.  When you get to the partition section, select Manual partitions.  Worked pretty well for me.

As far as I know, Grub is located in hd0,0.

By the way, it seems like there is a problem with the Edgy installer when trying to recognize certain partition schemes, but there is a workaround that I found.  Hope all goes well.



Hi thanks for the help.
So what is the gParted? some utility cd that it is bootable?
So i have the partitions in place, probably similar as you, i have Windows partition, root partition, swap partition and home partition. So the problem for me now is to know how can i format the root and swap partitions only.. and from where?from a boot cd? from the live cd?

And once that is done, how can i assign to home, the partition that i have currently as home so i dont loose the data.

So any idea? Anyone else who can give some tips or help?

Javi

---

### Post by maino82 on 2006-10-27
gParted is the Gnome Partion Editor. It's like Partition Magic and let's you a) modify the way your system is partitioned and b) find out where your current operating systems and data are located on your hard drive. For instance, I also have a dual boot with 3 different partitions. The first partition is windows, the second Ubuntu, and the third swap. If you have all your data stored on your home directory which you said was on another partition, you can just start installing a fresh copy of Ubuntu over your old copy, and then when it asks about partitioning just tell it which partition you want to mount as your /home directory and you should be good to go. Otherwise, you should back up any data you have on your current Ubuntu partition to your windows or /home partition, and then proceed as I've just described. Again, it can be helpful to open up gParted to see how your partitions are arranged before doing all of this.

If you already have gParted installed, it will be under "System -> Administration" and may show up as "GNOME Partition Editor." If you do not have it install, you can either open a terminal and do "sudo apt-get  install gparted" or go to "System -> Administration -> Synaptic Package Manager" and search for gparted and install as you normally would from synaptic. Also, you should be able to pop in the Edgy Install CD and do the same thing since it will boot you into a GUI.

Hope that helps!

---

### Post by rsambuca on 2006-10-27
Javi,

Yeah, as maino said, you can use GParted (the Gnome Partition Editor) from your existing ubuntu setup, or I assume from the liveCD as well.  I happened to already have a copy of the GParted bootable CD which you can get download for free from here:  

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

It sounds like you shouldn't really need to use it, because you already have the partitions set up anyways.  When you use the Edgy desktop CD and you go through the steps under the manual Partition section, formatting of the '/' and swap partitions is manditory, and you have an option to format the /home partition.  Just make sure to leave the /home partition unchecked and Edgy will be installed in the /root, but should leave your /home partition untouched.  Grub will automatically be installed properly to give you the boot options of XP or the new ubuntu.

I would suggest just going through the installation steps on the liveCD to get a feel for what we are talking about.  You can always just press 'cancel' prior to the very last step and your hard drive will be left untouched.

---

### Post by Craigus on 2006-10-27
> By the way, it seems like there is a problem with the Edgy installer when trying to recognize certain partition schemes, but there is a workaround that I found. Hope all goes well.

This sounds like the problem I am having - could you please share some information about the workaround ?

---

### Post by rsambuca on 2006-10-27
When I tried to install 6.10 overtop of my existing 6.06 ubuntu, it wouldn't let me.  I believe at the partition step it said "no root file system", eventhough I had it selected.  I found a workaround here:

[http://www.ubuntuforums.org/showpost.php?p=1656061&postcount=5](http://www.ubuntuforums.org/showpost.php?p=1656061&postcount=5)

Once I had loaded the live CD, I just used the command:

sudo gedit /usr/lib/ubiquity/ubiquity/validation.py

I then changed the code as per the instructions in the other thread.  Saved the file and then went through the install process and it worked.

---

### Post by Craigus on 2006-10-27
Thanks. I've also posted a solution in my own thread:

[http://www.ubuntuforums.org/showthread.php?t=286436]("http://www.ubuntuforums.org/showthread.php?t=286436")

---

### Post by javierfh on 2006-10-28
Hello and thanks a lot to Maino82 and rsambuca,

i havent checked the messages until now since we have the time difference and now it is the morning here in europe.
So, i have installed gparted and these are the partitions that shows 

[ATTACH]18374[/ATTACH]

I have also downloaded the livecd and checked that it works.
So now just for security i will backup my data from /home folder, just in case..better to be safe than sorry and since im not very confident..just in case i screw something.

So in practice i assume that what i have to do it is to format sda2 and sda5 but i wonder what it is sda3, do i need to do something for that one?

I will also try what you said about going through the steps before doing it for real.

Ill post my results when im done .. hopefully succesfull ones :)


Javi

---

### Post by maino82 on 2006-10-28
sda3 is your swap drive and will be automatically formatted for you (so long as you select that same partition as swap again, which it may do for you automatically as well). the swap drive contains only volatile information (information that isnotpermanently stored on your harddrive) so it is ok that it will format it. you won't loose any information when it does so.

---

### Post by javierfh on 2006-10-28
Thanks for the answer.

Now i have finnished to back up the /home.
I started testing the live cd and everything seems fine..and seems very logic and easy to use..so i decided to go for it.
But when i am in the step 5 of 6 called " prepare mount points" i select the following

/media/sda1  partition 1 disc sata 1 (primary) [sda1]
swap         partition 5 disc sata 1 (logical) [sda5]
/            partition 2 disc sata 1 (primary) [sda2]
/home        partition 4 disc sata 1 (primary) [sda4]

And then when i click forward i get an error saying that no root file system.

What im doing wrong?

I really dont understand everything seems logic to me.

Javi



EDIT: ok now i saw the error that rsambuca commented here is the one im having..ill try to edit that file to see what happens.

---

### Post by javierfh on 2006-10-28
Thanks to all that helped here.
Finally working fine. Now trying to update all the missing things.

By the way, i have noticed that some applications were installed in my /home folder or part of the installation went to /home and now these wont work anymore. Is there some default place where to install applications?
I guess now i have to remove these applications from /home...which it is little bit scary since i was hopping to have clean table, but seems i didnt do it properly and might have some crap still in home.. but well you learn :) 
Javi

---

### Post by rsambuca on 2006-10-30
Javi,

I read somewhere in another thread about how some people leave the /home directory in the main partition along with the root directory, and then use symlinks to link certain folders in /home to another partition.  Then you can save photos, other documents etc. on a separate partition, but if you want to re-install for any reason, you get a clean /home directory but all of the data on the other partition you keep untouched.  This way, you don't have to worry about the config files that are on the /home, and you get a fresh install.  I think it said you then have to re-create the symlinks.  It makes sense to me, but I haven't tried it yet.

---

