---
title: "gnu grub 1.97~beta4 error - possible solution"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by brian_martin on 2010-01-30
I installed Karmic, using wubi, on  Windows 7. For some nine/ten weeks it worked well. I did an update and got the above error following that update, the grub menu had vanished.

I googled and got several suggestions on what to do. I felt they were beyond my competence and skill level. I also found a suggestion the error might be due to to two grub updates.

I uninstalled Karmic then re-installed. I did an update but excluded the two grub packages - grub-common and grub-pc. Everything has been working for the past five days.

My question. having excluded the packages have I introduced a security risk?

Brian

---

### Post by presence1960 on 2010-01-30
Unfortunately there are problems with wubi in karmic. Why don't you do yourself a favor and do a proper full installation of Ubuntu? Here are some reasons to do so:

1. Wubi is not meant to be a permanent installation. I realize a lot try to use it as such. Here is a [link]("http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/") to an interview with wubi's developer. Note his answer to the second question.

2. Wubi is not as fast as a full install of Ubuntu and is subject to performance degradation because of file system fragmentation since it inside the windows filesystem. See here for more info: [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

3. It is way harder getting support for wubi for the simple fact most users do not use wubi, they have full installs of ubuntu. Therefore there is limited help you will receive because a lot know very little or nothing about wubi.

---

### Post by kansasnoob on 2010-01-30
Have you seen this:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

I'd particularly stress:

> Since any kernel or Grub update relocates some of the boot files, you might be hit by this bug at any time. 

---

### Post by brian_martin on 2010-01-30
I am new to ubuntu so using wubi seemed a good starting point. Despite the grub problem I plan to continue to stick to ubuntu. When I am confident about it I will move to a dual boot system.
So "Why don't you do yourself a favor and do a proper full installation of Ubuntu?" is not very helpful to a beginner.

Thanks to kansasnoob for pointing me to the possibility of continuing problems using wubi. It is worth the risk while I am gaining confidence.

Brian

---

### Post by Leppie on 2010-01-30
i would strongly recommend you to a side by side install. if windows isn't shut down properly, ubuntu cannot be booted either with a wubi install. as wubi places the ubuntu filesystem within the windows' ntfs filesystem, corruption of the ubuntu "partition" may even occur.
i don't believe a wubi install is a lot easier than a side by side install. the only thing you need to think a little bit about is disk partitioning. but i don't think that would outweigh the advantages (like being able to access all your data even if windows doesn't boot) of the side by side install.

wubi installs quite often seem to give troubles.

---

### Post by presence1960 on 2010-01-30
> **brian_martin said:**
> I am new to ubuntu so using wubi seemed a good starting point. Despite the grub problem I plan to continue to stick to ubuntu. When I am confident about it I will move to a dual boot system.
**_So "Why don't you do yourself a favor and do a proper full installation of Ubuntu?" is not very helpful to a beginner._**

Thanks to kansasnoob for pointing me to the possibility of continuing problems using wubi. It is worth the risk while I am gaining confidence.

Brian

Brian as a beginner wubi in karmic has many problems that you may not be able to handle. If it was wubi 9.04 or 8.10 you would have less problems. But the fact remains that it is way more difficult to get support for wubi simply because hardly anyone really uses it on a regular basis.

Based on all the troubles in 9.10 wubi and the level of support for wubi, and the fact that you are a beginner it is in your best interests to consider a proper dual boot setup. I am not here to make friends but rather to learn myself to increase my knowledge and try to help those who need help. You don't have to like the help you get as long as it is helpful.

Now for the bold, underlined in the quoted text above. You cut that out and took it totally out of context. If you read the statements following  that in my post you will see that there are reasons which all lead up to the conclusion you take out of context. But that is alright you will get over it.

---

### Post by meierfra. on 2010-01-30
> Unfortunately there are problems with wubi in karmic. 
Wubi 9.10 has been hit by a bug in Grub 2.  Otherwise, as afar as I know, Wubi 9.10 is performing just as well as the previous versions. This bug in Grub2 can be fixed in a couple of minutes by downloading one file. (See the link posted by kansasnoob).   Ubuntu 9.10 also had its share of problems caused by  the introduction of Grub2.   
 So   the recent problems in Wubi are no valid reason to rant against Wubi.

> wubi in karmic has many problems that you may not be able to handle. 
I disagree.  See  the above.


> Wubi is not as fast as a full install of Ubuntu
Wubi is a little bit slower than Ubuntu, but not much. I have Wubi installed for testing purposes and  I actually don't notice any difference in speed.

> 
It is way harder getting support for wubi for the simple fact most users do not use wubi, they have full installs of ubuntu. Therefore there is limited help you will receive because a lot know very little or nothing about wubi.
There really is not  much difference between Ubuntu and Wubi. The booting  works slightly different: Wubi uses "wubildr", which  essentially  is core.img plus various of the modules. Also Wubi lives on a file rather than on   partition. So  mounting  Wubi and running a file system check is a little  different for Wubi. 
 
So  if  you (presence1960 and Leppie) would spend just a little bit of time learning  how Wubi works, the help for Wubu users would already improve dramatically.

Many of the Wubi users have very limited computer knowledge. Telling them to install Ubuntu, even if they have only have a very small problem, is a  bad idea. Many of these users will give up on Wubi and Ubuntu altogether.


> Wubi is subject to performance degradation because of file system fragmentation since it inside the windows filesystem. 
True.

> if windows isn't shut down properly, ubuntu cannot be booted either with a wubi install. as wubi places the ubuntu filesystem within the windows' ntfs filesystem, corruption of the ubuntu "partition" may even occur.
True.

> the only thing you need to think a little bit about is disk partitioning.
And that is the main advantage of Wubi. Partitioning is very scary to  many users, and rightfully so.  There have been any many cases where the Windows partition was wiped out during the Ubuntu installation.


> I am new to ubuntu so using wubi seemed a good starting point. Despite the grub problem I plan to continue to stick to ubuntu. When I am confident about it I will move to a dual boot system.

Well said. That's exactly how Wubi is supposed to work. Please don't be discouraged by the negative attitude towards Wubi in this forum.

---

### Post by presence1960 on 2010-01-30
> So  if  you **_(preserve1960_** and Leppie) would spend just a little bit of type learn  how Wubi works, the help for Wubu users would already improve dramatically.


meierfra: ha-ha! whether intentional or not I had to laugh at the screen name! I did have wubi installed about a year or so ago to just see how it worked. Back then there weren't so many requests for help with it as there are now. You make a valid point about that maybe I should install it and learn about especially since I am pretty active in here.

I can see how wubi would be ok, I don't deny that fact. It is just with all those threads about wubi in 9.10 I feel that it was prudent to direct users away from that. I still believe a full install is the way to go, but I will install wubi this coming week and attempt to learn some about it. It is definitely a better thing to be part of a solution.

BTW I really respect your opinion. I am pretty fortunate as I have never had to start a thread about any problem I have encountered (and I have had them). I was able to do a search mostly in the forums, some Google and once finding a thread with the solution to my problem read it and implement the fix. I used to and still do peruse your posts as a nice chunk of what I have learned about linux has come from your writing.

Lesson here for me- I still feel a full install is the way to go but let the user decide which option. Since I will be taking this approach I need to install wubi at least to learn it.

---

### Post by meierfra. on 2010-01-30
> meierfra: ha-ha! whether intentional or no
It wasn't intentional. If you look  at  boot_info_script049.sh (which has been displayed accidentally is some threads) you will see that I misspelled my own name.

> It is just with all those threads about wubi in 9.10
Yes, but almost all  those threads have been caused by the same bug in Grub2.  A very easy fix for that bug was released by Russo in the  middle of December.  Unfortunately, he hid his fix in the middle of a bug report and so it took another  month  until the fix appeared in the ubuntu forum. 


> still feel a full install is the way to go but let the user decide which option
I aggree.

> Since I will be taking this approach I need to install wubi at least to learn it. 
Great.

---

### Post by brian_martin on 2010-02-01
meierfra

Thanks for your very positive comments.

Your statement on the partition accurately addresses my fear. I was aware of the need for a partition and that put me off - what happens if i mess up? - do I really trust the image that was provided with the laptop? Wubi was ideal as it avoids the need. Now I can sample ubuntu. I am happy to accept ubuntu will be slower than in its own partition but that is not a problem as it is seems faster than Windows7 doing the same task. So no issue to me.

Apart from the grub problem I am impressed by Karmic. Everything I want to do can be done apart from using audacity to record streaming radio but I am working on it.

Brian

---

### Post by Leppie on 2010-02-01
> **meierfra. said:**
> So  if  you (presence1960 and Leppie) would spend just a little bit of type learn  how Wubi works, the help for Wubu users would already improve dramatically.
i know that wubi is where i properly lack knowledge, i will look into wuvi installs as soon as i've set up my virtualbox windows image.

---

