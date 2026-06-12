---
title: "HOW DO I GET ext4 on jauntu jackalope 9.04"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by niva01 on 2009-03-28
How do I get ext 4 on ubuntu 9.04 ?

I just installed ubuntu 9.04 Beta on top of 8.10 through synaptic so I don't want to make a complete reinstall... 
Is it possible to change from ext3 to ext4 after the upgrade?

---

### Post by zvacet on 2009-03-29
I think it is still experimental,so there is no reason to do that at this time.

---

### Post by hyper_ch on 2009-03-29
I would not use ext4 for the time being.

---

### Post by ZarathustraDK on 2009-03-29
Ext4 has this bug where a sudden loss of power will bork the files which are currently being written to. That's pretty major considering it very likely could hose the system if such a thing happened while using a system process. Maybe even worse, you could loose your personal files if you kept them on ext4.

I'd love them to fix that bug, ext4 rocks in terms of speed. But for now it's better to stay with ext3 unless you like living dangerously.

---

### Post by bardioc39 on 2009-03-29
Aside from any concerns about losing data or borking my system when using EXT4, can anyone actually answer the OP's question? (EXT3 -> EXT4) I'm curious myself and willing to take the risk, as I'm on a test system anyway. (I do not want to do a fresh install either).

---

### Post by hyper_ch on 2009-03-29
> **bardioc39 said:**
> Aside from any concerns about losing data or borking my system when using EXT4, can anyone actually answer the OP's question?

Well, as the OP doesn't know how to migrate this tells me he has not the experience yet and doesn't know of the risks that switching to ext4 can do. So I rather see it my duty to warn him about it.

---

### Post by autocrosser on 2009-03-29
I've been using ext4 for 4 months now--I was one of the early adopters & I have only had 2 problems (both very early on)....If you take the proper steps (use a UPS on your system & do proper backups), you DON'T have problems..that being said---look at this thread: [http://ubuntuforums.org/showthread.php?t=1108452&highlight=ext4](http://ubuntuforums.org/showthread.php?t=1108452&highlight=ext4)  [http://ubuntuforums.org/showthread.php?t=1107027&highlight=ext4](http://ubuntuforums.org/showthread.php?t=1107027&highlight=ext4)  [http://ubuntuforums.org/showthread.php?t=1104822&highlight=ext4](http://ubuntuforums.org/showthread.php?t=1104822&highlight=ext4)  [http://ubuntuforums.org/showthread.php?t=1040199&highlight=ext4](http://ubuntuforums.org/showthread.php?t=1040199&highlight=ext4) [http://ubuntuforums.org/showthread.php?t=1092173&highlight=ext4](http://ubuntuforums.org/showthread.php?t=1092173&highlight=ext4) [http://ubuntuforums.org/showthread.php?t=1087225&highlight=ext4](http://ubuntuforums.org/showthread.php?t=1087225&highlight=ext4)  [http://ubuntuforums.org/showthread.php?t=965879&highlight=ext4](http://ubuntuforums.org/showthread.php?t=965879&highlight=ext4) (main thread)  & read the other information I posted...Like it or not, ext4 is the future--apps need to be re-written to parse to disc with delayed allocation in mind & users really should backup their data on a regular basis.

I converted one of my Jaunty installs around Alpha 2 & did a fresh install on the other one at Alpha3---the converted one is slightly slower that the fresh install--but both are much faster than my baseline Intrepid ext3 install--typical transfer is 2~3 times faster with ext4.

You might search this forum for ext4 also---there has been quite a bit of talk both pro & con about it---look thru all of it & after weighing the gain vs loss---make up your mind.

More info: to give you a feel for it---1 G folder with lots of little files transfer in my system--25/30MB/s---2G video file 35/45MB/s. That is from my user folder to my primary storage drive. All drives are SATA, 1 SATAI & 3 SATAII--I hold 1.75TB of drives in my system--2 Jaunty installs, 1 Fedora11 install & main storage are ext4---1 Intrepid install, 1 Elive gem install & secondary storage drive are ext3--the ext3 drives max out @ 25/30MB/s on video files.


Lastly--my bootchart running a very loaded Jaunty install & the Plymouth development bootload... note the disc thruput!!! (91MB/s)

---

### Post by Seventh Reign on 2009-03-29
I'm using ext4 on 3 of my Jaunty (Beta) systems.  I've had to use the PC's reset switch about 25 times in the past 3 days to reset one of them after the PC froze while emptying the Recycle Bin.   I havent noticed any loss of Data other than the files I was trying to delete were STILL there ..

Overall I'm Impressed.

---

### Post by 73ckn797 on 2009-03-29
I have just installed the Jaunty beta. I was only successful after formatting to ext3. There were several errors and I could not get the Nvidia drivers to activate. What I could do with the ext4 was revealing a noticeably faster system response. I just did not want to take the time to figure out all of the work arounds or fixes required. I have 8.10 running great on another drive and will not be dumping that very soon.

---

### Post by novafluxx on 2009-03-29
Have the problems with ext4 been resolved in the new kernel maybe? 2.6.29?

---

### Post by BGFG on 2009-03-29
> **novafluxx said:**
> Have the problems with ext4 been resolved in the new kernel maybe? 2.6.29?

Doesn't really have problems, current software doesn't optimize use of one of it's main features: 'Delayed Write'. That being said, in the -30 kernel i think, a patch will be included to 'fix' the 'data loss' problem. This will come at a slight performance loss.

Hopefully it won't last in the kernel too long and by 9.10 we will see GNU/FOSS apps maximizing the use of these new modern filesystems.

---

### Post by FuturePilot on 2009-03-29
The patches for the data loss issue has already been included in the Ubuntu kernel
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/154]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/154")

---

### Post by BGFG on 2009-03-29
I hope the patch doesn't last too long in the kernel. delayed write seems to preserve battery life, these patches do the opposite.

---

### Post by warped0ne on 2009-03-30
I tried installing 9.04 on my system 3 times using ext4, and once in a VirtualBox environ, every time I had the same problem.  The installation would finish and automatically reboot into a LiveCD environment.  After I took out the CD, I would get a GRUB error 15 with a blinking cursor and no response from anything except the power button on my tower.

Tried one last time with the same CD, same configuration, except I used ext3, and everything is up and running, no problems.

I'm currently on an older system

2.5GHz Pentium 4
2GB 400MHz DDR
60GB IDE 100 (mounted as '/')
80GB IDE 100 (mounted as '/home')
Nvidia GeForce FX5200

Are there hardware requirements for ext4? If so, would this system meet those requirements?

---

### Post by int on 2009-03-30
> **warped0ne said:**
> I tried installing 9.04 on my system 3 times using ext4, and once in a VirtualBox environ, every time I had the same problem.  The installation would finish and automatically reboot into a LiveCD environment.  After I took out the CD, I would get a GRUB error 15 with a blinking cursor and no response from anything except the power button on my tower.

Tried one last time with the same CD, same configuration, except I used ext3, and everything is up and running, no problems.

I'm currently on an older system

2.5GHz Pentium 4
2GB 400MHz DDR
60GB IDE 100 (mounted as '/')
80GB IDE 100 (mounted as '/home')
Nvidia GeForce FX5200

Are there hardware requirements for ext4? If so, would this system meet those requirements?

if you have the Ubuntu 9.04 Beta LiveCD, it should run fine.

---

### Post by amano on 2009-03-30
> **FuturePilot said:**
> The patches for the data loss issue has already been included in the Ubuntu kernel
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/154]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/317781/comments/154")

Yes. That looks like that could be the right patches (taken from 2.6.30?). I wonder that they are from Freburary though...

---

### Post by BGFG on 2009-03-30
> **warped0ne said:**
> I tried installing 9.04 on my system 3 times using ext4, and once in a VirtualBox environ, every time I had the same problem.  The installation would finish and automatically reboot into a LiveCD environment.  After I took out the CD, I would get a GRUB error 15 with a blinking cursor and no response from anything except the power button on my tower.

Tried one last time with the same CD, same configuration, except I used ext3, and everything is up and running, no problems.

I'm currently on an older system

2.5GHz Pentium 4
2GB 400MHz DDR
60GB IDE 100 (mounted as '/')
80GB IDE 100 (mounted as '/home')
Nvidia GeForce FX5200

Are there hardware requirements for ext4? If so, would this system meet those requirements?

I have a multi-drive setup also, and got the same 'errror 15' problem. The resolution for me was the 'Advanced options' button on the final page of the install. Ensure that you set grub to install on the same drive as '/'.
Nothing wrong with using ext4 as default. just put grub on the correct drive :)

---

### Post by moma on 2009-03-30
Hello,

A testimonial:
I have run Jaunty with EXT4 on a dedicated harddisk partition around two months time now. No errors, no failure. It's fast and 100% OK. I remember that EXT4 was an installation option during (manual) partitioning step. I have active GRUB/menu.lst on another, ext3 (/dev/sda9) partition.

So after installation I started grub and typed
$ sudo grub
grub> root (hd0,8 )
grub> setup (hd0)

This installs grub on MBR (hd0) (=/dev/sda).
I've also modified the active menu.lst [it's on (hd0,8 )/boot/grub/ ] and added entry for Jaunty.
----------

ps. check and test the latest [gscreendump...]("http://code.google.com/p/gscreendump/wiki/PicturesAndScreenshots") now.

---

### Post by darkstaar on 2009-03-30
> **niva01 said:**
> How do I get ext 4 on ubuntu 9.04 ?

This option is only available as a fresh install (not an upgrade) as the partitions will have to be reformatted as ext4.

Personally, I wouldn't reformat my /home partition as ext4 just yet unless I'm absolutely certain that I'll have no reason to go back to an earlier version of Linux (I'm not that certain). You might just save yourself a lot of work and/or grief by sticking with ext3 for that reason alone, at least for now.

Of course, if you have a lot of time and space to backup your current /home partition,..go for it.

You could choose to backup just your / partition for now but the speed benefits of
ext4 won't be very noticeable.

--Leisa

---

### Post by autocrosser on 2009-03-30
Good Info for everyone:  [http://www.linux-mag.com/cache/7271/1.html](http://www.linux-mag.com/cache/7271/1.html)

---

### Post by darkstaar on 2009-03-30
> **darkstaar said:**
> ...the partitions will have to be reformatted as ext4.

Oops! It appears that I may have been mistaken with that statement.

--Leisa

---

### Post by autocrosser on 2009-03-30
I forgive you------:popcorn:

---

### Post by 73ckn797 on 2009-03-31
To try and reformat without re-installation is about like pulling out the ground you stand on and expecting everything to stay in its place! You remove the foundation and nothing stands.):P

---

### Post by alphacrucis2 on 2009-03-31
> **73ckn797 said:**
> To try and reformat without re-installation is about like pulling out the ground you stand on and expecting everything to stay in its place! You remove the foundation and nothing stands.):P

I first reformatted my /home partition to ext4 using tune2fs. You just have to remember to efsck it afterwards. After a few days running with that I got brave and decided to convert / using the Jaunty Alpha6 live CD. It all worked no problem at all even though I half expected GRUB to blow up on me when I booted off the converted partition. There is a noticable performance improvement. Of course the machine I did this on is a sort of play machine, so I would recommend that anyone doing this has a back up of any important data (but that goes without saying whether or not you are trying anything risky).

---

