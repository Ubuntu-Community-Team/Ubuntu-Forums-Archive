---
title: "Help with dual-boot installation"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by abc006 on 2007-12-15
Hi, I'm pretty clueless with most of this stuff, so I'd appreciate if you could help me out. I posted in the absolute beginner's forum, but in a seperate thread of mine not really having to do with this, so I've created this one. Also, I was frustrated with that particular forum section seeing as if a thread doesn't get responded to within half an hour, it gets pushed back to the third page where no one ever checks or responds. I think some admins should consider reformatting it so that it doesn't get flooded as much and more people's questions get answered, but that's beside the point. I'm trying to install a dual boot with vista and ubuntu, and I'd appreciate any help you can offer.

First of all, I found this tutorial that seems to be accurate:
[http://www.youtube.com/watch?v=JBfl3oViny8](http://www.youtube.com/watch?v=JBfl3oViny8)
However, someone suggested I put the home folder in a seperate partition. So, A) What does this do/mean? and B) How would I go about doing this? Does this have anything to do with having files (for example, what would be your personal documents) that can be accessed by both vista and ubuntu? If not, is that possible and how would I go about doing that?

Thanks for all your help in advance!

---

### Post by Partyboi2 on 2007-12-15
> **abc006 said:**
> Hi, I'm pretty clueless with most of this stuff, so I'd appreciate if you could help me out. I posted in the absolute beginner's forum, but in a seperate thread of mine not really having to do with this, so I've created this one. Also, I was frustrated with that particular forum section seeing as if a thread doesn't get responded to within half an hour, it gets pushed back to the third page where no one ever checks or responds. I think some admins should consider reformatting it so that it doesn't get flooded as much and more people's questions get answered, but that's beside the point. I'm trying to install a dual boot with vista and ubuntu, and I'd appreciate any help you can offer.

First of all, I found this tutorial that seems to be accurate:
[http://www.youtube.com/watch?v=JBfl3oViny8](http://www.youtube.com/watch?v=JBfl3oViny8)
However, someone suggested I put the home folder in a seperate partition. So, A) What does this do/mean? and B) How would I go about doing this? Does this have anything to do with having files (for example, what would be your personal documents) that can be accessed by both vista and ubuntu? If not, is that possible and how would I go about doing that?

Thanks for all your help in advance!
By putting your /home on a seperate partition, if you were needing to do a reinstall in the future you would not loose what is stored in  /home which is your personal doc's and settings. You would only be reinstalling the system, handy if you plan to play around with ubuntu.
Gusty can read and write to ntfs. So when you are running Gusty you will have access to whats on your windows partition. Windows will not see the linux partition unless you install a program to do that.
[http://www.supriyadisw.net/2006/09/how-to-read-ubuntu-partition-on-windows](http://www.supriyadisw.net/2006/09/how-to-read-ubuntu-partition-on-windows)
To create a seperate /home partiton when you reach the partitioning option when installing choose manual and create your partitions manually.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.pcmech.com/article/installing-ubuntu-linux/](http://www.pcmech.com/article/installing-ubuntu-linux/)

---

### Post by abc006 on 2007-12-15
OK, thanks! Regarding the pcmech.com article: In other tutorials, I've seen the "manual" settings formatted a bit differently in the install program on the LiveCD than what appears on the tutorial. I'll have to check again, but it seems like the interface differs from what I've seen. Is the pcmech tutorial possibly using a different version? Just clarifying since I want everything figured out before I install. Thanks.

Also, will it make a difference in any part of the installation if I'm using vista?

---

### Post by abc006 on 2007-12-15
Update: I think I understand what to do now. I've got a 45 GB main hard drive with 13 gigs left. So, would it be accurate:

8 GB under "ext3" for "/"
I have about a 2000 MB RAM, so I guess 3 GB for the swap.
... But then, I'm thoroughly confused. Since I don't have much space left, how do get the /home - shared data on there like here:
[img]http://img379.imageshack.us/my.php?image=partitioning5bu8.png[/img]
Would I have to backup all my document files on vista, delete them all making room for the /home - shared data partition, then recopy them to the shared folder once I'm on ubuntu? Or do I do something else to make the files automatically transfer over or something? Or am I completely wrong about all of this? Thanks again for all your help.

---

### Post by Partyboi2 on 2007-12-16
If you want you can resize Vista and make it alittle smaller so that you can allocate more room to ubuntu. To do this you would need to use the resizing tool that comes with Vista.
Your /swap partition, you should be ok with giving it 1gig
the operating system can run ok with 5 gig so you could make the / partition 5 gig giving the rest to your /home partition.
Personally I would try and give as much as you can to the /home partition as this is where all your music, videos etc will be.

---

### Post by Partyboi2 on 2007-12-16
I recommend to backup. Always to be safe if you are not wanting to loose anything. In case something happens.

> Would I have to backup all my document files on vista, delete them all making room for the /home - shared data partition, then recopy them to the shared folder once I'm on ubuntu? Or do I do something else to make the files automatically transfer over or something? Or am I completely wrong about all of this? Thanks again for all your help.

When ubuntu is installed you will be able to access your files on Windows by mounting the windows partition. (Not to hard, just a couple of clicks, all going well) When that happens you can see all the files on Vista as well.

---

### Post by abc006 on 2007-12-16
I see, so I could just access all the files on the windows partition from ubuntu and I would use that other program you mentioned to access ubuntu files on windows? If that's the case, is there anything special I need to do to the "/home" partition to make it shared or would it automatically be like accessible on ubuntu? So, to update:

5 GB for "/"
1 GB for "/swap"
7 GB for "/home" (Hopefully I can shrink a few stuff down to get this larger)
Rest (approx 30 GB) for vista.

---

### Post by Partyboi2 on 2007-12-16
> see, so I could just access all the files on the windows partition from ubuntu and I would use that other program you mentioned to access ubuntu files on windows?
Correct, you got it.
>  If that's the case, is there anything special I need to do to the "/home" partition to make it shared or would it automatically be like accessible on ubuntu? So, to update:
Ubuntu will be able to access it as all you are doing is moving the home folder that the auto install puts on the /partition with the system files and giving it its own partition. Make sure that / and /home are formated as ext not ntfs as ext is linux native filesystem.

>  5 GB for "/"
1 GB for "/swap"
7 GB for "/home" (Hopefully I can shrink a few stuff down to get this larger)
Rest (approx 30 GB) for vistalooking good:).

---

### Post by abc006 on 2007-12-16
OK, great, hopefully I'll get this set up soon!

---

