---
title: "Installing on a different drive via Ubuntu Software Center and Blender issues"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by SiGabse2984 on 2011-05-15
Hi

 From what I thought I guess Ubuntu Software Center(USC) is somewhat the only "legit" way of installing applications for ubuntu..as to like when installing application on windows and it gets registered and the sort. 

 I tried installing blender via downloading it from their website, extracted the folder inside my user folder (one with my name in it) and clicked blender then it ran like it  was already installed..It kinda felt like something's missing or is that how it runs truly?

 There's one available at USC but it's outdated but I should install that so that's "officially" installed in my system and probably I could update it later..by means that I don't know either.

 Problem now is that I want to install my applications to a different hard drive instead of all of them installing on my disk that has ubuntu. Seems that USC is installing the applications at that disk only and I can't find any option for it to install in my other hard drives.

 And would it install in a NTFS drive or should I reformat it to a ext4?

 Thanks..please let me know if I haven't provided enough info about my problem and about taking screenshots for my partition I don't know how to do that..I'm learning to use this OS from scratch and have it replace windows as my only OS in my PC so that I would be forced to use it more often.

I'm using Ubuntu 11.04

 Thanks again

---

### Post by dino99 on 2011-05-15
no software-center is not the only way, better to use synaptic

[http://www.techdrivein.com/2011/01/blender-256-beta-releasedubuntu-ppa.html](http://www.techdrivein.com/2011/01/blender-256-beta-releasedubuntu-ppa.html)

your installation should look like:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

and apps are installed where /home is.

---

### Post by SiGabse2984 on 2011-05-15
Thanks for the reply

Well I had one HD where my ubuntu(main disk) is and the other in NTFS..

I was wondering if there a way that I could reinstall my applications in the NTFS disk so that my main disk won't be full.

or that's not possible and I have to format it to ext4

[IMG]http://img.photobucket.com/albums/v325/GennyGen/Disk2.png[/IMG]

That's my other hd where I planned to reinstall my application. Finally figured out how to make screenshots of my partition

---

### Post by Dutch70 on 2011-05-15
AFAIK it's not possible to install Linux applications to a Windows file system & they also have to be installed to the same partition as "/" aka "root".

We could probably get a better idea of your partitions from a screenshot of Gparted. Also, you can attach the screenshot to your post by using the paper clip in the toolbar. It just works a little better that way IMHO.

---

### Post by SiGabse2984 on 2011-05-17
Here's a screenshot from Gparted..used the clip icon for uploading it too..let me know if you guys see it.

thanks

---

### Post by Dutch70 on 2011-05-17
Well, that's a great pic of 2 NTFS partitions & we can see it much better. 

I'm not really sure what your other questions are, or why you would give us a pic of NTFS file systems though. As I stated above, you can use ntfs for storage, but not for apps. I don't even think you can format them to ext4 and install apps to them unless you use that space to increase your "/" aka "root" partition. Which you didn't give us a pic of.

---

### Post by SiGabse2984 on 2011-05-19
Sorry about that..I've added both screenshots of my main disk and the NTFS disk this time.

> As I stated above, you can use ntfs for storage, but not for apps. I don't even think you can format them to ext4 and install apps to them unless you use that space to increase your "/" aka "root" partition. Which you didn't give us a pic of

So even formatting my other drive (either one or all the NTFS partitions I've shown in my last post) ubuntu won't install apps these drives still?

and increasing the root partition. That be the one in my main drive (the new screenshot)..Is there a way I could instruct ubuntu to install them on a different drive instead of my main drive?

Kinda like in windows where we'd get to choose the location to where the programs would be installed..via synaptic and USC I doesn't tell me where to install them but just installs them..from what you said it would be in my main drive since that's where my root partition or the /home directory is.

---

### Post by Dutch70 on 2011-05-20
:shock: You've got over 70GB for Ubuntu. You have to install apps to /, which is your Ubuntu system. I don't know of any other way to do it & can't imagine why in the world you'd want to. If you put your data on a separate partition, you'll never fill up half of that 70GB with apps. 

I keep my data on a separate partition from / and I've never installed enough apps to use more than 10-15GB.

---

### Post by linuxinstalledfromhdd on 2011-05-20
I would reisntall Ubuntu entirely and follow a to-do list if you are at all unsure of your previous software installations..  This to do list includes blender PPA too.

[http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/](http://cinderbox.net/2011/04/03/to-do-list-after-installing-ubuntu-11-04-aka-natty-narwhal/)

---

### Post by SiGabse2984 on 2011-05-20
I guess I'm use to windows' style in which most users recommend that we don't install anything in the main drive but windows updates only..guess it's ok to keep the rest of my hard drives in NTFS and there seems to be no big issues about it.

I would be reinstalling ubuntu then..seems that it's sort of recommended that we install application here via terminal instead of synaptic or the USC..or probably Synaptic instead of USC.

Thanks for everyone's help.

---

### Post by linuxinstalledfromhdd on 2011-05-20
I was just like you years ago. I was fresh out of windows and alittle intimated by the command line. It's better than anything in the entire world of windows honestly.  You need to learn it eventually.  Take the plunge. :)

---

### Post by Dutch70 on 2011-05-20
> **SiGabse2984 said:**
> I guess I'm use to windows' style in which most users recommend that we don't install anything in the **main drive** but windows updates only..guess it's ok to keep the rest of my hard drives in NTFS and there seems to be no big issues about it.

I would be reinstalling ubuntu then..seems that it's sort of recommended that we install application here via terminal instead of synaptic or the USC..or probably Synaptic instead of USC.

Thanks for everyone's help.

I'm not sure what you mean by not installing anything to the main drive on windows, or what you're calling the main drive. Are you talking about the recovery partition? 
Regardless, you can't bring windows knowledge to Linux or it will slow down the learning process & leave you feeling frustrated. Just take your time.

No, the terminal is not the recommended over Software Center, it's just much easier for us to tell you how to do it in the terminal, plus if there is a problem, it tends to give you more info.

Most of the apps you need will be in Software Center, use it first, but if they're not in there, then look in synaptic. There are many more there. 

You really don't need to worry about learning the terminal at all right now. There are basically 2 times you should use it. 
1. When you're getting support from here or another website.
2. When you feel like playing around with it.

I'm going to say this again. You do not need to worry about learning the terminal right now. Just play around with & enjoy Ubuntu. The terminal is a great tool as "linuxinstalledfromhdd" said, but it's not something you have to use or learn right away. That's a serious misconception with Ubuntu & runs a lot of people off for the wrong reasons.

---

