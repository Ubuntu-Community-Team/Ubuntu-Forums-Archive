---
title: "How to limit disk size with install"
date: 2016-09-10
forum: Installation &amp; Upgrades
---

### Post by FerryGnu on 2016-09-10
Is there a simple method to limit disk size with an Install of 14LTS?

How?

I have a dual boot with Vista and installed Ubuntu but it used all the remaining available space, about 180GB. I'd like Ubuntu to have only about 40 or 60 of that.

I tried messing with the "Something else" version of install but could not get a combination to work. I kept getting errors about "no root defined." I finally gave up and let it install and grab the 180GB. Then tried to used GParted but have screwed up the entire thing. I am now about to install it all again.

So, how can I ****simply**** limit the install to 40GB or whatever if that is too small? I only use Ubuntu for streaming youtube to the Home Theater.

I know there is 16LTS and I tried that and it is very buggy and sloooow on this old x86 laptop, so staying with 14LTS if that matters. :)

Thanks

---

### Post by deadflowr on 2016-09-10
When you set the something else option, you need to add a mountpoint.
When you don't, you get the no root defined message.

Basically when you set the partition, first you set the size, then set the file system type 
(Ubuntu's default is ext4, so that's usually a good option. Never set ntfs for Ubuntu's file system, but most any other option is fine)
This is set through a dropdown menu, which you toggle by clicking the file system type bar)
Then after that you can set the mountpoint.
This, again, is done through a dropdown menu, which yo again access by toggling the mountpoint bar.
The top option should be /, this equals root.
Once you set both the file system type and the mountpoint, click OK and the installer's partition manager program will start to set them up.

On top of this you might want to create a swap partition.
To do this, leave a small amount of space (1 to 4 GB is fine) left over when you created the root file system.
And when the system gets back to the something else main page, there should be an entry for unallocated space.
Simply click on this one to edit it, and all you need to do is set the file system type as linux-swap.
(swap has no mountpoint so just setting the partition as linux swap, swap, is all you need to do.
The press OK and let the installer set it up.

After that you should be able to proceed with the installation.

Hope that helps
Or make sense

---

### Post by oldfred on 2016-09-10
Some more examples of Something Else install.

 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using) 

I prefer to use gparted to create partitions in advance. But you still have to use Something  Else and choose (change button) the partition for / and if separate partition for /home. If swap already exists, it will auto find it.

---

### Post by FerryGnu on 2016-09-10
OK, thanks very much for the quick replies. I am currently waiting for it to install. 

I set the root and home both at 20000MB and the swap 2000MB was already there so left it as was.  

@oldfred: I am following the second link, but it leaves a lot unsaid to the non-Linux person. I am using the 
  2. Manually setting up the partition layout for Ubuntu  

And it shows two options, root only or root and home. Now that may all mean something to a Linux person, but then they probably would not need the guide anyway. A brief explanation as to why I might choose one or the other would be helpful. I of course chose the root+home figuring it was better to have too many partitions than not enough. 

 Between creating each new size partition it might be helpful to also mention, "Select free space" each time. I realize it is obvious to a Linux person, but not so, even to me and I have been a Programmer and Technical Writer for 40-years, just never Linux. It is confusing for me, so I feel bad for anyone who is new to computers and wants to make Ubuntu their chosen OS. It's a tough and confusing road and one that encourages into giving up quickly and just go back to with windows and the sound-raping that entails. :) 

 While typing this, the install is locked up at "select keyboard," but there is the occasional rattle of the CD. I assume that GParted is setting up the partitions, but then, maybe not. 

No cursor movement nothing except the occasional rattle of the CD. 

Ten minutes and counting, so till looks locked up. 

 OK, got some cursor control back, but the "Continue" button does not work and select keyboard still showing. 

Really guys, if you can get to Canonical, then this needs to be a lot better to coax windows folk here.  

Finally keyboard offer just went and now have the "Who are you?" so I guess I am on my way again. 

I can see why so many people have told me that they gave up.

---

### Post by oldfred on 2016-09-10
Are you trying to install Ubuntu on an old Vista machine?
How much RAM and what video.
Ubuntu uses Unity which requires lots of video horsepower or a relatively newer video system and more RAM. If an older system, usually Lubuntu or Xubuntu is recommended. Full Ubuntu now is for newer machines that have more capability.

I do a total install in 10 Min. But I have already downloaded ISO and partitioned a 25GB partition for / (root).
For newer users all you may need is / (root). If using more space then a separate /home can be an advantage. From as far back as I can remember even with DOS, I tried to keep operating system in one partition and data in another. With separate /home you are able to reinstall, but easily keep you same settings & data. But backups are still required.

I do not use /home but have a /mnt/data, but that is more advanced, since you have to set ownership & permission where /home has that done automatically.  With Windows & NTFS there is no ownership & permissions. A user, standard Windows user is the Admin, can do anything which is part of the security risk of that type of system.

---

### Post by yancek on 2016-09-10
I think most of your problems are a result of not having enough experience/information on installing operating systems.  Also, if you are using a vista machine, the hardware may be to minimal to run a full fledged Ubuntu.  The minimum and recommended requirements are on the Ubuntu site.  When your doing something new, some research is useful.  If you had read the detailed tutorial/explanation at the site below, I expect you would not have had many of the problems you are encountering.  There is no need for 'programming' knowledge to install any operating system.

 [http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by RobGoss on 2016-09-11
Ubuntu is a learning curve but! coming from Windows as I have also and are now a full time Linux user. With all the information provides here in these forums I don't see how anyone can't move forward

> [COLOR=#000000]While typing this, the install is locked up at "select keyboard," but there is the occasional rattle of the CD. I assume that GParted is setting up the partitions, but then, maybe not. [/COLOR]

This tells me that you're using a very old machine if your hearing this rattling noise I know I also have machines this old not Ubuntu's fault

> [COLOR=#000000]Really guys, if you can get to Canonical, then this needs to be a lot better to coax windows folk here. [/COLOR]

I think Ubuntu / Linux has done a outstanding job providing installation media the way they do it does not get much easier then this the key is **read** and more **reading**

> [COLOR=#000000]I can see why so many people have told me that they gave up.[/COLOR]

Yes Linux is very different that's why we need to do a lot of reading before we take the leap into the Linux world. Linux has come a long way to get were they are today

Remember the people in these forums are** volunteers,** who offer their time and knowledge, they do not get payed for any services. With that said, we are all here for one reason, we love Linux and are willing to learn all we can to be productive in the Linux community

Frustration will get you know were in the Linux world  :D

---

